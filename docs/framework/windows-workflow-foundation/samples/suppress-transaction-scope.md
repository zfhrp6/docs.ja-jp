---
title: トランザクション スコープの抑制
ms.date: 03/30/2017
ms.assetid: 49fb6dd4-30d4-4067-925c-c5de44c8c740
ms.openlocfilehash: b38d168e7da4510b75ebeda7f4984c26fb68898d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518461"
---
# <a name="suppress-transaction-scope"></a>トランザクション スコープの抑制
このサンプルでは、アンビエント ランタイム トランザクションが存在する場合はそのトランザクションを抑制するカスタム `SuppressTransactionScope` アクティビティを作成する方法を示します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\SuppressTransactionScope`  
  
## <a name="sample-details"></a>サンプルの詳細  
 このカスタム アクティビティを使用すると、トランザクション フローが特定のシナリオに適さない場合に、別のサービスにトランザクションがフローされないようにすることができます。 ワークフロー ランタイムには <xref:System.Activities.NativeActivity> クラスのアンビエント トランザクションを抑制するためのサポートが組み込まれていますが、そのサポートを使用するには、このサンプルで示すようなカスタム <xref:System.Activities.NativeActivity> アクティビティを作成する必要があります。  
  
 このシナリオは、3 つの部分で構成されています。 まず、<xref:System.Activities.Statements.TransactionScope> によって、アンビエントになるランタイム トランザクションが作成されます。 これは、トランザクションのローカル識別子と分散識別子を出力するカスタム アクティビティによって検証されます。 その後、トランザクションがリモート サービスにフローされてから、2 番目の部分が始まります。 2 番目の部分では、ワークフローが `SuppressTransactionScope` に移り、トランザクション識別子を出力してトランザクションをフローさせるプロセスがもう一度繰り返されます。 ただし、カスタム アクティビティでアンビエント トランザクションを探さないため、サービスにフローされるメッセージにはトランザクションが含まれません。 その結果、サービスによってトランザクションが作成され、クライアントとサービスで出力される分散 ID が一致しなくなります。 最後の部分は、`SuppressTransactionScope` が終了した後の部分です。分散識別子が最初のメッセージの識別子と一致する別のメッセージがサービスにフローされ、そのメッセージによる検証でランタイム トランザクションがもう一度アンビエントになります。  
  
 アクティビティ自体は、子アクティビティをスケジュールして実行プロパティを追加する必要があるため、<xref:System.Activities.NativeActivity> から派生します。 `SuppressTransactionScope` には、<xref:System.Activities.Variable> 型の <xref:System.Activities.RuntimeTransactionHandle> が含まれます。ハンドルを初期化する必要があるため、<xref:System.Activities.RuntimeTransactionHandle> 型のインスタンス フィールドではなく、この変数を使用する必要があります。 `Variable<RuntimeTransactionHandle>` は内部でのみ使用されるため、実装変数としてアクティビティのメタデータに追加されます。  
  
 アクティビティを実行すると、まず本体が指定されているかどうかがチェックされ、指定されていれば `SuppressTransaction` に <xref:System.Activities.RuntimeTransactionHandle> プロパティが設定されます。 このプロパティは、設定されると実行プロパティに追加され、アンビエントになります。 つまり、`SuppressTransactionScope` のすべての子アクティビティがこのプロパティを参照できるようになります。これにより、ランタイム トランザクションの抑制が適用され、入れ子になった <xref:System.Activities.Statements.TransactionScope> で例外がスローされます。 実行プロパティにハンドルが追加されると、本体の実行がスケジュールされます。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で SuppressTransactionScope.sln ソリューションを開きます。  
  
2.  ソリューションをビルドするには、ctrl キーと shift キーを押しながら B キーを押してまたは選択**ソリューションのビルド**から、**ビルド**メニュー。  
  
3.  ビルドが成功した後、ソリューションを右クリックし  **スタートアップ プロジェクトの**します。 ダイアログ ボックスで、次のように選択します。**マルチ スタートアップ プロジェクト**両方のプロジェクトのアクションを確認してください**開始**です。  
  
4.  F5 キーを押すか、選択**デバッグの開始**から、**デバッグ**メニュー。 または、ctrl キーを押しながら f5 キーを押してまたは選択**デバッグなしで開始**から、**デバッグ**] メニューの [デバッグなしで実行します。  
  
    > [!NOTE]
    >  クライアントを起動する前に、サーバーを起動しておく必要があります。 サービスをホストするコンソール ウィンドウの出力で、起動された時間が示されます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\SuppressTransactionScope`