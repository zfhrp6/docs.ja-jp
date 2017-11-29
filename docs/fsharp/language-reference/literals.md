---
title: "リテラル (F#)"
description: "F# のプログラミング言語でリテラルの型について説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4b1d6e9d-f933-4cd4-966d-d643152c27e4
ms.openlocfilehash: 6bb1f233b6846e226c4e73aee00b8cf77735fe2d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="literals"></a><span data-ttu-id="79fee-104">リテラル</span><span class="sxs-lookup"><span data-stu-id="79fee-104">Literals</span></span>

> [!NOTE]
<span data-ttu-id="79fee-105">この記事の API の参照リンクを移動して msdn (現在のところ)。</span><span class="sxs-lookup"><span data-stu-id="79fee-105">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="79fee-106">このトピックでは、F# でリテラルの型を指定する方法を示す表を示します。</span><span class="sxs-lookup"><span data-stu-id="79fee-106">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="79fee-107">リテラル型</span><span class="sxs-lookup"><span data-stu-id="79fee-107">Literal Types</span></span>
<span data-ttu-id="79fee-108">F# のリテラル型を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="79fee-108">The following table shows the literal types in F#.</span></span> <span data-ttu-id="79fee-109">16 進表記で桁を表す文字は、大文字と小文字を区別しません。型を識別する文字は、大文字と小文字を区別します。</span><span class="sxs-lookup"><span data-stu-id="79fee-109">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="79fee-110">型</span><span class="sxs-lookup"><span data-stu-id="79fee-110">Type</span></span>|<span data-ttu-id="79fee-111">説明</span><span class="sxs-lookup"><span data-stu-id="79fee-111">Description</span></span>|<span data-ttu-id="79fee-112">サフィックスまたはプリフィックス</span><span class="sxs-lookup"><span data-stu-id="79fee-112">Suffix or prefix</span></span>|<span data-ttu-id="79fee-113">例</span><span class="sxs-lookup"><span data-stu-id="79fee-113">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="79fee-114">sbyte</span><span class="sxs-lookup"><span data-stu-id="79fee-114">sbyte</span></span>|<span data-ttu-id="79fee-115">符号付き 8 ビット整数</span><span class="sxs-lookup"><span data-stu-id="79fee-115">signed 8-bit integer</span></span>|<span data-ttu-id="79fee-116">Y</span><span class="sxs-lookup"><span data-stu-id="79fee-116">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="79fee-117">byte</span><span class="sxs-lookup"><span data-stu-id="79fee-117">byte</span></span>|<span data-ttu-id="79fee-118">符号なし 8 ビット自然数</span><span class="sxs-lookup"><span data-stu-id="79fee-118">unsigned 8-bit natural number</span></span>|<span data-ttu-id="79fee-119">uy</span><span class="sxs-lookup"><span data-stu-id="79fee-119">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="79fee-120">int16</span><span class="sxs-lookup"><span data-stu-id="79fee-120">int16</span></span>|<span data-ttu-id="79fee-121">16 ビット符号付き整数</span><span class="sxs-lookup"><span data-stu-id="79fee-121">signed 16-bit integer</span></span>|<span data-ttu-id="79fee-122">s</span><span class="sxs-lookup"><span data-stu-id="79fee-122">s</span></span>|`86s`|
|<span data-ttu-id="79fee-123">uint16</span><span class="sxs-lookup"><span data-stu-id="79fee-123">uint16</span></span>|<span data-ttu-id="79fee-124">符号なし 16 ビット自然数</span><span class="sxs-lookup"><span data-stu-id="79fee-124">unsigned 16-bit natural number</span></span>|<span data-ttu-id="79fee-125">us</span><span class="sxs-lookup"><span data-stu-id="79fee-125">us</span></span>|`86us`|
|<span data-ttu-id="79fee-126">int</span><span class="sxs-lookup"><span data-stu-id="79fee-126">int</span></span><br /><br /><span data-ttu-id="79fee-127">int32</span><span class="sxs-lookup"><span data-stu-id="79fee-127">int32</span></span>|<span data-ttu-id="79fee-128">32 ビット符号付き整数</span><span class="sxs-lookup"><span data-stu-id="79fee-128">signed 32-bit integer</span></span>|<span data-ttu-id="79fee-129">l または none</span><span class="sxs-lookup"><span data-stu-id="79fee-129">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="79fee-130">uint</span><span class="sxs-lookup"><span data-stu-id="79fee-130">uint</span></span><br /><br /><span data-ttu-id="79fee-131">uint32</span><span class="sxs-lookup"><span data-stu-id="79fee-131">uint32</span></span>|<span data-ttu-id="79fee-132">符号なし 32 ビット自然数</span><span class="sxs-lookup"><span data-stu-id="79fee-132">unsigned 32-bit natural number</span></span>|<span data-ttu-id="79fee-133">u または ul</span><span class="sxs-lookup"><span data-stu-id="79fee-133">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="79fee-134">unativeint</span><span class="sxs-lookup"><span data-stu-id="79fee-134">unativeint</span></span>|<span data-ttu-id="79fee-135">符号なし自然数としてのネイティブ ポインター</span><span class="sxs-lookup"><span data-stu-id="79fee-135">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="79fee-136">un</span><span class="sxs-lookup"><span data-stu-id="79fee-136">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="79fee-137">int64</span><span class="sxs-lookup"><span data-stu-id="79fee-137">int64</span></span>|<span data-ttu-id="79fee-138">64 ビット符号付き整数</span><span class="sxs-lookup"><span data-stu-id="79fee-138">signed 64-bit integer</span></span>|<span data-ttu-id="79fee-139">L</span><span class="sxs-lookup"><span data-stu-id="79fee-139">L</span></span>|`86L`|
|<span data-ttu-id="79fee-140">uint64</span><span class="sxs-lookup"><span data-stu-id="79fee-140">uint64</span></span>|<span data-ttu-id="79fee-141">符号なし 64 ビット自然数</span><span class="sxs-lookup"><span data-stu-id="79fee-141">unsigned 64-bit natural number</span></span>|<span data-ttu-id="79fee-142">UL</span><span class="sxs-lookup"><span data-stu-id="79fee-142">UL</span></span>|`86UL`|
|<span data-ttu-id="79fee-143">single、float32</span><span class="sxs-lookup"><span data-stu-id="79fee-143">single, float32</span></span>|<span data-ttu-id="79fee-144">32 ビット浮動小数点数</span><span class="sxs-lookup"><span data-stu-id="79fee-144">32-bit floating point number</span></span>|<span data-ttu-id="79fee-145">F または f</span><span class="sxs-lookup"><span data-stu-id="79fee-145">F or f</span></span>|<span data-ttu-id="79fee-146">`4.14F` または `4.14f`</span><span class="sxs-lookup"><span data-stu-id="79fee-146">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="79fee-147">lf</span><span class="sxs-lookup"><span data-stu-id="79fee-147">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="79fee-148">float、double</span><span class="sxs-lookup"><span data-stu-id="79fee-148">float; double</span></span>|<span data-ttu-id="79fee-149">64 ビット浮動小数点数</span><span class="sxs-lookup"><span data-stu-id="79fee-149">64-bit floating point number</span></span>|<span data-ttu-id="79fee-150">none</span><span class="sxs-lookup"><span data-stu-id="79fee-150">none</span></span>|<span data-ttu-id="79fee-151">`4.14` または `2.3E+32` または `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="79fee-151">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="79fee-152">LF</span><span class="sxs-lookup"><span data-stu-id="79fee-152">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="79fee-153">bigint</span><span class="sxs-lookup"><span data-stu-id="79fee-153">bigint</span></span>|<span data-ttu-id="79fee-154">64 ビット表現に制限されない整数</span><span class="sxs-lookup"><span data-stu-id="79fee-154">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="79fee-155">I</span><span class="sxs-lookup"><span data-stu-id="79fee-155">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="79fee-156">decimal</span><span class="sxs-lookup"><span data-stu-id="79fee-156">decimal</span></span>|<span data-ttu-id="79fee-157">固定小数点数または有理数として表現される小数</span><span class="sxs-lookup"><span data-stu-id="79fee-157">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="79fee-158">M または m</span><span class="sxs-lookup"><span data-stu-id="79fee-158">M or m</span></span>|<span data-ttu-id="79fee-159">`0.7833M` または `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="79fee-159">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="79fee-160">Char</span><span class="sxs-lookup"><span data-stu-id="79fee-160">Char</span></span>|<span data-ttu-id="79fee-161">Unicode 文字</span><span class="sxs-lookup"><span data-stu-id="79fee-161">Unicode character</span></span>|<span data-ttu-id="79fee-162">none</span><span class="sxs-lookup"><span data-stu-id="79fee-162">none</span></span>|`'a'`|
|<span data-ttu-id="79fee-163">文字列型</span><span class="sxs-lookup"><span data-stu-id="79fee-163">String</span></span>|<span data-ttu-id="79fee-164">Unicode 文字列</span><span class="sxs-lookup"><span data-stu-id="79fee-164">Unicode string</span></span>|<span data-ttu-id="79fee-165">none</span><span class="sxs-lookup"><span data-stu-id="79fee-165">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="79fee-166">または</span><span class="sxs-lookup"><span data-stu-id="79fee-166">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="79fee-167">または</span><span class="sxs-lookup"><span data-stu-id="79fee-167">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="79fee-168">または</span><span class="sxs-lookup"><span data-stu-id="79fee-168">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="79fee-169">関連項目[文字列](Strings.md)です。</span><span class="sxs-lookup"><span data-stu-id="79fee-169">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="79fee-170">byte</span><span class="sxs-lookup"><span data-stu-id="79fee-170">byte</span></span>|<span data-ttu-id="79fee-171">ASCII 文字</span><span class="sxs-lookup"><span data-stu-id="79fee-171">ASCII character</span></span>|<span data-ttu-id="79fee-172">B</span><span class="sxs-lookup"><span data-stu-id="79fee-172">B</span></span>|`'a'B`|
|<span data-ttu-id="79fee-173">byte[]</span><span class="sxs-lookup"><span data-stu-id="79fee-173">byte[]</span></span>|<span data-ttu-id="79fee-174">ASCII 文字列</span><span class="sxs-lookup"><span data-stu-id="79fee-174">ASCII string</span></span>|<span data-ttu-id="79fee-175">B</span><span class="sxs-lookup"><span data-stu-id="79fee-175">B</span></span>|`"text"B`|
|<span data-ttu-id="79fee-176">String または byte[]</span><span class="sxs-lookup"><span data-stu-id="79fee-176">String or byte[]</span></span>|<span data-ttu-id="79fee-177">逐語的文字列</span><span class="sxs-lookup"><span data-stu-id="79fee-177">verbatim string</span></span>|<span data-ttu-id="79fee-178">@ プリフィックス</span><span class="sxs-lookup"><span data-stu-id="79fee-178">@ prefix</span></span>|<span data-ttu-id="79fee-179">`@"\\server\share"`(Unicode)</span><span class="sxs-lookup"><span data-stu-id="79fee-179">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="79fee-180">`@"\\server\share"B`(ASCII)</span><span class="sxs-lookup"><span data-stu-id="79fee-180">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="remarks"></a><span data-ttu-id="79fee-181">コメント</span><span class="sxs-lookup"><span data-stu-id="79fee-181">Remarks</span></span>
<span data-ttu-id="79fee-182">Unicode 文字列を使用して指定できる明示的なエンコーディングを含めることができる`\u`後に 16 ビットの 16 進数コードまたは utf-32 エンコーディングを使用して指定できる`\U`Unicode を表す 32 ビットの 16 進数コードを続けてサロゲート ペア。</span><span class="sxs-lookup"><span data-stu-id="79fee-182">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents a Unicode surrogate pair.</span></span>

<span data-ttu-id="79fee-183">F# 3.1 で使用することができます、`+`文字列リテラルを結合にサインインします。</span><span class="sxs-lookup"><span data-stu-id="79fee-183">As of F# 3.1, you can use the `+` sign to combine string literals.</span></span> <span data-ttu-id="79fee-184">使用することも、ビットごとまたは (`|||`) 列挙型フラグを結合する演算子です。</span><span class="sxs-lookup"><span data-stu-id="79fee-184">You can also use the bitwise or (`|||`) operator to combine enum flags.</span></span> <span data-ttu-id="79fee-185">たとえば、F# 3.1 では次のようなコードが有効です。</span><span class="sxs-lookup"><span data-stu-id="79fee-185">For example, the following code is legal in F# 3.1:</span></span>

```fsharp
[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

<span data-ttu-id="79fee-186">その他のビットごとの演算子は使用できません。</span><span class="sxs-lookup"><span data-stu-id="79fee-186">The use of other bitwise operators isn't allowed.</span></span>


## <a name="named-literals"></a><span data-ttu-id="79fee-187">名前付きリテラル</span><span class="sxs-lookup"><span data-stu-id="79fee-187">Named Literals</span></span>
<span data-ttu-id="79fee-188">マークできるの定数にするのには、値、[リテラル](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285)属性。</span><span class="sxs-lookup"><span data-stu-id="79fee-188">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="79fee-189">この属性には、値が定数としてコンパイルされる効果があります。</span><span class="sxs-lookup"><span data-stu-id="79fee-189">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="79fee-190">パターン マッチ式では、小文字で始まる識別子は、リテラルとしてではなく常にバインドされる変数として扱われます。そのため、一般的に、リテラルを定義する場合は先頭大文字を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="79fee-190">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="79fee-191">その他の基底の整数</span><span class="sxs-lookup"><span data-stu-id="79fee-191">Integers In Other Bases</span></span>

<span data-ttu-id="79fee-192">16 進数、8 進数、またはバイナリを使用して 32 ビット符号付き整数を指定することも、 `0x`、`0o`または`0b`それぞれプレフィックスします。</span><span class="sxs-lookup"><span data-stu-id="79fee-192">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let Numbers = (0x9F, 0o77, 0b1010)
// Result: Numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="79fee-193">数値リテラルにアンダー スコア</span><span class="sxs-lookup"><span data-stu-id="79fee-193">Underscores in Numeric Literals</span></span>

<span data-ttu-id="79fee-194">4.1 以降では F# を区切ることができます桁の数字、アンダー スコア文字 (`_`)。</span><span class="sxs-lookup"><span data-stu-id="79fee-194">Starting with F# 4.1, you can separate digits with the underscore character (`_`).</span></span>

```fsharp
let DeadBeef = 0xDEAD_BEEF

let DeadBeefAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let ExampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="79fee-195">関連項目</span><span class="sxs-lookup"><span data-stu-id="79fee-195">See Also</span></span>

[<span data-ttu-id="79fee-196">Core.LiteralAttribute クラス</span><span class="sxs-lookup"><span data-stu-id="79fee-196">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
