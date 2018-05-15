---
title: 型文字 (Visual Basic)
ms.date: 01/31/2018
helpviewer_keywords:
- '&H prefix for hexadecimal values'
- hexadecimal literals [Visual Basic]
- F literal type character [Visual Basic]
- '& identifier type character'
- type characters [Visual Basic]
- octal literals [Visual Basic]
- literals [Visual Basic], hexadecimal
- '&O prefix for octal values'
- literals [Visual Basic], default types
- defaults, literal types
- C literal type character [Visual Basic]
- type characters [Visual Basic], literal
- $ identifier type character
- L literal type character [Visual Basic]
- UI literal type characters [Visual Basic]
- default literal types [Visual Basic]
- D literal type character [Visual Basic]
- literals [Visual Basic], octal
- S literal type character [Visual Basic]
- '! identifier type character'
- US literal type characters [Visual Basic]
- '% identifier type character'
- data types [Visual Basic], type characters
- characters [Visual Basic], identifier type
- type characters [Visual Basic], identifier
- '# identifier type character'
- identifier type characters [Visual Basic]
- literal type characters [Visual Basic]
- I literal type character [Visual Basic]
- R literal type character [Visual Basic]
- '@ identifier type character'
- UL literal type characters [Visual Basic]
- literal types [Visual Basic], default
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9262c57c5773b947f18fd9e8cf9087bb8e02de7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="type-characters-visual-basic"></a><span data-ttu-id="297ca-102">文字 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="297ca-102">Type characters (Visual Basic)</span></span>

<span data-ttu-id="297ca-103">を、宣言ステートメントでのデータ型を指定するだけでなくでプログラミング要素のデータ型を強制することができます、*文字入力*です。</span><span class="sxs-lookup"><span data-stu-id="297ca-103">In addition to specifying a data type in a declaration statement, you can force the data type of some programming elements with a *type character*.</span></span> <span data-ttu-id="297ca-104">型文字間にある任意の種類の文字を含まない、要素の直後にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="297ca-104">The type character must immediately follow the element, with no intervening characters of any kind.</span></span>

<span data-ttu-id="297ca-105">型文字は、要素の名前の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="297ca-105">The type character is not part of the name of the element.</span></span> <span data-ttu-id="297ca-106">型文字を使用せず、型文字で定義された要素を参照できます。</span><span class="sxs-lookup"><span data-stu-id="297ca-106">An element defined with a type character can be referenced without the type character.</span></span>

## <a name="identifier-type-characters"></a><span data-ttu-id="297ca-107">識別子の型文字</span><span class="sxs-lookup"><span data-stu-id="297ca-107">Identifier type characters</span></span>

<span data-ttu-id="297ca-108">Visual Basic のセットを提供する*識別子の型文字*変数または定数のデータ型を指定する宣言で使用できます。</span><span class="sxs-lookup"><span data-stu-id="297ca-108">Visual Basic supplies a set of *identifier type characters* that you can use in a declaration to specify the data type of a variable or constant.</span></span> <span data-ttu-id="297ca-109">次の表は、使用状況の例で使用できる識別子の型文字を示します。</span><span class="sxs-lookup"><span data-stu-id="297ca-109">The following table shows the available identifier type characters with examples of usage.</span></span>
  
|<span data-ttu-id="297ca-110">識別子の型文字</span><span class="sxs-lookup"><span data-stu-id="297ca-110">Identifier type character</span></span>|<span data-ttu-id="297ca-111">データの種類</span><span class="sxs-lookup"><span data-stu-id="297ca-111">Data type</span></span>|<span data-ttu-id="297ca-112">例</span><span class="sxs-lookup"><span data-stu-id="297ca-112">Example</span></span>|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 <span data-ttu-id="297ca-113">識別子の型文字が存在しない、 `Boolean`、 `Byte`、 `Char`、 `Date`、 `Object`、 `SByte`、 `Short`、 `UInteger`、 `ULong`、または`UShort`データ型、またはのいずれか配列や構造体などの複合データ型。</span><span class="sxs-lookup"><span data-stu-id="297ca-113">No identifier type characters exist for the `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="297ca-114">場合によっては、追加することができます、 `$` Visual Basic の関数では、たとえば文字`Left$`の代わりに`Left`、返される型の値を取得する`String`です。</span><span class="sxs-lookup"><span data-stu-id="297ca-114">In some cases, you can append the `$` character to a Visual Basic function, for example `Left$` instead of `Left`, to obtain a returned value of type `String`.</span></span>

<span data-ttu-id="297ca-115">すべての場合、識別子の型文字は、識別子名の直後にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="297ca-115">In all cases, the identifier type character must immediately follow the identifier name.</span></span>

## <a name="literal-type-characters"></a><span data-ttu-id="297ca-116">リテラルの型文字</span><span class="sxs-lookup"><span data-stu-id="297ca-116">Literal type characters</span></span>

<span data-ttu-id="297ca-117">A*リテラル*データ型の特定の値のテキスト表現です。</span><span class="sxs-lookup"><span data-stu-id="297ca-117">A *literal* is a textual representation of a particular value of a data type.</span></span>  

### <a name="default-literal-types"></a><span data-ttu-id="297ca-118">既定のリテラル型</span><span class="sxs-lookup"><span data-stu-id="297ca-118">Default literal types</span></span>

<span data-ttu-id="297ca-119">リテラルの形式、コードに通常表示されるデータ型を決定します。</span><span class="sxs-lookup"><span data-stu-id="297ca-119">The form of a literal as it appears in your code ordinarily determines its data type.</span></span> <span data-ttu-id="297ca-120">次の表は、これらの既定値の型を示します。</span><span class="sxs-lookup"><span data-stu-id="297ca-120">The following table shows these default types.</span></span>  
  
|<span data-ttu-id="297ca-121">リテラルのテキストの形式</span><span class="sxs-lookup"><span data-stu-id="297ca-121">Textual form of literal</span></span>|<span data-ttu-id="297ca-122">既定のデータ型</span><span class="sxs-lookup"><span data-stu-id="297ca-122">Default data type</span></span>|<span data-ttu-id="297ca-123">例</span><span class="sxs-lookup"><span data-stu-id="297ca-123">Example</span></span>|  
|-----------------------------|-----------------------|-------------|  
|<span data-ttu-id="297ca-124">数値いいえ小数部のあります。</span><span class="sxs-lookup"><span data-stu-id="297ca-124">Numeric, no fractional part</span></span>|`Integer`|`2147483647`|  
|<span data-ttu-id="297ca-125">数値いいえ小数部のある、に対して大きすぎます `Integer`</span><span class="sxs-lookup"><span data-stu-id="297ca-125">Numeric, no fractional part, too large for `Integer`</span></span>|`Long`|`2147483648`|  
|<span data-ttu-id="297ca-126">数値、小数部の一部</span><span class="sxs-lookup"><span data-stu-id="297ca-126">Numeric, fractional part</span></span>|`Double`|`1.2`|  
|<span data-ttu-id="297ca-127">二重引用符で囲まれました。</span><span class="sxs-lookup"><span data-stu-id="297ca-127">Enclosed in double quotation marks</span></span>|`String`|`"A"`|  
|<span data-ttu-id="297ca-128">番号記号で囲まれました。</span><span class="sxs-lookup"><span data-stu-id="297ca-128">Enclosed within number signs</span></span>|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a><span data-ttu-id="297ca-129">リテラル型の強制</span><span class="sxs-lookup"><span data-stu-id="297ca-129">Forced literal types</span></span>

<span data-ttu-id="297ca-130">Visual Basic のセットを提供する*リテラルの型文字*、もの以外のデータ型にそのフォームを想定するリテラルを強制的に使用できることを示します。</span><span class="sxs-lookup"><span data-stu-id="297ca-130">Visual Basic supplies a set of *literal type characters*, which you can use to force a literal to assume a data type other than the one its form indicates.</span></span> <span data-ttu-id="297ca-131">リテラルの末尾に文字を追加して行います。</span><span class="sxs-lookup"><span data-stu-id="297ca-131">You do this by appending the character to the end of the literal.</span></span> <span data-ttu-id="297ca-132">次の表は、使用状況の例で使用可能なリテラルの型文字を示します。</span><span class="sxs-lookup"><span data-stu-id="297ca-132">The following table shows the available literal type characters with examples of usage.</span></span>
  
|<span data-ttu-id="297ca-133">リテラルの型文字</span><span class="sxs-lookup"><span data-stu-id="297ca-133">Literal type character</span></span>|<span data-ttu-id="297ca-134">データの種類</span><span class="sxs-lookup"><span data-stu-id="297ca-134">Data type</span></span>|<span data-ttu-id="297ca-135">例</span><span class="sxs-lookup"><span data-stu-id="297ca-135">Example</span></span>|  
|----------------------------|---------------|-------------|  
|`S`|`Short`|`I = 347S`|
|`I`|`Integer`|`J = 347I`|
|`L`|`Long`|`K = 347L`|
|`D`|`Decimal`|`X = 347D`|
|`F`|`Single`|`Y = 347F`|
|`R`|`Double`|`Z = 347R`|
|`US`|`UShort`|`L = 347US`|
|`UI`|`UInteger`|`M = 347UI`|
|`UL`|`ULong`|`N = 347UL`|
|`C`|`Char`|`Q = "."C`|

<span data-ttu-id="297ca-136">リテラルの型文字が存在しない、 `Boolean`、 `Byte`、 `Date`、 `Object`、 `SByte`、または`String`データ型、または配列や構造体などの任意の複合データ型。</span><span class="sxs-lookup"><span data-stu-id="297ca-136">No literal type characters exist for the `Boolean`, `Byte`, `Date`, `Object`, `SByte`, or `String` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="297ca-137">リテラルには、識別子の型文字が使用してもできます (`%`、 `&`、 `@`、 `!`、 `#`、 `$`)、変数、定数、および式のことができます。</span><span class="sxs-lookup"><span data-stu-id="297ca-137">Literals can also use the identifier type characters (`%`, `&`, `@`, `!`, `#`, `$`), as can variables, constants, and expressions.</span></span> <span data-ttu-id="297ca-138">ただし、リテラルの型文字 (`S`、 `I`、 `L`、 `D`、 `F`、 `R`、 `C`) リテラルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="297ca-138">However, the literal type characters (`S`, `I`, `L`, `D`, `F`, `R`, `C`) can be used only with literals.</span></span>

<span data-ttu-id="297ca-139">すべての場合、リテラルの型文字は、リテラル値の直後にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="297ca-139">In all cases, the literal type character must immediately follow the literal value.</span></span>

## <a name="hexadecimal-binary-and-octal-literals"></a><span data-ttu-id="297ca-140">16 進数、バイナリ、および 8 進数リテラル</span><span class="sxs-lookup"><span data-stu-id="297ca-140">Hexadecimal, binary, and octal literals</span></span>

<span data-ttu-id="297ca-141">コンパイラは、通常、10 進数 (基数 10) 番号システム内にある整数リテラルを解釈します。</span><span class="sxs-lookup"><span data-stu-id="297ca-141">The compiler normally interprets an integer literal to be in the decimal (base 10) number system.</span></span> <span data-ttu-id="297ca-142">16 進数 (基数 16) を付けて、整数リテラルを定義することも、 `&H` (基本 2 進数値で、プレフィックス、`&B`プレフィックス、および 8 進数 (基本 8) として番号、`&O`プレフィックス。</span><span class="sxs-lookup"><span data-stu-id="297ca-142">You can also define an integer literal as a hexadecimal (base 16) number with the `&H` prefix, as a binary (base 2) number with the `&B` prefix, and as an octal (base 8) number with the `&O` prefix.</span></span> <span data-ttu-id="297ca-143">プレフィックスに続く数字を数値システムに適したにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="297ca-143">The digits that follow the prefix must be appropriate for the number system.</span></span> <span data-ttu-id="297ca-144">次の表を示します。</span><span class="sxs-lookup"><span data-stu-id="297ca-144">The following table illustrates this.</span></span>  
  
|<span data-ttu-id="297ca-145">基本の数</span><span class="sxs-lookup"><span data-stu-id="297ca-145">Number base</span></span>|<span data-ttu-id="297ca-146">プレフィックス</span><span class="sxs-lookup"><span data-stu-id="297ca-146">Prefix</span></span>|<span data-ttu-id="297ca-147">有効桁の値</span><span class="sxs-lookup"><span data-stu-id="297ca-147">Valid digit values</span></span>|<span data-ttu-id="297ca-148">例</span><span class="sxs-lookup"><span data-stu-id="297ca-148">Example</span></span>|
|-----------------|------------|------------------------|-------------|
|<span data-ttu-id="297ca-149">16 進数 (基数 16)。</span><span class="sxs-lookup"><span data-stu-id="297ca-149">Hexadecimal (base 16)</span></span>|`&H`|<span data-ttu-id="297ca-150">0 ~ 9 および A ~ F</span><span class="sxs-lookup"><span data-stu-id="297ca-150">0-9 and A-F</span></span>|`&HFFFF`|
|<span data-ttu-id="297ca-151">バイナリ (基本 2)</span><span class="sxs-lookup"><span data-stu-id="297ca-151">Binary (base 2)</span></span>|`&B`|<span data-ttu-id="297ca-152">0-1</span><span class="sxs-lookup"><span data-stu-id="297ca-152">0-1</span></span>|`&B01111100`|
|<span data-ttu-id="297ca-153">8 進数 (基数 8)。</span><span class="sxs-lookup"><span data-stu-id="297ca-153">Octal (base 8)</span></span>|`&O`|<span data-ttu-id="297ca-154">0-7</span><span class="sxs-lookup"><span data-stu-id="297ca-154">0-7</span></span>|`&O77`|

<span data-ttu-id="297ca-155">Visual Basic 2017 以降、アンダー スコア文字を使用することができます (`_`) 整数リテラルの読みやすさを強化するために桁区切り記号として。</span><span class="sxs-lookup"><span data-stu-id="297ca-155">Starting in Visual Basic 2017, you can use the underscore character (`_`) as a group separator to enhance the readability of an integral literal.</span></span> <span data-ttu-id="297ca-156">次の例では、`_`バイナリ リテラルを 8 ビットのグループにグループ化する文字。</span><span class="sxs-lookup"><span data-stu-id="297ca-156">The following example uses the `_` character to group a binary literal into 8-bit groups:</span></span>

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

<span data-ttu-id="297ca-157">リテラルの型文字を持つプレフィックスが指定されたリテラルに従うことができます。</span><span class="sxs-lookup"><span data-stu-id="297ca-157">You can follow a prefixed literal with a literal type character.</span></span> <span data-ttu-id="297ca-158">この例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="297ca-158">The following example shows this.</span></span>

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

<span data-ttu-id="297ca-159">前の例では、 `counter` -32768 の 10 進値を持つと`flags`+32768 の 10 進値を持つファイルです。</span><span class="sxs-lookup"><span data-stu-id="297ca-159">In the previous example, `counter` has the decimal value of -32768, and `flags` has the decimal value of +32768.</span></span>

<span data-ttu-id="297ca-160">Visual Basic 15.5 から始めて、使用することできますも、アンダー スコア文字 (`_`) のプレフィックスと 16 進数、バイナリ、または 8 進数の数字間に先行する区切り記号として。</span><span class="sxs-lookup"><span data-stu-id="297ca-160">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="297ca-161">例えば:</span><span class="sxs-lookup"><span data-stu-id="297ca-161">For example:</span></span>

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a><span data-ttu-id="297ca-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="297ca-162">See Also</span></span>

 [<span data-ttu-id="297ca-163">データの種類</span><span class="sxs-lookup"><span data-stu-id="297ca-163">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="297ca-164">基本データ型</span><span class="sxs-lookup"><span data-stu-id="297ca-164">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="297ca-165">値型と参照型</span><span class="sxs-lookup"><span data-stu-id="297ca-165">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="297ca-166">Visual Basic での型変換</span><span class="sxs-lookup"><span data-stu-id="297ca-166">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="297ca-167">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="297ca-167">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="297ca-168">変数宣言</span><span class="sxs-lookup"><span data-stu-id="297ca-168">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="297ca-169">データの種類</span><span class="sxs-lookup"><span data-stu-id="297ca-169">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
