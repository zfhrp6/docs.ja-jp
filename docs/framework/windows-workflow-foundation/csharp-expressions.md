---
title: "C# の式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29110be7-f4e3-407e-8dbe-78102eb21115
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fffceba415bbdfdb15647ab67b01031b99e48b2b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="c-expressions"></a>C# の式
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降では、[!INCLUDE[wf](../../../includes/wf-md.md)] で C# 式がサポートされています。 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] で作成された、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] を対象とする新しい C# ワークフロー プロジェクトでは C# 式が使用され、Visual Basic ワークフロー プロジェクトでは Visual Basic 式が使用されます。 Visual Basic 式を使用する既存の [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] ワークフロー プロジェクトは、プロジェクトの言語に関係なく [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] に移行することができ、サポートされています。 ここでは、[!INCLUDE[wf1](../../../includes/wf1-md.md)] での C# 式の概要について説明します。  
  
## <a name="using-c-expressions-in-workflows"></a>ワークフローでの C# 式の使用  
  
-   [ワークフロー デザイナーで c# 式の使用](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFDesigner)  
  
    -   [旧バージョンとの互換性](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#BackwardCompat)  
  
-   [コード ワークフローで c# 式の使用](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows)  
  
-   [XAML ワークフローで c# 式の使用](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#XamlWorkflows)  
  
    -   [コンパイルされた Xaml](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)  
  
    -   [Loose Xaml](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)  
  
-   [XAMLX ワークフロー サービスで c# 式の使用](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFServices)  
  
###  <a name="WFDesigner"></a>ワークフロー デザイナーで c# 式の使用  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降では、[!INCLUDE[wf](../../../includes/wf-md.md)] で C# 式がサポートされています。 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] で作成された、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] を対象とする C# ワークフロー プロジェクトでは C# 式が使用されるのに対し、Visual Basic ワークフロー プロジェクトでは Visual Basic 式が使用されます。 目的の c# の式を指定するラベルの付いたボックスに入力**c# 式を入力**です。 このラベルは、プロパティ ウィンドウ (デザイナーでアクティビティを選択した場合) またはワークフロー デザイナーのアクティビティに表示されます。 次の例では、2 つの `WriteLine` アクティビティが `Sequence` の中で `NoPersistScope` 内に含まれています。  
  
 ![自動的に作成された sequence アクティビティ](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")  
  
> [!NOTE]
>  C# 式は、[!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] のみでサポートされており、再ホストされたワークフロー デザイナーではサポートされていません。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]再ホストされたデザイナーでサポートされている新しい WF45 機能を参照してください[、再ホストされたワークフロー デザイナーで新しい Workflow Foundation 4.5 機能のサポート](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md)です。  
  
####  <a name="BackwardCompat"></a>旧バージョンとの互換性  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] に移行した既存の [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] C# ワークフロー プロジェクトの Visual Basic 式はサポートされています。 Visual Basic 式をワークフロー デザイナーで表示すると、既存の Visual Basic の式のテキストが置き換え**値が XAML で設定された**Visual Basic の式が有効な c# 構文でない限り、します。 Visual Basic 式が有効な C# 構文である場合は、式が表示されます。 Visual Basic 式を C# に更新するには、ワークフロー デザイナーでその式を編集して、対応する C# 式を指定します。 Visual Basic 式を C# に更新する必要はありませんが、ワークフロー デザイナーで式を更新すると、式は C# に変換され、Visual Basic に戻すことができなくなる場合があります。  
  
###  <a name="CodeWorkflows"></a>コード ワークフローで c# 式の使用  
 C# 式は、[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] コードベースのワークフローでサポートされていますが、ワークフローを呼び出す前に、<xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType> を使用して C# 式をコンパイルする必要があります。 ワークフローの作成者は、`CSharpValue` を使用して式の右辺値を表し、`CSharpReference` を使用して式の左辺値を表すことができます。 次の例では、`Assign` アクティビティに含まれる `WriteLine` アクティビティと `Sequence` アクティビティを使用してワークフローを作成します。 `CSharpReference` は `To` の `Assign` 引数として指定され、式の左辺値を表します。 `CSharpValue` は `Value` の `Assign` 引数、および `Text` の `WriteLine` 引数として指定され、2 つの式の右辺値を表します。  
  
```csharp  
Variable<int> n = new Variable<int>  
{  
    Name = "n"  
};  
  
Activity wf = new Sequence  
{  
    Variables = { n },  
    Activities =  
    {  
        new Assign<int>  
        {  
            To = new CSharpReference<int>("n"),  
            Value = new CSharpValue<int>("new Random().Next(1, 101)")  
        },  
        new WriteLine  
        {  
            Text = new CSharpValue<string>("\"The number is \" + n")  
        }  
    }  
};  
  
CompileExpressions(wf);  
  
WorkflowInvoker.Invoke(wf);  
```  
  
 ワークフローが作成されると、`CompileExpressions` ヘルパー メソッドを呼び出して C# 式がコンパイルされ、ワークフローが呼び出されます。 次の例は、`CompileExpressions` メソッドです。  
  
```csharp  
static void CompileExpressions(Activity activity)  
{  
    // activityName is the Namespace.Type of the activity that contains the  
    // C# expressions.  
    string activityName = activity.GetType().ToString();  
  
    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name  
    // to represent the new type that represents the compiled expressions.  
    // Take everything after the last . for the type name.  
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";  
    // Take everything before the last . for the namespace.  
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());  
  
    // Create a TextExpressionCompilerSettings.  
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings  
    {  
        Activity = activity,  
        Language = "C#",  
        ActivityName = activityType,  
        ActivityNamespace = activityNamespace,  
        RootNamespace = null,  
        GenerateAsPartialClass = false,  
        AlwaysGenerateSource = true,  
        ForImplementation = false  
    };  
  
    // Compile the C# expression.  
    TextExpressionCompilerResults results =  
        new TextExpressionCompiler(settings).Compile();  
  
    // Any compilation errors are contained in the CompilerMessages.  
    if (results.HasErrors)  
    {  
        throw new Exception("Compilation failed.");  
    }  
  
    // Create an instance of the new compiled expression type.  
    ICompiledExpressionRoot compiledExpressionRoot =  
        Activator.CreateInstance(results.ResultType,  
            new object[] { activity }) as ICompiledExpressionRoot;  
  
    // Attach it to the activity.  
    CompiledExpressionInvoker.SetCompiledExpressionRoot(  
        activity, compiledExpressionRoot);  
}  
```  
  
> [!NOTE]
>  C# 式がコンパイルされていない場合、<xref:System.NotSupportedException>には、次のようなメッセージ、ワークフローが呼び出される場合にスローされます。 `Expression Activity type 'CSharpValue`1' を実行するにはコンパイルを必要とします。  ワークフローがコンパイルされていることを確認してください '。  
  
 カスタムのコードベースのワークフローで `DynamicActivity` を使用する場合は、次のコード例に示すように、`CompileExpressions` メソッドに変更を加える必要があります。  
  
```csharp  
static void CompileExpressions(DynamicActivity dynamicActivity)  
{  
    // activityName is the Namespace.Type of the activity that contains the  
    // C# expressions. For Dynamic Activities this can be retrieved using the  
    // name property , which must be in the form Namespace.Type.  
    string activityName = dynamicActivity.Name;  
  
    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name  
    // to represent the new type that represents the compiled expressions.  
    // Take everything after the last . for the type name.  
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";  
    // Take everything before the last . for the namespace.  
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());  
  
    // Create a TextExpressionCompilerSettings.  
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings  
    {  
        Activity = dynamicActivity,  
        Language = "C#",  
        ActivityName = activityType,  
        ActivityNamespace = activityNamespace,  
        RootNamespace = null,  
        GenerateAsPartialClass = false,  
        AlwaysGenerateSource = true,  
        ForImplementation = true  
    };  
  
    // Compile the C# expression.  
    TextExpressionCompilerResults results =  
        new TextExpressionCompiler(settings).Compile();  
  
    // Any compilation errors are contained in the CompilerMessages.  
    if (results.HasErrors)  
    {  
        throw new Exception("Compilation failed.");  
    }  
  
    // Create an instance of the new compiled expression type.  
    ICompiledExpressionRoot compiledExpressionRoot =  
        Activator.CreateInstance(results.ResultType,  
            new object[] { dynamicActivity }) as ICompiledExpressionRoot;  
  
    // Attach it to the activity.  
    CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation(  
        dynamicActivity, compiledExpressionRoot);  
}  
```  
  
 動的アクティビティで C# 式をコンパイルする `CompileExpressions` オーバーロードには、いくつかの相違点があります。  
  
-   `CompileExpressions` のパラメーターが `DynamicActivity` です。  
  
-   型名および名前空間の取得に `DynamicActivity.Name` プロパティが使用されます。  
  
-   `TextExpressionCompilerSettings.ForImplementation` が `true` に設定されます。  
  
-   `CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` の代わりに `CompiledExpressionInvoker.SetCompiledExpressionRoot` が呼び出されます。  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]コード内の式の操作を参照してください[オーサリング ワークフロー、アクティビティ、および命令型コードを使用して式](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)です。  
  
###  <a name="XamlWorkflows"></a>XAML ワークフローで c# 式の使用  
 C# 式は XAML ワークフローでサポートされています。 コンパイルされた XAML ワークフローは型にコンパイルされ、Loose XAML ワークフローはランタイムによって読み込まれ、ワークフローの実行時にアクティビティ ツリーにコンパイルされます。  
  
-   [コンパイルされた Xaml](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)  
  
-   [Loose Xaml](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)  
  
####  <a name="CompiledXaml"></a>コンパイルされた Xaml  
 C# 式は、コンパイルされた XAML ワークフローでサポートされており、[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] を対象とする C# ワークフロー プロジェクトの一部として型にコンパイルされます。 コンパイルされた XAML は、[!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] でワークフローを作成する際の既定の種類です。また、[!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] で作成された、[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] を対象とする C# ワークフロー プロジェクトでは C# 式が使用されます。  
  
####  <a name="LooseXaml"></a>Loose Xaml  
 C# 式は Loose XAML ワークフローでがサポートされています。 Loose XAML ワークフローを読み込んで呼び出すワークフロー ホスト プログラムは、[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] を対象としている必要があります。また、<xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> は `true` (既定値は `false`) に設定する必要がります。 <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> を `true` に設定するには、<xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> プロパティが <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> に設定されている `true` インスタンスを作成し、そのインスタンスを <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType> へパラメーターとして渡します。 場合`CompileExpressions`に設定されていない`true`、<xref:System.NotSupportedException>には、次のようなメッセージがスローされます。 `Expression Activity type 'CSharpValue`1' を実行するにはコンパイルを必要とします。  ワークフローがコンパイルされていることを確認してください '。  
  
```csharp  
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings  
{  
    CompileExpressions = true  
};  
  
DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]XAML ワークフローと連携するを参照してください[をシリアル化するワークフローとアクティビティの XAML との間](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md)です。  
  
###  <a name="WFServices"></a>XAMLX ワークフロー サービスで c# 式の使用  
 C# 式は XAMLX ワークフロー サービスでがサポートされています。 ワークフロー サービスが IIS または WAS でホストされている場合、追加の手順は必要ありません。ただし、XAML ワークフロー サービスが自己ホスト型サービスの場合は、C# 式をコンパイルする必要があります。 自己ホスト XAMLX ワークフロー サービスで c# 式をコンパイルするには、最初に XAMLX ファイルを読み込む、 `WorkflowService`、しに渡す、`Body`の`WorkflowService`を`CompileExpressions`前で説明した方法[c# を使用します。コード ワークフローで式](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows)セクションです。 次の例では、XAMLX ワークフロー サービスが読み込まれ、C# 式がコンパイルされた後、ワークフロー サービスが開かれて要求を待機します。  
  
```csharp  
// Load the XAMLX workflow service.  
WorkflowService workflow1 =  
    (WorkflowService)XamlServices.Load(xamlxPath);  
  
// Compile the C# expressions in the workflow by passing the Body to CompileExpressions.  
CompileExpressions(workflow1.Body);  
  
// Initialize the WorkflowServiceHost.  
var host = new WorkflowServiceHost(workflow1, new Uri("http://localhost:8293/Service1.xamlx"));  
  
// Enable Metadata publishing/  
ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
smb.HttpGetEnabled = true;  
smb.MetadataExporter.PolicyVersion = PolicyVersion.Policy15;  
host.Description.Behaviors.Add(smb);  
  
// Open the WorkflowServiceHost and wait for requests.  
host.Open();  
Console.WriteLine("Press enter to quit");  
Console.ReadLine();  
```  
  
 C# 式がコンパイルされないと、`Open` の処理は成功しますが、ワークフローは呼び出し時に失敗します。 次`CompileExpressions`メソッドは、前のメソッドと同じ[コード ワークフローで c# を使用して式](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows)セクションです。  
  
```csharp  
static void CompileExpressions(Activity activity)  
{  
    // activityName is the Namespace.Type of the activity that contains the  
    // C# expressions.  
    string activityName = activity.GetType().ToString();  
  
    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name  
    // to represent the new type that represents the compiled expressions.  
    // Take everything after the last . for the type name.  
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";  
    // Take everything before the last . for the namespace.  
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());  
  
    // Create a TextExpressionCompilerSettings.  
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings  
    {  
        Activity = activity,  
        Language = "C#",  
        ActivityName = activityType,  
        ActivityNamespace = activityNamespace,  
        RootNamespace = null,  
        GenerateAsPartialClass = false,  
        AlwaysGenerateSource = true,  
        ForImplementation = false  
    };  
  
    // Compile the C# expression.  
    TextExpressionCompilerResults results =  
        new TextExpressionCompiler(settings).Compile();  
  
    // Any compilation errors are contained in the CompilerMessages.  
    if (results.HasErrors)  
    {  
        throw new Exception("Compilation failed.");  
    }  
  
    // Create an instance of the new compiled expression type.  
    ICompiledExpressionRoot compiledExpressionRoot =  
        Activator.CreateInstance(results.ResultType,  
            new object[] { activity }) as ICompiledExpressionRoot;  
  
    // Attach it to the activity.  
    CompiledExpressionInvoker.SetCompiledExpressionRoot(  
        activity, compiledExpressionRoot);  
}  
```
