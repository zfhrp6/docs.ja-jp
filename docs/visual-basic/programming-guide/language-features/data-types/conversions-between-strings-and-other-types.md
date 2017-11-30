---
title: "文字列とその他の型との変換 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 71ece18d4ce33b7b637410110e825b389affcd67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a><span data-ttu-id="18700-102">文字列とその他の型との変換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18700-102">Conversions Between Strings and Other Types (Visual Basic)</span></span>
<span data-ttu-id="18700-103">数値を変換する`Boolean`、または日付/時刻値を`String`です。</span><span class="sxs-lookup"><span data-stu-id="18700-103">You can convert a numeric, `Boolean`, or date/time value to a `String`.</span></span> <span data-ttu-id="18700-104">逆方向に変換することもできます。-数値、文字列値から`Boolean`、または`Date`— 先のデータ型の有効な値として解釈される場合、文字列の内容。</span><span class="sxs-lookup"><span data-stu-id="18700-104">You can also convert in the reverse direction — from a string value to numeric, `Boolean`, or `Date` — provided the contents of the string can be interpreted as a valid value of the destination data type.</span></span> <span data-ttu-id="18700-105">できない場合は、実行時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="18700-105">If they cannot, a run-time error occurs.</span></span>  
  
 <span data-ttu-id="18700-106">いずれかの方向で、これらすべての割り当ては縮小変換します。</span><span class="sxs-lookup"><span data-stu-id="18700-106">The conversions for all these assignments, in either direction, are narrowing conversions.</span></span> <span data-ttu-id="18700-107">型変換のキーワードを使用する必要があります (`CBool`、 `CByte`、 `CDate`、 `CDbl`、 `CDec`、 `CInt`、 `CLng`、 `CSByte`、 `CShort`、 `CSng`、 `CStr`、`CUInt`、 `CULng`、 `CUShort`、および`CType`)。</span><span class="sxs-lookup"><span data-stu-id="18700-107">You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`).</span></span> <span data-ttu-id="18700-108"><xref:Microsoft.VisualBasic.Strings.Format%2A>と<xref:Microsoft.VisualBasic.Conversion.Val%2A>関数は、文字列や数値の間の変換の詳細に制御を提供します。</span><span class="sxs-lookup"><span data-stu-id="18700-108">The <xref:Microsoft.VisualBasic.Strings.Format%2A> and <xref:Microsoft.VisualBasic.Conversion.Val%2A> functions give you additional control over conversions between strings and numbers.</span></span>  
  
 <span data-ttu-id="18700-109">クラスまたは構造体を定義した場合は、間の型変換演算子を定義できます`String`とクラスまたは構造体の型。</span><span class="sxs-lookup"><span data-stu-id="18700-109">If you have defined a class or structure, you can define type conversion operators between `String` and the type of your class or structure.</span></span> <span data-ttu-id="18700-110">詳細については、次を参照してください。[する方法: 変換演算子を定義する](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)です。</span><span class="sxs-lookup"><span data-stu-id="18700-110">For more information, see [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="conversion-of-numbers-to-strings"></a><span data-ttu-id="18700-111">数値の文字列への変換</span><span class="sxs-lookup"><span data-stu-id="18700-111">Conversion of Numbers to Strings</span></span>  
 <span data-ttu-id="18700-112">使用することができます、`Format`だけでなく、適切な桁の数字を含めることができます、書式設定された文字列を数値に変換する機能しますが、ありますも通貨記号などのシンボルの書式設定 (など`$`)、何千もの区切り記号または*桁区切りシンボル*(など`,`)、および小数点記号 (など`.`)。</span><span class="sxs-lookup"><span data-stu-id="18700-112">You can use the `Format` function to convert a number to a formatted string, which can include not only the appropriate digits but also formatting symbols such as a currency sign (such as `$`), thousands separators or *digit grouping symbols* (such as `,`), and a decimal separator (such as `.`).</span></span> <span data-ttu-id="18700-113">`Format`に従って適切なシンボルを自動的に使用して、**地域のオプション**、Windows で指定された設定**コントロール パネルの **です。</span><span class="sxs-lookup"><span data-stu-id="18700-113">`Format` automatically uses the appropriate symbols according to the **Regional Options** settings specified in the Windows **Control Panel**.</span></span>  
  
 <span data-ttu-id="18700-114">なお、連結したもの (`&`) 演算子は文字列に数値を暗黙的に、次の例のように変換できます。</span><span class="sxs-lookup"><span data-stu-id="18700-114">Note that the concatenation (`&`) operator can convert a number to a string implicitly, as the following example shows.</span></span>  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a><span data-ttu-id="18700-115">数値の文字列の変換</span><span class="sxs-lookup"><span data-stu-id="18700-115">Conversion of Strings to Numbers</span></span>  
 <span data-ttu-id="18700-116">使用することができます、`Val`関数を明示的に文字列内の数字を数値に変換します。</span><span class="sxs-lookup"><span data-stu-id="18700-116">You can use the `Val` function to explicitly convert the digits in a string to a number.</span></span> <span data-ttu-id="18700-117">`Val`数字、スペース、タブ、改行、またはピリオド以外の文字を検出するまでは、文字列を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="18700-117">`Val` reads the string until it encounters a character other than a digit, space, tab, line feed, or period.</span></span> <span data-ttu-id="18700-118">シーケンスは、"& O"と「(& H)」と、数値の底を変更して、スキャンが終了します。</span><span class="sxs-lookup"><span data-stu-id="18700-118">The sequences "&O" and "&H" alter the base of the number system and terminate the scanning.</span></span> <span data-ttu-id="18700-119">読み取りを停止するまで`Val`すべての適切な文字の数値に変換します。</span><span class="sxs-lookup"><span data-stu-id="18700-119">Until it stops reading, `Val` converts all appropriate characters to a numeric value.</span></span> <span data-ttu-id="18700-120">たとえば、次のステートメントが、値を返す`141.825`です。</span><span class="sxs-lookup"><span data-stu-id="18700-120">For example, the following statement returns the value `141.825`.</span></span>  
  
 `Val("   14   1.825 miles")`  
  
 <span data-ttu-id="18700-121">ときに[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]、文字列、数値に変換を使用して、**地域のオプション**、Windows の設定**コントロール パネルの **桁を解釈する区切り記号、桁区切り記号、および通貨記号。</span><span class="sxs-lookup"><span data-stu-id="18700-121">When [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] converts a string to a numeric value, it uses the **Regional Options** settings specified in the Windows **Control Panel** to interpret the thousands separator, decimal separator, and currency symbol.</span></span> <span data-ttu-id="18700-122">これは、変換は成功可能性がありますも、別の設定の 1 つ下にあることを意味します。</span><span class="sxs-lookup"><span data-stu-id="18700-122">This means that a conversion might succeed under one setting but not another.</span></span> <span data-ttu-id="18700-123">たとえば、`"$14.20"`が許容される任意のフランス語のロケールではなく、英語 (米国) ロケールにします。</span><span class="sxs-lookup"><span data-stu-id="18700-123">For example, `"$14.20"` is acceptable in the English (United States) locale but not in any French locale.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18700-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="18700-124">See Also</span></span>  
 [<span data-ttu-id="18700-125">Visual Basic での型変換</span><span class="sxs-lookup"><span data-stu-id="18700-125">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="18700-126">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="18700-126">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="18700-127">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="18700-127">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="18700-128">方法: オブジェクトを Visual Basic での別の型に変換</span><span class="sxs-lookup"><span data-stu-id="18700-128">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [<span data-ttu-id="18700-129">配列変換</span><span class="sxs-lookup"><span data-stu-id="18700-129">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [<span data-ttu-id="18700-130">データの種類</span><span class="sxs-lookup"><span data-stu-id="18700-130">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="18700-131">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="18700-131">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="18700-132">.NET Framework ベースの国際対応アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="18700-132">Introduction to International Applications Based on the .NET Framework</span></span>](/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)
