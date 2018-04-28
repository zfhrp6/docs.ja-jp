---
title: XAML との間のワークフローおよびアクティビティのシリアル化
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37685b32-24e3-4d72-88d8-45d5fcc49ec2
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9a215be76002b9e8fca8ac4a9073885b3b30a97b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="serializing-workflows-and-activities-to-and-from-xaml"></a><span data-ttu-id="6b372-102">XAML との間のワークフローおよびアクティビティのシリアル化</span><span class="sxs-lookup"><span data-stu-id="6b372-102">Serializing Workflows and Activities to and from XAML</span></span>
<span data-ttu-id="6b372-103">ワークフロー定義は、アセンブリに含まれる型にコンパイルされるほか、XAML にシリアル化することもできます。</span><span class="sxs-lookup"><span data-stu-id="6b372-103">In addition to being compiled into types that are contained in assemblies, workflow definitions can also be serialized to XAML.</span></span> <span data-ttu-id="6b372-104">これらのシリアル化された定義は、編集や検査のために再度読み込んだり、コンパイルのためにビルド システムに渡したり、読み込んで呼び出したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="6b372-104">These serialized definitions can be reloaded for editing or inspection, passed to a build system for compilation, or loaded and invoked.</span></span> <span data-ttu-id="6b372-105">このトピックでは、ワークフロー定義のシリアル化と XAML ワークフロー定義の使用に関する概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="6b372-105">This topic provides an overview of serializing workflow definitions and working with XAML workflow definitions.</span></span>  
  
## <a name="working-with-xaml-workflow-definitions"></a><span data-ttu-id="6b372-106">XAML ワークフロー定義の使用</span><span class="sxs-lookup"><span data-stu-id="6b372-106">Working with XAML Workflow Definitions</span></span>  
 <span data-ttu-id="6b372-107">シリアル化するワークフロー定義を作成するには、<xref:System.Activities.ActivityBuilder> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="6b372-107">To create a workflow definition for serialization, the <xref:System.Activities.ActivityBuilder> class is used.</span></span> <span data-ttu-id="6b372-108"><xref:System.Activities.ActivityBuilder> の作成は、<xref:System.Activities.DynamicActivity> の作成とほとんど同じです。</span><span class="sxs-lookup"><span data-stu-id="6b372-108">Creating an <xref:System.Activities.ActivityBuilder> is very similar to creating a <xref:System.Activities.DynamicActivity>.</span></span> <span data-ttu-id="6b372-109">目的の引数を指定し、動作を構成するアクティビティを構成します。</span><span class="sxs-lookup"><span data-stu-id="6b372-109">Any desired arguments are specified, and the activities that constitute the behavior are configured.</span></span> <span data-ttu-id="6b372-110">次の例では、2 つの入力引数を受け取り、それらを加算して結果を返す `Add` アクティビティを作成しています。</span><span class="sxs-lookup"><span data-stu-id="6b372-110">In the following example, an `Add` activity is created that takes two input arguments, adds them together, and returns the result.</span></span> <span data-ttu-id="6b372-111">このアクティビティは結果を返すため、ジェネリック <xref:System.Activities.ActivityBuilder%601> クラスが使用されています。</span><span class="sxs-lookup"><span data-stu-id="6b372-111">Because this activity returns a result, the generic <xref:System.Activities.ActivityBuilder%601> class is used.</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#41](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#41)]  
  
 <span data-ttu-id="6b372-112">それぞれの <xref:System.Activities.DynamicActivityProperty> インスタンスでワークフローへの入力引数を 1 つずつ表し、<xref:System.Activities.ActivityBuilder.Implementation%2A> にワークフローのロジックを構成するアクティビティが格納されています。</span><span class="sxs-lookup"><span data-stu-id="6b372-112">Each of the <xref:System.Activities.DynamicActivityProperty> instances represents one of the input arguments to the workflow, and the <xref:System.Activities.ActivityBuilder.Implementation%2A> contains the activities that make up the logic of the workflow.</span></span> <span data-ttu-id="6b372-113">この例では、右辺値の式が Visual Basic 式であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6b372-113">Note that the r-value expressions in this example are Visual Basic expressions.</span></span> <span data-ttu-id="6b372-114"><xref:System.Activities.Expressions.ExpressionServices.Convert%2A> を使用しないと、ラムダ式は XAML 形式にシリアル化できません。</span><span class="sxs-lookup"><span data-stu-id="6b372-114">Lambda expressions are not serializable to XAML unless <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> is used.</span></span> <span data-ttu-id="6b372-115">シリアル化されたワーク フローをワークフロー デザイナーで開くか編集することを目的としている場合は、Visual Basic 式を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b372-115">If the serialized workflows are intended to be opened or edited in the workflow designer then Visual Basic expressions should be used.</span></span> <span data-ttu-id="6b372-116">詳細については、次を参照してください。[オーサリング ワークフロー、アクティビティ、および命令型コードを使用して式](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)です。</span><span class="sxs-lookup"><span data-stu-id="6b372-116">For more information, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>  
  
 <span data-ttu-id="6b372-117">XAML への <xref:System.Activities.ActivityBuilder> インスタンスで表されるワークフロー定義を XAML 形式にシリアル化するには、<xref:System.Activities.XamlIntegration.ActivityXamlServices> を使用して <xref:System.Xaml.XamlWriter> を作成した後、その <xref:System.Xaml.XamlServices> を使用することで、<xref:System.Xaml.XamlWriter> を使用してワークフロー定義をシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="6b372-117">To serialize the workflow definition represented by the <xref:System.Activities.ActivityBuilder> instance to XAML, use <xref:System.Activities.XamlIntegration.ActivityXamlServices> to create a <xref:System.Xaml.XamlWriter>, and then use <xref:System.Xaml.XamlServices> to serialize the workflow definition by using the <xref:System.Xaml.XamlWriter>.</span></span> <span data-ttu-id="6b372-118"><xref:System.Activities.XamlIntegration.ActivityXamlServices> には、<xref:System.Activities.ActivityBuilder> インスタンスを XAML との間でマッピングしたり、XAML ワークフローを読み込んで、呼び出し可能な <xref:System.Activities.DynamicActivity> を返したりするメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="6b372-118"><xref:System.Activities.XamlIntegration.ActivityXamlServices> has methods to map <xref:System.Activities.ActivityBuilder> instances to and from XAML, and to load XAML workflows and return a <xref:System.Activities.DynamicActivity> that can be invoked.</span></span> <span data-ttu-id="6b372-119">次の例では、前の例の <xref:System.Activities.ActivityBuilder> インスタンスを文字列にシリアル化し、さらにファイルに保存しています。</span><span class="sxs-lookup"><span data-stu-id="6b372-119">In the following example, the <xref:System.Activities.ActivityBuilder> instance from the previous example is serialized to a string, and also saved to a file.</span></span>  
  
```csharp  
// Serialize the workflow to XAML and store it in a string.  
StringBuilder sb = new StringBuilder();  
StringWriter tw = new StringWriter(sb);  
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(tw, new XamlSchemaContext()));  
XamlServices.Save(xw , ab);  
string serializedAB = sb.ToString();  
  
// Display the XAML to the console.  
Console.WriteLine(serializedAB);  
  
// Serialize the workflow to XAML and save it to a file.  
StreamWriter sw = File.CreateText(@"C:\Workflows\add.xaml");  
XamlWriter xw2 = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));  
XamlServices.Save(xw2, ab);  
sw.Close();  
```  
  
 <span data-ttu-id="6b372-120">シリアル化されたワークフローの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6b372-120">The following example represents the serialized workflow.</span></span>  
  
```xaml  
<Activity   
  x:TypeArguments="x:Int32"   
  x:Class="Add"   
  xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"   
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <x:Members>  
    <x:Property Name="Operand1" Type="InArgument(x:Int32)" />  
    <x:Property Name="Operand2" Type="InArgument(x:Int32)" />  
  </x:Members>  
  <Sequence>  
    <WriteLine Text="[Operand1.ToString() + " + " + Operand2.ToString()]" />  
    <Assign x:TypeArguments="x:Int32" Value="[Operand1 + Operand2]">  
      <Assign.To>  
        <OutArgument x:TypeArguments="x:Int32">  
          <ArgumentReference x:TypeArguments="x:Int32" ArgumentName="Result" />  
          </OutArgument>  
      </Assign.To>  
    </Assign>  
  </Sequence>  
</Activity>  
```  
  
 <span data-ttu-id="6b372-121">シリアル化されたワークフローを読み込み、 <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="6b372-121">To load a serialized workflow, the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method is used.</span></span> <span data-ttu-id="6b372-122">このメソッドは、シリアル化されたワークフロー定義を受け取り、ワークフロー定義を表す <xref:System.Activities.DynamicActivity> を返します。</span><span class="sxs-lookup"><span data-stu-id="6b372-122">This takes the serialized workflow definition and returns a <xref:System.Activities.DynamicActivity> that represents the workflow definition.</span></span> <span data-ttu-id="6b372-123">検証プロセス中に <xref:System.Activities.Activity.CacheMetadata%2A> の本体で <xref:System.Activities.DynamicActivity> が呼び出されるまでは、XAML は逆シリアル化されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6b372-123">Note that the XAML is not deserialized until <xref:System.Activities.Activity.CacheMetadata%2A> is called on the body of the <xref:System.Activities.DynamicActivity> during the validation process.</span></span> <span data-ttu-id="6b372-124">検証が明示的に呼び出されない場合は、ワークフローが呼び出されたときに実行されます。</span><span class="sxs-lookup"><span data-stu-id="6b372-124">If validation is not explicitly called then it is performed when the workflow is invoked.</span></span> <span data-ttu-id="6b372-125">XAML ワークフロー定義が無効な場合、<xref:System.ArgumentException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="6b372-125">If the XAML workflow definition is invalid, then an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="6b372-126"><xref:System.Activities.Activity.CacheMetadata%2A> からスローされる例外は、<xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> への呼び出しからエスケープされ、呼び出し元によって処理される必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b372-126">Any exceptions thrown from <xref:System.Activities.Activity.CacheMetadata%2A> escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span> <span data-ttu-id="6b372-127">次の例では、前の例のシリアル化されたワークフローを読み込み、<xref:System.Activities.WorkflowInvoker> を使用して呼び出しています。</span><span class="sxs-lookup"><span data-stu-id="6b372-127">In the following example, the serialized workflow from the previous example is loaded and invoked by using <xref:System.Activities.WorkflowInvoker>.</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#43](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#43)]  
  
 <span data-ttu-id="6b372-128">このワークフローが呼び出されると、次の出力がコンソールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6b372-128">When this workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="6b372-129">**25 + 15**</span><span class="sxs-lookup"><span data-stu-id="6b372-129">**25 + 15**</span></span>  
<span data-ttu-id="6b372-130">**40**</span><span class="sxs-lookup"><span data-stu-id="6b372-130">**40**</span></span>    
> [!NOTE]
>  [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="6b372-131"> 複数の入力と出力引数を指定してワークフローを呼び出すを参照してください[を使用して WorkflowInvoker と WorkflowApplication](../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md)と<xref:System.Activities.WorkflowInvoker.Invoke%2A>です。</span><span class="sxs-lookup"><span data-stu-id="6b372-131"> invoking workflows with input and output arguments, see [Using WorkflowInvoker and WorkflowApplication](../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md) and <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span>  
  
 <span data-ttu-id="6b372-132">シリアル化されたワークフローに c# 式が含まれている場合、<xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings>インスタンスをその<xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A>プロパティに設定`true`へのパラメーターとして渡す必要があります<xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>、それ以外の場合、<xref:System.NotSupportedException>するようなメッセージがスローされます、次の: `Expression Activity type 'CSharpValue`1' を実行するのにはコンパイルを必要とします。</span><span class="sxs-lookup"><span data-stu-id="6b372-132">If the serialized workflow contains C# expressions, then an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true` must be passed as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, otherwise a <xref:System.NotSupportedException> will be thrown with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="6b372-133">ワークフローがコンパイルされていることを確認してください '。</span><span class="sxs-lookup"><span data-stu-id="6b372-133">Please ensure that the workflow has been compiled.\`</span></span>  
  
```csharp  
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings  
{  
    CompileExpressions = true  
};  
  
DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;  
```  
  
 <span data-ttu-id="6b372-134">詳細については、次を参照してください。 [c# 式](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md)です。</span><span class="sxs-lookup"><span data-stu-id="6b372-134">For more information, see [C# Expressions](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).</span></span>  
  
 <span data-ttu-id="6b372-135">シリアル化されたワークフロー定義を読み込むことも、<xref:System.Activities.ActivityBuilder>インスタンスを使用して、 <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="6b372-135">A serialized workflow definition can also be loaded into an <xref:System.Activities.ActivityBuilder> instance by using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> method.</span></span> <span data-ttu-id="6b372-136">シリアル化されたワークフローを <xref:System.Activities.ActivityBuilder> インスタンスに読み込むと、検査や変更が可能になります。</span><span class="sxs-lookup"><span data-stu-id="6b372-136">After a serialized workflow is loaded into an <xref:System.Activities.ActivityBuilder> instance it can be inspected and modified.</span></span> <span data-ttu-id="6b372-137">これにより、デザイン プロセス中にワークフロー定義を保存したり再度読み込んだりするためのメカニズムが提供され、カスタム ワークフロー デザイナーを作成するときに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6b372-137">This is useful for custom workflow designer authors and provides a mechanism for saving and reloading workflow definitions during the design process.</span></span> <span data-ttu-id="6b372-138">次の例では、前の例のシリアル化されたワークフロー定義を読み込み、そのプロパティを検査しています。</span><span class="sxs-lookup"><span data-stu-id="6b372-138">In the following example, the serialized workflow definition from the previous example is loaded and its properties are inspected.</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#44](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#44)]
