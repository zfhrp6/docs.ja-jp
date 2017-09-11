---
title: "数値データ型 (Visual Basic) |Microsoft ドキュメント"
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
- integral types, Visual Basic
- Short data type, numeric data types
- Double data type, numeric data types
- Long data type, Visual Basic numeric data types
- numbers, whole
- fractions
- numbers
- whole numbers
- integer numbers
- numbers, integer
- fractional data types
- mantissas, of fractional numbers
- mantissas
- data types [Visual Basic], numeric
- Integer data type, numeric data types
- exponent, of fractional numbers
- integers
- numeric data types, Visual Basic
- Single data type, numeric types
- Decimal data type, numeric data types
ms.assetid: a27bd4d0-7e14-43eb-9cc4-b42eaab323c9
caps.latest.revision: 25
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
ms.openlocfilehash: af87b895c04cf89ba217c9c3a46dc259103d50b4
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="numeric-data-types-visual-basic"></a><span data-ttu-id="44135-102">数値データ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44135-102">Numeric Data Types (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="44135-103">いくつか提供*数値データ型*さまざまな表現で数値を処理するためです。</span><span class="sxs-lookup"><span data-stu-id="44135-103"> supplies several *numeric data types* for handling numbers in various representations.</span></span> <span data-ttu-id="44135-104">*整数*型を表す整数のみ (正、負、およびゼロ)、および*非整数*型では、数値を表す整数と小数部の両方にします。</span><span class="sxs-lookup"><span data-stu-id="44135-104">*Integral* types represent only whole numbers (positive, negative, and zero), and *nonintegral* types represent numbers with both integer and fractional parts.</span></span>  
  
 <span data-ttu-id="44135-105">サイド バイ サイドの比較を示す表に、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]データ型を参照してください[データ型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)します。</span><span class="sxs-lookup"><span data-stu-id="44135-105">For a table showing a side-by-side comparison of the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types, see [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span></span>  
  
## <a name="integral-numeric-types"></a><span data-ttu-id="44135-106">整数数値型</span><span class="sxs-lookup"><span data-stu-id="44135-106">Integral Numeric Types</span></span>  
 <span data-ttu-id="44135-107">*整数データ型*は小数部のない数だけを表す。</span><span class="sxs-lookup"><span data-stu-id="44135-107">*Integral data types* are those that represent only numbers without fractional parts.</span></span>  
  
 <span data-ttu-id="44135-108">*署名*整数データ型は[SByte データ型](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)(8 ビット)、 [Short データ型](../../../../visual-basic/language-reference/data-types/short-data-type.md)(16 ビット)、[整数データ型](../../../../visual-basic/language-reference/data-types/integer-data-type.md)(32 ビット) および[Long データ型](../../../../visual-basic/language-reference/data-types/long-data-type.md)(64 ビット)。</span><span class="sxs-lookup"><span data-stu-id="44135-108">The *signed* integral data types are [SByte Data Type](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md) (8-bit), [Short Data Type](../../../../visual-basic/language-reference/data-types/short-data-type.md) (16-bit), [Integer Data Type](../../../../visual-basic/language-reference/data-types/integer-data-type.md) (32-bit), and [Long Data Type](../../../../visual-basic/language-reference/data-types/long-data-type.md) (64-bit).</span></span> <span data-ttu-id="44135-109">変数は、小数部ではなく、整数を常に保存する場合は、これらの型のいずれかとしてを宣言します。</span><span class="sxs-lookup"><span data-stu-id="44135-109">If a variable always stores integers rather than fractional numbers, declare it as one of these types.</span></span>  
  
 <span data-ttu-id="44135-110">*符号なし*整数型では[Byte データ型](../../../../visual-basic/language-reference/data-types/byte-data-type.md)(8 ビット)、 [UShort データ型](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)(16 ビット)、 [UInteger データ型](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)(32 ビット) および[ULong データ型](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)(64 ビット)。</span><span class="sxs-lookup"><span data-stu-id="44135-110">The *unsigned* integral types are [Byte Data Type](../../../../visual-basic/language-reference/data-types/byte-data-type.md) (8-bit), [UShort Data Type](../../../../visual-basic/language-reference/data-types/ushort-data-type.md) (16-bit), [UInteger Data Type](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md) (32-bit), and [ULong Data Type](../../../../visual-basic/language-reference/data-types/ulong-data-type.md) (64-bit).</span></span> <span data-ttu-id="44135-111">変数にバイナリ データ、または不明のデータが含まれる場合は、これらの型のいずれかとしてを宣言します。</span><span class="sxs-lookup"><span data-stu-id="44135-111">If a variable contains binary data, or data of unknown nature, declare it as one of these types.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="44135-112">パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="44135-112">Performance</span></span>  
 <span data-ttu-id="44135-113">算術演算は、他のデータ型よりも整数型の高速化します。</span><span class="sxs-lookup"><span data-stu-id="44135-113">Arithmetic operations are faster with integral types than with other data types.</span></span> <span data-ttu-id="44135-114">最も高速なは、`Integer`と`UInteger`型[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="44135-114">They are fastest with the `Integer` and `UInteger` types in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
### <a name="large-integers"></a><span data-ttu-id="44135-115">大きな整数</span><span class="sxs-lookup"><span data-stu-id="44135-115">Large Integers</span></span>  
 <span data-ttu-id="44135-116">大きい整数値を保持する必要がある場合、`Integer`使用すると、データ型を保持できる、`Long`代わりにデータを入力します。</span><span class="sxs-lookup"><span data-stu-id="44135-116">If you need to hold an integer larger than the `Integer` data type can hold, you can use the `Long` data type instead.</span></span> <span data-ttu-id="44135-117">`Long`変数は、9,223,372,036,854,775,807 を通じて-9,223,372,036,854,775,808 から数値を保持できます。</span><span class="sxs-lookup"><span data-stu-id="44135-117">`Long` variables can hold numbers from -9,223,372,036,854,775,808 through 9,223,372,036,854,775,807.</span></span> <span data-ttu-id="44135-118">操作が`Long`でよりも少し低速`Integer`します。</span><span class="sxs-lookup"><span data-stu-id="44135-118">Operations with `Long` are slightly slower than with `Integer`.</span></span>  
  
 <span data-ttu-id="44135-119">さらに大きな値が必要な場合を使用できます、 [Decimal データ型](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)します。</span><span class="sxs-lookup"><span data-stu-id="44135-119">If you need even larger values, you can use the [Decimal Data Type](../../../../visual-basic/language-reference/data-types/decimal-data-type.md).</span></span> <span data-ttu-id="44135-120">79,228,162,514,264,337,593,543,950,335 を通じて-79,228,162,514,264,337,593,543,950,335 から数値を保持することができます、`Decimal`変数の場合は、小数点以下桁数を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="44135-120">You can hold numbers from -79,228,162,514,264,337,593,543,950,335 through 79,228,162,514,264,337,593,543,950,335 in a `Decimal` variable if you do not use any decimal places.</span></span> <span data-ttu-id="44135-121">ただし、操作が`Decimal`番号は、その他の数値データ型よりもかなり遅くなります。</span><span class="sxs-lookup"><span data-stu-id="44135-121">However, operations with `Decimal` numbers are considerably slower than with any other numeric data type.</span></span>  
  
### <a name="small-integers"></a><span data-ttu-id="44135-122">小さい整数</span><span class="sxs-lookup"><span data-stu-id="44135-122">Small Integers</span></span>  
 <span data-ttu-id="44135-123">すべての範囲を必要としない場合、`Integer`に使用できるデータの種類、`Short`データ型は、-32,768 ~ 32,767 の整数を格納することができます。</span><span class="sxs-lookup"><span data-stu-id="44135-123">If you do not need the full range of the `Integer` data type, you can use the `Short` data type, which can hold integers from -32,768 through 32,767.</span></span> <span data-ttu-id="44135-124">最小の整数の範囲の`SByte`データ型は-128 ~ 127 の整数値を格納します。</span><span class="sxs-lookup"><span data-stu-id="44135-124">For the smallest integer range, the `SByte` data type holds integers from -128 through 127.</span></span> <span data-ttu-id="44135-125">非常に多くの小さい整数を保持する変数を設定していれば、共通言語ランタイムを格納できる場合があります、`Short`と`SByte`変数より効率的かつメモリ消費量を保存します。</span><span class="sxs-lookup"><span data-stu-id="44135-125">If you have a very large number of variables that hold small integers, the common language runtime can sometimes store your `Short` and `SByte` variables more efficiently and save memory consumption.</span></span> <span data-ttu-id="44135-126">ただし、操作が`Short`と`SByte`でよりもやや低速`Integer`します。</span><span class="sxs-lookup"><span data-stu-id="44135-126">However, operations with `Short` and `SByte` are somewhat slower than with `Integer`.</span></span>  
  
### <a name="unsigned-integers"></a><span data-ttu-id="44135-127">符号なし整数</span><span class="sxs-lookup"><span data-stu-id="44135-127">Unsigned Integers</span></span>  
 <span data-ttu-id="44135-128">変数が負の値を保持する必要はありません、使用することがわかっている場合、*型の符号なし*`Byte`、 `UShort`、 `UInteger`、および`ULong`です。</span><span class="sxs-lookup"><span data-stu-id="44135-128">If you know that your variable never needs to hold a negative number, you can use the *unsigned types*`Byte`, `UShort`, `UInteger`, and `ULong`.</span></span> <span data-ttu-id="44135-129">正の整数を&2; 回よりも小さい符号付きの型を対応するこれらのデータ型の各保持できます (`SByte`、 `Short`、 `Integer`、および`Long`)。</span><span class="sxs-lookup"><span data-stu-id="44135-129">Each of these data types can hold a positive integer twice as large as its corresponding signed type (`SByte`, `Short`, `Integer`, and `Long`).</span></span> <span data-ttu-id="44135-130">パフォーマンスの面では、各符号なしの型は、対応する符号付きの型と同じくらい効率的です。</span><span class="sxs-lookup"><span data-stu-id="44135-130">In terms of performance, each unsigned type is exactly as efficient as its corresponding signed type.</span></span> <span data-ttu-id="44135-131">具体的には、`UInteger`と共有`Integer`の最も効率的なすべての基本的な数値データ型が区別されます。</span><span class="sxs-lookup"><span data-stu-id="44135-131">In particular, `UInteger` shares with `Integer` the distinction of being the most efficient of all the elementary numeric data types.</span></span>  
  
## <a name="nonintegral-numeric-types"></a><span data-ttu-id="44135-132">非整数の数値型</span><span class="sxs-lookup"><span data-stu-id="44135-132">Nonintegral Numeric Types</span></span>  
 <span data-ttu-id="44135-133">*整数以外のデータ型*は整数と小数部の両方で数値を表す。</span><span class="sxs-lookup"><span data-stu-id="44135-133">*Nonintegral data types* are those that represent numbers with both integer and fractional parts.</span></span>  
  
 <span data-ttu-id="44135-134">非整数の数値データ型は`Decimal`(128 ビットの固定小数点)、 [Single データ型](../../../../visual-basic/language-reference/data-types/single-data-type.md)(32 ビット浮動小数点数)、および[Double データ型](../../../../visual-basic/language-reference/data-types/double-data-type.md)(64 ビットの浮動小数点)。</span><span class="sxs-lookup"><span data-stu-id="44135-134">The nonintegral numeric data types are `Decimal` (128-bit fixed point), [Single Data Type](../../../../visual-basic/language-reference/data-types/single-data-type.md) (32-bit floating point), and [Double Data Type](../../../../visual-basic/language-reference/data-types/double-data-type.md) (64-bit floating point).</span></span> <span data-ttu-id="44135-135">これらは、すべて署名済みの種類です。</span><span class="sxs-lookup"><span data-stu-id="44135-135">They are all signed types.</span></span> <span data-ttu-id="44135-136">変数には、小数が含まれることができます、これらの型のいずれかとしてを宣言します。</span><span class="sxs-lookup"><span data-stu-id="44135-136">If a variable can contain a fraction, declare it as one of these types.</span></span>  
  
 <span data-ttu-id="44135-137">`Decimal`浮動小数点データ型がありません。</span><span class="sxs-lookup"><span data-stu-id="44135-137">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="44135-138">`Decimal`数値は、バイナリの整数値と値のどの部分が、小数を指定する整数値のスケール ファクターがあります。</span><span class="sxs-lookup"><span data-stu-id="44135-138">`Decimal` numbers have a binary integer value and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span>  
  
 <span data-ttu-id="44135-139">使用する`Decimal`money 値として変数をします。</span><span class="sxs-lookup"><span data-stu-id="44135-139">You can use `Decimal` variables for money values.</span></span> <span data-ttu-id="44135-140">利点は、値の有効桁数です。</span><span class="sxs-lookup"><span data-stu-id="44135-140">The advantage is the precision of the values.</span></span> <span data-ttu-id="44135-141">`Double`データ型が高速より少ないメモリが必要ですが、丸め誤差が発生します。</span><span class="sxs-lookup"><span data-stu-id="44135-141">The `Double` data type is faster and requires less memory, but it is subject to rounding errors.</span></span> <span data-ttu-id="44135-142">`Decimal`データ型は小数点以下桁数が 28 の完全な精度を保持します。</span><span class="sxs-lookup"><span data-stu-id="44135-142">The `Decimal` data type retains complete accuracy to 28 decimal places.</span></span>  
  
 <span data-ttu-id="44135-143">浮動小数点 (`Single`と`Double`) の数値よりも大きい範囲がある`Decimal`番号が、丸め誤差が発生することができます。</span><span class="sxs-lookup"><span data-stu-id="44135-143">Floating-point (`Single` and `Double`) numbers have larger ranges than `Decimal` numbers but can be subject to rounding errors.</span></span> <span data-ttu-id="44135-144">浮動小数点型サポートの有効桁数よりも少ない`Decimal`ですより大きい値を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="44135-144">Floating-point types support fewer significant digits than `Decimal` but can represent values of greater magnitude.</span></span>  
  
 <span data-ttu-id="44135-145">非整数の数値として表現できます mmmEeee にある mmm、*仮数*(有効桁数)、eee、*指数*(10 の累乗) します。</span><span class="sxs-lookup"><span data-stu-id="44135-145">Nonintegral number values can be expressed as mmmEeee, in which mmm is the *mantissa* (the significant digits) and eee is the *exponent* (a power of 10).</span></span> <span data-ttu-id="44135-146">非整数型の最も高い正の値は 7.9228162514264337593543950335 e + 28 `Decimal`、3.4028235 e + 38 `Single`、および 1.79769313486231570 e + 308 の`Double`です。</span><span class="sxs-lookup"><span data-stu-id="44135-146">The highest positive values of the nonintegral types are 7.9228162514264337593543950335E+28 for `Decimal`, 3.4028235E+38 for `Single`, and 1.79769313486231570E+308 for `Double`.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="44135-147">パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="44135-147">Performance</span></span>  
 <span data-ttu-id="44135-148">`Double`小数部のデータ型の最も効率的な現在のプラットフォーム上のプロセッサでは、倍精度浮動小数点演算を実行するためです。</span><span class="sxs-lookup"><span data-stu-id="44135-148">`Double` is the most efficient of the fractional data types, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="44135-149">ただし、操作が`Double`などの整数型と同様に高速ではない`Integer`します。</span><span class="sxs-lookup"><span data-stu-id="44135-149">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>  
  
### <a name="small-magnitudes"></a><span data-ttu-id="44135-150">小さい絶対値</span><span class="sxs-lookup"><span data-stu-id="44135-150">Small Magnitudes</span></span>  
 <span data-ttu-id="44135-151">(0 に最も近い)、可能な大きさの最小の数値の`Double`変数に保持できます - 4.94065645841246544E ように小規模の 324 の負の値および 4.94065645841246544E-の正の値。</span><span class="sxs-lookup"><span data-stu-id="44135-151">For numbers with the smallest possible magnitude (closest to 0), `Double` variables can hold numbers as small as -4.94065645841246544E-324 for negative values and 4.94065645841246544E-324 for positive values.</span></span>  
  
### <a name="small-fractional-numbers"></a><span data-ttu-id="44135-152">小さい小数値</span><span class="sxs-lookup"><span data-stu-id="44135-152">Small Fractional Numbers</span></span>  
 <span data-ttu-id="44135-153">すべての範囲を必要としない場合、`Double`に使用できるデータの種類、 `Single` 3.4028235 e + 38 から 3.4028235 e + 38 までの浮動小数点数を保持できるデータ型。</span><span class="sxs-lookup"><span data-stu-id="44135-153">If you do not need the full range of the `Double` data type, you can use the `Single` data type, which can hold floating-point numbers from -3.4028235E+38 through 3.4028235E+38.</span></span> <span data-ttu-id="44135-154">最も小さいマグニチュード`Single`変数は、- 1.401298E-45 の負の値および 1.401298-の正の値。</span><span class="sxs-lookup"><span data-stu-id="44135-154">The smallest magnitudes for `Single` variables are -1.401298E-45 for negative values and 1.401298E-45 for positive values.</span></span> <span data-ttu-id="44135-155">共通言語ランタイムを格納できますも非常に多くの小規模の浮動小数点数を保持する変数があれば、`Single`変数より効率的かつメモリ消費量を保存します。</span><span class="sxs-lookup"><span data-stu-id="44135-155">If you have a very large number of variables that hold small floating-point numbers, the common language runtime can sometimes store your `Single` variables more efficiently and save memory consumption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44135-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="44135-156">See Also</span></span>  
 <span data-ttu-id="44135-157">[基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="44135-157">[Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span></span>  
<span data-ttu-id="44135-158"> [文字データ型](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="44135-158"> [Character Data Types](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md) </span></span>  
<span data-ttu-id="44135-159"> [その他のデータ型](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="44135-159"> [Miscellaneous Data Types](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md) </span></span>  
<span data-ttu-id="44135-160"> [データ型のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="44135-160"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="44135-161"> [方法 : 符号なしの型を使用する Windows の機能を呼び出す](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)</span><span class="sxs-lookup"><span data-stu-id="44135-161"> [How to: Call a Windows Function that Takes Unsigned Types](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)</span></span>
