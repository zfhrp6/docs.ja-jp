---
title: "Visual Studio (Visual Basic) で式ツリーのデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 84de749afad6abb748d0622561f8ee7cd399ed54
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="1aabb-102">Visual Studio (Visual Basic) で式ツリーのデバッグ</span><span class="sxs-lookup"><span data-stu-id="1aabb-102">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="1aabb-103">アプリケーションをデバッグするときは、構造と式ツリーの内容を分析できます。</span><span class="sxs-lookup"><span data-stu-id="1aabb-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="1aabb-104">式ツリー構造の簡単な概要を取得するには、使用することができます、`DebugView`プロパティで、デバッグ モードでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="1aabb-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which is available only in debug mode.</span></span> <span data-ttu-id="1aabb-105">デバッグの詳細については、次を参照してください。 [Visual Studio でのデバッグ](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio)します。</span><span class="sxs-lookup"><span data-stu-id="1aabb-105">For more information about debugging, see [Debugging in Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
 <span data-ttu-id="1aabb-106">式ツリーの内容をわかりやすく示した、`DebugView`プロパティは、Visual Studio ビジュアライザーを使用します。</span><span class="sxs-lookup"><span data-stu-id="1aabb-106">To better represent the content of expression trees, the `DebugView` property uses Visual Studio visualizers.</span></span> <span data-ttu-id="1aabb-107">詳細については、次を参照してください。[カスタム ビジュアライザーの作成](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)します。</span><span class="sxs-lookup"><span data-stu-id="1aabb-107">For more information, see [Create Custom Visualizers](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data).</span></span>  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="1aabb-108">式ツリーのビジュアライザーを開く</span><span class="sxs-lookup"><span data-stu-id="1aabb-108">To open a visualizer for an expression tree</span></span>  
  
1.  <span data-ttu-id="1aabb-109">横に表示される、虫眼鏡アイコンをクリックして、`DebugView`プロパティで、式ツリーの**データヒント**、**ウォッチ**ウィンドウで、 **[自動変数]**ウィンドウで、または**[ローカル]**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="1aabb-109">Click the magnifying glass icon that appears next to the `DebugView` property of an expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="1aabb-110">ビジュアライザーの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1aabb-110">A list of visualizers is displayed.</span></span>  
  
2.  <span data-ttu-id="1aabb-111">使用するビジュアライザーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1aabb-111">Click the visualizer you want to use.</span></span>  
  
 <span data-ttu-id="1aabb-112">各式の型は、次のセクションで説明されているビジュアライザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="1aabb-112">Each expression type is displayed in the visualizer as described in the following sections.</span></span>  
  
## <a name="parameterexpressions"></a><span data-ttu-id="1aabb-113">ParameterExpressions</span><span class="sxs-lookup"><span data-stu-id="1aabb-113">ParameterExpressions</span></span>  
 <span data-ttu-id="1aabb-114"><xref:System.Linq.Expressions.ParameterExpression>変数名には、先頭に「$」記号が表示されます。</xref:System.Linq.Expressions.ParameterExpression></span><span class="sxs-lookup"><span data-stu-id="1aabb-114"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>  
  
 <span data-ttu-id="1aabb-115">パラメーターが名前を持たない場合、名前が割り当てられます、自動的に生成されたなど`$var1`または`$var2`です。</span><span class="sxs-lookup"><span data-stu-id="1aabb-115">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="1aabb-116">例</span><span class="sxs-lookup"><span data-stu-id="1aabb-116">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer), "num")  
    ```  
  
     <span data-ttu-id="1aabb-117">`DebugView` プロパティ</span><span class="sxs-lookup"><span data-stu-id="1aabb-117">`DebugView` property</span></span>  
  
     `$num`  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer))  
    ```  
  
     <span data-ttu-id="1aabb-118">`DebugView` プロパティ</span><span class="sxs-lookup"><span data-stu-id="1aabb-118">`DebugView` property</span></span>  
  
     `$var1`  
  
## <a name="constantexpressions"></a><span data-ttu-id="1aabb-119">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="1aabb-119">ConstantExpressions</span></span>  
 <span data-ttu-id="1aabb-120"><xref:System.Linq.Expressions.ConstantExpression>、文字列、整数値を表すオブジェクトと`null`定数の値が表示されます</xref:System.Linq.Expressions.ConstantExpression>。</span><span class="sxs-lookup"><span data-stu-id="1aabb-120">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="1aabb-121">例</span><span class="sxs-lookup"><span data-stu-id="1aabb-121">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim num as Integer= 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     <span data-ttu-id="1aabb-122">`DebugView` プロパティ</span><span class="sxs-lookup"><span data-stu-id="1aabb-122">`DebugView` property</span></span>  
  
     <span data-ttu-id="1aabb-123">10</span><span class="sxs-lookup"><span data-stu-id="1aabb-123">10</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim num As Double = 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     <span data-ttu-id="1aabb-124">`DebugView` プロパティ</span><span class="sxs-lookup"><span data-stu-id="1aabb-124">`DebugView` property</span></span>  
  
     <span data-ttu-id="1aabb-125">10 日</span><span class="sxs-lookup"><span data-stu-id="1aabb-125">10D</span></span>  
  
## <a name="blockexpression"></a><span data-ttu-id="1aabb-126">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="1aabb-126">BlockExpression</span></span>  
 <span data-ttu-id="1aabb-127">場合の種類、<xref:System.Linq.Expressions.BlockExpression>オブジェクトは、ブロックの最後の式の型とは異なるに、型を表示、`DebugInfo`山かっこでプロパティ (\<と >).</xref:System.Linq.Expressions.BlockExpression></span><span class="sxs-lookup"><span data-stu-id="1aabb-127">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="1aabb-128">それ以外の場合の種類、<xref:System.Linq.Expressions.BlockExpression>オブジェクトは表示されません</xref:System.Linq.Expressions.BlockExpression>。</span><span class="sxs-lookup"><span data-stu-id="1aabb-128">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="1aabb-129">例</span><span class="sxs-lookup"><span data-stu-id="1aabb-129">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))  
    ```  
  
     <span data-ttu-id="1aabb-130">`DebugView` プロパティ</span><span class="sxs-lookup"><span data-stu-id="1aabb-130">`DebugView` property</span></span>  
  
     `.Block() {`  
  
     `"test"`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression =   
    Expression.Block(GetType(Object), Expression.Constant("test"))  
    ```  
  
     <span data-ttu-id="1aabb-131">`DebugView` プロパティ</span><span class="sxs-lookup"><span data-stu-id="1aabb-131">`DebugView` property</span></span>  
  
     `.Block<System.Object>() {`  
  
     `"test"`  
  
     `}`  
  
## <a name="lambdaexpression"></a><span data-ttu-id="1aabb-132">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="1aabb-132">LambdaExpression</span></span>  
 <span data-ttu-id="1aabb-133"><xref:System.Linq.Expressions.LambdaExpression>オブジェクトは、デリゲート型と共に表示されます。</xref:System.Linq.Expressions.LambdaExpression></span><span class="sxs-lookup"><span data-stu-id="1aabb-133"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>  
  
 <span data-ttu-id="1aabb-134">ラムダ式が名を持たない場合、名前が割り当てられます、自動的に生成されたなど`#Lambda1`または`#Lambda2`です。</span><span class="sxs-lookup"><span data-stu-id="1aabb-134">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="1aabb-135">例</span><span class="sxs-lookup"><span data-stu-id="1aabb-135">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))  
    ```  
  
     <span data-ttu-id="1aabb-136">`DebugView` プロパティ</span><span class="sxs-lookup"><span data-stu-id="1aabb-136">`DebugView` property</span></span>  
  
     `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLamda", Nothing)  
    ```  
  
     <span data-ttu-id="1aabb-137">`DebugView` プロパティ</span><span class="sxs-lookup"><span data-stu-id="1aabb-137">`DebugView` property</span></span>  
  
     `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
## <a name="labelexpression"></a><span data-ttu-id="1aabb-138">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="1aabb-138">LabelExpression</span></span>  
 <span data-ttu-id="1aabb-139">既定値を指定する場合、<xref:System.Linq.Expressions.LabelExpression>オブジェクトの前にこの値が表示されて、<xref:System.Linq.Expressions.LabelTarget>オブジェクト</xref:System.Linq.Expressions.LabelTarget></xref:System.Linq.Expressions.LabelExpression>。</span><span class="sxs-lookup"><span data-stu-id="1aabb-139">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>  
  
 <span data-ttu-id="1aabb-140">`.Label`トークンは、ラベルの先頭を指定します。</span><span class="sxs-lookup"><span data-stu-id="1aabb-140">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="1aabb-141">`.LabelTarget`トークンにジャンプ先のターゲットの送信先を示します。</span><span class="sxs-lookup"><span data-stu-id="1aabb-141">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>  
  
 <span data-ttu-id="1aabb-142">ラベルが名前を持たない場合、名前が割り当てられます、自動的に生成されたなど`#Label1`または`#Label2`です。</span><span class="sxs-lookup"><span data-stu-id="1aabb-142">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="1aabb-143">例</span><span class="sxs-lookup"><span data-stu-id="1aabb-143">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")  
    Dim label1 As BlockExpression = Expression.Block(  
    Expression.Goto(target, Expression.Constant(0)),  
    Expression.Label(target, Expression.Constant(-1)))  
    ```  
  
     <span data-ttu-id="1aabb-144">`DebugView` プロパティ</span><span class="sxs-lookup"><span data-stu-id="1aabb-144">`DebugView` property</span></span>  
  
     `.Block() {`  
  
     `.Goto SampleLabel { 0 };`  
  
     `.Label`  
  
     `-1`  
  
     `.LabelTarget SampleLabel:`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim target As LabelTarget = Expression.Label()  
    Dim block As BlockExpression = Expression.Block(  
    Expression.Goto(target), Expression.Label(target))  
    ```  
  
     <span data-ttu-id="1aabb-145">`DebugView` プロパティ</span><span class="sxs-lookup"><span data-stu-id="1aabb-145">`DebugView` property</span></span>  
  
     `.Block() {`  
  
     `.Goto #Label1 { };`  
  
     `.Label`  
  
     `.LabelTarget #Label1:`  
  
     `}`  
  
## <a name="checked-operators"></a><span data-ttu-id="1aabb-146">Checked 演算子</span><span class="sxs-lookup"><span data-stu-id="1aabb-146">Checked Operators</span></span>  
 <span data-ttu-id="1aabb-147">Checked 演算子は、演算子の前に「#」記号が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1aabb-147">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="1aabb-148">チェックされた加算演算子として表示するなどの`#+`です。</span><span class="sxs-lookup"><span data-stu-id="1aabb-148">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="1aabb-149">例</span><span class="sxs-lookup"><span data-stu-id="1aabb-149">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.AddChecked(  
    Expression.Constant(1), Expression.Constant(2))  
    ```  
  
     <span data-ttu-id="1aabb-150">`DebugView` プロパティ</span><span class="sxs-lookup"><span data-stu-id="1aabb-150">`DebugView` property</span></span>  
  
     `1 #+ 2`  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.ConvertChecked(  
    Expression.Constant(10.0), GetType(Integer))  
    ```  
  
     <span data-ttu-id="1aabb-151">`DebugView` プロパティ</span><span class="sxs-lookup"><span data-stu-id="1aabb-151">`DebugView` property</span></span>  
  
     `#(System.Int32)10D`  
  
## <a name="see-also"></a><span data-ttu-id="1aabb-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="1aabb-152">See Also</span></span>  
 <span data-ttu-id="1aabb-153">[式ツリー (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md) </span><span class="sxs-lookup"><span data-stu-id="1aabb-153">[Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md) </span></span>  
<span data-ttu-id="1aabb-154"> [Visual Studio でのデバッグ](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio) </span><span class="sxs-lookup"><span data-stu-id="1aabb-154"> [Debugging in Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio) </span></span>  
<span data-ttu-id="1aabb-155"> [カスタム ビジュアライザーを作成します。](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)</span><span class="sxs-lookup"><span data-stu-id="1aabb-155"> [Create Custom Visualizers](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)</span></span>
