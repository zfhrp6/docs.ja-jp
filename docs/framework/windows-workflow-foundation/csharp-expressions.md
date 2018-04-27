---
title: C# の式
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29110be7-f4e3-407e-8dbe-78102eb21115
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ea613d21cf7c8064938b94df3826e40caeecf3c3
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="c-expressions"></a><span data-ttu-id="325b7-102">C# の式</span><span class="sxs-lookup"><span data-stu-id="325b7-102">C# Expressions</span></span>
<span data-ttu-id="325b7-103">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降では、[!INCLUDE[wf](../../../includes/wf-md.md)] で C# 式がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="325b7-103">Starting with [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# expressions are supported in [!INCLUDE[wf](../../../includes/wf-md.md)].</span></span> <span data-ttu-id="325b7-104">[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] で作成された、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] を対象とする新しい C# ワークフロー プロジェクトでは C# 式が使用され、Visual Basic ワークフロー プロジェクトでは Visual Basic 式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="325b7-104">New C# workflow projects created in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] that target [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] use C# expressions, and Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="325b7-105">Visual Basic 式を使用する既存の [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] ワークフロー プロジェクトは、プロジェクトの言語に関係なく [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] に移行することができ、サポートされています。</span><span class="sxs-lookup"><span data-stu-id="325b7-105">Existing [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] workflow projects that use Visual Basic expressions can be migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] regardless of the project language and are supported.</span></span> <span data-ttu-id="325b7-106">ここでは、[!INCLUDE[wf1](../../../includes/wf1-md.md)] での C# 式の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="325b7-106">This topic provides an overview of C# expressions in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span>  
  
## <a name="using-c-expressions-in-workflows"></a><span data-ttu-id="325b7-107">ワークフローでの C# 式の使用</span><span class="sxs-lookup"><span data-stu-id="325b7-107">Using C# expressions in workflows</span></span>  
  
-   [<span data-ttu-id="325b7-108">ワークフロー デザイナーで c# 式の使用</span><span class="sxs-lookup"><span data-stu-id="325b7-108">Using C# expressions in the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFDesigner)  
  
    -   [<span data-ttu-id="325b7-109">旧バージョンとの互換性</span><span class="sxs-lookup"><span data-stu-id="325b7-109">Backwards compatibility</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#BackwardCompat)  
  
-   [<span data-ttu-id="325b7-110">コード ワークフローで c# 式の使用</span><span class="sxs-lookup"><span data-stu-id="325b7-110">Using C# expressions in code workflows</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows)  
  
-   [<span data-ttu-id="325b7-111">XAML ワークフローで c# 式の使用</span><span class="sxs-lookup"><span data-stu-id="325b7-111">Using C# expressions in XAML workflows</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#XamlWorkflows)  
  
    -   [<span data-ttu-id="325b7-112">コンパイルされた Xaml</span><span class="sxs-lookup"><span data-stu-id="325b7-112">Compiled Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)  
  
    -   [<span data-ttu-id="325b7-113">Loose Xaml</span><span class="sxs-lookup"><span data-stu-id="325b7-113">Loose Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)  
  
-   [<span data-ttu-id="325b7-114">XAMLX ワークフロー サービスで c# 式の使用</span><span class="sxs-lookup"><span data-stu-id="325b7-114">Using C# expressions in XAMLX workflow services</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFServices)  
  
###  <a name="WFDesigner"></a> <span data-ttu-id="325b7-115">ワークフロー デザイナーで c# 式の使用</span><span class="sxs-lookup"><span data-stu-id="325b7-115">Using C# expressions in the Workflow Designer</span></span>  
 <span data-ttu-id="325b7-116">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降では、[!INCLUDE[wf](../../../includes/wf-md.md)] で C# 式がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="325b7-116">Starting with [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# expressions are supported in [!INCLUDE[wf](../../../includes/wf-md.md)].</span></span> <span data-ttu-id="325b7-117">[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] で作成された、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] を対象とする C# ワークフロー プロジェクトでは C# 式が使用されるのに対し、Visual Basic ワークフロー プロジェクトでは Visual Basic 式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="325b7-117">C# workflow projects created in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] that target [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] use C# expressions, while Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="325b7-118">目的の c# の式を指定するラベルの付いたボックスに入力**c# 式を入力**です。</span><span class="sxs-lookup"><span data-stu-id="325b7-118">To specify the desired C# expression, type it into the box labeled **Enter a C# expression**.</span></span> <span data-ttu-id="325b7-119">このラベルは、プロパティ ウィンドウ (デザイナーでアクティビティを選択した場合) またはワークフロー デザイナーのアクティビティに表示されます。</span><span class="sxs-lookup"><span data-stu-id="325b7-119">This label is displayed in the properties window when the activity is selected in the designer, or on the activity in the workflow designer.</span></span> <span data-ttu-id="325b7-120">次の例では、2 つの `WriteLine` アクティビティが `Sequence` の中で `NoPersistScope` 内に含まれています。</span><span class="sxs-lookup"><span data-stu-id="325b7-120">In the following example, two `WriteLine` activities are contained within a `Sequence` inside a `NoPersistScope`.</span></span>  
  
 <span data-ttu-id="325b7-121">![自動的に作成された sequence アクティビティ](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")</span><span class="sxs-lookup"><span data-stu-id="325b7-121">![Automatically created sequence activity](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="325b7-122">C# 式は、Visual Studio でのみサポートされてし、再ホストされたワークフロー デザイナーでサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="325b7-122">C# expressions are supported only in Visual Studio, and are not supported in the re-hosted workflow designer.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="325b7-123"> 再ホストされたデザイナーでサポートされている新しい WF45 機能を参照してください[、再ホストされたワークフロー デザイナーで新しい Workflow Foundation 4.5 機能のサポート](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md)です。</span><span class="sxs-lookup"><span data-stu-id="325b7-123"> new WF45 features supported in the re-hosted designer, see [Support for New Workflow Foundation 4.5 Features in the Rehosted Workflow Designer](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md).</span></span>  
  
####  <a name="BackwardCompat"></a> <span data-ttu-id="325b7-124">旧バージョンとの互換性</span><span class="sxs-lookup"><span data-stu-id="325b7-124">Backwards compatibility</span></span>  
 <span data-ttu-id="325b7-125">[!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] に移行した既存の [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] C# ワークフロー プロジェクトの Visual Basic 式はサポートされています。</span><span class="sxs-lookup"><span data-stu-id="325b7-125">Visual Basic expressions in existing [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] C# workflow projects that have been migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are supported.</span></span> <span data-ttu-id="325b7-126">Visual Basic 式をワークフロー デザイナーで表示すると、既存の Visual Basic の式のテキストが置き換え**値が XAML で設定された**Visual Basic の式が有効な c# 構文でない限り、します。</span><span class="sxs-lookup"><span data-stu-id="325b7-126">When the Visual Basic expressions are viewed in the workflow designer, the text of the existing Visual Basic expression is replaced with **Value was set in XAML**, unless the Visual Basic expression is valid C# syntax.</span></span> <span data-ttu-id="325b7-127">Visual Basic 式が有効な C# 構文である場合は、式が表示されます。</span><span class="sxs-lookup"><span data-stu-id="325b7-127">If the Visual Basic expression is valid C# syntax, then the expression is displayed.</span></span> <span data-ttu-id="325b7-128">Visual Basic 式を C# に更新するには、ワークフロー デザイナーでその式を編集して、対応する C# 式を指定します。</span><span class="sxs-lookup"><span data-stu-id="325b7-128">To update the Visual Basic expressions to C#, you can edit them in the workflow designer and specify the equivalent C# expression.</span></span> <span data-ttu-id="325b7-129">Visual Basic 式を C# に更新する必要はありませんが、ワークフロー デザイナーで式を更新すると、式は C# に変換され、Visual Basic に戻すことができなくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="325b7-129">It is not required to update the Visual Basic expressions to C#, but once the expressions are updated in the workflow designer they are converted to C# and may not be reverted to Visual Basic.</span></span>  
  
###  <a name="CodeWorkflows"></a> <span data-ttu-id="325b7-130">コード ワークフローで c# 式の使用</span><span class="sxs-lookup"><span data-stu-id="325b7-130">Using C# expressions in code workflows</span></span>  
 <span data-ttu-id="325b7-131">C# 式は、[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] コードベースのワークフローでサポートされていますが、ワークフローを呼び出す前に、<xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType> を使用して C# 式をコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="325b7-131">C# expressions are supported in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] code based workflows, but before the workflow can be invoked the C# expressions must be compiled using <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="325b7-132">ワークフローの作成者は、`CSharpValue` を使用して式の右辺値を表し、`CSharpReference` を使用して式の左辺値を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="325b7-132">Workflow authors can use `CSharpValue` to represent the r-value of an expression, and `CSharpReference` to represent the l-value of an expression.</span></span> <span data-ttu-id="325b7-133">次の例では、`Assign` アクティビティに含まれる `WriteLine` アクティビティと `Sequence` アクティビティを使用してワークフローを作成します。</span><span class="sxs-lookup"><span data-stu-id="325b7-133">In the following example, a workflow is created with an `Assign` activity and a `WriteLine` activity contained in a `Sequence` activity.</span></span> <span data-ttu-id="325b7-134">`CSharpReference` は `To` の `Assign` 引数として指定され、式の左辺値を表します。</span><span class="sxs-lookup"><span data-stu-id="325b7-134">A `CSharpReference` is specified for the `To` argument of the `Assign`, and represents the l-value of the expression.</span></span> <span data-ttu-id="325b7-135">`CSharpValue` は `Value` の `Assign` 引数、および `Text` の `WriteLine` 引数として指定され、2 つの式の右辺値を表します。</span><span class="sxs-lookup"><span data-stu-id="325b7-135">A `CSharpValue` is specified for the `Value` argument of the `Assign`, and for the `Text` argument of the `WriteLine`, and represents the r-value for those two expressions.</span></span>  
  
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
  
 <span data-ttu-id="325b7-136">ワークフローが作成されると、`CompileExpressions` ヘルパー メソッドを呼び出して C# 式がコンパイルされ、ワークフローが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="325b7-136">After the workflow is constructed, the C# expressions are compiled by calling the `CompileExpressions` helper method and then the workflow is invoked.</span></span> <span data-ttu-id="325b7-137">次の例は、`CompileExpressions` メソッドです。</span><span class="sxs-lookup"><span data-stu-id="325b7-137">The following example is the `CompileExpressions` method.</span></span>  
  
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
>  <span data-ttu-id="325b7-138">C# 式がコンパイルされていない場合、<xref:System.NotSupportedException>には、次のようなメッセージ、ワークフローが呼び出される場合にスローされます。 `Expression Activity type 'CSharpValue`1' を実行するにはコンパイルを必要とします。</span><span class="sxs-lookup"><span data-stu-id="325b7-138">If the C# expressions are not compiled, a <xref:System.NotSupportedException> is thrown when the workflow is invoked with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="325b7-139">ワークフローがコンパイルされていることを確認してください '。</span><span class="sxs-lookup"><span data-stu-id="325b7-139">Please ensure that the workflow has been compiled.\`</span></span>  
  
 <span data-ttu-id="325b7-140">カスタムのコードベースのワークフローで `DynamicActivity` を使用する場合は、次のコード例に示すように、`CompileExpressions` メソッドに変更を加える必要があります。</span><span class="sxs-lookup"><span data-stu-id="325b7-140">If your custom code based workflow uses `DynamicActivity`, then some changes to the `CompileExpressions` method are required, as demonstrated in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="325b7-141">動的アクティビティで C# 式をコンパイルする `CompileExpressions` オーバーロードには、いくつかの相違点があります。</span><span class="sxs-lookup"><span data-stu-id="325b7-141">There are several differences in the `CompileExpressions` overload that compiles the C# expressions in a dynamic activity.</span></span>  
  
-   <span data-ttu-id="325b7-142">`CompileExpressions` のパラメーターが `DynamicActivity` です。</span><span class="sxs-lookup"><span data-stu-id="325b7-142">The parameter to `CompileExpressions` is a `DynamicActivity`.</span></span>  
  
-   <span data-ttu-id="325b7-143">型名および名前空間の取得に `DynamicActivity.Name` プロパティが使用されます。</span><span class="sxs-lookup"><span data-stu-id="325b7-143">The type name and namespace are retrieved using the `DynamicActivity.Name` property.</span></span>  
  
-   <span data-ttu-id="325b7-144">`TextExpressionCompilerSettings.ForImplementation` が `true` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="325b7-144">`TextExpressionCompilerSettings.ForImplementation` is set to `true`.</span></span>  
  
-   <span data-ttu-id="325b7-145">`CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` の代わりに `CompiledExpressionInvoker.SetCompiledExpressionRoot` が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="325b7-145">`CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` is called instead of `CompiledExpressionInvoker.SetCompiledExpressionRoot`.</span></span>  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="325b7-146"> コード内の式の操作を参照してください[オーサリング ワークフロー、アクティビティ、および命令型コードを使用して式](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)です。</span><span class="sxs-lookup"><span data-stu-id="325b7-146"> working with expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>  
  
###  <a name="XamlWorkflows"></a> <span data-ttu-id="325b7-147">XAML ワークフローで c# 式の使用</span><span class="sxs-lookup"><span data-stu-id="325b7-147">Using C# expressions in XAML workflows</span></span>  
 <span data-ttu-id="325b7-148">C# 式は XAML ワークフローでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="325b7-148">C# expressions are supported in XAML workflows.</span></span> <span data-ttu-id="325b7-149">コンパイルされた XAML ワークフローは型にコンパイルされ、Loose XAML ワークフローはランタイムによって読み込まれ、ワークフローの実行時にアクティビティ ツリーにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="325b7-149">Compiled XAML workflows are compiled into a type, and loose XAML workflows are loaded by the runtime and compiled into an activity tree when the workflow is executed.</span></span>  
  
-   [<span data-ttu-id="325b7-150">コンパイルされた Xaml</span><span class="sxs-lookup"><span data-stu-id="325b7-150">Compiled Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)  
  
-   [<span data-ttu-id="325b7-151">Loose Xaml</span><span class="sxs-lookup"><span data-stu-id="325b7-151">Loose Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)  
  
####  <a name="CompiledXaml"></a> <span data-ttu-id="325b7-152">コンパイルされた Xaml</span><span class="sxs-lookup"><span data-stu-id="325b7-152">Compiled Xaml</span></span>  
 <span data-ttu-id="325b7-153">C# 式は、コンパイルされた XAML ワークフローでサポートされており、[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] を対象とする C# ワークフロー プロジェクトの一部として型にコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="325b7-153">C# expressions are supported in compiled XAML workflows that are compiled to a type as part of a C# workflow project that targets [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span></span> <span data-ttu-id="325b7-154">コンパイルされた XAML ワークフローの作成、Visual Studio での既定の型は、c# ワークフロー プロジェクトを作成 Visual Studio を対象とする[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]c# 式を使用します。</span><span class="sxs-lookup"><span data-stu-id="325b7-154">Compiled XAML is the default type of workflow authoring in Visual Studio, and C# workflow projects created in Visual Studio that target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] use C# expressions.</span></span>  
  
####  <a name="LooseXaml"></a> <span data-ttu-id="325b7-155">Loose Xaml</span><span class="sxs-lookup"><span data-stu-id="325b7-155">Loose Xaml</span></span>  
 <span data-ttu-id="325b7-156">C# 式は Loose XAML ワークフローでがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="325b7-156">C# expressions are supported in loose XAML workflows.</span></span> <span data-ttu-id="325b7-157">Loose XAML ワークフローを読み込んで呼び出すワークフロー ホスト プログラムは、[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] を対象としている必要があります。また、<xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> は `true` (既定値は `false`) に設定する必要がります。</span><span class="sxs-lookup"><span data-stu-id="325b7-157">The workflow host program that loads and invokes the loose XAML workflow must target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], and <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> must be set to `true` (the default is `false`).</span></span> <span data-ttu-id="325b7-158"><xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> を `true` に設定するには、<xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> プロパティが <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> に設定されている `true` インスタンスを作成し、そのインスタンスを <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType> へパラメーターとして渡します。</span><span class="sxs-lookup"><span data-stu-id="325b7-158">To set <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> to `true`, create an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true`, and pass it as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="325b7-159">場合`CompileExpressions`に設定されていない`true`、<xref:System.NotSupportedException>には、次のようなメッセージがスローされます。 `Expression Activity type 'CSharpValue`1' を実行するにはコンパイルを必要とします。</span><span class="sxs-lookup"><span data-stu-id="325b7-159">If `CompileExpressions` Is not set to `true`, a <xref:System.NotSupportedException> will be thrown with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="325b7-160">ワークフローがコンパイルされていることを確認してください '。</span><span class="sxs-lookup"><span data-stu-id="325b7-160">Please ensure that the workflow has been compiled.\`</span></span>  
  
```csharp  
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings  
{  
    CompileExpressions = true  
};  
  
DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="325b7-161"> XAML ワークフローと連携するを参照してください[をシリアル化するワークフローとアクティビティの XAML との間](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md)です。</span><span class="sxs-lookup"><span data-stu-id="325b7-161"> working with XAML workflows, see [Serializing Workflows and Activities to and from XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).</span></span>  
  
###  <a name="WFServices"></a> <span data-ttu-id="325b7-162">XAMLX ワークフロー サービスで c# 式の使用</span><span class="sxs-lookup"><span data-stu-id="325b7-162">Using C# expressions in XAMLX workflow services</span></span>  
 <span data-ttu-id="325b7-163">C# 式は XAMLX ワークフロー サービスでがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="325b7-163">C# expressions are supported in XAMLX workflow services.</span></span> <span data-ttu-id="325b7-164">ワークフロー サービスが IIS または WAS でホストされている場合、追加の手順は必要ありません。ただし、XAML ワークフロー サービスが自己ホスト型サービスの場合は、C# 式をコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="325b7-164">When a workflow service is hosted in IIS or WAS then no additional steps are required, but if the XAML workflow service is self-hosted, then the C# expressions must be compiled.</span></span> <span data-ttu-id="325b7-165">自己ホスト XAMLX ワークフロー サービスで c# 式をコンパイルするには、最初に XAMLX ファイルを読み込む、 `WorkflowService`、しに渡す、`Body`の`WorkflowService`を`CompileExpressions`前で説明した方法[c# を使用します。コード ワークフローで式](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows)セクションです。</span><span class="sxs-lookup"><span data-stu-id="325b7-165">To compile the C# expressions in a self-hosted XAMLX workflow service, first load the XAMLX file into a `WorkflowService`, and then pass the `Body` of the `WorkflowService` to the `CompileExpressions` method described in the previous [Using C# expressions in code workflows](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) section.</span></span> <span data-ttu-id="325b7-166">次の例では、XAMLX ワークフロー サービスが読み込まれ、C# 式がコンパイルされた後、ワークフロー サービスが開かれて要求を待機します。</span><span class="sxs-lookup"><span data-stu-id="325b7-166">In the following example, a XAMLX workflow service is loaded, the C# expressions are compiled, and then the workflow service is opened and waits for requests.</span></span>  
  
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
  
 <span data-ttu-id="325b7-167">C# 式がコンパイルされないと、`Open` の処理は成功しますが、ワークフローは呼び出し時に失敗します。</span><span class="sxs-lookup"><span data-stu-id="325b7-167">If the C# expressions are not compiled, the `Open` operation succeeds but the workflow will fail when it is invoked.</span></span> <span data-ttu-id="325b7-168">次`CompileExpressions`メソッドは、前のメソッドと同じ[コード ワークフローで c# を使用して式](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows)セクションです。</span><span class="sxs-lookup"><span data-stu-id="325b7-168">The following `CompileExpressions` method is the same as the method from the previous [Using C# expressions in code workflows](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) section.</span></span>  
  
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
