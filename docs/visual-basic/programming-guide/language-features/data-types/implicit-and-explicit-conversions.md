---
title: "暗黙の型変換と明示的な型変換 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- conversions [Visual Basic], type
- variables [Visual Basic], changing data type
- casting
- conversions [Visual Basic], data type
- type conversion [Visual Basic], implicit conversions
- CType function [Visual Basic], conversions
- casting, data types
- data type conversion [Visual Basic], explicit
- type conversion [Visual Basic], explicit conversions
- data types [Visual Basic], casting
- conversions [Visual Basic], implicit
- explicit data type conversions [Visual Basic]
- conversions [Visual Basic]
- changing data types [Visual Basic]
- conversions [Visual Basic], explicit
- data type conversion [Visual Basic], implicit
- implicit data type conversions [Visual Basic]
ms.assetid: 77de1659-af8a-492c-967e-e7ef60ccce66
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6e9dd698e1cc84464cd12d33767feec960c511ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a><span data-ttu-id="6ce18-102">暗黙の型変換と明示的な型変換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ce18-102">Implicit and Explicit Conversions (Visual Basic)</span></span>
<span data-ttu-id="6ce18-103">*暗黙的な変換*特別な構文のソース コードでは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="6ce18-103">An *implicit conversion* does not require any special syntax in the source code.</span></span> <span data-ttu-id="6ce18-104">次の例では、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]の値を暗黙的に変換`k`単精度浮動小数点値を割り当てる前に`q`です。</span><span class="sxs-lookup"><span data-stu-id="6ce18-104">In the following example, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] implicitly converts the value of `k` to a single-precision floating-point value before assigning it to `q`.</span></span>  
  
```  
Dim k As Integer  
Dim q As Double  
' Integer widens to Double, so you can do this with Option Strict On.  
k = 432  
q = k  
```  
  
 <span data-ttu-id="6ce18-105">*明示的な変換*型の変換キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="6ce18-105">An *explicit conversion* uses a type conversion keyword.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="6ce18-106">このようなキーワードが複数、目的のデータ型をかっこで囲まれた式を強制するを提供します。</span><span class="sxs-lookup"><span data-stu-id="6ce18-106"> provides several such keywords, which coerce an expression in parentheses to the desired data type.</span></span> <span data-ttu-id="6ce18-107">関数と同様、これらのキーワードの動作が、コンパイラは、実行は、関数呼び出しよりもわずかに高速に、コード インラインを生成します。</span><span class="sxs-lookup"><span data-stu-id="6ce18-107">These keywords act like functions, but the compiler generates the code inline, so execution is slightly faster than with a function call.</span></span>  
  
 <span data-ttu-id="6ce18-108">前の例では、次の拡張機能に、`CInt`キーワードの値を変換する`q`に割り当てる前に整数に戻す`k`です。</span><span class="sxs-lookup"><span data-stu-id="6ce18-108">In the following extension of the preceding example, the `CInt` keyword converts the value of `q` back to an integer before assigning it to `k`.</span></span>  
  
```  
' q had been assigned the value 432 from k.  
q = Math.Sqrt(q)  
k = CInt(q)  
' k now has the value 21 (rounded square root of 432).  
```  
  
## <a name="conversion-keywords"></a><span data-ttu-id="6ce18-109">変換キーワード</span><span class="sxs-lookup"><span data-stu-id="6ce18-109">Conversion Keywords</span></span>  
 <span data-ttu-id="6ce18-110">次の表は、使用可能な変換のキーワードを示します。</span><span class="sxs-lookup"><span data-stu-id="6ce18-110">The following table shows the available conversion keywords.</span></span>  
  
|<span data-ttu-id="6ce18-111">型変換キーワード</span><span class="sxs-lookup"><span data-stu-id="6ce18-111">Type conversion keyword</span></span>|<span data-ttu-id="6ce18-112">データ型の式に変換します。</span><span class="sxs-lookup"><span data-stu-id="6ce18-112">Converts an expression to data type</span></span>|<span data-ttu-id="6ce18-113">変換する式のデータ型</span><span class="sxs-lookup"><span data-stu-id="6ce18-113">Allowable data types of expression to be converted</span></span>|  
|---|---|---|  
|`CBool`|[<span data-ttu-id="6ce18-114">Boolean データ型</span><span class="sxs-lookup"><span data-stu-id="6ce18-114">Boolean Data Type</span></span>](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="6ce18-115">任意の数値型 (など`Byte`、 `SByte`、および列挙型)、 `String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="6ce18-115">Any numeric type (including `Byte`, `SByte`, and enumerated types), `String`, `Object`</span></span>|  
|`CByte`|[<span data-ttu-id="6ce18-116">Byte データ型</span><span class="sxs-lookup"><span data-stu-id="6ce18-116">Byte Data Type</span></span>](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="6ce18-117">任意の数値型 (など`SByte`および列挙型)、 `Boolean`、 `String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="6ce18-117">Any numeric type (including `SByte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CChar`|[<span data-ttu-id="6ce18-118">Char データ型</span><span class="sxs-lookup"><span data-stu-id="6ce18-118">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="6ce18-119">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="6ce18-119">`String`, `Object`</span></span>|  
|`CDate`|[<span data-ttu-id="6ce18-120">Date データ型</span><span class="sxs-lookup"><span data-stu-id="6ce18-120">Date Data Type</span></span>](../../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="6ce18-121">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="6ce18-121">`String`, `Object`</span></span>|  
|`CDbl`|[<span data-ttu-id="6ce18-122">Double 型</span><span class="sxs-lookup"><span data-stu-id="6ce18-122">Double Data Type</span></span>](../../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="6ce18-123">任意の数値型 (など`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="6ce18-123">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CDec`|[<span data-ttu-id="6ce18-124">Decimal データ型</span><span class="sxs-lookup"><span data-stu-id="6ce18-124">Decimal Data Type</span></span>](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="6ce18-125">任意の数値型 (など`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="6ce18-125">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CInt`|[<span data-ttu-id="6ce18-126">整数データ型</span><span class="sxs-lookup"><span data-stu-id="6ce18-126">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="6ce18-127">任意の数値型 (など`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="6ce18-127">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CLng`|[<span data-ttu-id="6ce18-128">Long データ型</span><span class="sxs-lookup"><span data-stu-id="6ce18-128">Long Data Type</span></span>](../../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="6ce18-129">任意の数値型 (など`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="6ce18-129">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CObj`|[<span data-ttu-id="6ce18-130">Object 型</span><span class="sxs-lookup"><span data-stu-id="6ce18-130">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="6ce18-131">任意の型</span><span class="sxs-lookup"><span data-stu-id="6ce18-131">Any type</span></span>|  
|`CSByte`|[<span data-ttu-id="6ce18-132">SByte データ型</span><span class="sxs-lookup"><span data-stu-id="6ce18-132">SByte Data Type</span></span>](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="6ce18-133">任意の数値型 (など`Byte`および列挙型)、 `Boolean`、 `String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="6ce18-133">Any numeric type (including `Byte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CShort`|[<span data-ttu-id="6ce18-134">Short データ型</span><span class="sxs-lookup"><span data-stu-id="6ce18-134">Short Data Type</span></span>](../../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="6ce18-135">任意の数値型 (など`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="6ce18-135">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CSng`|[<span data-ttu-id="6ce18-136">Single データ型</span><span class="sxs-lookup"><span data-stu-id="6ce18-136">Single Data Type</span></span>](../../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="6ce18-137">任意の数値型 (など`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="6ce18-137">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CStr`|[<span data-ttu-id="6ce18-138">String データ型</span><span class="sxs-lookup"><span data-stu-id="6ce18-138">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="6ce18-139">任意の数値型 (など`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `Char`、`Char`配列、 `Date`、`Object`</span><span class="sxs-lookup"><span data-stu-id="6ce18-139">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `Char`, `Char` array, `Date`, `Object`</span></span>|  
|`CType`|<span data-ttu-id="6ce18-140">コンマの後に指定された型 (`,`)</span><span class="sxs-lookup"><span data-stu-id="6ce18-140">Type specified following the comma (`,`)</span></span>|<span data-ttu-id="6ce18-141">変換する際、*基本データ型*(基本型の配列を含む)、同じ種類として、対応する変換キーワードの許可</span><span class="sxs-lookup"><span data-stu-id="6ce18-141">When converting to an *elementary data type* (including an array of an elementary type), the same types as allowed for the corresponding conversion keyword</span></span><br /><br /> <span data-ttu-id="6ce18-142">変換する際、*複合データ型*、実装するインターフェイスとその継承元となるクラス</span><span class="sxs-lookup"><span data-stu-id="6ce18-142">When converting to a *composite data type*, the interfaces it implements and the classes from which it inherits</span></span><br /><br /> <span data-ttu-id="6ce18-143">オーバー ロードしたクラスまたは構造体に変換するときに`CType`、そのクラスまたは構造体</span><span class="sxs-lookup"><span data-stu-id="6ce18-143">When converting to a class or structure on which you have overloaded `CType`, that class or structure</span></span>|  
|`CUInt`|[<span data-ttu-id="6ce18-144">UInteger データ型</span><span class="sxs-lookup"><span data-stu-id="6ce18-144">UInteger Data Type</span></span>](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="6ce18-145">任意の数値型 (など`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="6ce18-145">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CULng`|[<span data-ttu-id="6ce18-146">ULong データ型</span><span class="sxs-lookup"><span data-stu-id="6ce18-146">ULong Data Type</span></span>](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="6ce18-147">任意の数値型 (など`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="6ce18-147">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CUShort`|[<span data-ttu-id="6ce18-148">UShort データ型</span><span class="sxs-lookup"><span data-stu-id="6ce18-148">UShort Data Type</span></span>](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="6ce18-149">任意の数値型 (など`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="6ce18-149">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
  
## <a name="the-ctype-function"></a><span data-ttu-id="6ce18-150">CType 関数</span><span class="sxs-lookup"><span data-stu-id="6ce18-150">The CType Function</span></span>  
 <span data-ttu-id="6ce18-151">[CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)は 2 つの引数で動作します。</span><span class="sxs-lookup"><span data-stu-id="6ce18-151">The [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) operates on two arguments.</span></span> <span data-ttu-id="6ce18-152">1 つは、変換する式、2 番目の変換先のデータ型またはオブジェクト クラス。</span><span class="sxs-lookup"><span data-stu-id="6ce18-152">The first is the expression to be converted, and the second is the destination data type or object class.</span></span> <span data-ttu-id="6ce18-153">最初の引数は型ではなく、式である必要がありますに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6ce18-153">Note that the first argument must be an expression, not a type.</span></span>  
  
 <span data-ttu-id="6ce18-154">`CType`*インライン関数*変換は、コンパイルされたコードの意味、多くの場合、呼び出す関数は生成されません。</span><span class="sxs-lookup"><span data-stu-id="6ce18-154">`CType` is an *inline function*, meaning the compiled code makes the conversion, often without generating a function call.</span></span> <span data-ttu-id="6ce18-155">これにより、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="6ce18-155">This improves performance.</span></span>  
  
 <span data-ttu-id="6ce18-156">比較について`CType`他の型変換のキーワードと、次を参照してください。 [DirectCast 演算子](../../../../visual-basic/language-reference/operators/directcast-operator.md)と[TryCast 演算子](../../../../visual-basic/language-reference/operators/trycast-operator.md)です。</span><span class="sxs-lookup"><span data-stu-id="6ce18-156">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>  
  
### <a name="elementary-types"></a><span data-ttu-id="6ce18-157">基本型</span><span class="sxs-lookup"><span data-stu-id="6ce18-157">Elementary Types</span></span>  
 <span data-ttu-id="6ce18-158">次の例は、`CType` の使い方を示しています。</span><span class="sxs-lookup"><span data-stu-id="6ce18-158">The following example demonstrates the use of `CType`.</span></span>  
  
```  
k = CType(q, Integer)  
' The following statement coerces w to the specific object class Label.  
f = CType(w, Label)  
```  
  
### <a name="composite-types"></a><span data-ttu-id="6ce18-159">複合型</span><span class="sxs-lookup"><span data-stu-id="6ce18-159">Composite Types</span></span>  
 <span data-ttu-id="6ce18-160">使用することができます`CType`値複合データ型および基本型に変換します。</span><span class="sxs-lookup"><span data-stu-id="6ce18-160">You can use `CType` to convert values to composite data types as well as to elementary types.</span></span> <span data-ttu-id="6ce18-161">また、次の例のように、そのインターフェイスのいずれかの型にオブジェクト クラスを強制的に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="6ce18-161">You can also use it to coerce an object class to the type of one of its interfaces, as in the following example.</span></span>  
  
```  
' Assume class cZone implements interface iZone.  
Dim h As Object  
' The first argument to CType must be an expression, not a type.  
Dim cZ As cZone  
' The following statement coerces a cZone object to its interface iZone.  
h = CType(cZ, iZone)  
```  
  
### <a name="array-types"></a><span data-ttu-id="6ce18-162">配列型</span><span class="sxs-lookup"><span data-stu-id="6ce18-162">Array Types</span></span>  
 <span data-ttu-id="6ce18-163">`CType`次の例のように、配列のデータ型を変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="6ce18-163">`CType` can also convert array data types, as in the following example.</span></span>  
  
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
  
 <span data-ttu-id="6ce18-164">例および詳細については、次を参照してください。[配列変換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)です。</span><span class="sxs-lookup"><span data-stu-id="6ce18-164">For more information and an example, see [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).</span></span>  
  
### <a name="types-defining-ctype"></a><span data-ttu-id="6ce18-165">CType を定義する型</span><span class="sxs-lookup"><span data-stu-id="6ce18-165">Types Defining CType</span></span>  
 <span data-ttu-id="6ce18-166">定義できます`CType`クラスまたは定義した構造にします。</span><span class="sxs-lookup"><span data-stu-id="6ce18-166">You can define `CType` on a class or structure you have defined.</span></span> <span data-ttu-id="6ce18-167">これにより、クラスまたは構造体の型との間の値を変換することができます。</span><span class="sxs-lookup"><span data-stu-id="6ce18-167">This allows you to convert values to and from the type of your class or structure.</span></span> <span data-ttu-id="6ce18-168">例および詳細については、次を参照してください。[する方法: 変換演算子を定義する](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)です。</span><span class="sxs-lookup"><span data-stu-id="6ce18-168">For more information and an example, see [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ce18-169">変換キーワードと共に使用される値を変換先データ型に対して有効にする必要があります。 またはエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="6ce18-169">Values used with a conversion keyword must be valid for the destination data type, or an error occurs.</span></span> <span data-ttu-id="6ce18-170">変換しようとする場合など、`Long`を`Integer`の値、`Long`の有効な範囲内である必要があります、`Integer`データ型。</span><span class="sxs-lookup"><span data-stu-id="6ce18-170">For example, if you attempt to convert a `Long` to an `Integer`, the value of the `Long` must be within the valid range for the `Integer` data type.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="6ce18-171">指定する`CType`ソースの種類が変換先の型から派生していない場合は、実行時に別の失敗を 1 つのクラス型から変換します。</span><span class="sxs-lookup"><span data-stu-id="6ce18-171">Specifying `CType` to convert from one class type to another fails at run time if the source type does not derive from the destination type.</span></span> <span data-ttu-id="6ce18-172">このようなエラーをスロー、<xref:System.InvalidCastException>例外。</span><span class="sxs-lookup"><span data-stu-id="6ce18-172">Such a failure throws an <xref:System.InvalidCastException> exception.</span></span>  
  
 <span data-ttu-id="6ce18-173">ただし、構造体またはクラスを定義した型の 1 つが、定義した場合`CType`その構造体またはクラスで、変換が成功する場合の要件を満たしていれば、`CType`です。</span><span class="sxs-lookup"><span data-stu-id="6ce18-173">However, if one of the types is a structure or class you have defined, and if you have defined `CType` on that structure or class, a conversion can succeed if it satisfies the requirements of your `CType`.</span></span> <span data-ttu-id="6ce18-174">参照してください[する方法: 変換演算子を定義する](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)です。</span><span class="sxs-lookup"><span data-stu-id="6ce18-174">See [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
 <span data-ttu-id="6ce18-175">明示的な変換を実行するとも呼ばれます*キャスト*指定されたデータ型またはオブジェクト クラスへの式。</span><span class="sxs-lookup"><span data-stu-id="6ce18-175">Performing an explicit conversion is also known as *casting* an expression to a given data type or object class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ce18-176">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ce18-176">See Also</span></span>  
 [<span data-ttu-id="6ce18-177">Visual Basic での型変換</span><span class="sxs-lookup"><span data-stu-id="6ce18-177">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="6ce18-178">文字列とその他の型との変換</span><span class="sxs-lookup"><span data-stu-id="6ce18-178">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [<span data-ttu-id="6ce18-179">方法: オブジェクトを Visual Basic での別の型に変換</span><span class="sxs-lookup"><span data-stu-id="6ce18-179">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [<span data-ttu-id="6ce18-180">構造体</span><span class="sxs-lookup"><span data-stu-id="6ce18-180">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="6ce18-181">データの種類</span><span class="sxs-lookup"><span data-stu-id="6ce18-181">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="6ce18-182">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="6ce18-182">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="6ce18-183">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="6ce18-183">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
