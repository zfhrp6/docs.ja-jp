---
title: "式ツリーのデバッグ (Visual Studio) (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0cf40b38ca9a6f743aca2894506e1d0ea80c9d57
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="cdfe2-102">式ツリーのデバッグ (Visual Studio) (C#)</span><span class="sxs-lookup"><span data-stu-id="cdfe2-102">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="cdfe2-103">アプリケーションをデバッグするときに、式ツリーの構造および内容を分析できます。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="cdfe2-104">式ツリーの構造を簡単に確認する場合は、`DebugView` プロパティを使用できます。このプロパティは、デバッグ モードでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which is available only in debug mode.</span></span> <span data-ttu-id="cdfe2-105">デバッグの詳細については、「[Visual Studio でのデバッグ](/visualstudio/debugger/debugging-in-visual-studio)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-105">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
 <span data-ttu-id="cdfe2-106">式ツリーの内容をわかりやすく表すために、`DebugView` プロパティでは Visual Studio ビジュアライザーを使用します。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-106">To better represent the content of expression trees, the `DebugView` property uses Visual Studio visualizers.</span></span> <span data-ttu-id="cdfe2-107">詳細については、「[Create Custom Visualizers](/visualstudio/debugger/create-custom-visualizers-of-data)」 (カスタム ビジュアライザーを作成する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-107">For more information, see [Create Custom Visualizers](/visualstudio/debugger/create-custom-visualizers-of-data).</span></span>  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="cdfe2-108">式ツリーのビジュアライザーを開くには</span><span class="sxs-lookup"><span data-stu-id="cdfe2-108">To open a visualizer for an expression tree</span></span>  
  
1.  <span data-ttu-id="cdfe2-109">**[データヒント]**、**[ウォッチ]** ウィンドウ、**[自動変数]** ウィンドウ、または **[ローカル]** ウィンドウで、式ツリーの `DebugView` プロパティの横に表示されている虫眼鏡のアイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-109">Click the magnifying glass icon that appears next to the `DebugView` property of an expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="cdfe2-110">ビジュアライザーの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-110">A list of visualizers is displayed.</span></span>  
  
2.  <span data-ttu-id="cdfe2-111">使用するビジュアライザーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-111">Click the visualizer you want to use.</span></span>  
  
 <span data-ttu-id="cdfe2-112">それぞれの式の型は、以下のセクションで説明するように、ビジュアライザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-112">Each expression type is displayed in the visualizer as described in the following sections.</span></span>  
  
## <a name="parameterexpressions"></a><span data-ttu-id="cdfe2-113">ParameterExpressions</span><span class="sxs-lookup"><span data-stu-id="cdfe2-113">ParameterExpressions</span></span>  
 <span data-ttu-id="cdfe2-114"><xref:System.Linq.Expressions.ParameterExpression> 変数名は、先頭に記号 "$" を付けて表示されます。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-114"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>  
  
 <span data-ttu-id="cdfe2-115">パラメーターに名前がない場合、`$var1` や `$var2` など、自動的に生成された名前が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-115">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="cdfe2-116">例</span><span class="sxs-lookup"><span data-stu-id="cdfe2-116">Examples</span></span>  
  
|<span data-ttu-id="cdfe2-117">式</span><span class="sxs-lookup"><span data-stu-id="cdfe2-117">Expression</span></span>|<span data-ttu-id="cdfe2-118">`DebugView` プロパティ</span><span class="sxs-lookup"><span data-stu-id="cdfe2-118">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");`|`$num`|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int));`|`$var1`|  
  
## <a name="constantexpressions"></a><span data-ttu-id="cdfe2-119">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="cdfe2-119">ConstantExpressions</span></span>  
 <span data-ttu-id="cdfe2-120">整数値、文字列、および `null` を表す <xref:System.Linq.Expressions.ConstantExpression> オブジェクトの場合、定数の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-120">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
 <span data-ttu-id="cdfe2-121">C# リテラルとしての標準のサフィックスを持つ数値型の場合、サフィックスが値に追加されます。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-121">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="cdfe2-122">さまざまな数値型に関連するサフィックスを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-122">The following table shows the suffixes associated with various numeric types.</span></span>  
  
|<span data-ttu-id="cdfe2-123">型</span><span class="sxs-lookup"><span data-stu-id="cdfe2-123">Type</span></span>|<span data-ttu-id="cdfe2-124">サフィックス</span><span class="sxs-lookup"><span data-stu-id="cdfe2-124">Suffix</span></span>|  
|----------|------------|  
|<xref:System.UInt32>|<span data-ttu-id="cdfe2-125">U</span><span class="sxs-lookup"><span data-stu-id="cdfe2-125">U</span></span>|  
|<xref:System.Int64>|<span data-ttu-id="cdfe2-126">L</span><span class="sxs-lookup"><span data-stu-id="cdfe2-126">L</span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="cdfe2-127">UL</span><span class="sxs-lookup"><span data-stu-id="cdfe2-127">UL</span></span>|  
|<xref:System.Double>|<span data-ttu-id="cdfe2-128">D</span><span class="sxs-lookup"><span data-stu-id="cdfe2-128">D</span></span>|  
|<xref:System.Single>|<span data-ttu-id="cdfe2-129">F</span><span class="sxs-lookup"><span data-stu-id="cdfe2-129">F</span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="cdfe2-130">M</span><span class="sxs-lookup"><span data-stu-id="cdfe2-130">M</span></span>|  
  
### <a name="examples"></a><span data-ttu-id="cdfe2-131">例</span><span class="sxs-lookup"><span data-stu-id="cdfe2-131">Examples</span></span>  
  
|<span data-ttu-id="cdfe2-132">式</span><span class="sxs-lookup"><span data-stu-id="cdfe2-132">Expression</span></span>|<span data-ttu-id="cdfe2-133">`DebugView` プロパティ</span><span class="sxs-lookup"><span data-stu-id="cdfe2-133">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`int num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="cdfe2-134">10</span><span class="sxs-lookup"><span data-stu-id="cdfe2-134">10</span></span>|  
|`double num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="cdfe2-135">10D</span><span class="sxs-lookup"><span data-stu-id="cdfe2-135">10D</span></span>|  
  
## <a name="blockexpression"></a><span data-ttu-id="cdfe2-136">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="cdfe2-136">BlockExpression</span></span>  
 <span data-ttu-id="cdfe2-137"><xref:System.Linq.Expressions.BlockExpression> オブジェクトの型が、ブロック内の最後の式の型と異なる場合、その型が `DebugInfo` プロパティに山かっこ (\< および >) で囲まれて表示されます。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-137">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="cdfe2-138">それ以外の場合、<xref:System.Linq.Expressions.BlockExpression> オブジェクトの型は表示されません。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-138">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="cdfe2-139">例</span><span class="sxs-lookup"><span data-stu-id="cdfe2-139">Examples</span></span>  
  
|<span data-ttu-id="cdfe2-140">式</span><span class="sxs-lookup"><span data-stu-id="cdfe2-140">Expression</span></span>|<span data-ttu-id="cdfe2-141">`DebugView` プロパティ</span><span class="sxs-lookup"><span data-stu-id="cdfe2-141">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`BlockExpression block = Expression.Block(Expression.Constant("test"));`|`.Block() {`<br /><br /> `"test"`<br /><br /> `}`|  
|`BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));`|`.Block<System.Object>() {`<br /><br /> `"test"`<br /><br /> `}`|  
  
## <a name="lambdaexpression"></a><span data-ttu-id="cdfe2-142">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="cdfe2-142">LambdaExpression</span></span>  
 <span data-ttu-id="cdfe2-143"><xref:System.Linq.Expressions.LambdaExpression> オブジェクトは、デリゲート型と共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-143"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>  
  
 <span data-ttu-id="cdfe2-144">ラムダ式に名前がない場合、`#Lambda1` や `#Lambda2` など、自動的に生成された名前が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-144">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="cdfe2-145">例</span><span class="sxs-lookup"><span data-stu-id="cdfe2-145">Examples</span></span>  
  
|<span data-ttu-id="cdfe2-146">式</span><span class="sxs-lookup"><span data-stu-id="cdfe2-146">Expression</span></span>|<span data-ttu-id="cdfe2-147">`DebugView` プロパティ</span><span class="sxs-lookup"><span data-stu-id="cdfe2-147">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));`|`.Lambda #Lambda1<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);`|`.Lambda SampleLambda<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
  
## <a name="labelexpression"></a><span data-ttu-id="cdfe2-148">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="cdfe2-148">LabelExpression</span></span>  
 <span data-ttu-id="cdfe2-149"><xref:System.Linq.Expressions.LabelExpression> オブジェクトの既定値を指定した場合、その値が <xref:System.Linq.Expressions.LabelTarget> オブジェクトの前に表示されます。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-149">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>  
  
 <span data-ttu-id="cdfe2-150">`.Label` トークンは、ラベルの開始を示します。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-150">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="cdfe2-151">`.LabelTarget` トークンは、ジャンプ先のターゲットを示します。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-151">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>  
  
 <span data-ttu-id="cdfe2-152">ラベルに名前がない場合、`#Label1` や `#Label2` など、自動的に生成された名前が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-152">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="cdfe2-153">例</span><span class="sxs-lookup"><span data-stu-id="cdfe2-153">Examples</span></span>  
  
|<span data-ttu-id="cdfe2-154">式</span><span class="sxs-lookup"><span data-stu-id="cdfe2-154">Expression</span></span>|<span data-ttu-id="cdfe2-155">`DebugView` プロパティ</span><span class="sxs-lookup"><span data-stu-id="cdfe2-155">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LabelTarget target = Expression.Label(typeof(int), "SampleLabel"); BlockExpression block = Expression.Block( Expression.Goto(target, Expression.Constant(0)), Expression.Label(target, Expression.Constant(-1)));`|`.Block() {`<br /><br /> `.Goto SampleLabel { 0 };`<br /><br /> `.Label`<br /><br /> `-1`<br /><br /> `.LabelTarget SampleLabel:`<br /><br /> `}`|  
|`LabelTarget target = Expression.Label(); BlockExpression block = Expression.Block( Expression.Goto(target5), Expression.Label(target5));`|`.Block() {`<br /><br /> `.Goto #Label1 { };`<br /><br /> `.Label`<br /><br /> `.LabelTarget #Label1:`<br /><br /> `}`|  
  
## <a name="checked-operators"></a><span data-ttu-id="cdfe2-156">checked 演算子</span><span class="sxs-lookup"><span data-stu-id="cdfe2-156">Checked Operators</span></span>  
 <span data-ttu-id="cdfe2-157">checked 演算子は、演算子の前に "#" 記号が付く形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-157">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="cdfe2-158">たとえば、checked 加算演算子は `#+` と表示されます。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-158">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="cdfe2-159">例</span><span class="sxs-lookup"><span data-stu-id="cdfe2-159">Examples</span></span>  
  
|<span data-ttu-id="cdfe2-160">式</span><span class="sxs-lookup"><span data-stu-id="cdfe2-160">Expression</span></span>|<span data-ttu-id="cdfe2-161">`DebugView` プロパティ</span><span class="sxs-lookup"><span data-stu-id="cdfe2-161">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));`|`1 #+ 2`|  
|`Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));`|`#(System.Int32)10D`|  
  
## <a name="see-also"></a><span data-ttu-id="cdfe2-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="cdfe2-162">See Also</span></span>  
 <span data-ttu-id="cdfe2-163">[式ツリー (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md) </span><span class="sxs-lookup"><span data-stu-id="cdfe2-163">[Expression Trees (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md) </span></span>  
 <span data-ttu-id="cdfe2-164">[Visual Studio でのデバッグ](/visualstudio/debugger/debugging-in-visual-studio) </span><span class="sxs-lookup"><span data-stu-id="cdfe2-164">[Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) </span></span>  
 [<span data-ttu-id="cdfe2-165">カスタム ビジュアライザーを作成する</span><span class="sxs-lookup"><span data-stu-id="cdfe2-165">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)

