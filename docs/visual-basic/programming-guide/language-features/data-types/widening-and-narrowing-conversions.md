---
title: 拡大変換と縮小変換 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- widening conversions [Visual Basic]
- narrowing conversions [Visual Basic]
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- conversions [Visual Basic], exceptions during conversion
- type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], data type
- conversions [Visual Basic], narrowing
- type conversion [Visual Basic], narrowing
- data type conversion [Visual Basic], widening
- data type conversion [Visual Basic], narrowing
- changing data types [Visual Basic]
- type conversion [Visual Basic], widening
- data type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], widening
ms.assetid: 058c3152-6c28-4268-af44-2209e774f0bd
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 960b4e4c7184309b6a84247d86fb94ccb2faf877
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a><span data-ttu-id="22ac0-102">拡大変換と縮小変換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22ac0-102">Widening and Narrowing Conversions (Visual Basic)</span></span>
<span data-ttu-id="22ac0-103">型変換で重要な考慮事項は、変換の結果が対象のデータ型の範囲内かどうかです。</span><span class="sxs-lookup"><span data-stu-id="22ac0-103">An important consideration with a type conversion is whether the result of the conversion is within the range of the destination data type.</span></span>  
  
 <span data-ttu-id="22ac0-104">A*拡大変換*元のデータのすべての値のことが許可されるデータ型に値を変更します。</span><span class="sxs-lookup"><span data-stu-id="22ac0-104">A *widening conversion* changes a value to a data type that can allow for any possible value of the original data.</span></span>  <span data-ttu-id="22ac0-105">拡大変換では、元の値を保持するが、その表現を変更できます。</span><span class="sxs-lookup"><span data-stu-id="22ac0-105">Widening conversions preserve the source value but can change its representation.</span></span> <span data-ttu-id="22ac0-106">これから整数型に変換する場合に発生`Decimal`、またはから`Char`に`String`です。</span><span class="sxs-lookup"><span data-stu-id="22ac0-106">This occurs if you convert from an integral type to `Decimal`, or from `Char` to `String`.</span></span>  
  
 <span data-ttu-id="22ac0-107">*縮小変換* により、有効値の一部を保持できない可能性のあるデータ型に値が変更されます。</span><span class="sxs-lookup"><span data-stu-id="22ac0-107">A *narrowing conversion* changes a value to a data type that might not be able to hold some of the possible values.</span></span> <span data-ttu-id="22ac0-108">たとえば、小数部の値は、整数型、および変換される数値型に変換されるときに丸められます`Boolean`がいずれかに縮小された`True`または`False`です。</span><span class="sxs-lookup"><span data-stu-id="22ac0-108">For example, a fractional value is rounded when it is converted to an integral type, and a numeric type being converted to `Boolean` is reduced to either `True` or `False`.</span></span>  
  
## <a name="widening-conversions"></a><span data-ttu-id="22ac0-109">拡大変換</span><span class="sxs-lookup"><span data-stu-id="22ac0-109">Widening Conversions</span></span>  
 <span data-ttu-id="22ac0-110">次の表は、標準の拡大変換を示します。</span><span class="sxs-lookup"><span data-stu-id="22ac0-110">The following table shows the standard widening conversions.</span></span>  
  
|<span data-ttu-id="22ac0-111">データの種類</span><span class="sxs-lookup"><span data-stu-id="22ac0-111">Data type</span></span>|<span data-ttu-id="22ac0-112">データ型に拡大変換<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="22ac0-112">Widens to data types <sup>1</sup></span></span>|  
|---|---|  
|[<span data-ttu-id="22ac0-113">SByte</span><span class="sxs-lookup"><span data-stu-id="22ac0-113">SByte</span></span>](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="22ac0-114">`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="22ac0-114">`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="22ac0-115">Byte</span><span class="sxs-lookup"><span data-stu-id="22ac0-115">Byte</span></span>](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="22ac0-116">`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long`、`ULong`、`Decimal`、`Single`、`Double`</span><span class="sxs-lookup"><span data-stu-id="22ac0-116">`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="22ac0-117">Short</span><span class="sxs-lookup"><span data-stu-id="22ac0-117">Short</span></span>](../../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="22ac0-118">`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="22ac0-118">`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="22ac0-119">UShort</span><span class="sxs-lookup"><span data-stu-id="22ac0-119">UShort</span></span>](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="22ac0-120">`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="22ac0-120">`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="22ac0-121">Integer</span><span class="sxs-lookup"><span data-stu-id="22ac0-121">Integer</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="22ac0-122">`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="22ac0-122">`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="22ac0-123">UInteger</span><span class="sxs-lookup"><span data-stu-id="22ac0-123">UInteger</span></span>](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="22ac0-124">`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="22ac0-124">`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="22ac0-125">Long</span><span class="sxs-lookup"><span data-stu-id="22ac0-125">Long</span></span>](../../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="22ac0-126">`Long`, `Decimal`, `Single`, `Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="22ac0-126">`Long`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="22ac0-127">ULong</span><span class="sxs-lookup"><span data-stu-id="22ac0-127">ULong</span></span>](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="22ac0-128">`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="22ac0-128">`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="22ac0-129">Decimal</span><span class="sxs-lookup"><span data-stu-id="22ac0-129">Decimal</span></span>](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="22ac0-130">`Decimal`, `Single`, `Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="22ac0-130">`Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="22ac0-131">Single</span><span class="sxs-lookup"><span data-stu-id="22ac0-131">Single</span></span>](../../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="22ac0-132">`Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="22ac0-132">`Single`, `Double`</span></span>|  
|[<span data-ttu-id="22ac0-133">Double</span><span class="sxs-lookup"><span data-stu-id="22ac0-133">Double</span></span>](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|<span data-ttu-id="22ac0-134">いずれかの列挙型 ([Enum](../../../../visual-basic/language-reference/statements/enum-statement.md))</span><span class="sxs-lookup"><span data-stu-id="22ac0-134">Any enumerated type ([Enum](../../../../visual-basic/language-reference/statements/enum-statement.md))</span></span>|<span data-ttu-id="22ac0-135">基になる整数型と任意の型を基になる型が拡大変換されます。</span><span class="sxs-lookup"><span data-stu-id="22ac0-135">Its underlying integral type and any type to which the underlying type widens.</span></span>|  
|[<span data-ttu-id="22ac0-136">Char</span><span class="sxs-lookup"><span data-stu-id="22ac0-136">Char</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="22ac0-137">`Char`, `String`</span><span class="sxs-lookup"><span data-stu-id="22ac0-137">`Char`, `String`</span></span>|  
|<span data-ttu-id="22ac0-138">`Char` 配列</span><span class="sxs-lookup"><span data-stu-id="22ac0-138">`Char` array</span></span>|<span data-ttu-id="22ac0-139">`Char` 配列、 `String`</span><span class="sxs-lookup"><span data-stu-id="22ac0-139">`Char` array, `String`</span></span>|  
|<span data-ttu-id="22ac0-140">任意の型</span><span class="sxs-lookup"><span data-stu-id="22ac0-140">Any type</span></span>|[<span data-ttu-id="22ac0-141">オブジェクト</span><span class="sxs-lookup"><span data-stu-id="22ac0-141">Object</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|<span data-ttu-id="22ac0-142">すべての派生型</span><span class="sxs-lookup"><span data-stu-id="22ac0-142">Any derived type</span></span>|<span data-ttu-id="22ac0-143">任意の派生元となる型の基本<sup>3</sup>です。</span><span class="sxs-lookup"><span data-stu-id="22ac0-143">Any base type from which it is derived <sup>3</sup>.</span></span>|  
|<span data-ttu-id="22ac0-144">任意の型</span><span class="sxs-lookup"><span data-stu-id="22ac0-144">Any type</span></span>|<span data-ttu-id="22ac0-145">任意のインターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="22ac0-145">Any interface it implements.</span></span>|  
|[<span data-ttu-id="22ac0-146">Nothing</span><span class="sxs-lookup"><span data-stu-id="22ac0-146">Nothing</span></span>](../../../../visual-basic/language-reference/nothing.md)|<span data-ttu-id="22ac0-147">任意のデータ型またはオブジェクトの種類。</span><span class="sxs-lookup"><span data-stu-id="22ac0-147">Any data type or object type.</span></span>|  
  
 <span data-ttu-id="22ac0-148"><sup>1</sup>定義では、すべてのデータ型は自動的に拡大します。</span><span class="sxs-lookup"><span data-stu-id="22ac0-148"><sup>1</sup> By definition, every data type widens to itself.</span></span>  
  
 <span data-ttu-id="22ac0-149"><sup>2</sup>から変換`Integer`、 `UInteger`、 `Long`、 `ULong`、または`Decimal`に`Single`または`Double`大きさが失われることはありませんが、精度が失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="22ac0-149"><sup>2</sup> Conversions from `Integer`, `UInteger`, `Long`, `ULong`, or `Decimal` to `Single` or `Double` might result in loss of precision, but never in loss of magnitude.</span></span> <span data-ttu-id="22ac0-150">この意味でこれらが発生しない情報が失われる。</span><span class="sxs-lookup"><span data-stu-id="22ac0-150">In this sense they do not incur information loss.</span></span>  
  
 <span data-ttu-id="22ac0-151"><sup>3</sup>派生型からその基本型のいずれかへの変換を拡大することにより意外かもしれません。</span><span class="sxs-lookup"><span data-stu-id="22ac0-151"><sup>3</sup> It might seem surprising that a conversion from a derived type to one of its base types is widening.</span></span> <span data-ttu-id="22ac0-152">理由は、基本型のインスタンスと見なされるにように、派生型にはで、基本型のすべてのメンバーが含まれているです。</span><span class="sxs-lookup"><span data-stu-id="22ac0-152">The justification is that the derived type contains all the members of the base type, so it qualifies as an instance of the base type.</span></span> <span data-ttu-id="22ac0-153">反対の方向に基本型では、派生型によって定義されたメンバーは含まれません。</span><span class="sxs-lookup"><span data-stu-id="22ac0-153">In the opposite direction, the base type does not contain any new members defined by the derived type.</span></span>  
  
 <span data-ttu-id="22ac0-154">拡大変換は実行時に常に成功して、データの損失が発生することはありません。</span><span class="sxs-lookup"><span data-stu-id="22ac0-154">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="22ac0-155">暗黙的に常に実行しているかどうか、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)チェックするスイッチの種類を設定`On`または`Off`です。</span><span class="sxs-lookup"><span data-stu-id="22ac0-155">You can always perform them implicitly, whether the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) sets the type checking switch to `On` or to `Off`.</span></span>  
  
## <a name="narrowing-conversions"></a><span data-ttu-id="22ac0-156">縮小変換</span><span class="sxs-lookup"><span data-stu-id="22ac0-156">Narrowing Conversions</span></span>  
 <span data-ttu-id="22ac0-157">標準の縮小変換は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="22ac0-157">The standard narrowing conversions include the following:</span></span>  
  
-   <span data-ttu-id="22ac0-158">逆方向の拡大変換、上記のテーブル (する点を除いてすべての型は、自動的に拡大)</span><span class="sxs-lookup"><span data-stu-id="22ac0-158">The reverse directions of the widening conversions in the preceding table (except that every type widens to itself)</span></span>  
  
-   <span data-ttu-id="22ac0-159">どちらの方向との間で変換[ブール](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)と任意の数値型</span><span class="sxs-lookup"><span data-stu-id="22ac0-159">Conversions in either direction between [Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) and any numeric type</span></span>  
  
-   <span data-ttu-id="22ac0-160">列挙型のいずれかの任意の数値型に変換 (`Enum`)</span><span class="sxs-lookup"><span data-stu-id="22ac0-160">Conversions from any numeric type to any enumerated type (`Enum`)</span></span>  
  
-   <span data-ttu-id="22ac0-161">どちらの方向との間で変換[文字列](../../../../visual-basic/language-reference/data-types/string-data-type.md)と任意の数値型`Boolean`、または[日付](../../../../visual-basic/language-reference/data-types/date-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="22ac0-161">Conversions in either direction between [String](../../../../visual-basic/language-reference/data-types/string-data-type.md) and any numeric type, `Boolean`, or [Date](../../../../visual-basic/language-reference/data-types/date-data-type.md)</span></span>  
  
-   <span data-ttu-id="22ac0-162">それから派生した型に型またはオブジェクトのデータ型からの変換</span><span class="sxs-lookup"><span data-stu-id="22ac0-162">Conversions from a data type or object type to a type derived from it</span></span>  
  
 <span data-ttu-id="22ac0-163">縮小変換は常にではありません、実行時に成功し失敗したり、データの損失を伴うできます。</span><span class="sxs-lookup"><span data-stu-id="22ac0-163">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="22ac0-164">対象のデータ型が変換される値を受信できない場合は、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="22ac0-164">An error occurs if the destination data type cannot receive the value being converted.</span></span> <span data-ttu-id="22ac0-165">たとえば、数値の変換はオーバーフローになります。</span><span class="sxs-lookup"><span data-stu-id="22ac0-165">For example, a numeric conversion can result in an overflow.</span></span> <span data-ttu-id="22ac0-166">コンパイラがしない限り、縮小変換を暗黙的に実行を許可していない、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)チェックするスイッチの種類を設定`Off`です。</span><span class="sxs-lookup"><span data-stu-id="22ac0-166">The compiler does not allow you to perform narrowing conversions implicitly unless the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) sets the type checking switch to `Off`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="22ac0-167">内の要素からの変換の縮小変換エラーは出力されず、`For Each…Next`ループ コントロール変数のコレクション。</span><span class="sxs-lookup"><span data-stu-id="22ac0-167">The narrowing-conversion error is suppressed for conversions from the elements in a `For Each…Next` collection to the loop control variable.</span></span> <span data-ttu-id="22ac0-168">詳細と例については、「縮小変換」セクションを参照して[ごとにしています.次のステートメントの](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="22ac0-168">For more information and examples, see the "Narrowing Conversions" section in [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
### <a name="when-to-use-narrowing-conversions"></a><span data-ttu-id="22ac0-169">縮小変換を使用する場合</span><span class="sxs-lookup"><span data-stu-id="22ac0-169">When to Use Narrowing Conversions</span></span>  
 <span data-ttu-id="22ac0-170">元の値は、エラーやデータ損失なし、移行先のデータ型に変換できることがわかっている場合に、縮小変換を使用します。</span><span class="sxs-lookup"><span data-stu-id="22ac0-170">You use a narrowing conversion when you know the source value can be converted to the destination data type without error or data loss.</span></span> <span data-ttu-id="22ac0-171">ある場合など、`String`がわかっている"True"または"False"を含む、行うこともできます、`CBool`に変換するキーワード`Boolean`です。</span><span class="sxs-lookup"><span data-stu-id="22ac0-171">For example, if you have a `String` that you know contains either "True" or "False," you can use the `CBool` keyword to convert it to `Boolean`.</span></span>  
  
## <a name="exceptions-during-conversion"></a><span data-ttu-id="22ac0-172">変換中に例外</span><span class="sxs-lookup"><span data-stu-id="22ac0-172">Exceptions During Conversion</span></span>  
 <span data-ttu-id="22ac0-173">拡大変換は常に、成功しますが、例外をスローしないでください。</span><span class="sxs-lookup"><span data-stu-id="22ac0-173">Because widening conversions always succeed, they do not throw exceptions.</span></span> <span data-ttu-id="22ac0-174">縮小変換、失敗した場合は、最もよく、次の例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="22ac0-174">Narrowing conversions, when they fail, most commonly throw the following exceptions:</span></span>  
  
-   <span data-ttu-id="22ac0-175"><xref:System.InvalidCastException> -次の 2 つの型の間で変換が定義されていない場合</span><span class="sxs-lookup"><span data-stu-id="22ac0-175"><xref:System.InvalidCastException> — if no conversion is defined between the two types</span></span>  
  
-   <span data-ttu-id="22ac0-176"><xref:System.OverflowException> — (整数型のみ) 指定した型の変換後の値が大きすぎる場合</span><span class="sxs-lookup"><span data-stu-id="22ac0-176"><xref:System.OverflowException> — (integral types only) if the converted value is too large for the target type</span></span>  
  
 <span data-ttu-id="22ac0-177">クラスまたは構造体が定義されている場合、 [CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)そのクラスまたは構造体、または変換演算子として使用するを`CType`適切と見なされるすべての例外をスローすることができます。</span><span class="sxs-lookup"><span data-stu-id="22ac0-177">If a class or structure defines a [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to serve as a conversion operator to or from that class or structure, that `CType` can throw any exception it deems appropriate.</span></span> <span data-ttu-id="22ac0-178">さらを`CType`Visual Basic の関数を呼び出すことがありますまたは[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]メソッドで、さらに、さまざまな例外をスローする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="22ac0-178">In addition, that `CType` might call Visual Basic functions or [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] methods, which in turn could throw a variety of exceptions.</span></span>  
  
## <a name="changes-during-reference-type-conversions"></a><span data-ttu-id="22ac0-179">参照型の変換中の変更</span><span class="sxs-lookup"><span data-stu-id="22ac0-179">Changes During Reference Type Conversions</span></span>  
 <span data-ttu-id="22ac0-180">変換、*型参照*ポインターだけが、値をコピーします。</span><span class="sxs-lookup"><span data-stu-id="22ac0-180">A conversion from a *reference type* copies only the pointer to the value.</span></span> <span data-ttu-id="22ac0-181">値そのものがコピーも、任意の方法で変更します。</span><span class="sxs-lookup"><span data-stu-id="22ac0-181">The value itself is neither copied nor changed in any way.</span></span> <span data-ttu-id="22ac0-182">変更可能な唯一の機能は、ポインターを保持する変数のデータ型です。</span><span class="sxs-lookup"><span data-stu-id="22ac0-182">The only thing that can change is the data type of the variable holding the pointer.</span></span> <span data-ttu-id="22ac0-183">次の例では、その基本クラスに、派生クラスからデータ型が変換されますが、両方の変数をポイントするようになりましたオブジェクトは変更されません。</span><span class="sxs-lookup"><span data-stu-id="22ac0-183">In the following example, the data type is converted from the derived class to its base class, but the object that both variables now point to is unchanged.</span></span>  
  
```  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a><span data-ttu-id="22ac0-184">関連項目</span><span class="sxs-lookup"><span data-stu-id="22ac0-184">See Also</span></span>  
 [<span data-ttu-id="22ac0-185">データの種類</span><span class="sxs-lookup"><span data-stu-id="22ac0-185">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="22ac0-186">Visual Basic での型変換</span><span class="sxs-lookup"><span data-stu-id="22ac0-186">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="22ac0-187">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="22ac0-187">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="22ac0-188">文字列とその他の型との変換</span><span class="sxs-lookup"><span data-stu-id="22ac0-188">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [<span data-ttu-id="22ac0-189">方法: オブジェクトを Visual Basic での別の型に変換</span><span class="sxs-lookup"><span data-stu-id="22ac0-189">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [<span data-ttu-id="22ac0-190">配列変換</span><span class="sxs-lookup"><span data-stu-id="22ac0-190">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [<span data-ttu-id="22ac0-191">データの種類</span><span class="sxs-lookup"><span data-stu-id="22ac0-191">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="22ac0-192">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="22ac0-192">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
