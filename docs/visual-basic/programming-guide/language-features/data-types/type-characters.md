---
title: "文字 (Visual Basic) を入力して |Microsoft ドキュメント"
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
- '&H prefix for hexadecimal values'
- hexadecimal literals
- F literal type character
- '& identifier type character'
- type characters
- octal literals
- literals, hexadecimal
- '&O prefix for octal values'
- literals, default types
- defaults, literal types
- C literal type character
- type characters, literal
- $ identifier type character
- L literal type character
- UI literal type characters
- default literal types
- D literal type character
- literals, octal
- S literal type character
- '! identifier type character'
- US literal type characters
- '% identifier type character'
- data types [Visual Basic], type characters
- characters, identifier type
- type characters, identifier
- '# identifier type character'
- identifier type characters
- literal type characters
- I literal type character
- R literal type character
- '@ identifier type character'
- UL literal type characters
- literal types, default
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
caps.latest.revision: 22
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
ms.openlocfilehash: 335306eca12070de456a72e918bcbba1e22ab55b
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="type-characters-visual-basic"></a><span data-ttu-id="4cba8-102">型文字 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4cba8-102">Type Characters (Visual Basic)</span></span>
<span data-ttu-id="4cba8-103">一部のプログラミング要素のデータ型を強制する宣言ステートメントでデータ型を指定することだけでなく、*文字を入力*します。</span><span class="sxs-lookup"><span data-stu-id="4cba8-103">In addition to specifying a data type in a declaration statement, you can force the data type of some programming elements with a *type character*.</span></span> <span data-ttu-id="4cba8-104">型の文字の任意の種類の要素の直後にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4cba8-104">The type character must immediately follow the element, with no intervening characters of any kind.</span></span>  
  
 <span data-ttu-id="4cba8-105">型文字は、要素の名前の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="4cba8-105">The type character is not part of the name of the element.</span></span> <span data-ttu-id="4cba8-106">型文字型の文字で定義された要素を参照できます。</span><span class="sxs-lookup"><span data-stu-id="4cba8-106">An element defined with a type character can be referenced without the type character.</span></span>  
  
## <a name="identifier-type-characters"></a><span data-ttu-id="4cba8-107">識別子の型文字</span><span class="sxs-lookup"><span data-stu-id="4cba8-107">Identifier Type Characters</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="4cba8-108">セットを提供*識別子の型文字*、変数または定数のデータ型を指定する宣言で使用することができます。</span><span class="sxs-lookup"><span data-stu-id="4cba8-108"> supplies a set of *identifier type characters*, which you can use in a declaration to specify the data type of a variable or constant.</span></span> <span data-ttu-id="4cba8-109">次の表は、使用状況の例を含む使用可能な識別子の型文字を示します。</span><span class="sxs-lookup"><span data-stu-id="4cba8-109">The following table shows the available identifier type characters with examples of usage.</span></span>  
  
|<span data-ttu-id="4cba8-110">識別子の型文字</span><span class="sxs-lookup"><span data-stu-id="4cba8-110">Identifier type character</span></span>|<span data-ttu-id="4cba8-111">データ型</span><span class="sxs-lookup"><span data-stu-id="4cba8-111">Data type</span></span>|<span data-ttu-id="4cba8-112">例</span><span class="sxs-lookup"><span data-stu-id="4cba8-112">Example</span></span>|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 <span data-ttu-id="4cba8-113">識別子の型文字が存在していない、 `Boolean`、 `Byte`、 `Char`、 `Date`、 `Object`、 `SByte`、 `Short`、 `UInteger`、 `ULong`、または`UShort`データ型、または配列や構造体などの任意の複合データ型。</span><span class="sxs-lookup"><span data-stu-id="4cba8-113">No identifier type characters exist for the `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort` data types, or for any composite data types such as arrays or structures.</span></span>  
  
 <span data-ttu-id="4cba8-114">場合によっては、追加することができます、`$`に、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]機能、たとえば`Left$`の代わりに`Left`、返される型の値を取得する`String`です。</span><span class="sxs-lookup"><span data-stu-id="4cba8-114">In some cases, you can append the `$` character to a [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] function, for example `Left$` instead of `Left`, to obtain a returned value of type `String`.</span></span>  
  
 <span data-ttu-id="4cba8-115">すべての場合、識別子の型文字は、識別名の直後にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4cba8-115">In all cases, the identifier type character must immediately follow the identifier name.</span></span>  
  
## <a name="literal-type-characters"></a><span data-ttu-id="4cba8-116">リテラルの型文字</span><span class="sxs-lookup"><span data-stu-id="4cba8-116">Literal Type Characters</span></span>  
 <span data-ttu-id="4cba8-117">A*リテラル*データ型の特定の値のテキスト表現です。</span><span class="sxs-lookup"><span data-stu-id="4cba8-117">A *literal* is a textual representation of a particular value of a data type.</span></span>  
  
### <a name="default-literal-types"></a><span data-ttu-id="4cba8-118">既定のリテラル型</span><span class="sxs-lookup"><span data-stu-id="4cba8-118">Default Literal Types</span></span>  
 <span data-ttu-id="4cba8-119">通常、コード内のリテラルの形式によってのデータ型が決まります。</span><span class="sxs-lookup"><span data-stu-id="4cba8-119">The form of a literal as it appears in your code ordinarily determines its data type.</span></span> <span data-ttu-id="4cba8-120">次の表は、これらの既定の種類を示します。</span><span class="sxs-lookup"><span data-stu-id="4cba8-120">The following table shows these default types.</span></span>  
  
|<span data-ttu-id="4cba8-121">リテラルのテキストの形式</span><span class="sxs-lookup"><span data-stu-id="4cba8-121">Textual form of literal</span></span>|<span data-ttu-id="4cba8-122">既定のデータ型</span><span class="sxs-lookup"><span data-stu-id="4cba8-122">Default data type</span></span>|<span data-ttu-id="4cba8-123">例</span><span class="sxs-lookup"><span data-stu-id="4cba8-123">Example</span></span>|  
|-----------------------------|-----------------------|-------------|  
|<span data-ttu-id="4cba8-124">数値の小数部のない部分</span><span class="sxs-lookup"><span data-stu-id="4cba8-124">Numeric, no fractional part</span></span>|`Integer`|`2147483647`|  
|<span data-ttu-id="4cba8-125">数値いいえ小数部のある、に対して大きすぎます`Integer`</span><span class="sxs-lookup"><span data-stu-id="4cba8-125">Numeric, no fractional part, too large for `Integer`</span></span>|`Long`|`2147483648`|  
|<span data-ttu-id="4cba8-126">数値、小数部の一部</span><span class="sxs-lookup"><span data-stu-id="4cba8-126">Numeric, fractional part</span></span>|`Double`|`1.2`|  
|<span data-ttu-id="4cba8-127">二重引用符で囲まれました。</span><span class="sxs-lookup"><span data-stu-id="4cba8-127">Enclosed in double quotation marks</span></span>|`String`|`"A"`|  
|<span data-ttu-id="4cba8-128">シャープ記号で囲まれました。</span><span class="sxs-lookup"><span data-stu-id="4cba8-128">Enclosed within number signs</span></span>|`Date`|`#5/17/1993 9:32 AM#`|  
  
### <a name="forced-literal-types"></a><span data-ttu-id="4cba8-129">リテラル型の強制</span><span class="sxs-lookup"><span data-stu-id="4cba8-129">Forced Literal Types</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="4cba8-130">セットを提供*リテラルの型文字*に、1 つ以外のデータ型の形式を強制的に使用できることを示します。</span><span class="sxs-lookup"><span data-stu-id="4cba8-130"> supplies a set of *literal type characters*, which you can use to force a literal to assume a data type other than the one its form indicates.</span></span> <span data-ttu-id="4cba8-131">リテラルの末尾に文字を付加して行います。</span><span class="sxs-lookup"><span data-stu-id="4cba8-131">You do this by appending the character to the end of the literal.</span></span> <span data-ttu-id="4cba8-132">次の表は、使用状況の例を含む使用可能なリテラルの型文字を示します。</span><span class="sxs-lookup"><span data-stu-id="4cba8-132">The following table shows the available literal type characters with examples of usage.</span></span>  
  
|<span data-ttu-id="4cba8-133">リテラルの型文字</span><span class="sxs-lookup"><span data-stu-id="4cba8-133">Literal type character</span></span>|<span data-ttu-id="4cba8-134">データ型</span><span class="sxs-lookup"><span data-stu-id="4cba8-134">Data type</span></span>|<span data-ttu-id="4cba8-135">例</span><span class="sxs-lookup"><span data-stu-id="4cba8-135">Example</span></span>|  
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
  
 <span data-ttu-id="4cba8-136">リテラルの型文字が存在していない、 `Boolean`、 `Byte`、 `Date`、 `Object`、 `SByte`、または`String`データ型、または配列や構造体などの任意の複合データ型。</span><span class="sxs-lookup"><span data-stu-id="4cba8-136">No literal type characters exist for the `Boolean`, `Byte`, `Date`, `Object`, `SByte`, or `String` data types, or for any composite data types such as arrays or structures.</span></span>  
  
 <span data-ttu-id="4cba8-137">リテラルは識別子の型文字にも行えます (`%`、 `&`、 `@`、 `!`、 `#`、 `$`)、変数、定数、式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="4cba8-137">Literals can also use the identifier type characters (`%`, `&`, `@`, `!`, `#`, `$`), as can variables, constants, and expressions.</span></span> <span data-ttu-id="4cba8-138">ただし、リテラルの型文字 (`S`、 `I`、 `L`、 `D`、 `F`、 `R`、 `C`) リテラルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="4cba8-138">However, the literal type characters (`S`, `I`, `L`, `D`, `F`, `R`, `C`) can be used only with literals.</span></span>  
  
 <span data-ttu-id="4cba8-139">すべての場合、リテラルの型文字はリテラル値の直後にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4cba8-139">In all cases, the literal type character must immediately follow the literal value.</span></span>  
  
## <a name="hexadecimal-and-octal-literals"></a><span data-ttu-id="4cba8-140">8 進数および&16; 進数リテラル</span><span class="sxs-lookup"><span data-stu-id="4cba8-140">Hexadecimal and Octal Literals</span></span>  
 <span data-ttu-id="4cba8-141">コンパイラでは、整数リテラルを 10 進数 (基数 10) の数のシステムで通常として解釈します。</span><span class="sxs-lookup"><span data-stu-id="4cba8-141">The compiler normally construes an integer literal to be in the decimal (base 10) number system.</span></span> <span data-ttu-id="4cba8-142">リテラルに整数を強制できます 16 進数 (基数 16)、`&H`プレフィックス、およびするは、8 進数 (基数 8) を使用する、`&O`プレフィックス。</span><span class="sxs-lookup"><span data-stu-id="4cba8-142">You can force an integer literal to be hexadecimal (base 16) with the `&H` prefix, and you can force it to be octal (base 8) with the `&O` prefix.</span></span> <span data-ttu-id="4cba8-143">続くプレフィックスの数字は、数のシステムに適切なである必要があります。</span><span class="sxs-lookup"><span data-stu-id="4cba8-143">The digits that follow the prefix must be appropriate for the number system.</span></span> <span data-ttu-id="4cba8-144">次の表を示します。</span><span class="sxs-lookup"><span data-stu-id="4cba8-144">The following table illustrates this.</span></span>  
  
|<span data-ttu-id="4cba8-145">基数</span><span class="sxs-lookup"><span data-stu-id="4cba8-145">Number base</span></span>|<span data-ttu-id="4cba8-146">プレフィックス</span><span class="sxs-lookup"><span data-stu-id="4cba8-146">Prefix</span></span>|<span data-ttu-id="4cba8-147">有効な文字</span><span class="sxs-lookup"><span data-stu-id="4cba8-147">Valid digit values</span></span>|<span data-ttu-id="4cba8-148">例</span><span class="sxs-lookup"><span data-stu-id="4cba8-148">Example</span></span>|  
|-----------------|------------|------------------------|-------------|  
|<span data-ttu-id="4cba8-149">16 進数 (基数 16)。</span><span class="sxs-lookup"><span data-stu-id="4cba8-149">Hexadecimal (base 16)</span></span>|`&H`|<span data-ttu-id="4cba8-150">0-9、A ~ F</span><span class="sxs-lookup"><span data-stu-id="4cba8-150">0-9 and A-F</span></span>|`&HFFFF`|  
|<span data-ttu-id="4cba8-151">8 進数 (基数 8)。</span><span class="sxs-lookup"><span data-stu-id="4cba8-151">Octal (base 8)</span></span>|`&O`|<span data-ttu-id="4cba8-152">0-7</span><span class="sxs-lookup"><span data-stu-id="4cba8-152">0-7</span></span>|`&O77`|  
  
 <span data-ttu-id="4cba8-153">リテラルの型文字とプレフィックスの付いたリテラルを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="4cba8-153">You can follow a prefixed literal with a literal type character.</span></span> <span data-ttu-id="4cba8-154">次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="4cba8-154">The following example shows this.</span></span>  
  
```  
Dim counter As Short = &H8000S  
Dim flags As UShort = &H8000US  
```  
  
 <span data-ttu-id="4cba8-155">前の例で`counter`-32768 の&10; 進数の値を持つと`flags`+32768 の&10; 進数の値を持つファイル。</span><span class="sxs-lookup"><span data-stu-id="4cba8-155">In the previous example, `counter` has the decimal value of -32768, and `flags` has the decimal value of +32768.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cba8-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="4cba8-156">See Also</span></span>  
 <span data-ttu-id="4cba8-157">[データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="4cba8-157">[Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="4cba8-158"> [基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="4cba8-158"> [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span></span>  
<span data-ttu-id="4cba8-159"> [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="4cba8-159"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
<span data-ttu-id="4cba8-160"> [Visual Basic における型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="4cba8-160"> [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="4cba8-161"> [データ型のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="4cba8-161"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="4cba8-162"> [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="4cba8-162"> [Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span></span>  
<span data-ttu-id="4cba8-163"> [データの種類](../../../../visual-basic/language-reference/data-types/data-type-summary.md)</span><span class="sxs-lookup"><span data-stu-id="4cba8-163"> [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)</span></span>
