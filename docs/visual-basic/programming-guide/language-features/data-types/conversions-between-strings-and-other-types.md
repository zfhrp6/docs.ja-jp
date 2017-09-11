---
title: "文字列とその他の型 (Visual Basic) 間で変換 |Microsoft ドキュメント"
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
- data type conversion, string
- conversions, type
- string conversion
- conversions, data type
- type conversion, string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
caps.latest.revision: 16
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
ms.openlocfilehash: 34eb32cb6e640d681db6853aaa164d84acca7e4f
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a><span data-ttu-id="2a002-102">文字列とその他の型との変換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a002-102">Conversions Between Strings and Other Types (Visual Basic)</span></span>
<span data-ttu-id="2a002-103">数値を変換する`Boolean`、または日付/時刻値を`String`です。</span><span class="sxs-lookup"><span data-stu-id="2a002-103">You can convert a numeric, `Boolean`, or date/time value to a `String`.</span></span> <span data-ttu-id="2a002-104">逆方向に変換することもできます。-数値、文字列値から`Boolean`、または`Date`: 文字列の内容はマッピング先データ型の有効な値として解釈されることができます。</span><span class="sxs-lookup"><span data-stu-id="2a002-104">You can also convert in the reverse direction — from a string value to numeric, `Boolean`, or `Date` — provided the contents of the string can be interpreted as a valid value of the destination data type.</span></span> <span data-ttu-id="2a002-105">できない場合は、実行時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="2a002-105">If they cannot, a run-time error occurs.</span></span>  
  
 <span data-ttu-id="2a002-106">どちらの方向に、これらすべての代入の変換には縮小変換を使用します。</span><span class="sxs-lookup"><span data-stu-id="2a002-106">The conversions for all these assignments, in either direction, are narrowing conversions.</span></span> <span data-ttu-id="2a002-107">You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`).</span><span class="sxs-lookup"><span data-stu-id="2a002-107">You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`).</span></span> <span data-ttu-id="2a002-108"><xref:Microsoft.VisualBasic.Strings.Format%2A>と<xref:Microsoft.VisualBasic.Conversion.Val%2A>関数は、文字列や数値の間の変換の詳細に制御を提供します</xref:Microsoft.VisualBasic.Conversion.Val%2A></xref:Microsoft.VisualBasic.Strings.Format%2A>。</span><span class="sxs-lookup"><span data-stu-id="2a002-108">The <xref:Microsoft.VisualBasic.Strings.Format%2A> and <xref:Microsoft.VisualBasic.Conversion.Val%2A> functions give you additional control over conversions between strings and numbers.</span></span>  
  
 <span data-ttu-id="2a002-109">クラスまたは構造体を定義した場合は、間の型変換演算子を定義できます`String`とクラスまたは構造体の型。</span><span class="sxs-lookup"><span data-stu-id="2a002-109">If you have defined a class or structure, you can define type conversion operators between `String` and the type of your class or structure.</span></span> <span data-ttu-id="2a002-110">詳細については、次を参照してください。[方法: 変換演算子を定義する](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)です。</span><span class="sxs-lookup"><span data-stu-id="2a002-110">For more information, see [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="conversion-of-numbers-to-strings"></a><span data-ttu-id="2a002-111">数値の文字列への変換</span><span class="sxs-lookup"><span data-stu-id="2a002-111">Conversion of Numbers to Strings</span></span>  
 <span data-ttu-id="2a002-112">使用することができます、`Format`だけでなく、適切な桁の数字を含めることができます、書式設定された文字列に数値を変換する機能しますが、通貨記号などのシンボルの書式設定も (など`$`)、何千もの区切り記号または*桁区切り記号*(など`,`)、および小数点記号 (など`.`)。</span><span class="sxs-lookup"><span data-stu-id="2a002-112">You can use the `Format` function to convert a number to a formatted string, which can include not only the appropriate digits but also formatting symbols such as a currency sign (such as `$`), thousands separators or *digit grouping symbols* (such as `,`), and a decimal separator (such as `.`).</span></span> <span data-ttu-id="2a002-113">`Format`」の手順に従って適切なシンボルを自動的に使用して、**地域のオプション**、Windows で指定された設定**コントロール パネルの **します。</span><span class="sxs-lookup"><span data-stu-id="2a002-113">`Format` automatically uses the appropriate symbols according to the **Regional Options** settings specified in the Windows **Control Panel**.</span></span>  
  
 <span data-ttu-id="2a002-114">なお、連結 (`&`) 演算子は文字列に数値を暗黙的に、次の例のように変換できます。</span><span class="sxs-lookup"><span data-stu-id="2a002-114">Note that the concatenation (`&`) operator can convert a number to a string implicitly, as the following example shows.</span></span>  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a><span data-ttu-id="2a002-115">文字列の数値への変換</span><span class="sxs-lookup"><span data-stu-id="2a002-115">Conversion of Strings to Numbers</span></span>  
 <span data-ttu-id="2a002-116">使用することができます、`Val`関数を明示的に文字列内の数字を数値に変換します。</span><span class="sxs-lookup"><span data-stu-id="2a002-116">You can use the `Val` function to explicitly convert the digits in a string to a number.</span></span> <span data-ttu-id="2a002-117">`Val`数字、スペース、タブ、ライン フィード、またはピリオド以外の文字に到達するまでは、文字列を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="2a002-117">`Val` reads the string until it encounters a character other than a digit, space, tab, line feed, or period.</span></span> <span data-ttu-id="2a002-118">シーケンスは、"< O"と">/reportbuilder/reportbuilder_3_0_0_0.application H"数値の底を変更し、スキャンが終了します。</span><span class="sxs-lookup"><span data-stu-id="2a002-118">The sequences "&O" and "&H" alter the base of the number system and terminate the scanning.</span></span> <span data-ttu-id="2a002-119">読み取りを停止するまで`Val`値を数値にすべての適切な文字を変換します。</span><span class="sxs-lookup"><span data-stu-id="2a002-119">Until it stops reading, `Val` converts all appropriate characters to a numeric value.</span></span> <span data-ttu-id="2a002-120">たとえば、次のステートメントが、値を返す`141.825`します。</span><span class="sxs-lookup"><span data-stu-id="2a002-120">For example, the following statement returns the value `141.825`.</span></span>  
  
 `Val("   14   1.825 miles")`  
  
 <span data-ttu-id="2a002-121">ときに[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]、文字列、数値を変換を使用して、**地域のオプション**、Windows の設定**コントロール パネルの **何千もの解釈に区切り記号、桁区切り記号および通貨記号。</span><span class="sxs-lookup"><span data-stu-id="2a002-121">When [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] converts a string to a numeric value, it uses the **Regional Options** settings specified in the Windows **Control Panel** to interpret the thousands separator, decimal separator, and currency symbol.</span></span> <span data-ttu-id="2a002-122">つまり、変換では、設定も、別の&1; つ下にある成功する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2a002-122">This means that a conversion might succeed under one setting but not another.</span></span> <span data-ttu-id="2a002-123">たとえば、`"$14.20"`が許容されるフランス語のロケールではなく英語 (米国) ロケールでします。</span><span class="sxs-lookup"><span data-stu-id="2a002-123">For example, `"$14.20"` is acceptable in the English (United States) locale but not in any French locale.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a002-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="2a002-124">See Also</span></span>  
 <span data-ttu-id="2a002-125">[Visual Basic における型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="2a002-125">[Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="2a002-126"> [拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="2a002-126"> [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span></span>  
<span data-ttu-id="2a002-127"> [明示的および暗黙的な変換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="2a002-127"> [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span></span>  
<span data-ttu-id="2a002-128"> [方法: Visual Basic での別の型のオブジェクトの変換](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md) </span><span class="sxs-lookup"><span data-stu-id="2a002-128"> [How to: Convert an Object to Another Type in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md) </span></span>  
<span data-ttu-id="2a002-129"> [配列の変換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="2a002-129"> [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md) </span></span>  
<span data-ttu-id="2a002-130"> [データ型](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="2a002-130"> [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="2a002-131"> [型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="2a002-131"> [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="2a002-132"> [.NET Framework ベースの国際対応アプリケーションの概要](https://docs.microsoft.com/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)</span><span class="sxs-lookup"><span data-stu-id="2a002-132"> [Introduction to International Applications Based on the .NET Framework](https://docs.microsoft.com/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)</span></span>
