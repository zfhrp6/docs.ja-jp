---
title: "InvokePowerShell アクティビティの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 956251a0-31ca-4183-bf76-d277c08585df
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b3ef8b539e490911e5454fe87db483508cc8a5d8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="using-the-invokepowershell-activity"></a>InvokePowerShell アクティビティの使用
InvokePowerShell サンプルでは、`InvokePowerShell` アクティビティを使用して Windows PowerShell コマンドを呼び出す方法を示します。  
  
## <a name="demonstrates"></a>使用例  
  
-   Windows PowerShell コマンドの簡便さと革新性。  
  
-   Windows PowerShell の出力パイプラインから値を取得してワークフロー変数に格納する。  
  
-   実行するコマンドのための入力パイプラインとして Windows PowerShell にデータを渡す。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`  
  
## <a name="discussion"></a>説明  
 このサンプルには次の 3 つのプロジェクトが含まれています。  
  
|プロジェクト名|説明|メイン ファイル|  
|------------------|-----------------|----------------|  
|CodedClient|PowerShell アクティビティを使用するサンプル クライアント アプリケーション。|-   **Program.cs**: InvokePowerShell アクティビティを呼び出すシーケンス ベースのワークフローをプログラムで作成します。|  
|DesignerClient|`InvokePowerShell` カスタム アクティビティや他のさまざまなカスタム アクティビティを含むカスタム アクティビティのセットと、それらを使用するワークフロー。|<ul><li>アクティビティ:<br /><br /> <ul><li>**PrintCollection.cs**: コンソールをコレクション内のすべての項目を出力するヘルパー アクティビティ。</li><li>**ReadLine.cs**: コンソールからの入力を読み取るのためのヘルパー アクティビティ。</li></ul></li><li>ファイル システム:<br /><br /> <ul><li>**Copy.xaml**: ファイルをコピーするアクティビティ。</li><li>**CreateFile.xaml**: ファイルを作成するアクティビティ。</li><li>**DeleteFile.xaml**: ファイルを削除するアクティビティ。</li><li>**MakeDir.xaml**: ディレクトリを作成するアクティビティ。</li><li>**Move.xaml**: ファイルを移動するアクティビティ。</li><li>**ReadFile.xaml**: ファイルを読み取り、その内容を返すアクティビティ。</li><li>**TestPath.xaml**: パスの存在をテストするアクティビティ。</li></ul></li><li>プロセス:<br /><br /> <ul><li>**GetProcess.xaml**: 実行中のプロセス一覧を取得するアクティビティ。</li><li>**StopProcess.xaml**: 特定のプロセスを停止するアクティビティ。</li></ul></li><li>**Program.cs**: Sequence1 ワークフローを呼び出します。</li><li>**Sequence1.xaml**: シーケンス ベースのワークフローです。</li></ul>|  
|PowerShell|`InvokePowerShell` アクティビティと、それに関連付けられたデザイナー。|アクティビティのファイル<br /><br /> -   **ExecutePowerShell.cs**: アクティビティのメインの実行ロジック。<br />-   **InvokePowerShell.cs**: ジェネリック (値を返す) バージョンと非ジェネリック (値) のバージョンを含むメインの実行ロジックのラッパー。 これは、アクティビティのパブリック インターフェイスです。<br />-   **NoPersistZone.cs**: このアクティビティでは、すべての子アクティビティがの永続化します。 このクラスは、`InvokePowerShell` アクティビティの実装の中で、アクティビティが実行の途中で永続化されるのを防ぐために使用されます。<br /><br /> デザイナーのファイル:<br /><br /> 1.**ArgumentDictionaryEditor.cs**: ユーザーがの引数を編集できる Windows ダイアログ、`InvokePowerShell`アクティビティ。<br />2.**GenericInvokePowerShellDesigner.xaml**と**GenericInvokePowerShellDesigner.xaml.cs**: ジェネリックの外観を定義`InvokePowerShell`でアクティビティ[!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]です。<br />3.**InvokePowerShellDesigner.xaml**と**InvokePowerShellDesigner.cs**: 非ジェネリックの外観を定義`InvokePowerShell`でアクティビティ[!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]です。|  
  
 PowerShell アクティビティの使用方法を把握しているとその内部機能を理解しやすくなるため、クライアント プロジェクトから先に説明します。  
  
## <a name="using-this-sample"></a>このサンプルの使用  
 以降では、このサンプルの 3 つのプロジェクトの使用方法について説明します。  
  
### <a name="using-the-coded-client-project"></a>CodedClient プロジェクトの使用  
 このサンプル クライアントは、`InvokePowerShell` アクティビティのさまざまな使用方法の例を含むシーケンス アクティビティをプログラムで作成します。 最初の呼び出しでは、メモ帳を起動します。  
  
```  
new InvokePowerShell()  
{  
    CommandText = "notepad"  
},  
```  
  
 2 番目の呼び出しでは、ローカル コンピューターで実行されているプロセスのリストを取得します。  
  
```  
new InvokePowerShell<Process>()  
{  
    CommandText = "Get-Process",  
    Output = processes1,  
},  
```  
  
 `Output` は、コマンドの出力を格納するための変数です。  
  
 次の呼び出しは、PowerShell 呼び出しの個々の出力の後処理のステップを実行する方法を示します。 `InitializationAction` は、各プロセスの文字列形式を出力する関数に設定されます。 それらの文字列のコレクションは、`Output` アクティビティによって `InvokePowerShell<string>` 変数で返されます。  
  
 その後に続く一連の `InvokePowerShell` の呼び出しは、アクティビティにデータを渡して出力とエラーを取得する方法を示しています。  
  
### <a name="using-the-designer-client-project"></a>DesignerClient プロジェクトの使用  
 DesignerClient プロジェクトは一連のカスタム アクティビティで構成されていますが、それらのほぼすべてに `InvokePowerShell` アクティビティが含まれています。 ほとんどのアクティビティは、非ジェネリック バージョンの `InvokePowerShell` アクティビティを呼び出します。したがって、戻り値を受け取りません。 ジェネリック バージョンの `InvokePowerShell` アクティビティを使用するその他のアクティビティは、`InitializationAction` 引数を使用して結果の後処理を行います。  
  
## <a name="using-the-powershell-project"></a>PowerShell プロジェクトの使用  
 アクティビティの主要なアクションは `ExecutePowerShell` クラスで実行されます。 PowerShell コマンドの実行によってメインのワークフロー スレッドがブロックされないようにする必要があるため、アクティビティは、<xref:System.Activities.AsyncCodeActivity> クラスを継承して非同期アクティビティとして作成されています。  
  
 ワークフロー ランタイムによって <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> メソッドが呼び出されると、アクティビティの実行が開始されます。 このメソッドは、まず最初に、PowerShell API を呼び出して PowerShell パイプラインを作成します。  
  
```  
runspace = RunspaceFactory.CreateRunspace();  
runspace.Open();  
pipeline = runspace.CreatePipeline();  
```  
  
 次に、PowerShell コマンドを作成してパラメーターと変数を設定します。  
  
```  
Command cmd = new Command(this.CommandText, this.IsScript);   
// loop over parameters and run: cmd.Parameters.Add(...)  
// loop over variables and run: runspace.SessionStateProxy.SetVariable(...)  
pipeline.Commands.Add(cmd);  
```  
  
 この時点で、パイプ入力された入力がパイプラインにも送信されます。 最後に、パイプラインが `PipelineInvokerAsyncResult` オブジェクトでラップされて返されます。 `PipelineInvokerAsyncResult` オブジェクトは、リスナーを登録してパイプラインを呼び出します。  
  
```  
pipeline.InvokeAsync();  
```  
  
 実行が終了すると、出力とエラーが同じ `PipelineInvokerAsyncResult` オブジェクトに格納され、最初に <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> に渡されたコールバック メソッドが呼び出されてワークフロー ランタイムに制御が返されます。  
  
 メソッドの実行の最後に、ワークフロー ランタイムがアクティビティの <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> メソッドを呼び出します。  
  
 `InvokePowerShell` クラスは `ExecutePowerShellCommand` クラスをラップして、ジェネリック バージョンと非ジェネリック バージョンの 2 つのバージョンのアクティビティを作成します。 非ジェネリック バージョンは PowerShell の実行の出力をそのまま返しますが、ジェネリック バージョンは個々の結果をジェネリック型に変換します。  
  
 ジェネリック バージョンのアクティビティは、`ExecutePowerShellCommand` を呼び出してその結果の後処理を行うシーケンシャル ワークフローとして実装されています。 後処理のステップでは、結果のコレクションの各要素に対して、`InitializationAction` が設定されている場合にはそれが呼び出され、 設定されていない場合には単純なキャストが行われます。  
  
```  
new ForEach<PSObject>  
{  
    Values = psObjects,  
    Body = new ActivityAction<PSObject>  
    {  
        Argument = psObject,  
        Handler = new Sequence  
        {  
            Activities =  
            {  
                new If  
                {  
                    Condition = // Is InitializationAction set?  
                    Then = new InvokeFunc<PSObject, TResult>  
                    {  
                        Argument = psObject,  
                        Result = outputObject,  
                        Func = this.InitializationAction  
                    },  
                    Else = new Assign<TResult>  
                    {  
                        To = outputObject,  
                        Value = new InArgument<TResult>(ctx => (TResult) psObject.Get(ctx).BaseObject),  
                    }  
                },  
                new AddToCollection<TResult>  
                {  
                    Collection = outputObjects,  
                    Item = outputObject  
                },  
            }  
        }  
    }  
},  
```  
  
 2 つの `InvokePowerShell` アクティビティ (ジェネリックと非ジェネリック) のそれぞれにデザイナーが用意されています。 InvokePowerShellDesigner.xaml とその関連 .cs ファイルは、非ジェネリック バージョンの [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] アクティビティの`InvokePowerShell`での外観を定義します。 InvokePowerShellDesigner.xaml では、<xref:System.Windows.Controls.DockPanel> を使用してグラフィカル インターフェイスを表しています。  
  
```  
<DockPanel x:Uid="DockPanel_1" LastChildFill="True">  
        <TextBlock x:Uid="TextBlock_1" Text="CommandText" />  
        <TextBox x:Uid="TextBox_1" Text="{Binding Path=ModelItem.CommandText, Mode=TwoWay}"  
                 TextWrapping="WrapWithOverflow"  AcceptsReturn="True" MinLines="4" MaxLines="4"  
                 Background="{x:Null}" Margin="3" />  
    </DockPanel>  
```  
  
 テキスト ボックスの `Text` プロパティが双方向のバインドになっているため、アクティビティの `CommandText` プロパティの値がデザイナーに入力された値と同じになります。  
  
 GenericInvokePowerShellDesigner.xaml とその関連 .cs ファイルは、ジェネリック `InvokePowerShell` アクティビティのグラフィカル インターフェイスを定義します。 このデザイナーは、`InitializationAction` を設定できるようになっているため、非ジェネリック バージョンのデザイナーに比べてやや複雑です。 ここでのポイントは、<xref:System.Activities.Presentation.WorkflowItemPresenter> を使用して、`InvokePowerShell` のデザイナー画面に子アクティビティをドラッグ アンド ドロップできるようにしていることです。  
  
```  
<sap:WorkflowItemPresenter x:Uid="sap:WorkflowItemPresenter_1" Margin="0,10,0,10"  
    HintText="Drop Activities Here"  
    AllowedItemType="{x:Type sa:Activity}"  
    Item="{Binding Path=ModelItem.InitializationAction.Handler, Mode=TwoWay}"  
    Grid.Row="1" Grid.Column="1" />  
```  
  
 デザイナーでカスタマイズできるのは、デザイン キャンバスでのアクティビティの外観を定義する .xaml ファイルだけではありません。 アクティビティのパラメーターを表示するために使用されるダイアログ ボックスもカスタマイズできます。 これらのパラメーターや PowerShell 変数は、PowerShell コマンドの動作に影響します。 アクティビティとして公開<!--zz <xref:System.Collections.Generic.Dictionary%601>-->`System.Collections.Generic.Dictionary`型です。 これらの型を編集できるダイアログ ボックスは、ArgumentDictionaryEditor.cs、PropertyEditorResources.xaml、および PropertyEditorResources.cs で定義されています。  
  
## <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
 このサンプルを実行するには Windows PowerShell をインストールする必要があります。 この場所から Windows PowerShell をインストールすることができます: [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=150383)です。  
  
#### <a name="to-run-the-coded-client"></a>コード クライアントを実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して PowerShell.sln を開きます。  
  
2.  ソリューションを右クリックしてビルドします。  
  
3.  右クリックし、 **CodedClient**プロジェクトし、選択**スタートアップ プロジェクトとして設定**です。  
  
4.  Ctrl キーを押しながら F5 キーを押してアプリケーションを実行します。  
  
#### <a name="to-run-the-designer-client"></a>デザイナー クライアントを実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して PowerShell.sln を開きます。  
  
2.  ソリューションを右クリックしてビルドします。  
  
3.  右クリックし、 **DesignerClient**プロジェクトし、選択**スタートアップ プロジェクトとして設定**です。  
  
4.  Ctrl キーを押しながら F5 キーを押してアプリケーションを実行します。  
  
## <a name="known-issues"></a>既知の問題  
  
1.  `InvokePowerShell` アクティビティのアセンブリやプロジェクトを別のプロジェクトから参照してビルド エラーが発生した場合は、必要に応じて、新しいプロジェクトの .csproj ファイル (`<SpecificVersion>True</SpecificVersion>` を参照している行の下) に `InvokePowerShell` 要素を手動で追加してください。  
  
2.  追加するとすぐに Visual Studio で次のエラー メッセージが表示される Windows PowerShell がインストールされていない場合、`InvokePowerShell`アクティビティをワークフローに。`Workflow Designer encountered problems with your document. Could not load file or assembly ‘System.Management.Automation’ ... or one of its dependencies. The system cannot find the file specified.`  
  
3.  Windows PowerShell 2.0 では、プログラムで `$input.MoveNext()` を呼び出すと呼び出しが失敗します。そのため、`$input.MoveNext()` を使用するスクリプトで予想外のエラーと結果が生成されます。 この問題を回避するには、配列を反復処理するときに、`foreach` を呼び出す代わりに PowerShell の動詞 `MoveNext()` を使用することを検討してください。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`