---
title: オブジェクト変数の値 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: a5152ad0e5e5ac876783c2b191ee13e845593df8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="object-variable-values-visual-basic"></a><span data-ttu-id="f456b-102">オブジェクト変数の値 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f456b-102">Object Variable Values (Visual Basic)</span></span>
<span data-ttu-id="f456b-103">変数、[オブジェクト データ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)できる任意の型のデータを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f456b-103">A variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) can refer to data of any type.</span></span> <span data-ttu-id="f456b-104">格納した値、`Object`変数が保持される他の場所で、メモリ内一方変数自体は、データへのポインターを保持します。</span><span class="sxs-lookup"><span data-stu-id="f456b-104">The value you store in an `Object` variable is kept elsewhere in memory, while the variable itself holds a pointer to the data.</span></span>  
  
## <a name="object-classifier-functions"></a><span data-ttu-id="f456b-105">オブジェクトの分類子関数</span><span class="sxs-lookup"><span data-stu-id="f456b-105">Object Classifier Functions</span></span>  
 <span data-ttu-id="f456b-106">Visual Basic には、新機能に関する情報を返す関数が用意されて、`Object`変数は、次の表に示すように参照します。</span><span class="sxs-lookup"><span data-stu-id="f456b-106">Visual Basic supplies functions that return information about what an `Object` variable refers to, as shown in the following table.</span></span>  
  
|<span data-ttu-id="f456b-107">関数</span><span class="sxs-lookup"><span data-stu-id="f456b-107">Function</span></span>|<span data-ttu-id="f456b-108">オブジェクト変数を参照する場合は True を返します</span><span class="sxs-lookup"><span data-stu-id="f456b-108">Returns True if the Object variable refers to</span></span>|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|<span data-ttu-id="f456b-109">1 つの値ではなく、値の配列</span><span class="sxs-lookup"><span data-stu-id="f456b-109">An array of values, rather than a single value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|<span data-ttu-id="f456b-110">A [Date データ型](../../../../visual-basic/language-reference/data-types/date-data-type.md)値、または日付と時刻の値として解釈できる文字列</span><span class="sxs-lookup"><span data-stu-id="f456b-110">A [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) value, or a string that can be interpreted as a date and time value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|<span data-ttu-id="f456b-111">型のオブジェクト<xref:System.DBNull>、または存在しないデータを表します</span><span class="sxs-lookup"><span data-stu-id="f456b-111">An object of type <xref:System.DBNull>, which represents missing or nonexistent data</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|<span data-ttu-id="f456b-112">派生する例外オブジェクト <xref:System.Exception></span><span class="sxs-lookup"><span data-stu-id="f456b-112">An exception object, which derives from <xref:System.Exception></span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|<span data-ttu-id="f456b-113">[何も](../../../../visual-basic/language-reference/nothing.md)、つまり、オブジェクトに現在割り当てられていない変数</span><span class="sxs-lookup"><span data-stu-id="f456b-113">[Nothing](../../../../visual-basic/language-reference/nothing.md), that is, no object is currently assigned to the variable</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|<span data-ttu-id="f456b-114">数値、または数値として解釈できる文字列</span><span class="sxs-lookup"><span data-stu-id="f456b-114">A number, or a string that can be interpreted as a number</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|<span data-ttu-id="f456b-115">参照型 (文字列、配列、デリゲート、クラス型など)</span><span class="sxs-lookup"><span data-stu-id="f456b-115">A reference type (such as a string, array, delegate, or class type)</span></span>|  
  
 <span data-ttu-id="f456b-116">これらの関数を使用して、操作またはプロシージャに無効な値の送信を回避することができます。</span><span class="sxs-lookup"><span data-stu-id="f456b-116">You can use these functions to avoid submitting an invalid value to an operation or a procedure.</span></span>  
  
## <a name="typeof-operator"></a><span data-ttu-id="f456b-117">TypeOf 演算子</span><span class="sxs-lookup"><span data-stu-id="f456b-117">TypeOf Operator</span></span>  
 <span data-ttu-id="f456b-118">使用することも、 [TypeOf 演算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)をオブジェクト変数が現在特定のデータ型を参照しているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="f456b-118">You can also use the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to determine whether an object variable currently refers to a specific data type.</span></span> <span data-ttu-id="f456b-119">`TypeOf`しています.`Is`式に評価される`True`オペランドの実行時の型から派生した、または指定された型を実装する場合。</span><span class="sxs-lookup"><span data-stu-id="f456b-119">The `TypeOf`...`Is` expression evaluates to `True` if the run-time type of the operand is derived from or implements the specified type.</span></span>  
  
 <span data-ttu-id="f456b-120">次の例では`TypeOf`値型と参照型を参照するオブジェクト変数です。</span><span class="sxs-lookup"><span data-stu-id="f456b-120">The following example uses `TypeOf` on object variables referring to value and reference types.</span></span>  
  
```  
' The following statement puts a value type (Integer) in an Object variable.  
Dim num As Object = 10  
' The following statement puts a reference type (Form) in an Object variable.  
Dim frm As Object = New Form()  
If TypeOf num Is Long Then Debug.WriteLine("num is Long")  
If TypeOf num Is Integer Then Debug.WriteLine("num is Integer")  
If TypeOf num Is Short Then Debug.WriteLine("num is Short")  
If TypeOf num Is Object Then Debug.WriteLine("num is Object")  
If TypeOf frm Is Form Then Debug.WriteLine("frm is Form")  
If TypeOf frm Is Label Then Debug.WriteLine("frm is Label")  
If TypeOf frm Is Object Then Debug.WriteLine("frm is Object")  
```  
  
 <span data-ttu-id="f456b-121">上記の例では、以下の行、**デバッグ**ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="f456b-121">The preceding example writes the following lines to the **Debug** window:</span></span>  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 <span data-ttu-id="f456b-122">オブジェクト変数`num`型のデータを指す`Integer`、および`frm`クラスのオブジェクトを指す<xref:System.Windows.Forms.Form>です。</span><span class="sxs-lookup"><span data-stu-id="f456b-122">The object variable `num` refers to data of type `Integer`, and `frm` refers to an object of class <xref:System.Windows.Forms.Form>.</span></span>  
  
## <a name="object-arrays"></a><span data-ttu-id="f456b-123">オブジェクトの配列</span><span class="sxs-lookup"><span data-stu-id="f456b-123">Object Arrays</span></span>  
 <span data-ttu-id="f456b-124">配列を宣言および使用する`Object`変数。</span><span class="sxs-lookup"><span data-stu-id="f456b-124">You can declare and use an array of `Object` variables.</span></span> <span data-ttu-id="f456b-125">これは、さまざまなデータ型とオブジェクトのクラスを処理する必要がある場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="f456b-125">This is useful when you need to handle a variety of data types and object classes.</span></span> <span data-ttu-id="f456b-126">配列内のすべての要素は同じ宣言されたデータ型が必要です。</span><span class="sxs-lookup"><span data-stu-id="f456b-126">All the elements in an array must have the same declared data type.</span></span> <span data-ttu-id="f456b-127">このデータ型として宣言する`Object`オブジェクトを格納し、クラス、配列内の他のデータ型と共にインスタンスことができます。</span><span class="sxs-lookup"><span data-stu-id="f456b-127">Declaring this data type as `Object` allows you to store objects and class instances alongside other data types in the array.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f456b-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="f456b-128">See Also</span></span>  
 [<span data-ttu-id="f456b-129">オブジェクト変数</span><span class="sxs-lookup"><span data-stu-id="f456b-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="f456b-130">オブジェクト変数の宣言</span><span class="sxs-lookup"><span data-stu-id="f456b-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="f456b-131">オブジェクト変数の代入</span><span class="sxs-lookup"><span data-stu-id="f456b-131">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="f456b-132">方法: オブジェクトの現在のインスタンスを参照する</span><span class="sxs-lookup"><span data-stu-id="f456b-132">How to: Refer to the Current Instance of an Object</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)  
 [<span data-ttu-id="f456b-133">方法: オブジェクト変数で参照している型を確認する</span><span class="sxs-lookup"><span data-stu-id="f456b-133">How to: Determine What Type an Object Variable Refers To</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)  
 [<span data-ttu-id="f456b-134">方法: 2 つのオブジェクトが関連しているかどうかを決める</span><span class="sxs-lookup"><span data-stu-id="f456b-134">How to: Determine Whether Two Objects Are Related</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [<span data-ttu-id="f456b-135">方法: 2 つのオブジェクトが同一であるかどうか判別する</span><span class="sxs-lookup"><span data-stu-id="f456b-135">How to: Determine Whether Two Objects Are Identical</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)  
 [<span data-ttu-id="f456b-136">データの種類</span><span class="sxs-lookup"><span data-stu-id="f456b-136">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
