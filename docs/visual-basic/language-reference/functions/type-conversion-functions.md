---
title: データ型変換関数 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.CUShort
- vb.csng
- vb.CDate
- CByte
- CSng
- vb.CDec
- CBool
- CStr
- vb.CULng
- CDec
- CVErr
- CDbl
- CShort
- vb.CObj
- vb.CVErr
- CULng
- vb.cdbl
- vb.cbool
- CObj
- CDate
- CLng
- vb.cstr
- vb.cbyte
- vb.clng
- vb.CChar
- CUShort
- vb.CUInt
- vb.cint
- vb.CShort
- CInt
- CUInt
- CChar
helpviewer_keywords:
- CDate function
- CByte function
- Integer data type [Visual Basic], converting
- string conversion [Visual Basic], conversion functions
- fractions
- data types [Visual Basic], converting
- text, converting
- CDec function
- Char data type [Visual Basic], converting
- type conversion [Visual Basic], functions for
- Single data type [Visual Basic], converting
- numbers [Visual Basic], rounding
- rounding numbers [Visual Basic], type conversion
- CUShort function
- Long data type [Visual Basic], converting
- return values [Visual Basic], data types
- single-precision numbers [Visual Basic], converting
- data type conversion [Visual Basic], functions for
- CStr function
- times [Visual Basic], converting
- CSng function
- conversions [Visual Basic], type conversion functions
- CBool function
- CDbl function
- CUInt function
- Currency data type [Visual Basic], conversion functions
- numbers [Visual Basic], converting
- Double data type [Visual Basic], converting
- CLng function
- CSByte function
- double-precision numbers
- Decimal data type [Visual Basic], converting
- Boolean data type [Visual Basic], converting
- integers [Visual Basic], type conversion functions
- dates [Visual Basic], converting
- CULng function
- CInt function
- Date data type [Visual Basic], converting
- Byte data type [Visual Basic], converting
- String data type [Visual Basic], converting
- CChar function
- banker's rounding
- Short data type [Visual Basic], converting
- rounding numbers [Visual Basic], banker's rounding
- type conversion [Visual Basic], Visual Basic vs. .NET Framework
ms.assetid: d9d8d165-f967-44ff-a6cd-598e4740a99e
ms.openlocfilehash: c9222bdb31f4fd7c792d5a50c100067e29e9d537
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605083"
---
# <a name="type-conversion-functions-visual-basic"></a><span data-ttu-id="b6904-102">データ型変換関数 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6904-102">Type Conversion Functions (Visual Basic)</span></span>
<span data-ttu-id="b6904-103">これらの関数は、コンパイルされたインラインで、変換コードは、式を評価するコードの一部を意味します。</span><span class="sxs-lookup"><span data-stu-id="b6904-103">These functions are compiled inline, meaning the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="b6904-104">場合によってパフォーマンスを向上させると、変換を行うプロシージャへの呼び出しはありません。</span><span class="sxs-lookup"><span data-stu-id="b6904-104">Sometimes there is no call to a procedure to accomplish the conversion, which improves performance.</span></span> <span data-ttu-id="b6904-105">各関数は、式を特定のデータ型を変換します。</span><span class="sxs-lookup"><span data-stu-id="b6904-105">Each function coerces an expression to a specific data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6904-106">構文</span><span class="sxs-lookup"><span data-stu-id="b6904-106">Syntax</span></span>  
  
```  
CBool(expression)  
CByte(expression)  
CChar(expression)  
CDate(expression)  
CDbl(expression)  
CDec(expression)  
CInt(expression)  
CLng(expression)  
CObj(expression)  
CSByte(expression)  
CShort(expression)  
CSng(expression)  
CStr(expression)  
CUInt(expression)  
CULng(expression)  
CUShort(expression)  
```  
  
## <a name="part"></a><span data-ttu-id="b6904-107">パーツ</span><span class="sxs-lookup"><span data-stu-id="b6904-107">Part</span></span>  
 `expression`  
 <span data-ttu-id="b6904-108">必須。</span><span class="sxs-lookup"><span data-stu-id="b6904-108">Required.</span></span> <span data-ttu-id="b6904-109">ソースのデータ型の任意の式。</span><span class="sxs-lookup"><span data-stu-id="b6904-109">Any expression of the source data type.</span></span>  
  
## <a name="return-value-data-type"></a><span data-ttu-id="b6904-110">戻り値のデータ型</span><span class="sxs-lookup"><span data-stu-id="b6904-110">Return Value Data Type</span></span>  
 <span data-ttu-id="b6904-111">関数名は、次の表に示すように、返されると、値のデータ型を決定します。</span><span class="sxs-lookup"><span data-stu-id="b6904-111">The function name determines the data type of the value it returns, as shown in the following table.</span></span>  
  
|<span data-ttu-id="b6904-112">関数名</span><span class="sxs-lookup"><span data-stu-id="b6904-112">Function name</span></span>|<span data-ttu-id="b6904-113">戻り値のデータ型</span><span class="sxs-lookup"><span data-stu-id="b6904-113">Return data type</span></span>|<span data-ttu-id="b6904-114">範囲`expression`引数</span><span class="sxs-lookup"><span data-stu-id="b6904-114">Range for `expression` argument</span></span>|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[<span data-ttu-id="b6904-115">Boolean データ型</span><span class="sxs-lookup"><span data-stu-id="b6904-115">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="b6904-116">任意の有効な`Char`または`String`または数値式です。</span><span class="sxs-lookup"><span data-stu-id="b6904-116">Any valid `Char` or `String` or numeric expression.</span></span>|  
|`CByte`|[<span data-ttu-id="b6904-117">Byte データ型</span><span class="sxs-lookup"><span data-stu-id="b6904-117">Byte Data Type</span></span>](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="b6904-118">0 ~ 255 (符号なし)。小数部は丸められます。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b6904-118">0 through 255 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
|`CChar`|[<span data-ttu-id="b6904-119">Char データ型</span><span class="sxs-lookup"><span data-stu-id="b6904-119">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="b6904-120">任意の有効な`Char`または`String`式以外の最初の文字のみの場合は、`String`に変換されます。 値は 0 ~ 65535 (符号なし) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b6904-120">Any valid `Char` or `String` expression; only first character of a `String` is converted; value can be 0 through 65535 (unsigned).</span></span>|  
|`CDate`|[<span data-ttu-id="b6904-121">Date データ型</span><span class="sxs-lookup"><span data-stu-id="b6904-121">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="b6904-122">任意の有効な日付と時刻の表現。</span><span class="sxs-lookup"><span data-stu-id="b6904-122">Any valid representation of a date and time.</span></span>|  
|`CDbl`|[<span data-ttu-id="b6904-123">Double 型</span><span class="sxs-lookup"><span data-stu-id="b6904-123">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="b6904-124">-- を 4.94065645841246544E-(負の値)。4.94065645841246544E-324 正の値の 1.79769313486231570 e + 308 ~ です。</span><span class="sxs-lookup"><span data-stu-id="b6904-124">-1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values; 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span>|  
|`CDec`|[<span data-ttu-id="b6904-125">Decimal データ型</span><span class="sxs-lookup"><span data-stu-id="b6904-125">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="b6904-126">数値のゼロ拡張 79,228,162,514,264,337,593,543,950,335、+/-小数点以下の桁数番号は、します。</span><span class="sxs-lookup"><span data-stu-id="b6904-126">+/-79,228,162,514,264,337,593,543,950,335 for zero-scaled numbers, that is, numbers with no decimal places.</span></span> <span data-ttu-id="b6904-127">小数点以下桁数が 28 数値の場合は、範囲は、7.9228162514264337593543950335 です。</span><span class="sxs-lookup"><span data-stu-id="b6904-127">For numbers with 28 decimal places, the range is +/-7.9228162514264337593543950335.</span></span> <span data-ttu-id="b6904-128">可能な 0 以外の最小値は、(1 e ~ 28) +/-0.0000000000000000000000000001 です。</span><span class="sxs-lookup"><span data-stu-id="b6904-128">The smallest possible non-zero number is 0.0000000000000000000000000001 (+/-1E-28).</span></span>|  
|`CInt`|[<span data-ttu-id="b6904-129">整数データ型</span><span class="sxs-lookup"><span data-stu-id="b6904-129">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="b6904-130">-2,147, 483,648 ~ 2,147, 483,647 です。小数部は丸められます。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b6904-130">-2,147,483,648 through 2,147,483,647; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CLng`|[<span data-ttu-id="b6904-131">Long データ型</span><span class="sxs-lookup"><span data-stu-id="b6904-131">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="b6904-132">9,223,372,036,854,775,807; を通じて-9,223,372,036,854,775,808小数部は丸められます。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b6904-132">-9,223,372,036,854,775,808 through 9,223,372,036,854,775,807; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CObj`|[<span data-ttu-id="b6904-133">Object 型</span><span class="sxs-lookup"><span data-stu-id="b6904-133">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="b6904-134">任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="b6904-134">Any valid expression.</span></span>|  
|`CSByte`|[<span data-ttu-id="b6904-135">SByte データ型</span><span class="sxs-lookup"><span data-stu-id="b6904-135">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="b6904-136">-128 ~ 127 です。小数部は丸められます。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b6904-136">-128 through 127; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CShort`|[<span data-ttu-id="b6904-137">Short データ型</span><span class="sxs-lookup"><span data-stu-id="b6904-137">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="b6904-138">-32,768 ~ 32,767 です。小数部は丸められます。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b6904-138">-32,768 through 32,767; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CSng`|[<span data-ttu-id="b6904-139">Single データ型</span><span class="sxs-lookup"><span data-stu-id="b6904-139">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="b6904-140">-3.402823 e + 38 ~ - 1.401298E-45 負の値です。1.401298E-45 正の値の 3.402823 e + 38 ~ です。</span><span class="sxs-lookup"><span data-stu-id="b6904-140">-3.402823E+38 through -1.401298E-45 for negative values; 1.401298E-45 through 3.402823E+38 for positive values.</span></span>|  
|`CStr`|[<span data-ttu-id="b6904-141">String データ型</span><span class="sxs-lookup"><span data-stu-id="b6904-141">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="b6904-142">返します`CStr`によって異なります、`expression`引数。</span><span class="sxs-lookup"><span data-stu-id="b6904-142">Returns for `CStr` depend on the `expression` argument.</span></span> <span data-ttu-id="b6904-143">参照してください[CStr 関数の戻り値](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md)です。</span><span class="sxs-lookup"><span data-stu-id="b6904-143">See [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>|  
|`CUInt`|[<span data-ttu-id="b6904-144">UInteger データ型</span><span class="sxs-lookup"><span data-stu-id="b6904-144">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="b6904-145">0 ~ 4,294,967,295 (符号なし)。小数部は丸められます。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b6904-145">0 through 4,294,967,295 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
|`CULng`|[<span data-ttu-id="b6904-146">ULong データ型</span><span class="sxs-lookup"><span data-stu-id="b6904-146">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="b6904-147">0 ~ 18,446,744,073,709,551,615 (符号なし)。小数部は丸められます。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b6904-147">0 through 18,446,744,073,709,551,615 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
|`CUShort`|[<span data-ttu-id="b6904-148">UShort データ型</span><span class="sxs-lookup"><span data-stu-id="b6904-148">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="b6904-149">0 ~ 65,535 (符号なし)。小数部は丸められます。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b6904-149">0 through 65,535 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
  
 <span data-ttu-id="b6904-150"><sup>1</sup>小数部分は、特殊な丸めと呼ばれるを受けることができます*銀行型丸め*です。</span><span class="sxs-lookup"><span data-stu-id="b6904-150"><sup>1</sup> Fractional parts can be subject to a special type of rounding called *banker's rounding*.</span></span> <span data-ttu-id="b6904-151">詳細については、「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6904-151">See "Remarks" for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6904-152">コメント</span><span class="sxs-lookup"><span data-stu-id="b6904-152">Remarks</span></span>  
 <span data-ttu-id="b6904-153">原則として、する必要があります、Visual Basic 型変換関数を使用、.NET Framework のメソッドよりもなど`ToString()`か、上、<xref:System.Convert>クラスまたは個々 の型の構造体またはクラス。</span><span class="sxs-lookup"><span data-stu-id="b6904-153">As a rule, you should use the Visual Basic type conversion functions in preference to the .NET Framework methods such as `ToString()`, either on the <xref:System.Convert> class or on an individual type structure or class.</span></span> <span data-ttu-id="b6904-154">Visual Basic の関数は最適な Visual Basic コード、対話するために設計されていてもソース コードできるだけ短く、また読みやすくします。</span><span class="sxs-lookup"><span data-stu-id="b6904-154">The Visual Basic functions are designed for optimal interaction with Visual Basic code, and they also make your source code shorter and easier to read.</span></span> <span data-ttu-id="b6904-155">さらに、.NET Framework 変換メソッドは、常に生成しない変換する場合の例については、Visual Basic の関数と同じ結果`Boolean`に`Integer`です。</span><span class="sxs-lookup"><span data-stu-id="b6904-155">In addition, the .NET Framework conversion methods do not always produce the same results as the Visual Basic functions, for example when converting `Boolean` to `Integer`.</span></span> <span data-ttu-id="b6904-156">詳細については、次を参照してください。[データ型のトラブルシューティング](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="b6904-156">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="b6904-157">動作</span><span class="sxs-lookup"><span data-stu-id="b6904-157">Behavior</span></span>  
  
-   <span data-ttu-id="b6904-158">**強制型変換です。**</span><span class="sxs-lookup"><span data-stu-id="b6904-158">**Coercion.**</span></span> <span data-ttu-id="b6904-159">一般に、データ型変換関数を使用して、既定のデータ型ではなく、特定のデータ型を操作の結果を強制することができます。</span><span class="sxs-lookup"><span data-stu-id="b6904-159">In general, you can use the data type conversion functions to coerce the result of an operation to a particular data type rather than the default data type.</span></span> <span data-ttu-id="b6904-160">たとえば、使用して`CDec`場合の単精度、倍精度、または整数算術演算は通常を行う場所の 10 進数の演算を強制的にします。</span><span class="sxs-lookup"><span data-stu-id="b6904-160">For example, use `CDec` to force decimal arithmetic in cases where single-precision, double-precision, or integer arithmetic would normally take place.</span></span>  
  
-   <span data-ttu-id="b6904-161">**変換の失敗。**</span><span class="sxs-lookup"><span data-stu-id="b6904-161">**Failed Conversions.**</span></span> <span data-ttu-id="b6904-162">場合、`expression`関数に渡されるが範囲外のデータ型の変換するのには、先に<xref:System.OverflowException>に発生します。</span><span class="sxs-lookup"><span data-stu-id="b6904-162">If the `expression` passed to the function is outside the range of the data type to which it is to be converted, an <xref:System.OverflowException> occurs.</span></span>  
  
-   <span data-ttu-id="b6904-163">**小数部分。**</span><span class="sxs-lookup"><span data-stu-id="b6904-163">**Fractional Parts.**</span></span> <span data-ttu-id="b6904-164">整数以外の値を整数に変換すると、型、整数の変換関数 (`CByte`、 `CInt`、 `CLng`、 `CSByte`、 `CShort`、 `CUInt`、 `CULng`、および`CUShort`) を削除します小数部分し、を最も近い整数値を丸めます。</span><span class="sxs-lookup"><span data-stu-id="b6904-164">When you convert a nonintegral value to an integral type, the integer conversion functions (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, and `CUShort`) remove the fractional part and round the value to the closest integer.</span></span>  
  
     <span data-ttu-id="b6904-165">場合は、小数部分が正確には 0.5、整数の変換関数に丸める、近い偶数の整数。</span><span class="sxs-lookup"><span data-stu-id="b6904-165">If the fractional part is exactly 0.5, the integer conversion functions round it to the nearest even integer.</span></span> <span data-ttu-id="b6904-166">たとえば、0.5 は、0、および 1.5 2.5 は 2 にどちらに切り上げられます。</span><span class="sxs-lookup"><span data-stu-id="b6904-166">For example, 0.5 rounds to 0, and 1.5 and 2.5 both round to 2.</span></span> <span data-ttu-id="b6904-167">これとも呼ばれます*銀行型丸めが*、その目的は、このような多くの数値をまとめて追加するときに蓄積する偏りを調整するとします。</span><span class="sxs-lookup"><span data-stu-id="b6904-167">This is sometimes called *banker's rounding*, and its purpose is to compensate for a bias that could accumulate when adding many such numbers together.</span></span>  
  
     <span data-ttu-id="b6904-168">`CInt` `CLng`は異なる、<xref:Microsoft.VisualBasic.Conversion.Int%2A>と<xref:Microsoft.VisualBasic.Conversion.Fix%2A>切り上げるには、数値の小数部ではなく、切り捨て関数。</span><span class="sxs-lookup"><span data-stu-id="b6904-168">`CInt` and `CLng` differ from the <xref:Microsoft.VisualBasic.Conversion.Int%2A> and <xref:Microsoft.VisualBasic.Conversion.Fix%2A> functions, which truncate, rather than round, the fractional part of a number.</span></span> <span data-ttu-id="b6904-169">また、`Fix`と`Int`を渡すと、同じデータ型の値を常に返します。</span><span class="sxs-lookup"><span data-stu-id="b6904-169">Also, `Fix` and `Int` always return a value of the same data type as you pass in.</span></span>  
  
-   <span data-ttu-id="b6904-170">**日付/時刻の変換。**</span><span class="sxs-lookup"><span data-stu-id="b6904-170">**Date/Time Conversions.**</span></span> <span data-ttu-id="b6904-171">使用して、<xref:Microsoft.VisualBasic.Information.IsDate%2A>値を日付と時刻に変換できるかどうかを判断する関数。</span><span class="sxs-lookup"><span data-stu-id="b6904-171">Use the <xref:Microsoft.VisualBasic.Information.IsDate%2A> function to determine if a value can be converted to a date and time.</span></span> <span data-ttu-id="b6904-172">`CDate` リテラルの日付と時刻リテラルが数値以外の値を認識します。</span><span class="sxs-lookup"><span data-stu-id="b6904-172">`CDate` recognizes date literals and time literals but not numeric values.</span></span> <span data-ttu-id="b6904-173">Visual Basic 6.0 を変換する`Date`値を`Date`Visual Basic 2005 での値またはそれ以降のバージョンでは、使用できます、<xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="b6904-173">To convert a Visual Basic 6.0 `Date` value to a `Date` value in Visual Basic 2005 or later versions, you can use the <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="b6904-174">**ニュートラル日付/時刻値。**</span><span class="sxs-lookup"><span data-stu-id="b6904-174">**Neutral Date/Time Values.**</span></span> <span data-ttu-id="b6904-175">[Date データ型](../../../visual-basic/language-reference/data-types/date-data-type.md)常に日付と時刻の両方の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b6904-175">The [Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md) always contains both date and time information.</span></span> <span data-ttu-id="b6904-176">型変換のため、Visual Basic 1/1/0001 (1 年 1 月、1) であると見なす、*ニュートラル値*日付、および 00時 00分: 00 (午前 0 時) に依存しない値であることにします。</span><span class="sxs-lookup"><span data-stu-id="b6904-176">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="b6904-177">変換する場合、`Date`値を文字列に`CStr`結果の文字列に中立的な値は含まれません。</span><span class="sxs-lookup"><span data-stu-id="b6904-177">If you convert a `Date` value to a string, `CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="b6904-178">変換する場合など、`#January 1, 0001 9:30:00#`文字列に、結果は"9時 30分: 00 AM"以外の場合は、日付情報は表示されません。</span><span class="sxs-lookup"><span data-stu-id="b6904-178">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="b6904-179">ただし、日付情報は、元にまだ存在している`Date`値し、などの関数で回復できる<xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>関数。</span><span class="sxs-lookup"><span data-stu-id="b6904-179">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> function.</span></span>  
  
-   <span data-ttu-id="b6904-180">**カルチャと小文字の区別します。**</span><span class="sxs-lookup"><span data-stu-id="b6904-180">**Culture Sensitivity.**</span></span> <span data-ttu-id="b6904-181">文字列に関係するデータ型変換関数は、アプリケーションの現在のカルチャ設定に基づく変換を実行します。</span><span class="sxs-lookup"><span data-stu-id="b6904-181">The type conversion functions involving strings perform conversions based on the current culture settings for the application.</span></span> <span data-ttu-id="b6904-182">たとえば、`CDate`システムのロケール設定に従って日付形式を認識します。</span><span class="sxs-lookup"><span data-stu-id="b6904-182">For example, `CDate` recognizes date formats according to the locale setting of your system.</span></span> <span data-ttu-id="b6904-183">日、月、および使用されるロケールの正しい順序で年を指定するか、日付が正しく解釈されない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b6904-183">You must provide the day, month, and year in the correct order for your locale, or the date might not be interpreted correctly.</span></span> <span data-ttu-id="b6904-184">長い日付形式は、「水曜日」などの曜日の文字列が含まれている場合に認識されません。</span><span class="sxs-lookup"><span data-stu-id="b6904-184">A long date format is not recognized if it contains a day-of-the-week string, such as "Wednesday".</span></span>  
  
     <span data-ttu-id="b6904-185">または現在のロケールで指定された 1 つは異なる形式で値の文字列形式からに変換する必要がある場合は、Visual Basic の型変換関数を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="b6904-185">If you need to convert to or from a string representation of a value in a format other than the one specified by your locale, you cannot use the Visual Basic type conversion functions.</span></span> <span data-ttu-id="b6904-186">これを行うを使用して、`ToString(IFormatProvider)`と`Parse(String, IFormatProvider)`値の型のメソッドです。</span><span class="sxs-lookup"><span data-stu-id="b6904-186">To do this, use the `ToString(IFormatProvider)` and `Parse(String, IFormatProvider)` methods of that value's type.</span></span> <span data-ttu-id="b6904-187">たとえば、使用<xref:System.Double.Parse%2A?displayProperty=nameWithType>を文字列に変換するときに、`Double`を使用して<xref:System.Double.ToString%2A?displayProperty=nameWithType>型の値を変換するときに`Double`を文字列にします。</span><span class="sxs-lookup"><span data-stu-id="b6904-187">For example, use <xref:System.Double.Parse%2A?displayProperty=nameWithType> when converting a string to a `Double`, and use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a string.</span></span>  
  
## <a name="ctype-function"></a><span data-ttu-id="b6904-188">CType Function</span><span class="sxs-lookup"><span data-stu-id="b6904-188">CType Function</span></span>  
 <span data-ttu-id="b6904-189">[CType 関数](../../../visual-basic/language-reference/functions/ctype-function.md)2 番目の引数を受け取り`typename`、強制`expression`に`typename`ここで、`typename`任意のデータ型、構造体、クラス、または有効な変換が存在するインターフェイスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b6904-189">The [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) takes a second argument, `typename`, and coerces `expression` to `typename`, where `typename` can be any data type, structure, class, or interface to which there exists a valid conversion.</span></span>  
  
 <span data-ttu-id="b6904-190">比較について`CType`他の型変換のキーワードと、次を参照してください。 [DirectCast 演算子](../../../visual-basic/language-reference/operators/directcast-operator.md)と[TryCast 演算子](../../../visual-basic/language-reference/operators/trycast-operator.md)です。</span><span class="sxs-lookup"><span data-stu-id="b6904-190">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>  
  
## <a name="cbool-example"></a><span data-ttu-id="b6904-191">CBool 例</span><span class="sxs-lookup"><span data-stu-id="b6904-191">CBool Example</span></span>  
 <span data-ttu-id="b6904-192">次の例では、`CBool`関数を式に変換する`Boolean`値。</span><span class="sxs-lookup"><span data-stu-id="b6904-192">The following example uses the `CBool` function to convert expressions to `Boolean` values.</span></span> <span data-ttu-id="b6904-193">0 以外の値に式が評価された場合`CBool`を返します`True`、それ以外を返します`False`です。</span><span class="sxs-lookup"><span data-stu-id="b6904-193">If an expression evaluates to a nonzero value, `CBool` returns `True`; otherwise, it returns `False`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#1](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_1.vb)]  
  
## <a name="cbyte-example"></a><span data-ttu-id="b6904-194">CByte 例</span><span class="sxs-lookup"><span data-stu-id="b6904-194">CByte Example</span></span>  
 <span data-ttu-id="b6904-195">次の例では、`CByte`関数を式に変換する、`Byte`です。</span><span class="sxs-lookup"><span data-stu-id="b6904-195">The following example uses the `CByte` function to convert an expression to a `Byte`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#2](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_2.vb)]  
  
## <a name="cchar-example"></a><span data-ttu-id="b6904-196">Cchar 関数の例</span><span class="sxs-lookup"><span data-stu-id="b6904-196">CChar Example</span></span>  
 <span data-ttu-id="b6904-197">次の例では、`CChar`関数の最初の文字に変換する、`String`式、`Char`型です。</span><span class="sxs-lookup"><span data-stu-id="b6904-197">The following example uses the `CChar` function to convert the first character of a `String` expression to a `Char` type.</span></span>  
  
 [!code-vb[VbVbalrFunctions#3](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_3.vb)]  
  
 <span data-ttu-id="b6904-198">入力引数`CChar`データ型でなければなりません`Char`または`String`です。</span><span class="sxs-lookup"><span data-stu-id="b6904-198">The input argument to `CChar` must be of data type `Char` or `String`.</span></span> <span data-ttu-id="b6904-199">使用することはできません`CChar`に変換する数値、文字、ため`CChar`数値データ型を受け入れることはできません。</span><span class="sxs-lookup"><span data-stu-id="b6904-199">You cannot use `CChar` to convert a number to a character, because `CChar` cannot accept a numeric data type.</span></span> <span data-ttu-id="b6904-200">次の例では、コード ポイント (文字コード) を表す数値を取得し、対応する文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="b6904-200">The following example obtains a number representing a code point (character code) and converts it to the corresponding character.</span></span> <span data-ttu-id="b6904-201">使用して、 <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> 、桁の数字の文字列を取得する関数`CInt`を入力文字列に変換する`Integer`、および`ChrW`を入力する数値を変換する`Char`です。</span><span class="sxs-lookup"><span data-stu-id="b6904-201">It uses the <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> function to obtain the string of digits, `CInt` to convert the string to type `Integer`, and `ChrW` to convert the number to type `Char`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#4](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_4.vb)]  
  
## <a name="cdate-example"></a><span data-ttu-id="b6904-202">Cdate 関数の例</span><span class="sxs-lookup"><span data-stu-id="b6904-202">CDate Example</span></span>  
 <span data-ttu-id="b6904-203">次の例では、`CDate`関数への文字列に変換する`Date`値。</span><span class="sxs-lookup"><span data-stu-id="b6904-203">The following example uses the `CDate` function to convert strings to `Date` values.</span></span> <span data-ttu-id="b6904-204">一般に、ハードコーディングされた日付と時刻文字列としてのこの例に示す) は推奨されません。</span><span class="sxs-lookup"><span data-stu-id="b6904-204">In general, hard-coding dates and times as strings (as shown in this example) is not recommended.</span></span> <span data-ttu-id="b6904-205">日付リテラルと #Feb 12、1969 # など、時刻のリテラルを使用し、# 4時 45分: 23 PM #、代わりにします。</span><span class="sxs-lookup"><span data-stu-id="b6904-205">Use date literals and time literals, such as #Feb 12, 1969# and #4:45:23 PM#, instead.</span></span>  
  
 [!code-vb[VbVbalrFunctions#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_5.vb)]  
  
## <a name="cdbl-example"></a><span data-ttu-id="b6904-206">CDbl 例</span><span class="sxs-lookup"><span data-stu-id="b6904-206">CDbl Example</span></span>  
 [!code-vb[VbVbalrFunctions#6](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_6.vb)]  
  
## <a name="cdec-example"></a><span data-ttu-id="b6904-207">CDec 例</span><span class="sxs-lookup"><span data-stu-id="b6904-207">CDec Example</span></span>  
 <span data-ttu-id="b6904-208">次の例では、`CDec`関数を数値に変換する`Decimal`です。</span><span class="sxs-lookup"><span data-stu-id="b6904-208">The following example uses the `CDec` function to convert a numeric value to `Decimal`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#7](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_7.vb)]  
  
## <a name="cint-example"></a><span data-ttu-id="b6904-209">CInt 例</span><span class="sxs-lookup"><span data-stu-id="b6904-209">CInt Example</span></span>  
 <span data-ttu-id="b6904-210">次の例では、`CInt`値を変換する関数`Integer`です。</span><span class="sxs-lookup"><span data-stu-id="b6904-210">The following example uses the `CInt` function to convert a value to `Integer`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#8](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_8.vb)]  
  
## <a name="clng-example"></a><span data-ttu-id="b6904-211">CLng 例</span><span class="sxs-lookup"><span data-stu-id="b6904-211">CLng Example</span></span>  
 <span data-ttu-id="b6904-212">次の例では、`CLng`値に変換する関数`Long`です。</span><span class="sxs-lookup"><span data-stu-id="b6904-212">The following example uses the `CLng` function to convert values to `Long`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#9](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_9.vb)]  
  
## <a name="cobj-example"></a><span data-ttu-id="b6904-213">CObj 例</span><span class="sxs-lookup"><span data-stu-id="b6904-213">CObj Example</span></span>  
 <span data-ttu-id="b6904-214">次の例では、`CObj`関数を数値に変換する`Object`です。</span><span class="sxs-lookup"><span data-stu-id="b6904-214">The following example uses the `CObj` function to convert a numeric value to `Object`.</span></span> <span data-ttu-id="b6904-215">`Object`変数自体を指す 4 バイト ポインターのみが含まれています、`Double`値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="b6904-215">The `Object` variable itself contains only a four-byte pointer, which points to the `Double` value assigned to it.</span></span>  
  
 [!code-vb[VbVbalrFunctions#10](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_10.vb)]  
  
## <a name="csbyte-example"></a><span data-ttu-id="b6904-216">CSByte 例</span><span class="sxs-lookup"><span data-stu-id="b6904-216">CSByte Example</span></span>  
 <span data-ttu-id="b6904-217">次の例では、`CSByte`関数を数値に変換する`SByte`です。</span><span class="sxs-lookup"><span data-stu-id="b6904-217">The following example uses the `CSByte` function to convert a numeric value to `SByte`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#11](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_11.vb)]  
  
## <a name="cshort-example"></a><span data-ttu-id="b6904-218">CShort 例</span><span class="sxs-lookup"><span data-stu-id="b6904-218">CShort Example</span></span>  
 <span data-ttu-id="b6904-219">次の例では、`CShort`関数を数値に変換する`Short`です。</span><span class="sxs-lookup"><span data-stu-id="b6904-219">The following example uses the `CShort` function to convert a numeric value to `Short`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#12](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_12.vb)]  
  
## <a name="csng-example"></a><span data-ttu-id="b6904-220">CSng 例</span><span class="sxs-lookup"><span data-stu-id="b6904-220">CSng Example</span></span>  
 <span data-ttu-id="b6904-221">次の例では、`CSng`値に変換する関数`Single`です。</span><span class="sxs-lookup"><span data-stu-id="b6904-221">The following example uses the `CSng` function to convert values to `Single`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#13](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_13.vb)]  
  
## <a name="cstr-example"></a><span data-ttu-id="b6904-222">Cstr 関数の例</span><span class="sxs-lookup"><span data-stu-id="b6904-222">CStr Example</span></span>  
 <span data-ttu-id="b6904-223">次の例では、`CStr`関数を数値に変換する`String`です。</span><span class="sxs-lookup"><span data-stu-id="b6904-223">The following example uses the `CStr` function to convert a numeric value to `String`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#14](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_14.vb)]  
  
 <span data-ttu-id="b6904-224">次の例では、`CStr`関数に変換する`Date`値`String`値。</span><span class="sxs-lookup"><span data-stu-id="b6904-224">The following example uses the `CStr` function to convert `Date` values to `String` values.</span></span>  
  
 [!code-vb[VbVbalrFunctions#15](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_15.vb)]  
  
 <span data-ttu-id="b6904-225">`CStr` 常に表示、`Date`現在のロケールのたとえば、標準の短い形式の値"2003 年 6 月 15/4時 35分: 47 PM"です。</span><span class="sxs-lookup"><span data-stu-id="b6904-225">`CStr` always renders a `Date` value in the standard short format for the current locale, for example, "6/15/2003 4:35:47 PM".</span></span> <span data-ttu-id="b6904-226">ただし、`CStr`抑制、*ニュートラル値*の日付と時刻の 00時 00分: 00 の 1/1/0001 です。</span><span class="sxs-lookup"><span data-stu-id="b6904-226">However, `CStr` suppresses the *neutral values* of 1/1/0001 for the date and 00:00:00 for the time.</span></span>  
  
 <span data-ttu-id="b6904-227">によって返される値の詳細については`CStr`を参照してください[CStr 関数の戻り値](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md)です。</span><span class="sxs-lookup"><span data-stu-id="b6904-227">For more detail on the values returned by `CStr`, see [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>  
  
## <a name="cuint-example"></a><span data-ttu-id="b6904-228">CUInt 例</span><span class="sxs-lookup"><span data-stu-id="b6904-228">CUInt Example</span></span>  
 <span data-ttu-id="b6904-229">次の例では、`CUInt`関数を数値に変換する`UInteger`です。</span><span class="sxs-lookup"><span data-stu-id="b6904-229">The following example uses the `CUInt` function to convert a numeric value to `UInteger`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#16](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_16.vb)]  
  
## <a name="culng-example"></a><span data-ttu-id="b6904-230">CULng 例</span><span class="sxs-lookup"><span data-stu-id="b6904-230">CULng Example</span></span>  
 <span data-ttu-id="b6904-231">次の例では、`CULng`関数を数値に変換する`ULong`です。</span><span class="sxs-lookup"><span data-stu-id="b6904-231">The following example uses the `CULng` function to convert a numeric value to `ULong`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#17](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_17.vb)]  
  
## <a name="cushort-example"></a><span data-ttu-id="b6904-232">CUShort 例</span><span class="sxs-lookup"><span data-stu-id="b6904-232">CUShort Example</span></span>  
 <span data-ttu-id="b6904-233">次の例では、`CUShort`関数を数値に変換する`UShort`です。</span><span class="sxs-lookup"><span data-stu-id="b6904-233">The following example uses the `CUShort` function to convert a numeric value to `UShort`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#18](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_18.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b6904-234">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6904-234">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 <xref:Microsoft.VisualBasic.Strings.Format%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Oct%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Str%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>  
 [<span data-ttu-id="b6904-235">変換関数</span><span class="sxs-lookup"><span data-stu-id="b6904-235">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)  
 [<span data-ttu-id="b6904-236">Visual Basic での型変換</span><span class="sxs-lookup"><span data-stu-id="b6904-236">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
