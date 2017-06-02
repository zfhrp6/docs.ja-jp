---
title: "Walkthrough: Querying Across Relationships (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 552abeb1-18f2-4e93-a9c6-ef7b2db30c32
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Walkthrough: Querying Across Relationships (C#)
このチュートリアルでは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の*関連付け*を使用してデータベース内の外部キー リレーションシップを表現する方法について説明します。  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 このチュートリアルは、Visual C\# 開発設定を使用して記述されています。  
  
## 必須コンポーネント  
 「[Walkthrough: Simple Object Model and Query \(C\#\)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md)」を終了している必要があります。  このチュートリアルは前のチュートリアルに基づいて作成されており、c:\\linqtest5 に northwnd.mdf ファイルがあることが前提です。  
  
## 概要  
 このチュートリアルは、主に次の 3 つの手順で構成されています。  
  
-   エンティティ クラスを追加して、Northwind サンプル データベース内の Orders テーブルを表します。  
  
-   `Customer` クラスに注釈を付けて、`Customer` クラスと `Order` クラス間のリレーションシップを強化します。  
  
-   クエリを作成および実行して、`Customer` クラスによる `Order` 情報の取得をテストします。  
  
## テーブル間のリレーションシップを指定する  
 `Customer` クラス定義の後に、次のコードから成る `Order` エンティティ クラス定義を作成します。これは、`Order.Customer` が外部キーとして `Customer.CustomerID` に関係することを示しています。  
  
#### Order エンティティ クラスを追加するには  
  
-   `Customer` クラスの後に次のコードを入力または貼り付けます。  
  
     [!code-csharp[DLinqWalk2CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#1)]  
  
## Customer クラスに注釈を付ける  
 ここでは、`Customer` クラスに注釈を付けて、`Order` クラスとのリレーションシップを指定します。  いずれかの方向のリレーションシップが定義されていればリンクを作成できるため、この注釈の追加は必ずしも必要ではありません。  しかし、この注釈を追加することで、どちらの方向でも簡単にオブジェクトを移動できます。  
  
#### Customer クラスに注釈を付けるには  
  
-   `Customer` クラスに次のコードを入力または貼り付けます。  
  
     [!code-csharp[DLinqWalk2CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#2)]  
  
## Customer\-Order リレーションシップ間のクエリを作成および実行する  
 `Customer` オブジェクトから `Order` オブジェクトに、またはその逆の順序で、直接アクセスできます。  Customer と Order の間に、明示的な*結合*は必要ありません。  
  
#### Customer オブジェクトを使用して Order オブジェクトにアクセスするには  
  
1.  `Main` メソッドに次のコードを入力または貼り付けることによって、メソッドを変更します。  
  
     [!code-csharp[DLinqWalk2CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#3)]  
  
2.  F5 キーを押して、アプリケーションをデバッグします。  
  
    > [!NOTE]
    >  `db.Log = Console.Out;` をコメント アウトすることによって、コンソール ウィンドウ内の SQL コードを除去できます。  
  
3.  コンソール ウィンドウで Enter キーを押して、デバッグを停止します。  
  
## データベースの厳密に型指定されたビューを作成する  
 データベースの厳密に型指定されたビューを使用すると、操作が非常に簡単になります。  <xref:System.Data.Linq.DataContext> オブジェクトを厳密に型指定することによって、<xref:System.Data.Linq.DataContext.GetTable%2A> を呼び出す必要がありません。  厳密に型指定された <xref:System.Data.Linq.DataContext> オブジェクトを使用する場合は、すべてのクエリで、厳密に型指定されたテーブルを使用できます。  
  
 次の手順では、データベース内の Customers テーブルに対応する厳密に型指定されたテーブルとして、`Customers` を作成します。  
  
#### DataContext オブジェクトを厳密に型指定するには  
  
1.  `Customer` クラス宣言の上に次のコードを追加します。  
  
     [!code-csharp[DLinqWalk2CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#4)]  
  
2.  `Main` メソッドを次のように変更し、厳密に型指定された <xref:System.Data.Linq.DataContext> を使用するようにします。  
  
     [!code-csharp[DLinqWalk2CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#5)]  
  
3.  F5 キーを押して、アプリケーションをデバッグします。  
  
     コンソール ウィンドウの出力は次のとおりです。  
  
     `ID=WHITC`  
  
4.  コンソール ウィンドウで Enter キーを押して、デバッグを停止します。  
  
## 次の手順  
 次のチュートリアル \([Walkthrough: Manipulating Data \(C\#\)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)\) では、データの操作方法について説明します。  そのチュートリアルを実行するのに、既に終了したこのシリーズの 2 つのチュートリアルを保存する必要はありません。  
  
## 参照  
 [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)