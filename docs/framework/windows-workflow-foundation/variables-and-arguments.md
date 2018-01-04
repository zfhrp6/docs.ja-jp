---
title: "変数と引数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d01c31cce9aa6ae6d87773fc8e616e0e08bbd8c8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="variables-and-arguments"></a><span data-ttu-id="d3d22-102">変数と引数</span><span class="sxs-lookup"><span data-stu-id="d3d22-102">Variables and Arguments</span></span>
<span data-ttu-id="d3d22-103">[!INCLUDE[wf](../../../includes/wf-md.md)] では、変数はデータ ストレージを表し、引数はアクティビティとのデータ フローを表します。</span><span class="sxs-lookup"><span data-stu-id="d3d22-103">In [!INCLUDE[wf](../../../includes/wf-md.md)], variables represent the storage of data and arguments represent the flow of data into and out of an activity.</span></span> <span data-ttu-id="d3d22-104">アクティビティには一連の引数があり、その引数はアクティビティの署名を構成します。</span><span class="sxs-lookup"><span data-stu-id="d3d22-104">An activity has a set of arguments and they make up the signature of the activity.</span></span> <span data-ttu-id="d3d22-105">また、アクティビティは開発者がワークフローの設計時に変数を追加または削除できる変数のリストを保持しています。</span><span class="sxs-lookup"><span data-stu-id="d3d22-105">Additionally, an activity can maintain a list of variables to which a developer can add or remove variables during the design of a workflow.</span></span> <span data-ttu-id="d3d22-106">引数は、値を返す式を使用してバインドされます。</span><span class="sxs-lookup"><span data-stu-id="d3d22-106">An argument is bound using an expression that returns a value.</span></span>  
  
## <a name="variables"></a><span data-ttu-id="d3d22-107">変数</span><span class="sxs-lookup"><span data-stu-id="d3d22-107">Variables</span></span>  
 <span data-ttu-id="d3d22-108">変数はデータを保存する場所です。</span><span class="sxs-lookup"><span data-stu-id="d3d22-108">Variables are storage locations for data.</span></span> <span data-ttu-id="d3d22-109">変数はワークフロー定義の一部として宣言されます。</span><span class="sxs-lookup"><span data-stu-id="d3d22-109">Variables are declared as part of the definition of a workflow.</span></span> <span data-ttu-id="d3d22-110">変数は実行時に値を受け取ります。これらの値はワークフロー インスタンスの状態の一部として保存されます。</span><span class="sxs-lookup"><span data-stu-id="d3d22-110">Variables take on values at runtime and these values are stored as part of the state of a workflow instance.</span></span> <span data-ttu-id="d3d22-111">変数の定義では、変数の型を指定します。オプションで名前を指定する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="d3d22-111">A variable definition specifies the type of the variable and optionally, the name.</span></span> <span data-ttu-id="d3d22-112">変数を宣言し、<xref:System.Activities.Statements.Assign%601> アクティビティを使用して変数に値を代入し、その値を <xref:System.Activities.Statements.WriteLine> アクティビティを使用してコンソールに表示する方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="d3d22-112">The following code shows how to declare a variable, assign a value to it using an <xref:System.Activities.Statements.Assign%601> activity, and then display its value to the console using a <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
```csharp  
// Define a variable named "str" of type string.  
Variable<string> var = new Variable<string>  
{  
    Name = "str"  
};  
  
// Declare the variable within a Sequence, assign  
// a value to it, and then display it.  
Activity wf = new Sequence()  
{  
    Variables = { var },  
    Activities =  
    {  
        new Assign<string>  
        {  
            To = var,  
            Value = "Hello World."  
        },  
        new WriteLine  
        {  
            Text = var  
        }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
 <span data-ttu-id="d3d22-113">オプションで、変数宣言の一部として既定値の式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d3d22-113">A default value expression can optionally be specified as part of a variable declaration.</span></span> <span data-ttu-id="d3d22-114">また、変数は修飾子を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="d3d22-114">Variables also can have modifiers.</span></span> <span data-ttu-id="d3d22-115">たとえば変数が読み取り専用の場合は、読み取り専用の <xref:System.Activities.VariableModifiers> 修飾子を適用できます。</span><span class="sxs-lookup"><span data-stu-id="d3d22-115">For example, if a variable is read-only then the read-only <xref:System.Activities.VariableModifiers> modifier can be applied.</span></span> <span data-ttu-id="d3d22-116">次の例では、既定値を代入した読み取り専用の変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="d3d22-116">In the following example, a read-only variable is created that has a default value assigned.</span></span>  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a><span data-ttu-id="d3d22-117">変数のスコープ</span><span class="sxs-lookup"><span data-stu-id="d3d22-117">Variable Scoping</span></span>  
 <span data-ttu-id="d3d22-118">実行時の変数の有効期間は、変数を宣言したアクティビティの有効期間と同じです。</span><span class="sxs-lookup"><span data-stu-id="d3d22-118">The lifetime of a variable at runtime is equal to the lifetime of the activity that declares it.</span></span> <span data-ttu-id="d3d22-119">アクティビティが完了すると、その変数はクリーンアップされ、その後は参照できません。</span><span class="sxs-lookup"><span data-stu-id="d3d22-119">When an activity completes, its variables are cleaned up and can no longer be referenced.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="d3d22-120">引数</span><span class="sxs-lookup"><span data-stu-id="d3d22-120">Arguments</span></span>  
 <span data-ttu-id="d3d22-121">アクティビティの作成者は、引数を使用してアクティビティとのデータ フローの方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="d3d22-121">Activity authors use arguments to define the way data flows into and out of an activity.</span></span> <span data-ttu-id="d3d22-122">各引数には <xref:System.Activities.ArgumentDirection.In>、<xref:System.Activities.ArgumentDirection.Out>、<xref:System.Activities.ArgumentDirection.InOut> などの方向が指定されます。</span><span class="sxs-lookup"><span data-stu-id="d3d22-122">Each argument has a specified direction: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, or <xref:System.Activities.ArgumentDirection.InOut>.</span></span>  
  
 <span data-ttu-id="d3d22-123">ワークフロー ランタイムでは、アクティビティへのデータ移動のタイミングについて次のように保証しています。</span><span class="sxs-lookup"><span data-stu-id="d3d22-123">The workflow runtime makes the following guarantees about the timing of data movement into and out of activities:</span></span>  
  
1.  <span data-ttu-id="d3d22-124">アクティビティが実行を開始すると、すべての入力および入出力引数の値が計算されます。</span><span class="sxs-lookup"><span data-stu-id="d3d22-124">When an activity starts executing, the values of all of its input and input/output arguments are calculated.</span></span> <span data-ttu-id="d3d22-125">たとえば、<xref:System.Activities.Argument.Get%2A> が呼び出されるタイミングにかかわらず、返される値は `Execute` が呼び出される前にランタイムによって計算された値になります。</span><span class="sxs-lookup"><span data-stu-id="d3d22-125">For example, regardless of when <xref:System.Activities.Argument.Get%2A> is called, the value returned is the one calculated by the runtime prior to its invocation of `Execute`.</span></span>  
  
2.  <span data-ttu-id="d3d22-126"><xref:System.Activities.InOutArgument%601.Set%2A> が呼び出されると、ランタイムはすぐにその値を設定します。</span><span class="sxs-lookup"><span data-stu-id="d3d22-126">When <xref:System.Activities.InOutArgument%601.Set%2A> is called, the runtime sets the value immediately.</span></span>  
  
3.  <span data-ttu-id="d3d22-127">必要に応じて、引数に <xref:System.Activities.Argument.EvaluationOrder%2A> を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d3d22-127">Arguments can optionally have their <xref:System.Activities.Argument.EvaluationOrder%2A> specified.</span></span> <span data-ttu-id="d3d22-128"><xref:System.Activities.Argument.EvaluationOrder%2A> は引数の評価順序を指定するゼロベースの値です。</span><span class="sxs-lookup"><span data-stu-id="d3d22-128"><xref:System.Activities.Argument.EvaluationOrder%2A> is a zero-based value that specifies the order in which the argument is evaluated.</span></span> <span data-ttu-id="d3d22-129">既定では引数の評価順序は指定されておらず、<xref:System.Activities.Argument.UnspecifiedEvaluationOrder> の値と同じです。</span><span class="sxs-lookup"><span data-stu-id="d3d22-129">By default, the evaluation order of the argument is unspecified and is equal to the <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> value.</span></span> <span data-ttu-id="d3d22-130"><xref:System.Activities.Argument.EvaluationOrder%2A> に 0 以上の値を設定して、この引数の評価順序を指定します。</span><span class="sxs-lookup"><span data-stu-id="d3d22-130">Set <xref:System.Activities.Argument.EvaluationOrder%2A> to a value greater or equal to zero to specify an evaluation order for this argument.</span></span> [!INCLUDE[wf2](../../../includes/wf2-md.md)]<span data-ttu-id="d3d22-131"> は指定された評価順序を使用して昇順で引数を評価します。</span><span class="sxs-lookup"><span data-stu-id="d3d22-131"> evaluates arguments with a specified evaluation order in ascending order.</span></span> <span data-ttu-id="d3d22-132">評価順序が指定されていない引数は、評価順序が指定されている引数の前に評価されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d3d22-132">Note that arguments with an unspecified evaluation order are evaluated before those with a specified evaluation order.</span></span>  
  
 <span data-ttu-id="d3d22-133">アクティビティの作成者は、引数を公開する場合に厳密な型指定のメカニズムを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d3d22-133">An activity author can use a strongly-typed mechanism for exposing its arguments.</span></span> <span data-ttu-id="d3d22-134">これを行うには、<xref:System.Activities.InArgument%601>、<xref:System.Activities.OutArgument%601>、および <xref:System.Activities.InOutArgument%601> の型のプロパティを宣言します。</span><span class="sxs-lookup"><span data-stu-id="d3d22-134">This is accomplished by declaring properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="d3d22-135">これにより、アクティビティの作成者は、アクティビティに受け渡しするデータの特定のコントラクトを確立できます。</span><span class="sxs-lookup"><span data-stu-id="d3d22-135">This allows an activity author to establish a specific contract about the data going into and out of an activity.</span></span>  
  
### <a name="defining-the-arguments-on-an-activity"></a><span data-ttu-id="d3d22-136">アクティビティの引数の定義</span><span class="sxs-lookup"><span data-stu-id="d3d22-136">Defining the Arguments on an Activity</span></span>  
 <span data-ttu-id="d3d22-137"><xref:System.Activities.InArgument%601>、<xref:System.Activities.OutArgument%601>、および <xref:System.Activities.InOutArgument%601> 型のプロパティを指定することで、アクティビティに引数を定義できます。</span><span class="sxs-lookup"><span data-stu-id="d3d22-137">Arguments can be defined on an activity by specifying properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="d3d22-138">次のコードでは、ユーザーに表示する文字列を受け取り、ユーザーの応答を含む文字列を返す `Prompt` アクティビティの引数を定義する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d3d22-138">The following code shows how to define the arguments for a `Prompt` activity that takes in a string to display to the user and returns a string that contains the user's response.</span></span>  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="d3d22-139">1 つの値を返すアクティビティは、<xref:System.Activities.Activity%601>、<xref:System.Activities.NativeActivity%601>、または <xref:System.Activities.CodeActivity%601> から派生させることができます。</span><span class="sxs-lookup"><span data-stu-id="d3d22-139">Activities that return a single value can derive from <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, or <xref:System.Activities.CodeActivity%601>.</span></span> <span data-ttu-id="d3d22-140">これらのアクティビティは、アクティビティの戻り値を含む <xref:System.Activities.OutArgument%601> という名前の適切に定義された <xref:System.Activities.Activity%601.Result%2A> を持っています。</span><span class="sxs-lookup"><span data-stu-id="d3d22-140">These activities have a well-defined <xref:System.Activities.OutArgument%601> named <xref:System.Activities.Activity%601.Result%2A> that contains the return value of the activity.</span></span>  
  
### <a name="using-variables-and-arguments-in-workflows"></a><span data-ttu-id="d3d22-141">ワークフローでの変数と引数の使用</span><span class="sxs-lookup"><span data-stu-id="d3d22-141">Using Variables and Arguments in Workflows</span></span>  
 <span data-ttu-id="d3d22-142">次の例は、ワークフローで変数と引数を使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d3d22-142">The following example shows how variables and arguments are used in a workflow.</span></span> <span data-ttu-id="d3d22-143">このワークフローは、3 つの変数 `var1`、`var2`、`var3` を宣言するシーケンスです。</span><span class="sxs-lookup"><span data-stu-id="d3d22-143">The workflow is a sequence that declares three variables: `var1`, `var2`, and `var3`.</span></span> <span data-ttu-id="d3d22-144">このワークフローの最初のアクティビティは `Assign` アクティビティで、変数 `var1` の値を変数 `var2` に代入します。</span><span class="sxs-lookup"><span data-stu-id="d3d22-144">The first activity in the workflow is an `Assign` activity that assigns the value of variable `var1` to the variable `var2`.</span></span> <span data-ttu-id="d3d22-145">これに `WriteLine` アクティビティが続き、変数 `var2` の値を出力します。</span><span class="sxs-lookup"><span data-stu-id="d3d22-145">This is followed by a `WriteLine` activity that prints the value of the `var2` variable.</span></span> <span data-ttu-id="d3d22-146">その次はもう 1 つの `Assign` アクティビティで、変数 `var2` の値を変数 `var3` に代入します。</span><span class="sxs-lookup"><span data-stu-id="d3d22-146">Next is another `Assign` activity that assigns the value of variable `var2` to the variable `var3`.</span></span> <span data-ttu-id="d3d22-147">最後にもう 1 つの `WriteLine` アクティビティがあり、変数 `var3` の値を出力します。</span><span class="sxs-lookup"><span data-stu-id="d3d22-147">Finally there is another `WriteLine` activity that prints the value of the `var3` variable.</span></span> <span data-ttu-id="d3d22-148">最初の `Assign` アクティビティは、アクティビティの引数のバインドを明示的に表す `InArgument<string>` オブジェクトと `OutArgument<string>` オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="d3d22-148">The first `Assign` activity uses `InArgument<string>` and `OutArgument<string>` objects that explicitly represent the bindings for the activity's arguments.</span></span> <span data-ttu-id="d3d22-149">`InArgument<string>` は、値が <xref:System.Activities.Statements.Assign.Value%2A> アクティビティにその <xref:System.Activities.Statements.Assign%601> 引数を通ってフローするので、<xref:System.Activities.Statements.Assign.Value%2A> に使用されます。`OutArgument<string>` は、値が <xref:System.Activities.Statements.Assign.To%2A> 引数から変数へフローするので、<xref:System.Activities.Statements.Assign.To%2A> に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d3d22-149">`InArgument<string>` is used for <xref:System.Activities.Statements.Assign.Value%2A> because the value is flowing into the <xref:System.Activities.Statements.Assign%601> activity through its <xref:System.Activities.Statements.Assign.Value%2A> argument, and `OutArgument<string>` is used for <xref:System.Activities.Statements.Assign.To%2A> because the value is flowing out of the <xref:System.Activities.Statements.Assign.To%2A> argument into the variable.</span></span> <span data-ttu-id="d3d22-150">2 番目の `Assign` アクティビティは、より少ないコードで暗黙的なキャストを使用する同等の構文を使用して同じ内容を実行します。</span><span class="sxs-lookup"><span data-stu-id="d3d22-150">The second `Assign` activity accomplishes the same thing with more compact but equivalent syntax that uses implicit casts.</span></span> <span data-ttu-id="d3d22-151">`WriteLine` アクティビティも少ないコードの構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="d3d22-151">The `WriteLine` activities also use the compact syntax.</span></span>  
  
```csharp  
// Declare three variables; the first one is given an initial value.  
Variable<string> var1 = new Variable<string>()  
{  
    Default = "one"  
};  
Variable<string> var2 = new Variable<string>();  
Variable<string> var3 = new Variable<string>();  
  
// Define the workflow  
Activity wf = new Sequence  
{  
    Variables = { var1, var2, var3 },  
    Activities =   
    {  
        new Assign<string>()  
        {  
            Value = new InArgument<string>(var1),  
            To = new OutArgument<string>(var2)  
        },  
        new WriteLine() { Text = var2 },  
        new Assign<string>()  
        {  
            Value = var2,  
            To = var3  
        },  
        new WriteLine() { Text = var3 }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a><span data-ttu-id="d3d22-152">コードに基づいたアクティビティでの変数と引数の使用</span><span class="sxs-lookup"><span data-stu-id="d3d22-152">Using Variables and Arguments in Code-Based Activities</span></span>  
 <span data-ttu-id="d3d22-153">前の例は、ワークフローの引数と変数、および宣言型のアクティビティを使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d3d22-153">The previous examples show how to use arguments and variables in workflows and declarative activities.</span></span> <span data-ttu-id="d3d22-154">引数と変数は、コードに基づくアクティビティでも使用されます。</span><span class="sxs-lookup"><span data-stu-id="d3d22-154">Arguments and variables are also used in code-based activities.</span></span> <span data-ttu-id="d3d22-155">概念上は、使用法は非常に似ています。</span><span class="sxs-lookup"><span data-stu-id="d3d22-155">Conceptually the usage is very similar.</span></span> <span data-ttu-id="d3d22-156">変数はアクティビティ内のデータ ストレージを表し、引数はアクティビティへのデータ フローを表し、ワークフロー作成者によってワークフローでデータの受け渡しを行う場所を示す他の変数または引数にバインドされます。</span><span class="sxs-lookup"><span data-stu-id="d3d22-156">Variables represent data storage within the activity, and arguments represent the flow of data into or out of the activity, and are bound by the workflow author to other variables or arguments in the workflow that represent where the data flows to or from.</span></span> <span data-ttu-id="d3d22-157">アクティビティの変数または引数の値を取得または設定するには、アクティビティの現在の実行環境を表すアクティビティ コンテキストを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3d22-157">To get or set the value of a variable or argument in an activity, an activity context must be used that represents the current execution environment of the activity.</span></span> <span data-ttu-id="d3d22-158">これは、ワークフロー ランタイムによってアクティビティの <xref:System.Activities.CodeActivity%601.Execute%2A> メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="d3d22-158">This is passed into the <xref:System.Activities.CodeActivity%601.Execute%2A> method of the activity by the workflow runtime.</span></span> <span data-ttu-id="d3d22-159">次の例では、2 つの `Add` 引数を持つカスタムの <xref:System.Activities.ArgumentDirection.In> アクティビティが定義されています。</span><span class="sxs-lookup"><span data-stu-id="d3d22-159">In this example, a custom `Add` activity is defined that has two <xref:System.Activities.ArgumentDirection.In> arguments.</span></span> <span data-ttu-id="d3d22-160">この引数の値にアクセスするために <xref:System.Activities.Argument.Get%2A> メソッドが使用され、ワークフロー ランタイムによって渡されたコンテキストが使用されます。</span><span class="sxs-lookup"><span data-stu-id="d3d22-160">To access the value of the arguments, the <xref:System.Activities.Argument.Get%2A> method is used and the context that was passed in by the workflow runtime is used.</span></span>  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="d3d22-161">引数、変数、およびコード内の式の使用を参照してください[オーサリング ワークフロー、アクティビティ、および命令型コードを使用して式](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)と[ために必要な引数とオーバー ロード グループ](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md)です。</span><span class="sxs-lookup"><span data-stu-id="d3d22-161"> working with arguments, variables, and expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md) and [Required Arguments and Overload Groups](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md).</span></span>
