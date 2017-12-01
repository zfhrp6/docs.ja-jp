---
title: "チュートリアル: BatchBlock および BatchedJoinBlock を使用した効率の向上"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, improving efficiency
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc74b4acc5b29395c05e7c8302caefeb51718282
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a>チュートリアル: BatchBlock および BatchedJoinBlock を使用した効率の向上
TPL データ フロー ライブラリが提供する <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> および <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> クラスを使って、1 つ以上のソースからデータを受信してバッファーに格納し、それを 1 つのコレクションとして反映することができます。 このバッチ メカニズムは、1 つ以上のソースからデータを収集し、複数のデータ要素をバッチとして処理する場合に便利です。 例として、データフローを使ってレコードをデータベースに挿入するアプリケーションについて考えてみましょう。 この操作は、1 つずつ順番にではなく、複数の項目が同時に挿入される場合により効率的となります。 このドキュメントでは、<xref:System.Threading.Tasks.Dataflow.BatchBlock%601> クラスを使用して、そのようなデータベースの挿入操作を効率的に行う方法について説明します。 また、<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> クラスを使用して、プログラムでデータベースを読み取る場合に、その結果と発生する例外の両方をキャプチャする方法について説明します。  
  
> [!TIP]
>  TPL データ フローのライブラリ (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> 名前空間) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。 インストールする、<xref:System.Threading.Tasks.Dataflow>名前空間でプロジェクトを開く[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]、選択**NuGet パッケージの管理**プロジェクト メニューのおよびオンラインで検索から、`Microsoft.Tpl.Dataflow`パッケージ。  
  
## <a name="prerequisites"></a>必須コンポーネント  
  
1.  ブロックの結合」セクションを読み、[データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)このチュートリアルを開始する前に文書化します。  
  
2.  コンピューターに Northwind データベース (Northwind.sdf) のコピーがあることを確認します。 このファイルは通常、フォルダーにプログラム Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\です。  
  
    > [!IMPORTANT]
    >  Windows のバージョンによっては、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] が管理者以外のモードで実行されている場合には、Northwind.sdf に接続できません。 Northwind.sdf に接続するには、開始[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]または[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]のコマンド プロンプトで、**管理者として実行**モード。  
  
 このチュートリアルは、次のセクションで構成されています。  
  
-   [コンソール アプリケーションの作成](#creating)  
  
-   [Employee クラスの定義](#employeeClass)  
  
-   [従業員データベースの操作を定義します。](#operations)  
  
-   [バッファリングを使用しない従業員データをデータベースに追加します。](#nonBuffering)  
  
-   [バッファリングを使用して、従業員データをデータベースに追加するには](#buffering)  
  
-   [バッファリングされた結合を使用して、データベースから従業員データを読み取る](#bufferedJoin)  
  
-   [コード例全体](#complete)  
  
<a name="creating"></a>   
## <a name="creating-the-console-application"></a>コンソール アプリケーションの作成  
  
<a name="consoleApp"></a>   
1.  [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]、Visual c# または Visual Basic 作成**コンソール アプリケーション**プロジェクト。 このドキュメントでは、プロジェクトの名前を `DataflowBatchDatabase` とします。  
  
2.  プロジェクトで、System.Data.SqlServerCe.dll への参照と System.Threading.Tasks.Dataflow.dll への参照を追加します。  
  
3.  Form1.cs ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] の Form1.vb) が次の `using` (`Imports` の [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) ステートメントを含むことを確認します。  
  
     [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
     [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]  
  
4.  `Program` クラスに次のデータ メンバーを追加します。  
  
     [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
     [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]  
  
<a name="employeeClass"></a>   
## <a name="defining-the-employee-class"></a>Employee クラスの定義  
 `Program` クラスに `Employee` クラスを追加します。  
  
 [!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
 [!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]  
  
 `Employee` クラスには、`EmployeeID`、`LastName`、および `FirstName` という 3 つのプロパティが含まれています。 これらのプロパティは、Northwind データベースの `Employee ID` テーブルの `Last Name`、`First Name` および `Employees` の列に対応します。 このデモでは、`Employee` クラスは、プロパティに任意の値を持つ `Random` オブジェクトを作成する、`Employee` メソッドを定義します。  
  
<a name="operations"></a>   
## <a name="defining-employee-database-operations"></a>従業員データベースの操作の定義  
 `Program` クラスに `InsertEmployees`、`GetEmployeeCount` および `GetEmployeeID` メソッドを追加します。  
  
 [!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
 [!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]  
  
 `InsertEmployees` メソッドは、データベースに新しい従業員レコードを追加します。 `GetEmployeeCount` メソッドは `Employees` テーブルのエントリの数を取得します。 `GetEmployeeID` メソッドは、指定された名前を持つ最初の従業員 ID を取得します。 これらの各メソッドは、Northwind データベースへの接続文字列を受け取り、`System.Data.SqlServerCe` 名前空間の機能を使用して、データベースと通信します。  
  
<a name="nonBuffering"></a>   
## <a name="adding-employee-data-to-the-database-without-using-buffering"></a>バッファリングを使用しない従業員データのデータベースへの追加  
 `Program` クラスに `AddEmployees` および `PostRandomEmployees` メソッドを追加します。  
  
 [!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
 [!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]  
  
 `AddEmployees` メソッドは、データベースにデータ フローを使用して任意の従業員データを追加します。 それは、<xref:System.Threading.Tasks.Dataflow.ActionBlock%601> メソッドを呼び出す `InsertEmployees` オブジェクトを作成して、従業員のエントリをデータベースに追加します。 次に `AddEmployees` メソッドは、`PostRandomEmployees` メソッドを呼び出して、複数の `Employee` オブジェクトを <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> オブジェクトへポストします。 次に `AddEmployees` メソッドは、すべての挿入操作が終了するまで待機します。  
  
<a name="buffering"></a>   
## <a name="using-buffering-to-add-employee-data-to-the-database"></a>バッファリングを使用した従業員データのデータベースへの追加  
 `Program` クラスに `AddEmployeesBatched` メソッドを追加します。  
  
 [!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
 [!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]  
  
 このメソッドは `AddEmployees` に似ていますが、<xref:System.Threading.Tasks.Dataflow.BatchBlock%601> クラスを使用して複数の `Employee` オブジェクトをバッファリングしてから、それらのオブジェクトを <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> オブジェクトに送信する点が異なります。 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> クラスは複数の要素を 1 つのコレクションとして反映させるため、<xref:System.Threading.Tasks.Dataflow.ActionBlock%601> オブジェクトは `Employee` オブジェクトの配列として動作するように変更されます。 `AddEmployees` メソッドと同様に、`AddEmployeesBatched` は `PostRandomEmployees` メソッドを呼び出して複数の `Employee` オブジェクトをポストしますが、`AddEmployeesBatched` はこれらのオブジェクトを <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> オブジェクトにポストします。 `AddEmployeesBatched`メソッドは、すべての insert 操作を完了するのにも待機します。  
  
<a name="bufferedJoin"></a>   
## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a>バッファリングされた結合を使用した従業員データのデータベースからの読み込み  
 `Program` クラスに `GetRandomEmployees` メソッドを追加します。  
  
 [!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
 [!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]  
  
 このメソッドは任意の従業員の情報をコンソールに出力します。 それは複数の任意の `Employee` オブジェクトを作成し、`GetEmployeeID` メソッドを呼び出して、各オブジェクトの一意の識別子を取得します。 指定された姓名に一致する従業員がいない場合には `GetEmployeeID` メソッドは例外をスローするため、`GetRandomEmployees` メソッドは <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> クラスを使用して、`Employee` の呼び出しが成功した場合には `GetEmployeeID` オブジェクトを格納し、呼び出しが失敗した場合には <xref:System.Exception?displayProperty=nameWithType> オブジェクトを格納します。 この例では、<xref:System.Threading.Tasks.Dataflow.ActionBlock%601> オブジェクトは、<xref:System.Tuple%602> オブジェクトのリストと `Employee` オブジェクトのリストを持つ <xref:System.Exception> オブジェクトで動作します。 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> オブジェクトは、受け取った `Employee` および <xref:System.Exception> オブジェクトの数の合計がバッチのサイズと等しくなったときに、このデータを反映します。  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a>完全な例  
 完全なコード例を次に示します。 `Main` メソッドは、バッチされたデータベースの挿入の実行に必要な時間と、非バッチでのデータベースの挿入の実行時間を比較します。 また、バッファリングされた結合を使用した従業員データのデータベースから読み取りと、エラーの報告についても示します。  
  
 [!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
 [!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]  
  
## <a name="see-also"></a>関連項目  
 [データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
