---
title: "明示的および暗黙的な変換 (Visual Basic) |Microsoft ドキュメント"
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
- conversions, type
- variables [Visual Basic], changing data type
- casting
- conversions, data type
- type conversion, implicit conversions
- CType function, conversions
- casting, data types
- data type conversion, explicit
- type conversion, explicit conversions
- data types [Visual Basic], casting
- conversions, implicit
- explicit data type conversions
- conversions
- changing data types
- conversions, explicit
- data type conversion, implicit
- implicit data type conversions
ms.assetid: 77de1659-af8a-492c-967e-e7ef60ccce66
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
ms.openlocfilehash: 76f32fc4c8e26470c77e1415d96ed9035a4d9165
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="implicit-and-explicit-conversions-visual-basic"></a><span data-ttu-id="d3797-102">暗黙の型変換と明示的な型変換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3797-102">Implicit and Explicit Conversions (Visual Basic)</span></span>
<span data-ttu-id="d3797-103">*暗黙的な変換*ソース コードに特殊な構文は不要です。</span><span class="sxs-lookup"><span data-stu-id="d3797-103">An *implicit conversion* does not require any special syntax in the source code.</span></span> <span data-ttu-id="d3797-104">次の例で[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]の値を暗黙的に変換`k`を単精度浮動小数点の値を割り当てる前に`q`します。</span><span class="sxs-lookup"><span data-stu-id="d3797-104">In the following example, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] implicitly converts the value of `k` to a single-precision floating-point value before assigning it to `q`.</span></span>  
  
```  
Dim k As Integer  
Dim q As Double  
' Integer widens to Double, so you can do this with Option Strict On.  
k = 432  
q = k  
```  
  
 <span data-ttu-id="d3797-105">*明示的な変換*型変換のキーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="d3797-105">An *explicit conversion* uses a type conversion keyword.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="d3797-106">いくつかそのようなキーワード、目的のデータ型をかっこで指定した式変換を提供します。</span><span class="sxs-lookup"><span data-stu-id="d3797-106"> provides several such keywords, which coerce an expression in parentheses to the desired data type.</span></span> <span data-ttu-id="d3797-107">これらのキーワードが関数のように動作しますが、ため実行は、関数呼び出しよりもわずかに高速、コンパイラは、インライン コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="d3797-107">These keywords act like functions, but the compiler generates the code inline, so execution is slightly faster than with a function call.</span></span>  
  
 <span data-ttu-id="d3797-108">前の例の次の拡張機能で、`CInt`キーワードの値を変換する`q`に割り当てる前に整数に戻す`k`します。</span><span class="sxs-lookup"><span data-stu-id="d3797-108">In the following extension of the preceding example, the `CInt` keyword converts the value of `q` back to an integer before assigning it to `k`.</span></span>  
  
```  
' q had been assigned the value 432 from k.  
q = Math.Sqrt(q)  
k = CInt(q)  
' k now has the value 21 (rounded square root of 432).  
```  
  
## <a name="conversion-keywords"></a><span data-ttu-id="d3797-109">変換キーワード</span><span class="sxs-lookup"><span data-stu-id="d3797-109">Conversion Keywords</span></span>  
 <span data-ttu-id="d3797-110">次の表は、使用できる変換キーワードを示します。</span><span class="sxs-lookup"><span data-stu-id="d3797-110">The following table shows the available conversion keywords.</span></span>  
  
|<span data-ttu-id="d3797-111">型変換キーワード</span><span class="sxs-lookup"><span data-stu-id="d3797-111">Type conversion keyword</span></span>|<span data-ttu-id="d3797-112">データ型の式に変換します。</span><span class="sxs-lookup"><span data-stu-id="d3797-112">Converts an expression to data type</span></span>|<span data-ttu-id="d3797-113">変換する式のデータ型</span><span class="sxs-lookup"><span data-stu-id="d3797-113">Allowable data types of expression to be converted</span></span>|  
|---|---|---|  
|`CBool`|[<span data-ttu-id="d3797-114">Boolean データ型</span><span class="sxs-lookup"><span data-stu-id="d3797-114">Boolean Data Type</span></span>](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="d3797-115">任意の数値型 (を含む`Byte`、 `SByte`、および列挙型)、 `String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="d3797-115">Any numeric type (including `Byte`, `SByte`, and enumerated types), `String`, `Object`</span></span>|  
|`CByte`|[<span data-ttu-id="d3797-116">Byte データ型</span><span class="sxs-lookup"><span data-stu-id="d3797-116">Byte Data Type</span></span>](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="d3797-117">任意の数値型 (を含む`SByte`型および列挙型)、 `Boolean`、 `String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="d3797-117">Any numeric type (including `SByte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CChar`|[<span data-ttu-id="d3797-118">Char データ型</span><span class="sxs-lookup"><span data-stu-id="d3797-118">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="d3797-119">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="d3797-119">`String`, `Object`</span></span>|  
|`CDate`|[<span data-ttu-id="d3797-120">Date データ型</span><span class="sxs-lookup"><span data-stu-id="d3797-120">Date Data Type</span></span>](../../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="d3797-121">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="d3797-121">`String`, `Object`</span></span>|  
|`CDbl`|[<span data-ttu-id="d3797-122">Double 型</span><span class="sxs-lookup"><span data-stu-id="d3797-122">Double Data Type</span></span>](../../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="d3797-123">任意の数値型 (を含む`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="d3797-123">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CDec`|[<span data-ttu-id="d3797-124">Decimal データ型</span><span class="sxs-lookup"><span data-stu-id="d3797-124">Decimal Data Type</span></span>](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="d3797-125">任意の数値型 (を含む`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="d3797-125">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CInt`|[<span data-ttu-id="d3797-126">整数データ型</span><span class="sxs-lookup"><span data-stu-id="d3797-126">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="d3797-127">任意の数値型 (を含む`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="d3797-127">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CLng`|[<span data-ttu-id="d3797-128">Long データ型</span><span class="sxs-lookup"><span data-stu-id="d3797-128">Long Data Type</span></span>](../../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="d3797-129">任意の数値型 (を含む`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="d3797-129">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CObj`|[<span data-ttu-id="d3797-130">Object 型</span><span class="sxs-lookup"><span data-stu-id="d3797-130">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="d3797-131">任意の型</span><span class="sxs-lookup"><span data-stu-id="d3797-131">Any type</span></span>|  
|`CSByte`|[<span data-ttu-id="d3797-132">SByte データ型</span><span class="sxs-lookup"><span data-stu-id="d3797-132">SByte Data Type</span></span>](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="d3797-133">任意の数値型 (を含む`Byte`型および列挙型)、 `Boolean`、 `String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="d3797-133">Any numeric type (including `Byte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CShort`|[<span data-ttu-id="d3797-134">Short データ型</span><span class="sxs-lookup"><span data-stu-id="d3797-134">Short Data Type</span></span>](../../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="d3797-135">任意の数値型 (を含む`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="d3797-135">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CSng`|[<span data-ttu-id="d3797-136">Single データ型</span><span class="sxs-lookup"><span data-stu-id="d3797-136">Single Data Type</span></span>](../../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="d3797-137">任意の数値型 (を含む`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="d3797-137">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CStr`|[<span data-ttu-id="d3797-138">String データ型</span><span class="sxs-lookup"><span data-stu-id="d3797-138">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="d3797-139">任意の数値型 (を含む`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `Char`、`Char`配列、 `Date`、`Object`</span><span class="sxs-lookup"><span data-stu-id="d3797-139">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `Char`, `Char` array, `Date`, `Object`</span></span>|  
|`CType`|<span data-ttu-id="d3797-140">コンマの後に指定された型 (`,`)</span><span class="sxs-lookup"><span data-stu-id="d3797-140">Type specified following the comma (`,`)</span></span>|<span data-ttu-id="d3797-141">変換する際、*基本データ型*(基本型の配列を含む)、同じ型の変換の対応するキーワードが許容します。</span><span class="sxs-lookup"><span data-stu-id="d3797-141">When converting to an *elementary data type* (including an array of an elementary type), the same types as allowed for the corresponding conversion keyword</span></span><br /><br /> <span data-ttu-id="d3797-142">変換する際、*複合データ型*を実装しているインターフェイスとそれを継承するクラス</span><span class="sxs-lookup"><span data-stu-id="d3797-142">When converting to a *composite data type*, the interfaces it implements and the classes from which it inherits</span></span><br /><br /> <span data-ttu-id="d3797-143">持つオーバー ロードされたクラスまたは構造体に変換するときに`CType`、そのクラスまたは構造体</span><span class="sxs-lookup"><span data-stu-id="d3797-143">When converting to a class or structure on which you have overloaded `CType`, that class or structure</span></span>|  
|`CUInt`|[<span data-ttu-id="d3797-144">UInteger データ型</span><span class="sxs-lookup"><span data-stu-id="d3797-144">UInteger Data Type</span></span>](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="d3797-145">任意の数値型 (を含む`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="d3797-145">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CULng`|[<span data-ttu-id="d3797-146">ULong データ型</span><span class="sxs-lookup"><span data-stu-id="d3797-146">ULong Data Type</span></span>](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="d3797-147">任意の数値型 (を含む`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="d3797-147">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CUShort`|[<span data-ttu-id="d3797-148">UShort データ型</span><span class="sxs-lookup"><span data-stu-id="d3797-148">UShort Data Type</span></span>](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="d3797-149">任意の数値型 (を含む`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="d3797-149">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
  
## <a name="the-ctype-function"></a><span data-ttu-id="d3797-150">CType 関数</span><span class="sxs-lookup"><span data-stu-id="d3797-150">The CType Function</span></span>  
 <span data-ttu-id="d3797-151">[CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)は&2; つの引数で動作します。</span><span class="sxs-lookup"><span data-stu-id="d3797-151">The [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) operates on two arguments.</span></span> <span data-ttu-id="d3797-152">最初は、変換する式で、2 番目は、移行先のデータ型またはオブジェクト クラスです。</span><span class="sxs-lookup"><span data-stu-id="d3797-152">The first is the expression to be converted, and the second is the destination data type or object class.</span></span> <span data-ttu-id="d3797-153">最初の引数は型ではなく、式である必要がありますに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d3797-153">Note that the first argument must be an expression, not a type.</span></span>  
  
 <span data-ttu-id="d3797-154">`CType`*インライン関数*変換は、コンパイルされたコードの意味、多くの場合、呼び出す関数は生成されません。</span><span class="sxs-lookup"><span data-stu-id="d3797-154">`CType` is an *inline function*, meaning the compiled code makes the conversion, often without generating a function call.</span></span> <span data-ttu-id="d3797-155">これにより、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="d3797-155">This improves performance.</span></span>  
  
 <span data-ttu-id="d3797-156">比較について`CType`他の型変換キーワードで、次を参照してください。 [DirectCast 演算子](../../../../visual-basic/language-reference/operators/directcast-operator.md)と[TryCast 演算子](../../../../visual-basic/language-reference/operators/trycast-operator.md)します。</span><span class="sxs-lookup"><span data-stu-id="d3797-156">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>  
  
### <a name="elementary-types"></a><span data-ttu-id="d3797-157">基本型</span><span class="sxs-lookup"><span data-stu-id="d3797-157">Elementary Types</span></span>  
 <span data-ttu-id="d3797-158">次の例は、`CType` の使い方を示しています。</span><span class="sxs-lookup"><span data-stu-id="d3797-158">The following example demonstrates the use of `CType`.</span></span>  
  
```  
k = CType(q, Integer)  
' The following statement coerces w to the specific object class Label.  
f = CType(w, Label)  
```  
  
### <a name="composite-types"></a><span data-ttu-id="d3797-159">複合型</span><span class="sxs-lookup"><span data-stu-id="d3797-159">Composite Types</span></span>  
 <span data-ttu-id="d3797-160">使用する`CType`値複合データ型および基本型に変換します。</span><span class="sxs-lookup"><span data-stu-id="d3797-160">You can use `CType` to convert values to composite data types as well as to elementary types.</span></span> <span data-ttu-id="d3797-161">また、次の例のように、インターフェイスの&1; つの型にオブジェクト クラスを強制的に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="d3797-161">You can also use it to coerce an object class to the type of one of its interfaces, as in the following example.</span></span>  
  
```  
' Assume class cZone implements interface iZone.  
Dim h As Object  
' The first argument to CType must be an expression, not a type.  
Dim cZ As cZone  
' The following statement coerces a cZone object to its interface iZone.  
h = CType(cZ, iZone)  
```  
  
### <a name="array-types"></a><span data-ttu-id="d3797-162">配列型</span><span class="sxs-lookup"><span data-stu-id="d3797-162">Array Types</span></span>  
 <span data-ttu-id="d3797-163">`CType`次の例のように、配列のデータ型を変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="d3797-163">`CType` can also convert array data types, as in the following example.</span></span>  
  
```  
Dim v() As classV  
Dim obArray() As Object  
' Assume some object array has been assigned to obArray.  
' Check for run-time type compatibility.  
If TypeOf obArray Is classV()  
    ' obArray can be converted to classV.  
    v = CType(obArray, classV())  
End If  
```  
  
 <span data-ttu-id="d3797-164">詳細と例では、次を参照してください。[配列変換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)します。</span><span class="sxs-lookup"><span data-stu-id="d3797-164">For more information and an example, see [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).</span></span>  
  
### <a name="types-defining-ctype"></a><span data-ttu-id="d3797-165">CType を定義する種類</span><span class="sxs-lookup"><span data-stu-id="d3797-165">Types Defining CType</span></span>  
 <span data-ttu-id="d3797-166">定義できます`CType`クラスや構造体を定義します。</span><span class="sxs-lookup"><span data-stu-id="d3797-166">You can define `CType` on a class or structure you have defined.</span></span> <span data-ttu-id="d3797-167">これにより、クラスまたは構造体の型との間に値を変換することができます。</span><span class="sxs-lookup"><span data-stu-id="d3797-167">This allows you to convert values to and from the type of your class or structure.</span></span> <span data-ttu-id="d3797-168">詳細と例では、次を参照してください。[方法: 変換演算子を定義する](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)です。</span><span class="sxs-lookup"><span data-stu-id="d3797-168">For more information and an example, see [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3797-169">変換キーワードと共に使用される値は、先のデータ型に対して有効である必要がありますか、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="d3797-169">Values used with a conversion keyword must be valid for the destination data type, or an error occurs.</span></span> <span data-ttu-id="d3797-170">変換しようとする場合など、`Long`に、`Integer`の値、`Long`の有効な範囲内になければなりません、`Integer`データ型。</span><span class="sxs-lookup"><span data-stu-id="d3797-170">For example, if you attempt to convert a `Long` to an `Integer`, the value of the `Long` must be within the valid range for the `Integer` data type.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="d3797-171">指定する`CType`ソースの種類が変換先の型から派生していない場合、1 つのクラス型から実行時に別の失敗に変換します。</span><span class="sxs-lookup"><span data-stu-id="d3797-171">Specifying `CType` to convert from one class type to another fails at run time if the source type does not derive from the destination type.</span></span> <span data-ttu-id="d3797-172">このようなエラーをスローする<xref:System.InvalidCastException>例外</xref:System.InvalidCastException>。</span><span class="sxs-lookup"><span data-stu-id="d3797-172">Such a failure throws an <xref:System.InvalidCastException> exception.</span></span>  
  
 <span data-ttu-id="d3797-173">ただし、構造体またはクラスを定義した型の&1; つは、定義した場合`CType`その構造体またはクラスで、変換が正常に完了の要件を満たす場合に、`CType`です。</span><span class="sxs-lookup"><span data-stu-id="d3797-173">However, if one of the types is a structure or class you have defined, and if you have defined `CType` on that structure or class, a conversion can succeed if it satisfies the requirements of your `CType`.</span></span> <span data-ttu-id="d3797-174">参照してください[方法: 変換演算子を定義する](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)です。</span><span class="sxs-lookup"><span data-stu-id="d3797-174">See [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
 <span data-ttu-id="d3797-175">明示的な変換を実行するとも呼ばれます*キャスト*指定されたデータ型またはオブジェクトのクラスへの式。</span><span class="sxs-lookup"><span data-stu-id="d3797-175">Performing an explicit conversion is also known as *casting* an expression to a given data type or object class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3797-176">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3797-176">See Also</span></span>  
 <span data-ttu-id="d3797-177">[Visual Basic における型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="d3797-177">[Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="d3797-178"> [文字列とその他の型の間の変換](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md) </span><span class="sxs-lookup"><span data-stu-id="d3797-178"> [Conversions Between Strings and Other Types](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md) </span></span>  
<span data-ttu-id="d3797-179"> [方法: Visual Basic での別の型のオブジェクトの変換](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md) </span><span class="sxs-lookup"><span data-stu-id="d3797-179"> [How to: Convert an Object to Another Type in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md) </span></span>  
<span data-ttu-id="d3797-180"> [構造体](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span><span class="sxs-lookup"><span data-stu-id="d3797-180"> [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span></span>  
<span data-ttu-id="d3797-181"> [データ型](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="d3797-181"> [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="d3797-182"> [型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="d3797-182"> [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="d3797-183"> [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="d3797-183"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)</span></span>
