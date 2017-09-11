---
title: "オブジェクト変数の値 (Visual Basic) |Microsoft ドキュメント"
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
helpviewer_keywords:
- object variables, values
- values, of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 5f42706a79212ae523b08ee336fdcacb3f761af6
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="object-variable-values-visual-basic"></a><span data-ttu-id="7b08c-102">オブジェクト変数の値 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b08c-102">Object Variable Values (Visual Basic)</span></span>
<span data-ttu-id="7b08c-103">変数、 [Object データ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)できる任意の型のデータを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b08c-103">A variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) can refer to data of any type.</span></span> <span data-ttu-id="7b08c-104">格納した値、`Object`変数が保持される他の場所で、メモリ内一方、変数自体が、データへのポインターを保持します。</span><span class="sxs-lookup"><span data-stu-id="7b08c-104">The value you store in an `Object` variable is kept elsewhere in memory, while the variable itself holds a pointer to the data.</span></span>  
  
## <a name="object-classifier-functions"></a><span data-ttu-id="7b08c-105">オブジェクトの分類子関数</span><span class="sxs-lookup"><span data-stu-id="7b08c-105">Object Classifier Functions</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="7b08c-106">内容に関する情報を返す関数が用意されて、`Object`変数は、次の表に示すように参照します。</span><span class="sxs-lookup"><span data-stu-id="7b08c-106"> supplies functions that return information about what an `Object` variable refers to, as shown in the following table.</span></span>  
  
|<span data-ttu-id="7b08c-107">関数</span><span class="sxs-lookup"><span data-stu-id="7b08c-107">Function</span></span>|<span data-ttu-id="7b08c-108">オブジェクト変数を指す場合、True を返します</span><span class="sxs-lookup"><span data-stu-id="7b08c-108">Returns True if the Object variable refers to</span></span>|  
|--------------|---------------------------------------------------|  
|<span data-ttu-id="7b08c-109"><xref:Microsoft.VisualBasic.Information.IsArray%2A></xref:Microsoft.VisualBasic.Information.IsArray%2A></span><span class="sxs-lookup"><span data-stu-id="7b08c-109"><xref:Microsoft.VisualBasic.Information.IsArray%2A></span></span>|<span data-ttu-id="7b08c-110">1 つの値ではなく、値の配列</span><span class="sxs-lookup"><span data-stu-id="7b08c-110">An array of values, rather than a single value</span></span>|  
|<span data-ttu-id="7b08c-111"><xref:Microsoft.VisualBasic.Information.IsDate%2A></xref:Microsoft.VisualBasic.Information.IsDate%2A></span><span class="sxs-lookup"><span data-stu-id="7b08c-111"><xref:Microsoft.VisualBasic.Information.IsDate%2A></span></span>|<span data-ttu-id="7b08c-112">A [Date データ型](../../../../visual-basic/language-reference/data-types/date-data-type.md)値、または日付と時刻の値として解釈できる文字列</span><span class="sxs-lookup"><span data-stu-id="7b08c-112">A [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) value, or a string that can be interpreted as a date and time value</span></span>|  
|<span data-ttu-id="7b08c-113"><xref:Microsoft.VisualBasic.Information.IsDBNull%2A></xref:Microsoft.VisualBasic.Information.IsDBNull%2A></span><span class="sxs-lookup"><span data-stu-id="7b08c-113"><xref:Microsoft.VisualBasic.Information.IsDBNull%2A></span></span>|<span data-ttu-id="7b08c-114">型<xref:System.DBNull>、または存在しないデータを表す</xref:System.DBNull>オブジェクト</span><span class="sxs-lookup"><span data-stu-id="7b08c-114">An object of type <xref:System.DBNull>, which represents missing or nonexistent data</span></span>|  
|<span data-ttu-id="7b08c-115"><xref:Microsoft.VisualBasic.Information.IsError%2A></xref:Microsoft.VisualBasic.Information.IsError%2A></span><span class="sxs-lookup"><span data-stu-id="7b08c-115"><xref:Microsoft.VisualBasic.Information.IsError%2A></span></span>|<span data-ttu-id="7b08c-116">派生する例外オブジェクト<xref:System.Exception></xref:System.Exception></span><span class="sxs-lookup"><span data-stu-id="7b08c-116">An exception object, which derives from <xref:System.Exception></span></span>|  
|<span data-ttu-id="7b08c-117"><xref:Microsoft.VisualBasic.Information.IsNothing%2A></xref:Microsoft.VisualBasic.Information.IsNothing%2A></span><span class="sxs-lookup"><span data-stu-id="7b08c-117"><xref:Microsoft.VisualBasic.Information.IsNothing%2A></span></span>|<span data-ttu-id="7b08c-118">[何も](../../../../visual-basic/language-reference/nothing.md)、つまり、オブジェクトに現在割り当てられていない変数</span><span class="sxs-lookup"><span data-stu-id="7b08c-118">[Nothing](../../../../visual-basic/language-reference/nothing.md), that is, no object is currently assigned to the variable</span></span>|  
|<span data-ttu-id="7b08c-119"><xref:Microsoft.VisualBasic.Information.IsNumeric%2A></xref:Microsoft.VisualBasic.Information.IsNumeric%2A></span><span class="sxs-lookup"><span data-stu-id="7b08c-119"><xref:Microsoft.VisualBasic.Information.IsNumeric%2A></span></span>|<span data-ttu-id="7b08c-120">数値、または数値として解釈できる文字列</span><span class="sxs-lookup"><span data-stu-id="7b08c-120">A number, or a string that can be interpreted as a number</span></span>|  
|<span data-ttu-id="7b08c-121"><xref:Microsoft.VisualBasic.Information.IsReference%2A></xref:Microsoft.VisualBasic.Information.IsReference%2A></span><span class="sxs-lookup"><span data-stu-id="7b08c-121"><xref:Microsoft.VisualBasic.Information.IsReference%2A></span></span>|<span data-ttu-id="7b08c-122">参照型 (文字列、配列、デリゲート、クラス型など)</span><span class="sxs-lookup"><span data-stu-id="7b08c-122">A reference type (such as a string, array, delegate, or class type)</span></span>|  
  
 <span data-ttu-id="7b08c-123">これらの関数を使用すると、無効な値を操作またはプロシージャの送信を回避します。</span><span class="sxs-lookup"><span data-stu-id="7b08c-123">You can use these functions to avoid submitting an invalid value to an operation or a procedure.</span></span>  
  
## <a name="typeof-operator"></a><span data-ttu-id="7b08c-124">TypeOf 演算子</span><span class="sxs-lookup"><span data-stu-id="7b08c-124">TypeOf Operator</span></span>  
 <span data-ttu-id="7b08c-125">使用することも、 [TypeOf 演算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)オブジェクト変数が現在特定のデータ型を表しているかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="7b08c-125">You can also use the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to determine whether an object variable currently refers to a specific data type.</span></span> <span data-ttu-id="7b08c-126">The `TypeOf`...`Is`式に評価される`True`オペランドの実行時の型から派生した、または指定された型を実装する場合。</span><span class="sxs-lookup"><span data-stu-id="7b08c-126">The `TypeOf`...`Is` expression evaluates to `True` if the run-time type of the operand is derived from or implements the specified type.</span></span>  
  
 <span data-ttu-id="7b08c-127">次の例では使用`TypeOf`オブジェクト変数の値と参照型を参照します。</span><span class="sxs-lookup"><span data-stu-id="7b08c-127">The following example uses `TypeOf` on object variables referring to value and reference types.</span></span>  
  
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
  
 <span data-ttu-id="7b08c-128">上記の例では、次の行を**デバッグ**ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="7b08c-128">The preceding example writes the following lines to the **Debug** window:</span></span>  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 <span data-ttu-id="7b08c-129">オブジェクト変数`num`型のデータを指す`Integer`、および`frm` <xref:System.Windows.Forms.Form>.</xref:System.Windows.Forms.Form>クラスのオブジェクトを参照</span><span class="sxs-lookup"><span data-stu-id="7b08c-129">The object variable `num` refers to data of type `Integer`, and `frm` refers to an object of class <xref:System.Windows.Forms.Form>.</span></span>  
  
## <a name="object-arrays"></a><span data-ttu-id="7b08c-130">オブジェクトの配列</span><span class="sxs-lookup"><span data-stu-id="7b08c-130">Object Arrays</span></span>  
 <span data-ttu-id="7b08c-131">配列を宣言および使用する`Object`変数です。</span><span class="sxs-lookup"><span data-stu-id="7b08c-131">You can declare and use an array of `Object` variables.</span></span> <span data-ttu-id="7b08c-132">これは、さまざまなデータ型とオブジェクトのクラスを処理する必要がある場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="7b08c-132">This is useful when you need to handle a variety of data types and object classes.</span></span> <span data-ttu-id="7b08c-133">配列内のすべての要素には、宣言されたデータ型は同じ必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b08c-133">All the elements in an array must have the same declared data type.</span></span> <span data-ttu-id="7b08c-134">このデータ型として宣言する`Object`オブジェクトを格納し、クラスのインスタンスは、配列内の他のデータ型と並行することができます。</span><span class="sxs-lookup"><span data-stu-id="7b08c-134">Declaring this data type as `Object` allows you to store objects and class instances alongside other data types in the array.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b08c-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b08c-135">See Also</span></span>  
 <span data-ttu-id="7b08c-136">[オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span><span class="sxs-lookup"><span data-stu-id="7b08c-136">[Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span></span>  
<span data-ttu-id="7b08c-137"> [オブジェクト変数の宣言](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="7b08c-137"> [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md) </span></span>  
<span data-ttu-id="7b08c-138"> [オブジェクト変数の代入](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md) </span><span class="sxs-lookup"><span data-stu-id="7b08c-138"> [Object Variable Assignment](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md) </span></span>  
<span data-ttu-id="7b08c-139"> [方法: オブジェクトの現在のインスタンスを参照してください](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md) </span><span class="sxs-lookup"><span data-stu-id="7b08c-139"> [How to: Refer to the Current Instance of an Object](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md) </span></span>  
<span data-ttu-id="7b08c-140"> [方法: オブジェクト変数が指す型を確認](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md) </span><span class="sxs-lookup"><span data-stu-id="7b08c-140"> [How to: Determine What Type an Object Variable Refers To](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md) </span></span>  
<span data-ttu-id="7b08c-141"> [方法:&2; つのオブジェクトが関連するかどうかを判別します。](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md) </span><span class="sxs-lookup"><span data-stu-id="7b08c-141"> [How to: Determine Whether Two Objects Are Related](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md) </span></span>  
<span data-ttu-id="7b08c-142"> [方法:&2; つのオブジェクトが同一かどうかを判断します。](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md) </span><span class="sxs-lookup"><span data-stu-id="7b08c-142"> [How to: Determine Whether Two Objects Are Identical](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md) </span></span>  
<span data-ttu-id="7b08c-143"> [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)</span><span class="sxs-lookup"><span data-stu-id="7b08c-143"> [Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md)</span></span>
