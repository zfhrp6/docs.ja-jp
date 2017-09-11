---
title: "オブジェクトの種類 (Visual Basic) を決定する |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables, testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
caps.latest.revision: 13
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
ms.openlocfilehash: fec7a275029dde469425b651d5b1220cb21ddbf6
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="determining-object-type-visual-basic"></a><span data-ttu-id="bee54-102">オブジェクトの型の決定 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bee54-102">Determining Object Type (Visual Basic)</span></span>
<span data-ttu-id="bee54-103">汎用オブジェクト変数 (つまり、変数として宣言する`Object`) 任意のクラスからオブジェクトを保持できます。</span><span class="sxs-lookup"><span data-stu-id="bee54-103">Generic object variables (that is, variables you declare as `Object`) can hold objects from any class.</span></span> <span data-ttu-id="bee54-104">型の変数を使用するときに`Object`オブジェクトのクラスに基づいて異なるアクションを実行する必要があります。 たとえば、いくつかのオブジェクトがありますをサポートしません特定のプロパティまたはメソッドです。</span><span class="sxs-lookup"><span data-stu-id="bee54-104">When using variables of type `Object`, you may need to take different actions based on the class of the object; for example, some objects might not support a particular property or method.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="bee54-105">オブジェクト変数に保存するオブジェクトの種類を決定する&2; つの手段を提供します。、`TypeName`関数および`TypeOf...Is`演算子。</span><span class="sxs-lookup"><span data-stu-id="bee54-105"> provides two means of determining which type of object is stored in an object variable: the `TypeName` function and the `TypeOf...Is` operator.</span></span>  
  
## <a name="typename-and-typeofis"></a><span data-ttu-id="bee54-106">型名および TypeOf.します。</span><span class="sxs-lookup"><span data-stu-id="bee54-106">TypeName and TypeOf…Is</span></span>  
 <span data-ttu-id="bee54-107">`TypeName`関数は、文字列が返され、最適な選択肢は、次のコード フラグメントで示すように、表示、オブジェクトのクラス名を保管する必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="bee54-107">The `TypeName` function returns a string and is the best choice when you need to store or display the class name of an object, as shown in the following code fragment:</span></span>  
  
 <span data-ttu-id="bee54-108">[!code-vb[VbVbalrOOP #&92;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="bee54-108">[!code-vb[VbVbalrOOP#92](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_1.vb)]</span></span>  
  
 <span data-ttu-id="bee54-109">`TypeOf...Is`演算子には、オブジェクトの型をテストするための最適な選択肢があると等価な文字列比較を使用して、高速であるため`TypeName`です。</span><span class="sxs-lookup"><span data-stu-id="bee54-109">The `TypeOf...Is` operator is the best choice for testing an object's type, because it is much faster than an equivalent string comparison using `TypeName`.</span></span> <span data-ttu-id="bee54-110">次のコード片では`TypeOf...Is`内で、`If...Then...Else`ステートメント。</span><span class="sxs-lookup"><span data-stu-id="bee54-110">The following code fragment uses `TypeOf...Is` within an `If...Then...Else` statement:</span></span>  
  
 <span data-ttu-id="bee54-111">[!code-vb[VbVbalrOOP #&93;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="bee54-111">[!code-vb[VbVbalrOOP#93](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_2.vb)]</span></span>  
  
 <span data-ttu-id="bee54-112">注意事項はここで原因です。</span><span class="sxs-lookup"><span data-stu-id="bee54-112">A word of caution is due here.</span></span> <span data-ttu-id="bee54-113">`TypeOf...Is`演算子が返す`True`オブジェクトは、特定の種類のまたは特定の型から派生した場合。</span><span class="sxs-lookup"><span data-stu-id="bee54-113">The `TypeOf...Is` operator returns `True` if an object is of a specific type, or is derived from a specific type.</span></span> <span data-ttu-id="bee54-114">ほとんどすべての作業で[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]オブジェクトは、通常は文字列や整数などのオブジェクトの一種と考えるいくつかの要素を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="bee54-114">Almost everything you do with [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] involves objects, which include some elements not normally thought of as objects, such as strings and integers.</span></span> <span data-ttu-id="bee54-115">これらのオブジェクトから派生し、 <xref:System.Object>。</xref:System.Object>からメソッドを継承</span><span class="sxs-lookup"><span data-stu-id="bee54-115">These objects are derived from and inherit methods from <xref:System.Object>.</span></span> <span data-ttu-id="bee54-116">渡されるときに、`Integer`と評価された、 `Object`、`TypeOf...Is`演算子を返します`True`します。</span><span class="sxs-lookup"><span data-stu-id="bee54-116">When passed an `Integer` and evaluated with `Object`, the `TypeOf...Is` operator returns `True`.</span></span> <span data-ttu-id="bee54-117">次の例では、レポートをパラメーター`InParam`は両方とも、`Object`と`Integer`:</span><span class="sxs-lookup"><span data-stu-id="bee54-117">The following example reports that the parameter `InParam` is both an `Object` and an `Integer`:</span></span>  
  
 <span data-ttu-id="bee54-118">[!code-vb[VbVbalrOOP #&94;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="bee54-118">[!code-vb[VbVbalrOOP#94](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_3.vb)]</span></span>  
  
 <span data-ttu-id="bee54-119">次の例では、両方は使用して`TypeOf...Is`と`TypeName`内で渡されるオブジェクトの種類を決定する、`Ctrl`引数。</span><span class="sxs-lookup"><span data-stu-id="bee54-119">The following example uses both `TypeOf...Is` and `TypeName` to determine the type of object passed to it in the `Ctrl` argument.</span></span> <span data-ttu-id="bee54-120">`TestObject`プロシージャ呼び出し`ShowType`3 つの異なる種類のコントロールにします。</span><span class="sxs-lookup"><span data-stu-id="bee54-120">The `TestObject` procedure calls `ShowType` with three different kinds of controls.</span></span>  
  
#### <a name="to-run-the-example"></a><span data-ttu-id="bee54-121">例を実行するには</span><span class="sxs-lookup"><span data-stu-id="bee54-121">To run the example</span></span>  
  
1.  <span data-ttu-id="bee54-122">新しい Windows アプリケーション プロジェクトを作成し、追加、<xref:System.Windows.Forms.Button>コントロール、<xref:System.Windows.Forms.CheckBox>コントロール、および<xref:System.Windows.Forms.RadioButton>コントロールをフォーム</xref:System.Windows.Forms.RadioButton></xref:System.Windows.Forms.CheckBox></xref:System.Windows.Forms.Button>。</span><span class="sxs-lookup"><span data-stu-id="bee54-122">Create a new Windows Application project and add a <xref:System.Windows.Forms.Button> control, a <xref:System.Windows.Forms.CheckBox> control, and a <xref:System.Windows.Forms.RadioButton> control to the form.</span></span>  
  
2.  <span data-ttu-id="bee54-123">フォームのボタンから呼び出して、`TestObject`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="bee54-123">From the button on your form, call the `TestObject` procedure.</span></span>  
  
3.  <span data-ttu-id="bee54-124">次のコードをフォームに追加します。</span><span class="sxs-lookup"><span data-stu-id="bee54-124">Add the following code to your form:</span></span>  
  
     <span data-ttu-id="bee54-125">[!code-vb[VbVbalrOOP #&95;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="bee54-125">[!code-vb[VbVbalrOOP#95](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_4.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bee54-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="bee54-126">See Also</span></span>  
 <span data-ttu-id="bee54-127"><xref:Microsoft.VisualBasic.Information.TypeName%2A></xref:Microsoft.VisualBasic.Information.TypeName%2A></span><span class="sxs-lookup"><span data-stu-id="bee54-127"><xref:Microsoft.VisualBasic.Information.TypeName%2A></span></span>   
<span data-ttu-id="bee54-128"> [プロパティまたは文字列の名前を使用して、メソッドの呼び出し](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md) </span><span class="sxs-lookup"><span data-stu-id="bee54-128"> [Calling a Property or Method Using a String Name](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md) </span></span>  
<span data-ttu-id="bee54-129"> [オブジェクトのデータ型](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="bee54-129"> [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span></span>  
<span data-ttu-id="bee54-130"> [もし。。。そうしたら。。。Else ステートメント](../../../../visual-basic/language-reference/statements/if-then-else-statement.md) </span><span class="sxs-lookup"><span data-stu-id="bee54-130"> [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md) </span></span>  
<span data-ttu-id="bee54-131"> [文字列データ型](../../../../visual-basic/language-reference/data-types/string-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="bee54-131"> [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) </span></span>  
<span data-ttu-id="bee54-132"> [整数データ型](../../../../visual-basic/language-reference/data-types/integer-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="bee54-132"> [Integer Data Type](../../../../visual-basic/language-reference/data-types/integer-data-type.md)</span></span>
