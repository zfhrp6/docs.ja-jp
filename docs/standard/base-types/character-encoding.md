---
title: ".NET での文字エンコード"
description: ".NET での文字エンコード"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: bce54e41-e9dc-493a-8988-1cbadc340fe8
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: a8f42fa6a37f8de6f13186ea2ac17b2b2ced1601
ms.contentlocale: ja-jp
ms.lasthandoff: 03/02/2017

---

# <a name="character-encoding-in-net"></a><span data-ttu-id="90cae-104">.NET での文字エンコード</span><span class="sxs-lookup"><span data-stu-id="90cae-104">Character encoding in .NET</span></span>

<span data-ttu-id="90cae-105">文字は、さまざまな方法で表現できる抽象エンティティです。</span><span class="sxs-lookup"><span data-stu-id="90cae-105">Characters are abstract entities that can be represented in many different ways.</span></span> <span data-ttu-id="90cae-106">文字エンコーディングとは、サポートされている文字セットの各文字を、その文字を表す値と組み合わせる体系です。</span><span class="sxs-lookup"><span data-stu-id="90cae-106">A character encoding is a system that pairs each character in a supported character set with some value that represents that character.</span></span> <span data-ttu-id="90cae-107">たとえばモールス符号は、ローマ字の各文字を、電信線での送信に適したドットとダッシュのパターンと組み合わせる文字エンコーディングです。</span><span class="sxs-lookup"><span data-stu-id="90cae-107">For example, Morse code is a character encoding that pairs each character in the Roman alphabet with a pattern of dots and dashes that are suitable for transmission over telegraph lines.</span></span> <span data-ttu-id="90cae-108">コンピューターの文字エンコーディングは、サポートされている文字セットの各文字を、その文字を表す数値と組み合わせます。</span><span class="sxs-lookup"><span data-stu-id="90cae-108">A character encoding for computers pairs each character in a supported character set with a numeric value that represents that character.</span></span> <span data-ttu-id="90cae-109">文字エンコーディングには、次の&2; つの異なるコンポーネントがあります。</span><span class="sxs-lookup"><span data-stu-id="90cae-109">A character encoding has two distinct components:</span></span>

* <span data-ttu-id="90cae-110">エンコーダー。文字シーケンスを数値 (バイト) シーケンスに変換します。</span><span class="sxs-lookup"><span data-stu-id="90cae-110">An encoder, which translates a sequence of characters into a sequence of numeric values (bytes).</span></span>

* <span data-ttu-id="90cae-111">デコーダー。バイト シーケンスを文字シーケンスに変換します。</span><span class="sxs-lookup"><span data-stu-id="90cae-111">A decoder, which translates a sequence of bytes into a sequence of characters.</span></span>

<span data-ttu-id="90cae-112">文字エンコーディングは、エンコーダーとデコーダーの動作を決める規則を表します。</span><span class="sxs-lookup"><span data-stu-id="90cae-112">Character encoding describes the rules by which an encoder and a decoder operate.</span></span> <span data-ttu-id="90cae-113">たとえば、[UTF8Encoding](xref:System.Text.UTF8Encoding) クラスは、1 ～ 4 バイトを使用して 1 つの Unicode 文字を表現する UTF-8 (8-bit Unicode Transformation Format) をエンコードおよびデコードするための規則を表します。</span><span class="sxs-lookup"><span data-stu-id="90cae-113">For example, the [UTF8Encoding](xref:System.Text.UTF8Encoding) class describes the rules for encoding to, and decoding from, 8-bit Unicode Transformation Format (UTF-8), which uses one to four bytes to represent a single Unicode character.</span></span> <span data-ttu-id="90cae-114">エンコードとデコードに検証を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="90cae-114">Encoding and decoding can also include validation.</span></span> <span data-ttu-id="90cae-115">たとえば、[UnicodeEncoding](xref:System.Text.UnicodeEncoding) クラスは、すべてのサロゲートを検証して、有効なサロゲート ペアが構成されていることを確認します </span><span class="sxs-lookup"><span data-stu-id="90cae-115">For example, the [UnicodeEncoding](xref:System.Text.UnicodeEncoding) class checks all surrogates to make sure they constitute valid surrogate pairs.</span></span> <span data-ttu-id="90cae-116">(サロゲート ペアは、U+D800 ～ U+DBFF の範囲のコード ポイントを持つ文字と、それに続く U+DC00 ～ U+DFFF の範囲のコード ポイントを持つ文字で構成されます)。エンコーダーが無効な文字を処理する方法や、デコーダーが無効なバイトを処理する方法は、フォールバック ストラテジによって決まります。</span><span class="sxs-lookup"><span data-stu-id="90cae-116">(A surrogate pair consists of a character with a code point that ranges from U+D800 to U+DBFF followed by a character with a code point that ranges from U+DC00 to U+DFFF.) A fallback strategy determines how an encoder handles invalid characters or how a decoder handles invalid bytes.</span></span> 

> [!WARNING]
> <span data-ttu-id="90cae-117">.NET のエンコーディング クラスは、文字データを格納および変換するためのものです。</span><span class="sxs-lookup"><span data-stu-id="90cae-117">The .NET encoding classes provide a way to store and convert character data.</span></span> <span data-ttu-id="90cae-118">バイナリ データを文字列形式で格納する目的では使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="90cae-118">They should not be used to store binary data in string form.</span></span> <span data-ttu-id="90cae-119">エンコーディング クラスを使用してバイナリ データを文字列形式に変換すると、使用されているエンコーディングによっては、予期しない動作が発生したり、不正確なデータや破損したデータが生成されたりする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="90cae-119">Depending on the encoding used, converting binary data to string format with the encoding classes can introduce unexpected behavior and produce inaccurate or corrupted data.</span></span> <span data-ttu-id="90cae-120">バイナリ データを文字列形式に変換するには、[Convert.ToBase64String](xref:System.Convert.ToBase64String(System.Byte[])) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="90cae-120">To convert binary data to a string form, use the [Convert.ToBase64String](xref:System.Convert.ToBase64String(System.Byte[])) method.</span></span> 
 
<span data-ttu-id="90cae-121">.NET では ([UnicodeEncoding](xref:System.Text.UnicodeEncoding) クラスによって表される) UTF-16 エンコーディングを使用して、文字と文字列を表します。</span><span class="sxs-lookup"><span data-stu-id="90cae-121">.NET uses the UTF-16 encoding (represented by the [UnicodeEncoding](xref:System.Text.UnicodeEncoding) class) to represent characters and strings.</span></span> <span data-ttu-id="90cae-122">共通言語ランタイムをターゲットとするアプリケーションは、エンコーダーを使用して、共通言語ランタイムによってサポートされている Unicode 文字表現を他のエンコーディング方式に変換し、</span><span class="sxs-lookup"><span data-stu-id="90cae-122">Applications that target the common language runtime use encoders to map Unicode character representations supported by the common language runtime to other encoding schemes.</span></span> <span data-ttu-id="90cae-123">デコーダーを使用して、Unicode 以外のエンコーディングの文字を Unicode に変換します。</span><span class="sxs-lookup"><span data-stu-id="90cae-123">They use decoders to map characters from non-Unicode encodings to Unicode.</span></span>

<span data-ttu-id="90cae-124">このトピックは、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="90cae-124">This topic consists of the following sections:</span></span>

* [<span data-ttu-id="90cae-125">.NET でのエンコード</span><span class="sxs-lookup"><span data-stu-id="90cae-125">Encodings in .NET</span></span>](#encodings-in-net)

* [<span data-ttu-id="90cae-126">エンコーディング クラスの選択</span><span class="sxs-lookup"><span data-stu-id="90cae-126">Selecting an encoding class</span></span>](#selecting-an-encoding-class)

* [<span data-ttu-id="90cae-127">エンコーディング オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="90cae-127">Using an encoding object</span></span>](#using-an-encoding-object)

* [<span data-ttu-id="90cae-128">フォールバック ストラテジの選択</span><span class="sxs-lookup"><span data-stu-id="90cae-128">Choosing a fallback strategy</span></span>](#choosing-a-fallback-strategy)

* [<span data-ttu-id="90cae-129">カスタム フォールバック ストラテジの実装</span><span class="sxs-lookup"><span data-stu-id="90cae-129">Implementing a custom fallback strategy</span></span>](#implementing-a-custom-fallback-strategy)

## <a name="encodings-in-net"></a><span data-ttu-id="90cae-130">.NET でのエンコード</span><span class="sxs-lookup"><span data-stu-id="90cae-130">Encodings in .NET</span></span>

<span data-ttu-id="90cae-131">.NET のすべての文字エンコーディング クラスは、すべての文字エンコーディングに共通の機能を定義する抽象クラスの [System.Text.Encoding](xref:System.Text.Encoding) クラスを継承します。</span><span class="sxs-lookup"><span data-stu-id="90cae-131">All character encoding classes in .NET inherit from the [System.Text.Encoding](xref:System.Text.Encoding) class, which is an abstract class that defines the functionality common to all character encodings.</span></span> <span data-ttu-id="90cae-132">.NET に実装されている個々のエンコーディング オブジェクトにアクセスするには次の方法があります。</span><span class="sxs-lookup"><span data-stu-id="90cae-132">To access the individual encoding objects implemented in .NET, do the following:</span></span>

* <span data-ttu-id="90cae-133">[Encoding](xref:System.Text.Encoding) クラスの静的プロパティを使用します。これらのプロパティは、.NET で使用できる標準の文字エンコーディング (ASCII、UTF-7、UTF-8、UTF-16、および UTF-32) を表すオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="90cae-133">Use the static properties of the [Encoding](xref:System.Text.Encoding) class, which return objects that represent the standard character encodings available in .NET (ASCII, UTF-7, UTF-8, UTF-16, and UTF-32).</span></span> <span data-ttu-id="90cae-134">たとえば、[Encoding.Unicode](xref:System.Text.Encoding.Unicode) プロパティは [UnicodeEncoding](xref:System.Text.UnicodeEncoding) オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="90cae-134">For example, the [Encoding.Unicode](xref:System.Text.Encoding.Unicode) property returns a [UnicodeEncoding](xref:System.Text.UnicodeEncoding) object.</span></span> <span data-ttu-id="90cae-135">各オブジェクトでは、エンコードできない文字列とデコードできないバイトを処理するために、置換フォールバックが使用されます </span><span class="sxs-lookup"><span data-stu-id="90cae-135">Each object uses replacement fallback to handle strings that it cannot encode and bytes that it cannot decode.</span></span> <span data-ttu-id="90cae-136">(詳細については、「[置換フォールバック](#replacement-fallback)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="90cae-136">(For more information, see the [Replacement fallback](#replacement-fallback) section.)</span></span>

* <span data-ttu-id="90cae-137">エンコーディングのクラス コンストラクターを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="90cae-137">Call the encoding's class constructor.</span></span> <span data-ttu-id="90cae-138">ASCII、UTF-7、UTF-8、UTF-16、および UTF-32 の各エンコーディングのオブジェクトは、この方法でインスタンス化できます。</span><span class="sxs-lookup"><span data-stu-id="90cae-138">Objects for the ASCII, UTF-7, UTF-8, UTF-16, and UTF-32 encodings can be instantiated in this way.</span></span> <span data-ttu-id="90cae-139">既定では、各オブジェクトはエンコードできない文字列とデコードできないバイトを処理するために置換フォールバックを使用します。ただし、代わりに例外がスローされるように指定することもできます </span><span class="sxs-lookup"><span data-stu-id="90cae-139">By default, each object uses replacement fallback to handle strings that it cannot encode and bytes that it cannot decode, but you can specify that an exception should be thrown instead.</span></span> <span data-ttu-id="90cae-140">(詳細については、「[置換フォールバック](#replacement-fallback)」と「[例外フォールバック](#exception-fallback)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="90cae-140">(For more information, see the [Replacement fallback](#replacement-fallback) and [Exception fallback](#exception-fallback) sections.)</span></span>

* <span data-ttu-id="90cae-141">[Encoding.Encoding(Int32)](xref:System.Text.Encoding.GetEncoding(System.Int32)) コンストラクターを呼び出して、エンコーディングを表す整数を渡します。</span><span class="sxs-lookup"><span data-stu-id="90cae-141">Call the [Encoding.Encoding(Int32)](xref:System.Text.Encoding.GetEncoding(System.Int32)) constructor and pass it an integer that represents the encoding.</span></span> <span data-ttu-id="90cae-142">エンコードできない文字列とデコードできないバイトの処理には、標準エンコーディングのエンコーディング オブジェクトでは置換フォールバックが、コード ページ エンコーディングと&2; バイト文字セット (DBCS) エンコーディングのエンコーディング オブジェクトでは最適フォールバックが使用されます </span><span class="sxs-lookup"><span data-stu-id="90cae-142">Standard encoding objects use replacement fallback, and code page and double-byte character set (DBCS) encoding objects use best-fit fallback to handle strings that they cannot encode and bytes that they cannot decode.</span></span> <span data-ttu-id="90cae-143">(詳細については、「[最適フォールバック](#best-fit-fallback)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="90cae-143">(For more information, see the [Best-Fit fallback](#best-fit-fallback) section.)</span></span>

* <span data-ttu-id="90cae-144">[Encoding.GetEncoding](xref:System.Text.Encoding.GetEncoding(System.Int32)) メソッドを呼び出します。このメソッドは、.NET で使用できる任意のエンコーディング (標準、コード ページ、または DBCS) を返します。</span><span class="sxs-lookup"><span data-stu-id="90cae-144">Call the [Encoding.GetEncoding](xref:System.Text.Encoding.GetEncoding(System.Int32)) method, which returns any standard, code page, or DBCS encoding available in .NET.</span></span> <span data-ttu-id="90cae-145">オーバーロードを使用すると、エンコーダーおよびデコーダーの両方のフォールバック オブジェクトを指定できます。</span><span class="sxs-lookup"><span data-stu-id="90cae-145">Overloads let you specify a fallback object for both the encoder and the decoder.</span></span>

> [!NOTE]
> <span data-ttu-id="90cae-146">Unicode 規格では、サポートされるすべてのスクリプトについて、各文字にコード ポイント (数値) と名前を割り当てています。</span><span class="sxs-lookup"><span data-stu-id="90cae-146">The Unicode Standard assigns a code point (a number) and a name to each character in every supported script.</span></span> <span data-ttu-id="90cae-147">たとえば、文字 "A" は U+0041 というコード ポイントと、"LATIN CAPITAL LETTER A" という名前で表されます。</span><span class="sxs-lookup"><span data-stu-id="90cae-147">For example, the character "A" is represented by the code point U+0041 and the name "LATIN CAPITAL LETTER A".</span></span> <span data-ttu-id="90cae-148">UTF (Unicode Transformation Format) エンコーディングは、そのコード ポイントを&1; つ以上のバイトのシーケンスにエンコードする方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="90cae-148">The Unicode Transformation Format (UTF) encodings define ways to encode that code point into a sequence of one or more bytes.</span></span> <span data-ttu-id="90cae-149">Unicode エンコーディング方式を使用すると、任意の文字セットの文字を&1; つのエンコーディング方式で表現できるため、国際対応アプリケーションの開発が簡素化されます。</span><span class="sxs-lookup"><span data-stu-id="90cae-149">A Unicode encoding scheme simplifies world-ready application development because it allows characters from any character set to be represented in a single encoding.</span></span> <span data-ttu-id="90cae-150">これにより、アプリケーション開発者が、特定の言語または書記体系の文字を表すために使用されるエンコーディング方式を追跡する必要はなくなります。また、データを破損することなく、各国のシステム間でデータを共有できます。</span><span class="sxs-lookup"><span data-stu-id="90cae-150">Application developers no longer have to keep track of the encoding scheme that was used to produce characters for a specific language or writing system, and data can be shared among systems internationally without being corrupted.</span></span>
>
>  <span data-ttu-id="90cae-151">.NET では、Unicode 規格によって定義されている UTF-8、UTF-16、および UTF-32 の&3; つのエンコーディングをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="90cae-151">.NET supports three encodings defined by the Unicode standard: UTF-8, UTF-16, and UTF-32.</span></span> <span data-ttu-id="90cae-152">詳細については、[Unicode](http://www.unicode.org/) ホーム ページの Unicode 標準を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90cae-152">For more information, see The Unicode Standard at the [Unicode](http://www.unicode.org/) home page.</span></span>
 
<span data-ttu-id="90cae-153">.NET でサポートされている文字エンコーディング システムを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="90cae-153">.NET supports the character encoding systems listed in the following table.</span></span>

<span data-ttu-id="90cae-154">エンコード</span><span class="sxs-lookup"><span data-stu-id="90cae-154">Encoding</span></span> | <span data-ttu-id="90cae-155">クラス</span><span class="sxs-lookup"><span data-stu-id="90cae-155">Class</span></span> | <span data-ttu-id="90cae-156">説明</span><span class="sxs-lookup"><span data-stu-id="90cae-156">Description</span></span> | <span data-ttu-id="90cae-157">長所/短所</span><span class="sxs-lookup"><span data-stu-id="90cae-157">Advantages/disadvantages</span></span>
-------- | ----- | ----------- | ------------------------ 
<span data-ttu-id="90cae-158">ASCII</span><span class="sxs-lookup"><span data-stu-id="90cae-158">ASCII</span></span> | [<span data-ttu-id="90cae-159">ASCIIEncoding</span><span class="sxs-lookup"><span data-stu-id="90cae-159">ASCIIEncoding</span></span>](xref:System.Text.ASCIIEncoding) | <span data-ttu-id="90cae-160">バイトの下位&7; ビットを使用して、限られた範囲の文字をエンコードします。</span><span class="sxs-lookup"><span data-stu-id="90cae-160">Encodes a limited range of characters by using the lower seven bits of a byte.</span></span> | <span data-ttu-id="90cae-161">ASCII エンコーディングでは、U+0000 から U+007F までの文字値しかサポートされていないため、ほとんどの場合、国際対応アプリケーションでは ASCII エンコーディングの使用は不適切です。</span><span class="sxs-lookup"><span data-stu-id="90cae-161">Because this encoding only supports character values from U+0000 through U+007F, in most cases it is inadequate for internationalized applications.</span></span>
<span data-ttu-id="90cae-162">UTF-7</span><span class="sxs-lookup"><span data-stu-id="90cae-162">UTF-7</span></span> | [<span data-ttu-id="90cae-163">UTF7Encoding</span><span class="sxs-lookup"><span data-stu-id="90cae-163">UTF7Encoding</span></span>](xref:System.Text.UTF7Encoding) | <span data-ttu-id="90cae-164">文字を 7 ビット ASCII 文字のシーケンスとして表します。</span><span class="sxs-lookup"><span data-stu-id="90cae-164">Represents characters as sequences of 7-bit ASCII characters.</span></span> <span data-ttu-id="90cae-165">ASCII 以外の Unicode 文字は、ASCII 文字のエスケープ シーケンスによって表します。</span><span class="sxs-lookup"><span data-stu-id="90cae-165">Non-ASCII Unicode characters are represented by an escape sequence of ASCII characters.</span></span> | <span data-ttu-id="90cae-166">UTF-7 は、電子メールやニュースグループなどのプロトコルをサポートします。</span><span class="sxs-lookup"><span data-stu-id="90cae-166">UTF-7 supports protocols such as e-mail and newsgroup protocols.</span></span> <span data-ttu-id="90cae-167">ただし、UTF-7 は特に安全でも堅牢でもありません。</span><span class="sxs-lookup"><span data-stu-id="90cae-167">However, UTF-7 is not particularly secure or robust.</span></span> <span data-ttu-id="90cae-168">場合によっては、1 ビットの変更により、UTF-7 文字列全体の解釈が完全に変わる場合があります。</span><span class="sxs-lookup"><span data-stu-id="90cae-168">In some cases, changing one bit can radically alter the interpretation of an entire UTF-7 string.</span></span> <span data-ttu-id="90cae-169">他の場合には、異なる UTF-7 文字列がエンコードによって同じテキストになる可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="90cae-169">In other cases, different UTF-7 strings can encode the same text.</span></span> <span data-ttu-id="90cae-170">ASCII 以外の文字を含むシーケンスの場合、UTF-7 は UTF-8 よりも多くの空間を必要とし、エンコードとデコードに時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="90cae-170">For sequences that include non-ASCII characters, UTF-7 requires more space than UTF-8, and encoding/decoding is slower.</span></span> <span data-ttu-id="90cae-171">したがって、可能であれば、UTF-7 ではなく UTF-8 を使用してください。</span><span class="sxs-lookup"><span data-stu-id="90cae-171">Consequently, you should use UTF-8 instead of UTF-7 if possible.</span></span>
<span data-ttu-id="90cae-172">UTF-8</span><span class="sxs-lookup"><span data-stu-id="90cae-172">UTF-8</span></span> | [<span data-ttu-id="90cae-173">UTF8Encoding</span><span class="sxs-lookup"><span data-stu-id="90cae-173">UTF8Encoding</span></span>](xref:System.Text.UTF8Encoding) | <span data-ttu-id="90cae-174">各 Unicode コード ポイントが、1 バイトから&4; バイトのシーケンスとして表現されます。</span><span class="sxs-lookup"><span data-stu-id="90cae-174">Represents each Unicode code point as a sequence of one to four bytes.</span></span> | <span data-ttu-id="90cae-175">UTF-8 では、8 ビット データ サイズがサポートされており、既存の多くのオペレーティング システムに対応できます。</span><span class="sxs-lookup"><span data-stu-id="90cae-175">UTF-8 supports 8-bit data sizes and works well with many existing operating systems.</span></span> <span data-ttu-id="90cae-176">ASCII 範囲の文字については、UTF-8 は ASCII エンコーディングと一致し、より広範な文字を提供します。</span><span class="sxs-lookup"><span data-stu-id="90cae-176">For the ASCII range of characters, UTF-8 is identical to ASCII encoding and allows a broader set of characters.</span></span> <span data-ttu-id="90cae-177">ただし、CJK (中国語、日本語、韓国語) スクリプトでは、UTF-8 の各文字に&3; バイトが必要となることがあり、データ サイズが UTF-16 より大きくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="90cae-177">However, for Chinese-Japanese-Korean (CJK) scripts, UTF-8 can require three bytes for each character, and can potentially cause larger data sizes than UTF-16.</span></span> <span data-ttu-id="90cae-178">ただし、CJK 範囲によるサイズの増加が HTML タグなどの ASCII データのサイズによって相殺されることもあります。</span><span class="sxs-lookup"><span data-stu-id="90cae-178">Note that sometimes the amount of ASCII data, such as HTML tags, justifies the increased size for the CJK range.</span></span>
<span data-ttu-id="90cae-179">UTF-16</span><span class="sxs-lookup"><span data-stu-id="90cae-179">UTF-16</span></span> | [<span data-ttu-id="90cae-180">UnicodeEncoding</span><span class="sxs-lookup"><span data-stu-id="90cae-180">UnicodeEncoding</span></span>](xref:System.Text.UnicodeEncoding) | <span data-ttu-id="90cae-181">各 Unicode コード ポイントが、1 つまたは 2 つの 16 ビット整数のシーケンスとして表現されます。</span><span class="sxs-lookup"><span data-stu-id="90cae-181">Represents each Unicode code point as a sequence of one or two 16-bit integers.</span></span> <span data-ttu-id="90cae-182">ほとんどの一般的な Unicode 文字で必要とされる UTF-16 コード ポイントは&1; つだけです。ただし、Unicode の補助文字 (U+10000 以上) には&2; つの UTF-16 サロゲート コード ポイントが必要です。</span><span class="sxs-lookup"><span data-stu-id="90cae-182">Most common Unicode characters require only one UTF-16 code point, although Unicode supplementary characters (U+10000 and greater) require two UTF-16 surrogate code points.</span></span> <span data-ttu-id="90cae-183">リトル エンディアンとビッグ エンディアンの両方のバイト順をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="90cae-183">Both little-endian and big-endian byte orders are supported.</span></span> | <span data-ttu-id="90cae-184">UTF-16 エンコーディングは、共通言語ランタイムでは Char および String の値を表現するために、Windows オペレーティング システムでは WCHAR の値を表現するために使用されています。</span><span class="sxs-lookup"><span data-stu-id="90cae-184">UTF-16 encoding is used by the common language runtime to represent Char and String values, and it is used by the Windows operating system to represent WCHAR values.</span></span>
<span data-ttu-id="90cae-185">UTF-32</span><span class="sxs-lookup"><span data-stu-id="90cae-185">UTF-32</span></span> | [<span data-ttu-id="90cae-186">UTF32Encoding</span><span class="sxs-lookup"><span data-stu-id="90cae-186">UTF32Encoding</span></span>](xref:System.Text.UTF32Encoding) | <span data-ttu-id="90cae-187">各 Unicode コード ポイントが 32 ビット整数として表現されます。</span><span class="sxs-lookup"><span data-stu-id="90cae-187">Represents each Unicode code point as a 32-bit integer.</span></span> <span data-ttu-id="90cae-188">リトル エンディアンとビッグ エンディアンの両方のバイト順をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="90cae-188">Both little-endian and big-endian byte orders are supported.</span></span> | <span data-ttu-id="90cae-189">UTF-32 エンコーディングは、エンコードされた空白がきわめて重要な意味を持つオペレーティング システムで、アプリケーションが UTF-16 エンコーディングのサロゲート コード ポイント動作を回避する必要がある場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="90cae-189">UTF-32 encoding is used when applications want to avoid the surrogate code point behavior of UTF-16 encoding on operating systems for which encoded space is too important.</span></span> <span data-ttu-id="90cae-190">ディスプレイ上でレンダリングされる&1; つのグリフも複数の UTF-32 文字でエンコードされることがあります。</span><span class="sxs-lookup"><span data-stu-id="90cae-190">Single glyphs rendered on a display can still be encoded with more than one UTF-32 character.</span></span>

<span data-ttu-id="90cae-191">これらのエンコーディングを使用することにより、Unicode 文字だけでなく、レガシ アプリケーションで最もよく使用されているエンコーディングにも対応できます。</span><span class="sxs-lookup"><span data-stu-id="90cae-191">These encodings enable you to work with Unicode characters as well as with encodings that are most commonly used in legacy applications.</span></span> <span data-ttu-id="90cae-192">また、[Encoding](xref:System.Text.Encoding) から派生するクラスを定義し、そのメンバーをオーバーライドして、カスタム エンコーディングを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="90cae-192">In addition, you can create a custom encoding by defining a class that derives from [Encoding](xref:System.Text.Encoding) and overriding its members.</span></span>

> [!NOTE]
> <span data-ttu-id="90cae-193">既定で、.NET Core では、コード ページ 28591 以外のコード ページ エンコーディングや Unicode エンコーディング (UTF-8 や UTF-16 など) を使用できません。</span><span class="sxs-lookup"><span data-stu-id="90cae-193">By default, .NET Core does not make available any code page encodings other than code page 28591 and the Unicode encodings, such as UTF-8 and UTF-16.</span></span> <span data-ttu-id="90cae-194">ただし、使用するアプリに、.NET Framework を対象とする標準の Windows アプリに含まれているコード ページ エンコーディングを追加できます。</span><span class="sxs-lookup"><span data-stu-id="90cae-194">However, you can add the code page encodings found in standard Windows apps that target the .NET Framework to your app.</span></span> <span data-ttu-id="90cae-195">詳細については、「[EncodingProvider](xref:System.Text.EncodingProvider)」のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="90cae-195">For complete information, see the [EncodingProvider](xref:System.Text.EncodingProvider) topic.</span></span> 

## <a name="selecting-an-encoding-class"></a><span data-ttu-id="90cae-196">エンコーディング クラスの選択</span><span class="sxs-lookup"><span data-stu-id="90cae-196">Selecting an Encoding class</span></span>

<span data-ttu-id="90cae-197">アプリケーションで使用するエンコーディングを選択できる場合は、Unicode エンコーディング (できれば [UTF8Encoding](xref:System.Text.UTF8Encoding) または [UnicodeEncoding](xref:System.Text.UnicodeEncoding)) を使用するようにしてください </span><span class="sxs-lookup"><span data-stu-id="90cae-197">If you have the opportunity to choose the encoding to be used by your application, you should use a Unicode encoding, preferably either [UTF8Encoding](xref:System.Text.UTF8Encoding) or [UnicodeEncoding](xref:System.Text.UnicodeEncoding).</span></span> <span data-ttu-id="90cae-198">(.NET でサポートされている Unicode エンコーディングには、そのほかに [UTF32Encoding](xref:System.Text.UTF32Encoding) もあります)。</span><span class="sxs-lookup"><span data-stu-id="90cae-198">(.NET also supports a third Unicode encoding, [UTF32Encoding](xref:System.Text.UTF32Encoding).)</span></span> 

<span data-ttu-id="90cae-199">ASCII エンコーディング ([ASCIIEncoding](xref:System.Text.ASCIIEncoding)) を使用しようとしている場合は、代わりに [UTF8Encoding](xref:System.Text.UTF8Encoding) を選択してください。</span><span class="sxs-lookup"><span data-stu-id="90cae-199">If you are planning to use an ASCII encoding ([ASCIIEncoding](xref:System.Text.ASCIIEncoding)), choose [UTF8Encoding](xref:System.Text.UTF8Encoding) instead.</span></span> <span data-ttu-id="90cae-200">この&2; つのエンコーディングは、ASCII 文字セットに対する動作は変わりませんが、[UTF8Encoding](xref:System.Text.UTF8Encoding) には次のような利点があります。</span><span class="sxs-lookup"><span data-stu-id="90cae-200">The two encodings are identical for the ASCII character set, but [UTF8Encoding](xref:System.Text.UTF8Encoding) has the following advantages:</span></span> 

* <span data-ttu-id="90cae-201">すべての Unicode 文字を表現できます ([ASCIIEncoding](xref:System.Text.ASCIIEncoding) でサポートされているのは U+0000 ～ U+007F の Unicode 文字値だけです)。</span><span class="sxs-lookup"><span data-stu-id="90cae-201">It can represent every Unicode character, whereas [ASCIIEncoding](xref:System.Text.ASCIIEncoding) supports only the Unicode character values between U+0000 and U+007F.</span></span>

* <span data-ttu-id="90cae-202">エラー検出に対応しており、セキュリティも強化されます。</span><span class="sxs-lookup"><span data-stu-id="90cae-202">It provides error detection and better security.</span></span>

* <span data-ttu-id="90cae-203">できるだけ高速になるように調整されているため、他のエンコーディングよりも高速です。</span><span class="sxs-lookup"><span data-stu-id="90cae-203">It has been tuned to be as fast as possible and should be faster than any other encoding.</span></span> <span data-ttu-id="90cae-204">全体が ASCII のコンテンツの場合でも、[UTF8Encoding](xref:System.Text.UTF8Encoding) で実行される演算は、[ASCIIEncoding](xref:System.Text.ASCIIEncoding) で実行される演算よりも高速になります。</span><span class="sxs-lookup"><span data-stu-id="90cae-204">Even for content that is entirely ASCII, operations performed with [UTF8Encoding](xref:System.Text.UTF8Encoding) are faster than operations performed with [ASCIIEncoding](xref:System.Text.ASCIIEncoding).</span></span>

<span data-ttu-id="90cae-205">[ASCIIEncoding](xref:System.Text.ASCIIEncoding) は、レガシ アプリケーションの場合にのみ使用を検討するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="90cae-205">You should consider using [ASCIIEncoding](xref:System.Text.ASCIIEncoding) only for legacy applications.</span></span> <span data-ttu-id="90cae-206">ただし、レガシ アプリケーションでも、次のような理由で [UTF8Encoding](xref:System.Text.UTF8Encoding) の方が適していることもあります (既定の設定の場合)。</span><span class="sxs-lookup"><span data-stu-id="90cae-206">However, even for legacy applications, [UTF8Encoding](xref:System.Text.UTF8Encoding) might be a better choice for the following reasons (assuming default settings):</span></span>

* <span data-ttu-id="90cae-207">厳密には ASCII でないコンテンツがアプリケーションに含まれている場合、それを [ASCIIEncoding](xref:System.Text.ASCIIEncoding) でエンコードすると、ASCII 以外の各文字は疑問符 (?) としてエンコードされます。</span><span class="sxs-lookup"><span data-stu-id="90cae-207">If your application has content that is not strictly ASCII and encodes it with [ASCIIEncoding](xref:System.Text.ASCIIEncoding), each non-ASCII character encodes as a question mark (?).</span></span> <span data-ttu-id="90cae-208">アプリケーションがこのデータをデコードすると、情報は失われます。</span><span class="sxs-lookup"><span data-stu-id="90cae-208">If the application then decodes this data, the information is lost.</span></span>


* <span data-ttu-id="90cae-209">厳密には ASCII でないコンテンツがアプリケーションに含まれている場合、それを [UTF8Encoding](xref:System.Text.UTF8Encoding) でエンコードすると、結果を ASCII として解釈しようとしても一見理解不能になります。</span><span class="sxs-lookup"><span data-stu-id="90cae-209">If your application has content that is not strictly ASCII and encodes it with [UTF8Encoding](xref:System.Text.UTF8Encoding), the result seems unintelligible if interpreted as ASCII.</span></span> <span data-ttu-id="90cae-210">ただし、アプリケーションがこのデータを UTF-8 デコーダーを使用してデコードすると、データのラウンド トリップが正常に行われます。</span><span class="sxs-lookup"><span data-stu-id="90cae-210">However, if the application then uses a UTF-8 decoder to decode this data, the data performs a round trip successfully.</span></span>

<span data-ttu-id="90cae-211">Web アプリケーションでは、Web 要求への応答としてクライアントに送信される文字に、クライアントで使用されているエンコーディングが反映されるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="90cae-211">In a web application, characters sent to the client in response to a web request should reflect the encoding used on the client.</span></span> <span data-ttu-id="90cae-212">ほとんどの場合は、ユーザーが期待するエンコーディングでテキストを表示するために、[HttpResponse.ContentEncoding](xref:System.Net.HttpResponseHeader.ContentEncoding) プロパティを [HttpRequestHeader.ContentEncoding](xref:System.Net.HttpRequestHeader.ContentEncoding) プロパティの戻り値に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90cae-212">In most cases, you should set the [HttpResponse.ContentEncoding](xref:System.Net.HttpResponseHeader.ContentEncoding) property to the value returned by the [HttpRequestHeader.ContentEncoding](xref:System.Net.HttpRequestHeader.ContentEncoding) property to display text in the encoding that the user expects.</span></span>

## <a name="using-an-encoding-object"></a><span data-ttu-id="90cae-213">エンコーディング オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="90cae-213">Using an encoding object</span></span>

<span data-ttu-id="90cae-214">エンコーダーは、文字列 (通常は Unicode 文字) を対応する数値 (バイト) に変換します。</span><span class="sxs-lookup"><span data-stu-id="90cae-214">An encoder converts a string of characters (most commonly, Unicode characters) to its numeric (byte) equivalent.</span></span> <span data-ttu-id="90cae-215">たとえば、ASCII エンコーダーを使用すると、Unicode 文字を ASCII に変換してコンソールに表示することができます。</span><span class="sxs-lookup"><span data-stu-id="90cae-215">For example, you might use an ASCII encoder to convert Unicode characters to ASCII so that they can be displayed at the console.</span></span> <span data-ttu-id="90cae-216">この変換を実行するには、[Encoding.GetBytes](xref:System.Text.Encoding.GetBytes(System.Char[])) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="90cae-216">To perform the conversion, you call the [Encoding.GetBytes](xref:System.Text.Encoding.GetBytes(System.Char[])) method.</span></span> <span data-ttu-id="90cae-217">エンコードされた文字列を格納するために必要なバイト数をエンコードの実行前に確認するには、[GetByteCount](xref:System.Text.Encoding.GetByteCount(System.Char[])) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="90cae-217">If you want to determine how many bytes are needed to store the encoded characters before performing the encoding, you can call the [GetByteCount](xref:System.Text.Encoding.GetByteCount(System.Char[])) method.</span></span>

<span data-ttu-id="90cae-218">次の例では、1 つのバイト配列を使用して、文字列を&2; つの個別の操作でエンコードしています。</span><span class="sxs-lookup"><span data-stu-id="90cae-218">The following example uses a single byte array to encode strings in two separate operations.</span></span> <span data-ttu-id="90cae-219">バイト配列内の次の ASCII エンコード済みバイト セットの開始位置を示すインデックスが保持されています。</span><span class="sxs-lookup"><span data-stu-id="90cae-219">It maintains an index that indicates the starting position in the byte array for the next set of ASCII-encoded bytes.</span></span> <span data-ttu-id="90cae-220">この例では、[ASCIIEncoding.GetByteCount(String)](xref:System.Text.ASCIIEncoding.GetByteCount(System.String)) メソッドを呼び出して、エンコードされた文字列を格納するために十分な大きさがバイト配列にあるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="90cae-220">It calls the [ASCIIEncoding.GetByteCount(String)](xref:System.Text.ASCIIEncoding.GetByteCount(System.String)) method to ensure that the byte array is large enough to accommodate the encoded string.</span></span> <span data-ttu-id="90cae-221">次に、[ASCIIEncoding.GetBytes(String, Int32, Int32, Byte[], Int32)](xref:System.Text.ASCIIEncoding.GetBytes(System.Char[],System.Int32,System.Int32,System.Byte[],System.Int32)) メソッドを呼び出して、文字列内の文字をエンコードします。</span><span class="sxs-lookup"><span data-stu-id="90cae-221">It then calls the [ASCIIEncoding.GetBytes(String, Int32, Int32, Byte[], Int32)](xref:System.Text.ASCIIEncoding.GetBytes(System.Char[],System.Int32,System.Int32,System.Byte[],System.Int32)) method to encode the characters in the string.</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      string[] strings= { "This is the first sentence. ", 
                          "This is the second sentence. " };
      Encoding asciiEncoding = Encoding.ASCII;

      // Create array of adequate size.
      byte[] bytes = new byte[49];
      // Create index for current position of array.
      int index = 0;

      Console.WriteLine("Strings to encode:");
      foreach (var stringValue in strings) {
         Console.WriteLine("   {0}", stringValue);

         int count = asciiEncoding.GetByteCount(stringValue);
         if (count + index >=  bytes.Length)
            Array.Resize(ref bytes, bytes.Length + 50);

         int written = asciiEncoding.GetBytes(stringValue, 0, 
                                              stringValue.Length, 
                                              bytes, index);    

         index = index + written; 
      } 
      Console.WriteLine("\nEncoded bytes:");
      Console.WriteLine("{0}", ShowByteValues(bytes, index));
      Console.WriteLine();

      // Decode Unicode byte array to a string.
      string newString = asciiEncoding.GetString(bytes, 0, index);
      Console.WriteLine("Decoded: {0}", newString);
   }

   private static string ShowByteValues(byte[] bytes, int last ) 
   {
      string returnString = "   ";
      for (int ctr = 0; ctr <= last - 1; ctr++) {
         if (ctr % 20 == 0)
            returnString += "\n   ";
         returnString += String.Format("{0:X2} ", bytes[ctr]);
      }
      return returnString;
   }
}
// The example displays the following output:
//       Strings to encode:
//          This is the first sentence.
//          This is the second sentence.
//       
//       Encoded bytes:
//       
//          54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
//          6E 74 65 6E 63 65 2E 20 54 68 69 73 20 69 73 20 74 68 65 20
//          73 65 63 6F 6E 64 20 73 65 6E 74 65 6E 63 65 2E 20
//       
//       Decoded: This is the first sentence. This is the second sentence.
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim strings() As String = { "This is the first sentence. ", 
                                  "This is the second sentence. " }
      Dim asciiEncoding As Encoding = Encoding.ASCII

      ' Create array of adequate size.
      Dim bytes(50) As Byte
      ' Create index for current position of array.
      Dim index As Integer = 0

      Console.WriteLine("Strings to encode:")
      For Each stringValue In strings
         Console.WriteLine("   {0}", stringValue)

         Dim count As Integer = asciiEncoding.GetByteCount(stringValue)
         If count + index >=  bytes.Length Then
            Array.Resize(bytes, bytes.Length + 50)
         End If
         Dim written As Integer = asciiEncoding.GetBytes(stringValue, 0, 
                                                         stringValue.Length, 
                                                         bytes, index)    

         index = index + written 
      Next 
      Console.WriteLine()
      Console.WriteLine("Encoded bytes:")
      Console.WriteLine("{0}", ShowByteValues(bytes, index))
      Console.WriteLine()

      ' Decode Unicode byte array to a string.
      Dim newString As String = asciiEncoding.GetString(bytes, 0, index)
      Console.WriteLine("Decoded: {0}", newString)
   End Sub

   Private Function ShowByteValues(bytes As Byte(), last As Integer) As String
      Dim returnString As String = "   "
      For ctr As Integer = 0 To last - 1
         If ctr Mod 20 = 0 Then returnString += vbCrLf + "   "
         returnString += String.Format("{0:X2} ", bytes(ctr))
      Next
      Return returnString
   End Function
End Module
' The example displays the following output:
'       Strings to encode:
'          This is the first sentence.
'          This is the second sentence.
'       
'       Encoded bytes:
'       
'          54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
'          6E 74 65 6E 63 65 2E 20 54 68 69 73 20 69 73 20 74 68 65 20
'          73 65 63 6F 6E 64 20 73 65 6E 74 65 6E 63 65 2E 20
'       
'       Decoded: This is the first sentence. This is the second sentence.
```

<span data-ttu-id="90cae-222">デコーダーは、特定の文字エンコーディングが反映されたバイト配列を、文字配列または文字列の一連の文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="90cae-222">A decoder converts a byte array that reflects a particular character encoding into a set of characters, either in a character array or in a string.</span></span> <span data-ttu-id="90cae-223">バイト配列を文字配列にデコードするには、[Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="90cae-223">To decode a byte array into a character array, you call the [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) method.</span></span> <span data-ttu-id="90cae-224">バイト配列を文字列にデコードするには、[GetString](xref:System.Text.Encoding.GetString(System.Byte[])) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="90cae-224">To decode a byte array into a string, you call the [GetString](xref:System.Text.Encoding.GetString(System.Byte[])) method.</span></span> <span data-ttu-id="90cae-225">デコードされたバイトを格納するために必要な文字数をデコードの実行前に確認するには、[GetCharCount](xref:System.Text.Encoding.GetCharCount(System.Byte[])) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="90cae-225">If you want to determine how many characters are needed to store the decoded bytes before performing the decoding, you can call the [GetCharCount](xref:System.Text.Encoding.GetCharCount(System.Byte[])) method.</span></span>

<span data-ttu-id="90cae-226">次の例では、3 つの文字列をエンコードした後、1 つの文字配列にデコードしています。</span><span class="sxs-lookup"><span data-stu-id="90cae-226">The following example encodes three strings and then decodes them into a single array of characters.</span></span> <span data-ttu-id="90cae-227">文字配列内の次のデコード済み文字セットの開始位置を示すインデックスが保持されています。</span><span class="sxs-lookup"><span data-stu-id="90cae-227">It maintains an index that indicates the starting position in the character array for the next set of decoded characters.</span></span> <span data-ttu-id="90cae-228">この例では、[GetCharCount](xref:System.Text.Encoding.GetCharCount(System.Byte[])) メソッドを呼び出して、デコードされたすべての文字を格納するために十分な大きさが文字配列にあるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="90cae-228">It calls the [GetCharCount](xref:System.Text.Encoding.GetCharCount(System.Byte[])) method to ensure that the character array is large enough to accommodate all the decoded characters.</span></span> <span data-ttu-id="90cae-229">次に、[ASCIIEncoding.GetChars(Byte[], Int32, Int32, Char[], Int32)](xref:System.Text.ASCIIEncoding.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) メソッドを呼び出して、バイト配列をデコードします。</span><span class="sxs-lookup"><span data-stu-id="90cae-229">It then calls the [ASCIIEncoding.GetChars(Byte[], Int32, Int32, Char[], Int32)](xref:System.Text.ASCIIEncoding.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) method to decode the byte array.</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      string[] strings = { "This is the first sentence. ", 
                           "This is the second sentence. ",
                           "This is the third sentence. " };
      Encoding asciiEncoding = Encoding.ASCII;
      // Array to hold encoded bytes.
      byte[] bytes;
      // Array to hold decoded characters.
      char[] chars = new char[50];
      // Create index for current position of character array.
      int index = 0;     

      foreach (var stringValue in strings) {
         Console.WriteLine("String to Encode: {0}", stringValue);
         // Encode the string to a byte array.
         bytes = asciiEncoding.GetBytes(stringValue);
         // Display the encoded bytes.
         Console.Write("Encoded bytes: ");
         for (int ctr = 0; ctr < bytes.Length; ctr++)
            Console.Write(" {0}{1:X2}", 
                          ctr % 20 == 0 ? Environment.NewLine : "", 
                          bytes[ctr]);
         Console.WriteLine();

         // Decode the bytes to a single character array.
         int count = asciiEncoding.GetCharCount(bytes);
         if (count + index >=  chars.Length)
            Array.Resize(ref chars, chars.Length + 50);

         int written = asciiEncoding.GetChars(bytes, 0, 
                                              bytes.Length, 
                                              chars, index);              
         index = index + written;
         Console.WriteLine();       
      }

      // Instantiate a single string containing the characters.
      string decodedString = new string(chars, 0, index - 1);
      Console.WriteLine("Decoded string: ");
      Console.WriteLine(decodedString);
   }
}
// The example displays the following output:
//    String to Encode: This is the first sentence.
//    Encoded bytes:
//    54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
//    6E 74 65 6E 63 65 2E 20
//    
//    String to Encode: This is the second sentence.
//    Encoded bytes:
//    54 68 69 73 20 69 73 20 74 68 65 20 73 65 63 6F 6E 64 20 73
//    65 6E 74 65 6E 63 65 2E 20
//    
//    String to Encode: This is the third sentence.
//    Encoded bytes:
//    54 68 69 73 20 69 73 20 74 68 65 20 74 68 69 72 64 20 73 65
//    6E 74 65 6E 63 65 2E 20
//    
//    Decoded string:
//    This is the first sentence. This is the second sentence. This is the third sentence.
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim strings() As String = { "This is the first sentence. ", 
                                  "This is the second sentence. ",
                                  "This is the third sentence. " }
      Dim asciiEncoding As Encoding = Encoding.ASCII
      ' Array to hold encoded bytes.
      Dim bytes() As Byte
      ' Array to hold decoded characters.
      Dim chars(50) As Char
      ' Create index for current position of character array.
      Dim index As Integer     

      For Each stringValue In strings
         Console.WriteLine("String to Encode: {0}", stringValue)
         ' Encode the string to a byte array.
         bytes = asciiEncoding.GetBytes(stringValue)
         ' Display the encoded bytes.
         Console.Write("Encoded bytes: ")
         For ctr As Integer = 0 To bytes.Length - 1
            Console.Write(" {0}{1:X2}", If(ctr Mod 20 = 0, vbCrLf, ""), 
                                        bytes(ctr))
         Next         
         Console.WriteLine()

         ' Decode the bytes to a single character array.
         Dim count As Integer = asciiEncoding.GetCharCount(bytes)
         If count + index >=  chars.Length Then
            Array.Resize(chars, chars.Length + 50)
         End If
         Dim written As Integer = asciiEncoding.GetChars(bytes, 0, 
                                                         bytes.Length, 
                                                         chars, index)              
         index = index + written
         Console.WriteLine()       
      Next

      ' Instantiate a single string containing the characters.
      Dim decodedString As New String(chars, 0, index - 1)
      Console.WriteLine("Decoded string: ")
      Console.WriteLine(decodedString)
   End Sub
End Module
' The example displays the following output:
'    String to Encode: This is the first sentence.
'    Encoded bytes:
'    54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
'    6E 74 65 6E 63 65 2E 20
'    
'    String to Encode: This is the second sentence.
'    Encoded bytes:
'    54 68 69 73 20 69 73 20 74 68 65 20 73 65 63 6F 6E 64 20 73
'    65 6E 74 65 6E 63 65 2E 20
'    
'    String to Encode: This is the third sentence.
'    Encoded bytes:
'    54 68 69 73 20 69 73 20 74 68 65 20 74 68 69 72 64 20 73 65
'    6E 74 65 6E 63 65 2E 20
'    
'    Decoded string:
'    This is the first sentence. This is the second sentence. This is the third sentence.
```

<span data-ttu-id="90cae-230">[Encoding](xref:System.Text.Encoding) から派生するクラスのエンコード メソッドとデコード メソッドは、データ全体を処理するように設計されています。つまり、エンコードまたはデコードするすべてのデータが&1; 回のメソッド呼び出しで渡されます。</span><span class="sxs-lookup"><span data-stu-id="90cae-230">The encoding and decoding methods of a class derived from [Encoding](xref:System.Text.Encoding) are designed to work on a complete set of data; that is, all the data to be encoded or decoded is supplied in a single method call.</span></span> <span data-ttu-id="90cae-231">ただし、場合によっては、データがストリームで提供され、エンコードまたはデコードするデータを複数の読み取り操作で取得しなければならないこともあります。</span><span class="sxs-lookup"><span data-stu-id="90cae-231">However, in some cases, data is available in a stream, and the data to be encoded or decoded may be available only from separate read operations.</span></span> <span data-ttu-id="90cae-232">このような場合は、エンコード操作またはデコード操作で、前回の実行時に保存した状態を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="90cae-232">This requires the encoding or decoding operation to remember any saved state from its previous invocation.</span></span> <span data-ttu-id="90cae-233">[Encoder](xref:System.Text.Encoder) および [Decoder](xref:System.Text.Decoder) から派生するクラスのメソッドでは、複数のメソッド呼び出しにまたがるエンコード操作とデコード操作を処理できます。</span><span class="sxs-lookup"><span data-stu-id="90cae-233">Methods of classes derived from [Encoder](xref:System.Text.Encoder) and [Decoder](xref:System.Text.Decoder) are able to handle encoding and decoding operations that span multiple method calls.</span></span>

<span data-ttu-id="90cae-234">特定のエンコーディングの [Encoder](xref:System.Text.Encoder) オブジェクトは、そのエンコーディングの [Encoding.GetEncoder](xref:System.Text.Encoding.GetEncoder) プロパティから取得できます。</span><span class="sxs-lookup"><span data-stu-id="90cae-234">An [Encoder](xref:System.Text.Encoder) object for a particular encoding is available from that encoding's [Encoding.GetEncoder](xref:System.Text.Encoding.GetEncoder) property.</span></span> <span data-ttu-id="90cae-235">特定のエンコーディングの [Decoder](xref:System.Text.Decoder) オブジェクトは、そのエンコーディングの [Encoding.GetDecoder](xref:System.Text.Encoding.GetDecoder) プロパティから取得できます。</span><span class="sxs-lookup"><span data-stu-id="90cae-235">A [Decoder](xref:System.Text.Decoder) object for a particular encoding is available from that encoding's [Encoding.GetDecoder](xref:System.Text.Encoding.GetDecoder) property.</span></span> <span data-ttu-id="90cae-236">デコード操作の場合、[Decoder](xref:System.Text.Decoder) から派生するクラスに含まれるのは [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) メソッドで、[Encoding.GetString](xref:System.Text.Encoding.GetString(System.Byte[])) に対応するメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="90cae-236">For decoding operations, note that classes derived from [Decoder](xref:System.Text.Decoder) include a [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) method, but they do not have a method that corresponds to [Encoding.GetString](xref:System.Text.Encoding.GetString(System.Byte[])).</span></span>

<span data-ttu-id="90cae-237">次の例は、Unicode のバイト配列のデコードに [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) メソッドを使用する場合と [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) メソッドを使用する場合の違いを示しています。</span><span class="sxs-lookup"><span data-stu-id="90cae-237">The following example illustrates the difference between using the [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) and [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) methods for decoding a Unicode byte array.</span></span> <span data-ttu-id="90cae-238">この例では、いくつかの Unicode 文字を含む文字列をファイルにエンコードした後、この&2; つのデコード メソッドを使用して一度に&10; バイトずつデコードしています。</span><span class="sxs-lookup"><span data-stu-id="90cae-238">The example encodes a string that contains some Unicode characters to a file, and then uses the two decoding methods to decode them ten bytes at a time.</span></span> <span data-ttu-id="90cae-239">10 番目と&11; 番目のバイトに出現するサロゲート ペアは、別のメソッド呼び出しでデコードされます。</span><span class="sxs-lookup"><span data-stu-id="90cae-239">Because a surrogate pair occurs in the tenth and eleventh bytes, it is decoded in separate method calls.</span></span> <span data-ttu-id="90cae-240">出力を見るとわかるように、[Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) メソッドではこれらのバイトが正しくデコードされず、U+FFFD (REPLACEMENT CHARACTER) に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="90cae-240">As the output shows, the [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) method is not able to correctly decode the bytes and instead replaces them with U+FFFD (REPLACEMENT CHARACTER).</span></span> <span data-ttu-id="90cae-241">一方、[Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) メソッドでは、このバイト配列が正しくデコードされて、元の文字列を取得できます。</span><span class="sxs-lookup"><span data-stu-id="90cae-241">On the other hand, the [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) method is able to successfully decode the byte array to get the original string.</span></span>

```csharp
using System;
using System.IO;
using System.Text;

public class Example
{
   public static void Main()
   {
      // Use default replacement fallback for invalid encoding.
      UnicodeEncoding enc = new UnicodeEncoding(true, false, false);

      // Define a string with various Unicode characters.
      string str1 = "AB YZ 19 \uD800\udc05 \u00e4"; 
      str1 += "Unicode characters. \u00a9 \u010C s \u0062\u0308"; 
      Console.WriteLine("Created original string...\n");

      // Convert string to byte array.                     
      byte[] bytes = enc.GetBytes(str1);

      FileStream fs = File.Create(@".\characters.bin");
      BinaryWriter bw = new BinaryWriter(fs);
      bw.Write(bytes);
      bw.Close();

      // Read bytes from file.
      FileStream fsIn = File.OpenRead(@".\characters.bin");
      BinaryReader br = new BinaryReader(fsIn);

      const int count = 10;            // Number of bytes to read at a time. 
      byte[] bytesRead = new byte[10]; // Buffer (byte array).
      int read;                        // Number of bytes actually read. 
      string str2 = String.Empty;      // Decoded string.

      // Try using Encoding object for all operations.
      do { 
         read = br.Read(bytesRead, 0, count);
         str2 += enc.GetString(bytesRead, 0, read); 
      } while (read == count);
      br.Close();
      Console.WriteLine("Decoded string using UnicodeEncoding.GetString()...");
      CompareForEquality(str1, str2);
      Console.WriteLine();

      // Use Decoder for all operations.
      fsIn = File.OpenRead(@".\characters.bin");
      br = new BinaryReader(fsIn);
      Decoder decoder = enc.GetDecoder();
      char[] chars = new char[50];
      int index = 0;                   // Next character to write in array.
      int written = 0;                 // Number of chars written to array.
      do { 
         read = br.Read(bytesRead, 0, count);
         if (index + decoder.GetCharCount(bytesRead, 0, read) - 1 >= chars.Length) 
            Array.Resize(ref chars, chars.Length + 50);

         written = decoder.GetChars(bytesRead, 0, read, chars, index);
         index += written;                          
      } while (read == count);
      br.Close();            
      // Instantiate a string with the decoded characters.
      string str3 = new String(chars, 0, index); 
      Console.WriteLine("Decoded string using UnicodeEncoding.Decoder.GetString()...");
      CompareForEquality(str1, str3); 
   }

   private static void CompareForEquality(string original, string decoded)
   {
      bool result = original.Equals(decoded);
      Console.WriteLine("original = decoded: {0}", 
                        original.Equals(decoded, StringComparison.Ordinal));
      if (! result) {
         Console.WriteLine("Code points in original string:");
         foreach (var ch in original)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));
         Console.WriteLine();

         Console.WriteLine("Code points in decoded string:");
         foreach (var ch in decoded)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));
         Console.WriteLine();
      }
   }
}
// The example displays the following output:
//    Created original string...
//    
//    Decoded string using UnicodeEncoding.GetString()...
//    original = decoded: False
//    Code points in original string:
//    0041 0042 0020 0059 005A 0020 0031 0039 0020 D800 DC05 0020 00E4 0055 006E 0069 0063 006F
//    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
//    0020 0073 0020 0062 0308
//    Code points in decoded string:
//    0041 0042 0020 0059 005A 0020 0031 0039 0020 FFFD FFFD 0020 00E4 0055 006E 0069 0063 006F
//    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
//    0020 0073 0020 0062 0308
//    
//    Decoded string using UnicodeEncoding.Decoder.GetString()...
//    original = decoded: True
```

```vb
Imports System.IO
Imports System.Text

Module Example
   Public Sub Main()
      ' Use default replacement fallback for invalid encoding.
      Dim enc As New UnicodeEncoding(True, False, False)

      ' Define a string with various Unicode characters.
      Dim str1 As String = String.Format("AB YZ 19 {0}{1} {2}", 
                                         ChrW(&hD800), ChrW(&hDC05), ChrW(&h00e4))
      str1 += String.Format("Unicode characters. {0} {1} s {2}{3}", 
                            ChrW(&h00a9), ChrW(&h010C), ChrW(&h0062), ChrW(&h0308))
      Console.WriteLine("Created original string...")
      Console.WriteLine()

      ' Convert string to byte array.                     
      Dim bytes() As Byte = enc.GetBytes(str1)

      Dim fs As FileStream = File.Create(".\characters.bin")
      Dim bw As New BinaryWriter(fs)
      bw.Write(bytes)
      bw.Close()

      ' Read bytes from file.
      Dim fsIn As FileStream = File.OpenRead(".\characters.bin")
      Dim br As New BinaryReader(fsIn)

      Const count As Integer = 10      ' Number of bytes to read at a time. 
      Dim bytesRead(9) As Byte         ' Buffer (byte array).
      Dim read As Integer              ' Number of bytes actually read. 
      Dim str2 As String = ""          ' Decoded string.

      ' Try using Encoding object for all operations.
      Do 
         read = br.Read(bytesRead, 0, count)
         str2 += enc.GetString(bytesRead, 0, read) 
      Loop While read = count
      br.Close()
      Console.WriteLine("Decoded string using UnicodeEncoding.GetString()...")
      CompareForEquality(str1, str2)
      Console.WriteLine()

      ' Use Decoder for all operations.
      fsIn = File.OpenRead(".\characters.bin")
      br = New BinaryReader(fsIn)
      Dim decoder As Decoder = enc.GetDecoder()
      Dim chars(50) As Char
      Dim index As Integer = 0         ' Next character to write in array.
      Dim written As Integer = 0       ' Number of chars written to array.
      Do 
         read = br.Read(bytesRead, 0, count)
         If index + decoder.GetCharCount(bytesRead, 0, read) - 1 >= chars.Length Then 
            Array.Resize(chars, chars.Length + 50)
         End If   
         written = decoder.GetChars(bytesRead, 0, read, chars, index)
         index += written                          
      Loop While read = count
      br.Close()            
      ' Instantiate a string with the decoded characters.
      Dim str3 As New String(chars, 0, index) 
      Console.WriteLine("Decoded string using UnicodeEncoding.Decoder.GetString()...")
      CompareForEquality(str1, str3) 
   End Sub

   Private Sub CompareForEquality(original As String, decoded As String)
      Dim result As Boolean = original.Equals(decoded)
      Console.WriteLine("original = decoded: {0}", 
                        original.Equals(decoded, StringComparison.Ordinal))
      If Not result Then
         Console.WriteLine("Code points in original string:")
         For Each ch In original
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
         Console.WriteLine()

         Console.WriteLine("Code points in decoded string:")
         For Each ch In decoded
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
         Console.WriteLine()
      End If
   End Sub
End Module
' The example displays the following output:
'    Created original string...
'    
'    Decoded string using UnicodeEncoding.GetString()...
'    original = decoded: False
'    Code points in original string:
'    0041 0042 0020 0059 005A 0020 0031 0039 0020 D800 DC05 0020 00E4 0055 006E 0069 0063 006F
'    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
'    0020 0073 0020 0062 0308
'    Code points in decoded string:
'    0041 0042 0020 0059 005A 0020 0031 0039 0020 FFFD FFFD 0020 00E4 0055 006E 0069 0063 006F
'    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
'    0020 0073 0020 0062 0308
'    
'    Decoded string using UnicodeEncoding.Decoder.GetString()...
'    original = decoded: True
```

## <a name="choosing-a-fallback-strategy"></a><span data-ttu-id="90cae-242">フォールバック ストラテジの選択</span><span class="sxs-lookup"><span data-stu-id="90cae-242">Choosing a fallback strategy</span></span>

<span data-ttu-id="90cae-243">メソッドから文字のエンコードまたはデコードを行おうとしたときにマッピングが存在しない場合は、失敗したマッピングの処理方法を決めるフォールバック ストラテジを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90cae-243">When a method tries to encode or decode a character but no mapping exists, it must implement a fallback strategy that determines how the failed mapping should be handled.</span></span> <span data-ttu-id="90cae-244">次の&3; 種類のフォールバック ストラテジがあります。</span><span class="sxs-lookup"><span data-stu-id="90cae-244">There are three types of fallback strategies:</span></span> 

* <span data-ttu-id="90cae-245">最適フォールバック</span><span class="sxs-lookup"><span data-stu-id="90cae-245">Best-fit fallback</span></span>

* <span data-ttu-id="90cae-246">置換フォールバック</span><span class="sxs-lookup"><span data-stu-id="90cae-246">Replacement fallback</span></span>

* <span data-ttu-id="90cae-247">例外フォールバック</span><span class="sxs-lookup"><span data-stu-id="90cae-247">Exception fallback</span></span>

> [!IMPORTANT]
> <span data-ttu-id="90cae-248">エンコード操作で最も一般的な問題は、Unicode 文字を特定のコード ページ エンコーディングにマップできない場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="90cae-248">The most common problems in encoding operations occur when a Unicode character cannot be mapped to a particular code page encoding.</span></span> <span data-ttu-id="90cae-249">デコード操作で最も一般的な問題は、無効なバイト シーケンスを有効な Unicode 文字に変換できない場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="90cae-249">The most common problems in decoding operations occur when invalid byte sequences cannot be translated into valid Unicode characters.</span></span> <span data-ttu-id="90cae-250">そのため、個々のエンコーディング オブジェクトで使用されるフォールバック ストラテジを把握しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="90cae-250">For these reasons, you should know which fallback strategy a particular encoding object uses.</span></span> <span data-ttu-id="90cae-251">エンコーディング オブジェクトをインスタンス化するときには、可能な限り、そのオブジェクトで使用されるフォールバック ストラテジを指定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="90cae-251">Whenever possible, you should specify the fallback strategy used by an encoding object when you instantiate the object.</span></span>
 
### <a name="best-fit-fallback"></a><span data-ttu-id="90cae-252">最適フォールバック</span><span class="sxs-lookup"><span data-stu-id="90cae-252">Best-fit fallback</span></span>

<span data-ttu-id="90cae-253">ターゲット エンコード内に厳密な一致がない文字について、エンコーダーは類似した文字へのマッピングを試みることができます </span><span class="sxs-lookup"><span data-stu-id="90cae-253">When a character does not have an exact match in the target encoding, the encoder can try to map it to a similar character.</span></span> <span data-ttu-id="90cae-254">(最適フォールバックは主にエンコード時の問題であり、デコード時の問題ではありません。</span><span class="sxs-lookup"><span data-stu-id="90cae-254">(Best-fit fallback is mostly an encoding rather than a decoding issue.</span></span> <span data-ttu-id="90cae-255">Unicode に正常にマッピングできない文字を含むコード ページはほとんどありません)。最適フォールバックは、[Encoding.GetEncoding(Int32)](xref:System.Text.Encoding.GetEncoding(System.Int32)) および [Encoding.GetEncoding(String)](xref:System.Text.Encoding.GetEncoding(System.String)) の各オーバーロードによって取得されるコード ページ エンコーディングと&2; バイト文字セット エンコーディングの既定のフォールバック ストラテジです。</span><span class="sxs-lookup"><span data-stu-id="90cae-255">There are very few code pages that contain characters that cannot be successfully mapped to Unicode.) Best-fit fallback is the default for code page and double-byte character set encodings that are retrieved by the [Encoding.GetEncoding(Int32)](xref:System.Text.Encoding.GetEncoding(System.Int32)) and [Encoding.GetEncoding(String)](xref:System.Text.Encoding.GetEncoding(System.String)) overloads.</span></span>

> [!NOTE]
> <span data-ttu-id="90cae-256">.NET の Unicode エンコーディング クラス ([UTF8Encoding](xref:System.Text.UTF8Encoding)、[UnicodeEncoding](xref:System.Text.UnicodeEncoding)、および [UTF32Encoding](xref:System.Text.UTF32Encoding)) では、理論上すべての文字セットのすべての文字がサポートされているため、これらのクラスを使用すると最適フォールバックの問題を解消できます。</span><span class="sxs-lookup"><span data-stu-id="90cae-256">In theory, the Unicode encoding classes provided in .NET ([UTF8Encoding](xref:System.Text.UTF8Encoding), [UnicodeEncoding](xref:System.Text.UnicodeEncoding), and [UTF32Encoding](xref:System.Text.UTF32Encoding)) support every character in every character set, so they can be used to eliminate best-fit fallback issues.</span></span> 
 

<span data-ttu-id="90cae-257">最適なストラテジはコード ページごとに異なるため、詳細には文書化されていません。</span><span class="sxs-lookup"><span data-stu-id="90cae-257">Best-fit strategies vary for different code pages, and they are not documented in detail.</span></span> <span data-ttu-id="90cae-258">たとえば、全角のアルファベットがより一般的な半角のアルファベットにマッピングされるコード ページもあれば、</span><span class="sxs-lookup"><span data-stu-id="90cae-258">For example, for some code pages, full-width Latin characters map to the more common half-width Latin characters.</span></span> <span data-ttu-id="90cae-259">そのようなマッピングが行われないコード ページもあります。</span><span class="sxs-lookup"><span data-stu-id="90cae-259">For other code pages, this mapping is not made.</span></span> <span data-ttu-id="90cae-260">積極的な最適ストラテジでも、一部のエンコーディングの一部の文字には可能な対応がない場合があります。</span><span class="sxs-lookup"><span data-stu-id="90cae-260">Even under an aggressive best-fit strategy, there is no imaginable fit for some characters in some encodings.</span></span> <span data-ttu-id="90cae-261">たとえば、中国語の漢字からコード ページ 1252 への適切なマッピングはありません。</span><span class="sxs-lookup"><span data-stu-id="90cae-261">For example, a Chinese ideograph has no reasonable mapping to code page 1252.</span></span> <span data-ttu-id="90cae-262">その場合は、置換文字列が使用されます。</span><span class="sxs-lookup"><span data-stu-id="90cae-262">In this case, a replacement string is used.</span></span> <span data-ttu-id="90cae-263">既定では、この文字列は単一の QUESTION MARK (疑問符) (U+003F) です。</span><span class="sxs-lookup"><span data-stu-id="90cae-263">By default, this string is just a single QUESTION MARK (U+003F).</span></span>

<span data-ttu-id="90cae-264">次の例では、コード ページ 1252 (西ヨーロッパ言語の Windows コード ページ) を使用して、最適マッピングとその欠点を示しています。</span><span class="sxs-lookup"><span data-stu-id="90cae-264">The following example uses code page 1252 (the Windows code page for Western European languages) to illustrate best-fit mapping and its drawbacks.</span></span> <span data-ttu-id="90cae-265">まず、[Encoding.GetEncoding(Int32](xref:System.Text.Encoding.GetEncoding(System.Int32)) メソッドを使用して、コード ページ 1252 のエンコーディング オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="90cae-265">The [Encoding.GetEncoding(Int32](xref:System.Text.Encoding.GetEncoding(System.Int32)) method is used to retrieve an encoding object for code page 1252.</span></span> <span data-ttu-id="90cae-266">このエンコーディング オブジェクトは、サポートされていない Unicode 文字に対して既定で最適マッピングを使用します。</span><span class="sxs-lookup"><span data-stu-id="90cae-266">By default, it uses a best-fit mapping for Unicode characters that it does not support.</span></span> <span data-ttu-id="90cae-267">次に、スペースで区切られた&3; つの非 ASCII 文字 (CIRCLED LATIN CAPITAL LETTER S (U+24C8)、SUPERSCRIPT FIVE (U+2075)、および INFINITY (U+221E)) を含む文字列をインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="90cae-267">The example instantiates a string that contains three non-ASCII characters - CIRCLED LATIN CAPITAL LETTER S (U+24C8), SUPERSCRIPT FIVE (U+2075), and INFINITY (U+221E) - separated by spaces.</span></span> <span data-ttu-id="90cae-268">出力を見るとわかるように、この文字列をエンコードすると、スペースを除く元の&3; つの文字が、QUESTION MARK (U+003F)、DIGIT FIVE (U+0035)、および DIGIT EIGHT (U+0038) に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="90cae-268">As the output from the example shows, when the string is encoded, the three original non-space characters are replaced by QUESTION MARK (U+003F), DIGIT FIVE (U+0035), and DIGIT EIGHT (U+0038).</span></span> <span data-ttu-id="90cae-269">DIGIT EIGHT は、サポートされていない INFINITY 文字の代替として最適とは言えません。QUESTION MARK は、元の文字に対応するマッピングがなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="90cae-269">DIGIT EIGHT is a particularly poor replacement for the unsupported INFINITY character, and QUESTION MARK indicates that no mapping was available for the original character.</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      // Get an encoding for code page 1252 (Western Europe character set).
      Encoding cp1252 = Encoding.GetEncoding(1252);

      // Define and display a string.
      string str = "\u24c8 \u2075 \u221e";
      Console.WriteLine("Original string: " + str);
      Console.Write("Code points in string: ");
      foreach (var ch in str)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine("\n");   

      // Encode a Unicode string.
      Byte[] bytes = cp1252.GetBytes(str);
      Console.Write("Encoded bytes: ");
      foreach (byte byt in bytes)
         Console.Write("{0:X2} ", byt);
      Console.WriteLine("\n");

      // Decode the string.
      string str2 = cp1252.GetString(bytes);
      Console.WriteLine("String round-tripped: {0}", str.Equals(str2));
      if (! str.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));
      }
   }
}
// The example displays the following output:
//       Original string: Ⓢ ⁵ ∞
//       Code points in string: 24C8 0020 2075 0020 221E
//       
//       Encoded bytes: 3F 20 35 20 38
//       
//       String round-tripped: False
//       ? 5 8
//       003F 0020 0035 0020 0038
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      ' Get an encoding for code page 1252 (Western Europe character set).
      Dim cp1252 As Encoding = Encoding.GetEncoding(1252)

      ' Define and display a string.
      Dim str As String = String.Format("{0} {1} {2}", ChrW(&h24c8), ChrW(&H2075), ChrW(&h221E))
      Console.WriteLine("Original string: " + str)
      Console.Write("Code points in string: ")
      For Each ch In str
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next
      Console.WriteLine()   
      Console.WriteLine()

      ' Encode a Unicode string.
      Dim bytes() As Byte = cp1252.GetBytes(str)
      Console.Write("Encoded bytes: ")
      For Each byt In bytes
         Console.Write("{0:X2} ", byt)
      Next
      Console.WriteLine()
      Console.WriteLine()

      ' Decode the string.
      Dim str2 As String = cp1252.GetString(bytes)
      Console.WriteLine("String round-tripped: {0}", str.Equals(str2))
      If Not str.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
      End If
   End Sub
End Module
' The example displays the following output:
'       Original string: Ⓢ ⁵ ∞
'       Code points in string: 24C8 0020 2075 0020 221E
'       
'       Encoded bytes: 3F 20 35 20 38
'       
'       String round-tripped: False
'       ? 5 8
'       003F 0020 0035 0020 0038
```

<span data-ttu-id="90cae-270">最適マッピングは、Unicode データをコード ページ データにエンコードする [Encoding](xref:System.Text.Encoding) オブジェクトの既定の動作です。レガシ アプリケーションの中には、この動作に依存するものがあります。</span><span class="sxs-lookup"><span data-stu-id="90cae-270">Best-fit mapping is the default behavior for an [Encoding](xref:System.Text.Encoding) object that encodes Unicode data into code page data, and there are legacy applications that rely on this behavior.</span></span> <span data-ttu-id="90cae-271">ただし、ほとんどの新しいアプリケーションでは、セキュリティ上の理由から、最適動作の使用を避ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="90cae-271">However, most new applications should avoid best-fit behavior for security reasons.</span></span> <span data-ttu-id="90cae-272">たとえば、アプリケーションで、最適エンコードを使用してドメイン名を付けないでください。</span><span class="sxs-lookup"><span data-stu-id="90cae-272">For example, applications should not put a domain name through a best-fit encoding.</span></span>

> [!Note]
> <span data-ttu-id="90cae-273">エンコーディングに対してカスタムの最適フォールバック マッピングを実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="90cae-273">You can also implement a custom best-fit fallback mapping for an encoding.</span></span> <span data-ttu-id="90cae-274">詳細については、「[カスタム フォールバック ストラテジの実装](#implementing-a-custom-fallback-strategy)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90cae-274">For more information, see the [Implementing a custom fallback strategy](#implementing-a-custom-fallback-strategy) section.</span></span>
 
<span data-ttu-id="90cae-275">エンコーディング オブジェクトの既定値が最適フォールバックである場合、[Encoding](xref:System.Text.Encoding) オブジェクトを取得するときに別のフォールバック ストラテジを選択することもできます。そのためには、[Encoding.GetEncoding(Int32, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)) または [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) のオーバーロードを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="90cae-275">If best-fit fallback is the default for an encoding object, you can choose another fallback strategy when you retrieve an [Encoding](xref:System.Text.Encoding) object by calling the [Encoding.GetEncoding(Int32, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)) or [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) overload.</span></span> <span data-ttu-id="90cae-276">次のセクションでは、コード ページ 1252 にマップできない文字をアスタリスク (\*) に置き換える例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="90cae-276">The following section includes an example that replaces each character that cannot be mapped to code page 1252 with an asterisk (\*).</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding cp1252r = Encoding.GetEncoding(1252, 
                                  new EncoderReplacementFallback("*"),
                                  new DecoderReplacementFallback("*"));

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine();

      byte[] bytes = cp1252r.GetBytes(str1);
      string str2 = cp1252r.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      } 
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       Round-trip: False
//       * * *
//       002A 0020 002A 0020 002A
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim cp1252r As Encoding = Encoding.GetEncoding(1252, 
                                         New EncoderReplacementFallback("*"),
                                         New DecoderReplacementFallback("*"))

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()

      Dim bytes() As Byte = cp1252r.GetBytes(str1)
      Dim str2 As String = cp1252r.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next    
         Console.WriteLine()
      End If 
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       Round-trip: False
'       * * *
'       002A 0020 002A 0020 002A
```

### <a name="replacement-fallback"></a><span data-ttu-id="90cae-277">置換フォールバック</span><span class="sxs-lookup"><span data-stu-id="90cae-277">Replacement fallback</span></span>

<span data-ttu-id="90cae-278">ターゲット スキームに厳密な一致がなく、マップできる適切な文字もない文字について、アプリケーションで置換文字または置換文字列を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="90cae-278">When a character does not have an exact match in the target scheme, but there is no appropriate character that it can be mapped to, the application can specify a replacement character or string.</span></span> <span data-ttu-id="90cae-279">これは Unicode デコーダーの既定の動作です。Unicode デコーダーでは、デコードできない&2; バイトのシーケンスが REPLACEMENT_CHARACTER (U+FFFD) に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="90cae-279">This is the default behavior for the Unicode decoder, which replaces any two-byte sequence that it cannot decode with REPLACEMENT_CHARACTER (U+FFFD).</span></span> <span data-ttu-id="90cae-280">また、[ASCIIEncoding](xref:System.Text.ASCIIEncoding) クラスの既定の動作でもあり、その場合はエンコードまたはデコードできない文字が疑問符に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="90cae-280">It is also the default behavior of the [ASCIIEncoding](xref:System.Text.ASCIIEncoding) class, which replaces each character that it cannot encode or decode with a question mark.</span></span> <span data-ttu-id="90cae-281">次の例は、前の例の Unicode 文字列に対する文字置換を示しています。</span><span class="sxs-lookup"><span data-stu-id="90cae-281">The following example illustrates character replacement for the Unicode string from the previous example.</span></span> <span data-ttu-id="90cae-282">出力を見るとわかるように、ASCII バイト値にデコードできない文字は 0x3F (疑問符に対応する ASCII コード) に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="90cae-282">As the output shows, each character that cannot be decoded into an ASCII byte value is replaced by 0x3F, which is the ASCII code for a question mark.</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding enc = Encoding.ASCII;

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine("\n");

      // Encode the original string using the ASCII encoder.
      byte[] bytes = enc.GetBytes(str1);
      Console.Write("Encoded bytes: ");
      foreach (var byt in bytes)
         Console.Write("{0:X2} ", byt);
      Console.WriteLine("\n");

      // Decode the ASCII bytes.
      string str2 = enc.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      } 
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       
//       Encoded bytes: 3F 20 3F 20 3F
//       
//       Round-trip: False
//       ? ? ?
//       003F 0020 003F 0020 003F
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim enc As Encoding = Encoding.Ascii

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()
      Console.WriteLine() 

      ' Encode the original string using the ASCII encoder.
      Dim bytes() As Byte = enc.GetBytes(str1)
      Console.Write("Encoded bytes: ")
      For Each byt In bytes
         Console.Write("{0:X2} ", byt)
      Next
      Console.WriteLine()
      Console.WriteLine()

      ' Decode the ASCII bytes.
      Dim str2 As String = enc.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next    
         Console.WriteLine()
      End If 
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       
'       Encoded bytes: 3F 20 3F 20 3F
'       
'       Round-trip: False
'       ? ? ?
'       003F 0020 003F 0020 003F
```

<span data-ttu-id="90cae-283">.NET には、エンコード操作またはデコード操作で正確にマップできない文字を置換文字列に置き換える [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) クラスと [DecoderReplacementFallback](xref:System.Text.DecoderReplacementFallback) クラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="90cae-283">.NET includes the [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) and [DecoderReplacementFallback](xref:System.Text.DecoderReplacementFallback) classes, which substitute a replacement string if a character does not map exactly in an encoding or decoding operation.</span></span> <span data-ttu-id="90cae-284">この置換文字列は、既定では疑問符ですが、クラス コンストラクターのオーバーロードを呼び出して別の文字列を選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="90cae-284">By default, this replacement string is a question mark, but you can call a class constructor overload to choose a different string.</span></span> <span data-ttu-id="90cae-285">通常は単一の文字を使用しますが、単一でなくてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="90cae-285">Typically, the replacement string is a single character, although this is not a requirement.</span></span> <span data-ttu-id="90cae-286">次の例では、置換文字列としてアスタリスク (\*) を使用する [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) オブジェクトをインスタンス化して、コード ページ 1252 のエンコーダーの動作を変更しています。</span><span class="sxs-lookup"><span data-stu-id="90cae-286">The following example changes the behavior of the code page 1252 encoder by instantiating an [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) object that uses an asterisk (\*) as a replacement string.</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding cp1252r = Encoding.GetEncoding(1252, 
                                  new EncoderReplacementFallback("*"),
                                  new DecoderReplacementFallback("*"));

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine();

      byte[] bytes = cp1252r.GetBytes(str1);
      string str2 = cp1252r.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      } 
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       Round-trip: False
//       * * *
//       002A 0020 002A 0020 002A
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim cp1252r As Encoding = Encoding.GetEncoding(1252, 
                                         New EncoderReplacementFallback("*"),
                                         New DecoderReplacementFallback("*"))

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()

      Dim bytes() As Byte = cp1252r.GetBytes(str1)
      Dim str2 As String = cp1252r.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next    
         Console.WriteLine()
      End If 
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       Round-trip: False
'       * * *
'       002A 0020 002A 0020 002A
```

> [!NOTE]
> <span data-ttu-id="90cae-287">エンコーディング用の置換クラスを実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="90cae-287">You can also implement a replacement class for an encoding.</span></span> <span data-ttu-id="90cae-288">詳細については、「[カスタム フォールバック ストラテジの実装](#implementing-a-custom-fallback-strategy)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90cae-288">For more information, see the [Implementing a custom fallback strategy](#implementing-a-custom-fallback-strategy) section.</span></span>
 
<span data-ttu-id="90cae-289">置換文字列としては、QUESTION MARK (U+003F) のほか、特に Unicode 文字列に正しく変換できないバイト シーケンスをデコードする場合に、Unicode REPLACEMENT CHARACTER (U+FFFD) がよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="90cae-289">In addition to QUESTION MARK (U+003F), the Unicode REPLACEMENT CHARACTER (U+FFFD) is commonly used as a replacement string, particularly when decoding byte sequences that cannot be successfully translated into Unicode characters.</span></span> <span data-ttu-id="90cae-290">ただし、置換文字列は自由に選択できます。置換文字列に複数の文字を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="90cae-290">However, you are free to choose any replacement string, and it can contain multiple characters.</span></span>

### <a name="exception-fallback"></a><span data-ttu-id="90cae-291">例外フォールバック</span><span class="sxs-lookup"><span data-stu-id="90cae-291">Exception fallback</span></span>

<span data-ttu-id="90cae-292">最適フォールバックや置換文字列を提供する代わりに、エンコーダーで一連の文字をエンコードできない場合に [EncoderFallbackException](xref:System.Text.EncoderFallbackException) をスローしたり、デコーダーでバイト配列をデコードできない場合に [DecoderFallbackException](xref:System.Text.DecoderFallbackException) をスローしたりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="90cae-292">Instead of providing a best-fit fallback or a replacement string, an encoder can throw an [EncoderFallbackException](xref:System.Text.EncoderFallbackException) if it is unable to encode a set of characters, and a decoder can throw a [DecoderFallbackException](xref:System.Text.DecoderFallbackException) if it is unable to decode a byte array.</span></span> <span data-ttu-id="90cae-293">エンコードおよびデコード操作で例外をスローするには、[EncoderFallbackException](xref:System.Text.EncoderFallbackException) オブジェクトと [DecoderFallbackException](xref:System.Text.DecoderFallbackException) オブジェクトをそれぞれ [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) メソッドに指定します。</span><span class="sxs-lookup"><span data-stu-id="90cae-293">To throw an exception in encoding and decoding operations, you supply an [EncoderFallbackException](xref:System.Text.EncoderFallbackException) object and a [DecoderFallbackException](xref:System.Text.DecoderFallbackException) object, respectively, to the [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) method.</span></span> <span data-ttu-id="90cae-294">次の例は、ASCIIEncoding クラスによる例外フォールバックを示しています。</span><span class="sxs-lookup"><span data-stu-id="90cae-294">The following example illustrates exception fallback with the ASCIIEncoding class.</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding enc = Encoding.GetEncoding("us-ascii", 
                                          new EncoderExceptionFallback(), 
                                          new DecoderExceptionFallback());

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine("\n");

      // Encode the original string using the ASCII encoder.
      byte[] bytes = {};
      try {
         bytes = enc.GetBytes(str1);
         Console.Write("Encoded bytes: ");
         foreach (var byt in bytes)
            Console.Write("{0:X2} ", byt);

         Console.WriteLine();
      }
      catch (EncoderFallbackException e) {
         Console.Write("Exception: ");
         if (e.IsUnknownSurrogate())
            Console.WriteLine("Unable to encode surrogate pair 0x{0:X4} 0x{1:X3} at index {2}.", 
                              Convert.ToUInt16(e.CharUnknownHigh), 
                              Convert.ToUInt16(e.CharUnknownLow), 
                              e.Index);
         else
            Console.WriteLine("Unable to encode 0x{0:X4} at index {1}.", 
                              Convert.ToUInt16(e.CharUnknown), 
                              e.Index);
         return;
      }
      Console.WriteLine();

      // Decode the ASCII bytes.
      try {
         string str2 = enc.GetString(bytes);
         Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
         if (! str1.Equals(str2)) {
            Console.WriteLine(str2);
            foreach (var ch in str2)
               Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

            Console.WriteLine();
         } 
      }
      catch (DecoderFallbackException e) {
         Console.Write("Unable to decode byte(s) ");
         foreach (byte unknown in e.BytesUnknown)
            Console.Write("0x{0:X2} ");

         Console.WriteLine("at index {0}", e.Index);
      }
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       
//       Exception: Unable to encode 0x24C8 at index 0.
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim enc As Encoding = Encoding.GetEncoding("us-ascii", 
                                                 New EncoderExceptionFallback(), 
                                                 New DecoderExceptionFallback())

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()
      Console.WriteLine() 

      ' Encode the original string using the ASCII encoder.
      Dim bytes() As Byte = {}
      Try
         bytes = enc.GetBytes(str1)
         Console.Write("Encoded bytes: ")
         For Each byt In bytes
            Console.Write("{0:X2} ", byt)
         Next
         Console.WriteLine()
      Catch e As EncoderFallbackException
         Console.Write("Exception: ")
         If e.IsUnknownSurrogate() Then
            Console.WriteLine("Unable to encode surrogate pair 0x{0:X4} 0x{1:X3} at index {2}.", 
                              Convert.ToUInt16(e.CharUnknownHigh), 
                              Convert.ToUInt16(e.CharUnknownLow), 
                              e.Index)
         Else
            Console.WriteLine("Unable to encode 0x{0:X4} at index {1}.", 
                              Convert.ToUInt16(e.CharUnknown), 
                              e.Index)
         End If                              
         Exit Sub
      End Try
      Console.WriteLine()

      ' Decode the ASCII bytes.
      Try
         Dim str2 As String = enc.GetString(bytes)
         Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
         If Not str1.Equals(str2) Then
            Console.WriteLine(str2)
            For Each ch In str2
               Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
            Next    
            Console.WriteLine()
         End If 
      Catch e As DecoderFallbackException
         Console.Write("Unable to decode byte(s) ")
         For Each unknown As Byte In e.BytesUnknown
            Console.Write("0x{0:X2} ")
         Next
         Console.WriteLine("at index {0}", e.Index)
      End Try
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       
'       Exception: Unable to encode 0x24C8 at index 0.
```

> [!NOTE]
> <span data-ttu-id="90cae-295">エンコード操作用のカスタム例外ハンドラーを実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="90cae-295">You can also implement a custom exception handler for an encoding operation.</span></span> <span data-ttu-id="90cae-296">詳細については、「[カスタム フォールバック ストラテジの実装](#implementing-a-custom-fallback-strategy)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90cae-296">For more information, see the [Implementing a custom fallback strategy](#implementing-a-custom-fallback-strategy) section.</span></span>
 
<span data-ttu-id="90cae-297">[EncoderFallbackException](xref:System.Text.EncoderFallbackException) オブジェクトと [DecoderFallbackException](xref:System.Text.DecoderFallbackException) オブジェクトは、例外を引き起こした状況について以下の情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="90cae-297">The [EncoderFallbackException](xref:System.Text.EncoderFallbackException) and [DecoderFallbackException](xref:System.Text.DecoderFallbackException) objects provide the following information about the condition that caused the exception:</span></span> 

* <span data-ttu-id="90cae-298">[EncoderFallbackException](xref:System.Text.EncoderFallbackException) オブジェクトに含まれている [IsUnknownSurrogate](xref:System.Text.EncoderFallbackException.IsUnknownSurrogate) メソッドにより、エンコードできない文字が不明なサロゲート ペアか (この場合は `true` が返されます)、不明な単一文字か (この場合は `false` が返されます) が示されます。</span><span class="sxs-lookup"><span data-stu-id="90cae-298">The [EncoderFallbackException](xref:System.Text.EncoderFallbackException) object includes an [IsUnknownSurrogate](xref:System.Text.EncoderFallbackException.IsUnknownSurrogate) method, which indicates whether the character or characters that cannot be encoded represent an unknown surrogate pair (in which case, the method returns `true`) or an unknown single character (in which case, the method returns `false`).</span></span> <span data-ttu-id="90cae-299">サロゲート ペアの文字は、[EncoderFallbackException.CharUnknownHigh](xref:System.Text.EncoderFallbackException.CharUnknownHigh) プロパティと [EncoderFallbackException.CharUnknownLow](xref:System.Text.EncoderFallbackException.CharUnknownLow) プロパティから取得できます。</span><span class="sxs-lookup"><span data-stu-id="90cae-299">The characters in the surrogate pair are available from the [EncoderFallbackException.CharUnknownHigh](xref:System.Text.EncoderFallbackException.CharUnknownHigh) and [EncoderFallbackException.CharUnknownLow](xref:System.Text.EncoderFallbackException.CharUnknownLow) properties.</span></span> <span data-ttu-id="90cae-300">不明な単一文字は、[EncoderFallbackException.CharUnknown](xref:System.Text.EncoderFallbackException.CharUnknown) プロパティから取得できます。</span><span class="sxs-lookup"><span data-stu-id="90cae-300">The unknown single character is available from the [EncoderFallbackException.CharUnknown](xref:System.Text.EncoderFallbackException.CharUnknown) property.</span></span> <span data-ttu-id="90cae-301">また、[EncoderFallbackException.Index](xref:System.Text.EncoderFallbackException.Index) プロパティにより、エンコードできない最初の文字が見つかった文字列内の位置が示されます。</span><span class="sxs-lookup"><span data-stu-id="90cae-301">The [EncoderFallbackException.Index](xref:System.Text.EncoderFallbackException.Index) property indicates the position in the string at which the first character that could not be encoded was found.</span></span>

* <span data-ttu-id="90cae-302">[DecoderFallbackException](xref:System.Text.DecoderFallbackException) オブジェクトに含まれている [BytesUnknown](xref:System.Text.DecoderFallbackException.BytesUnknown) プロパティにより、デコードできないバイト配列が返されます。</span><span class="sxs-lookup"><span data-stu-id="90cae-302">The [DecoderFallbackException](xref:System.Text.DecoderFallbackException) object includes a [BytesUnknown](xref:System.Text.DecoderFallbackException.BytesUnknown) property that returns an array of bytes that cannot be decoded.</span></span> <span data-ttu-id="90cae-303">また、[DecoderFallbackException.Index](xref:System.Text.DecoderFallbackException.Index) プロパティにより、不明なバイトの開始位置が示されます。</span><span class="sxs-lookup"><span data-stu-id="90cae-303">The [DecoderFallbackException.Index](xref:System.Text.DecoderFallbackException.Index) property indicates the starting position of the unknown bytes.</span></span>

<span data-ttu-id="90cae-304">[EncoderFallbackException](xref:System.Text.EncoderFallbackException) オブジェクトと [DecoderFallbackException](xref:System.Text.DecoderFallbackException) オブジェクトでは、例外に関する診断情報は十分に入手できますが、エンコード バッファーやデコード バッファーにアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="90cae-304">Although the [EncoderFallbackException](xref:System.Text.EncoderFallbackException) and [DecoderFallbackException](xref:System.Text.DecoderFallbackException) objects provide adequate diagnostic information about the exception, they do not provide access to the encoding or decoding buffer.</span></span> <span data-ttu-id="90cae-305">したがって、エンコード メソッド内またはデコード メソッド内で無効なデータを置換したり修正したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="90cae-305">Therefore, they do not allow invalid data to be replaced or corrected within the encoding or decoding method.</span></span>

## <a name="implementing-a-custom-fallback-strategy"></a><span data-ttu-id="90cae-306">カスタム フォールバック ストラテジの実装</span><span class="sxs-lookup"><span data-stu-id="90cae-306">Implementing a custom fallback strategy</span></span>

<span data-ttu-id="90cae-307">.NET には、コード ページによって内部的に実装される最適マッピングに加えて、フォールバック ストラテジを実装するための次のクラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="90cae-307">In addition to the best-fit mapping that is implemented internally by code pages, .NET includes the following classes for implementing a fallback strategy:</span></span>

* <span data-ttu-id="90cae-308">[EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) および [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer)。エンコード操作中に文字を置換します。</span><span class="sxs-lookup"><span data-stu-id="90cae-308">Use [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) and [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) to replace characters in encoding operations.</span></span>

* <span data-ttu-id="90cae-309">[DecoderReplacementFallback](xref:System.Text.DecoderReplacementFallback) および [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer)。デコード操作中に文字を置換します。</span><span class="sxs-lookup"><span data-stu-id="90cae-309">Use [DecoderReplacementFallback](xref:System.Text.DecoderReplacementFallback) and [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) to replace characters in decoding operations.</span></span>

* <span data-ttu-id="90cae-310">[EncoderExceptionFallback](xref:System.Text.EncoderExceptionFallback) および [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer)。文字をエンコードできない場合に [EncoderFallbackException](xref:System.Text.EncoderFallbackException) をスローします。</span><span class="sxs-lookup"><span data-stu-id="90cae-310">Use [EncoderExceptionFallback](xref:System.Text.EncoderExceptionFallback) and [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) to throw an [EncoderFallbackException](xref:System.Text.EncoderFallbackException) when a character cannot be encoded.</span></span>

* <span data-ttu-id="90cae-311">[DecoderExceptionFallback](xref:System.Text.DecoderExceptionFallback) および [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer)。文字をエンコードできない場合に [DecoderFallbackException](xref:System.Text.DecoderFallbackException) をスローします。</span><span class="sxs-lookup"><span data-stu-id="90cae-311">Use [DecoderExceptionFallback](xref:System.Text.DecoderExceptionFallback) and [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) to throw a [DecoderFallbackException](xref:System.Text.DecoderFallbackException) when a character cannot be decoded.</span></span>

<span data-ttu-id="90cae-312">さらに、次の手順に従って、最適フォールバック、置換フォールバック、または例外フォールバックを使用するカスタム ソリューションを実装できます。</span><span class="sxs-lookup"><span data-stu-id="90cae-312">In addition, you can implement a custom solution that uses best-fit fallback, replacement fallback, or exception fallback, by following these steps:</span></span> 

1. <span data-ttu-id="90cae-313">エンコード操作の場合は [EncoderFallback](xref:System.Text.EncoderFallback)、デコード操作の場合は [DecoderFallback](xref:System.Text.DecoderFallback) の派生クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="90cae-313">Derive a class from [EncoderFallback](xref:System.Text.EncoderFallback) for encoding operations, and from [DecoderFallback](xref:System.Text.DecoderFallback) for decoding operations.</span></span>

2. <span data-ttu-id="90cae-314">エンコード操作の場合は [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer)、デコード操作の場合は [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) の派生クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="90cae-314">Derive a class from [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) for encoding operations, and from [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) for decoding operations.</span></span>

3. <span data-ttu-id="90cae-315">例外フォールバックにおいて、あらかじめ定義されている [EncoderFallbackException](xref:System.Text.EncoderFallbackException) クラスと [DecoderFallbackException](xref:System.Text.DecoderFallbackException) クラスが目的に合わない場合は、[Exception](xref:System.Exception) や [ArgumentException](xref:System.ArgumentException) などの例外オブジェクトから派生クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="90cae-315">For exception fallback, if the predefined [EncoderFallbackException](xref:System.Text.EncoderFallbackException) and [DecoderFallbackException](xref:System.Text.DecoderFallbackException) classes do not meet your needs, derive a class from an exception object such as [Exception](xref:System.Exception) or [ArgumentException](xref:System.ArgumentException).</span></span>

### <a name="deriving-from-encoderfallback-or-decoderfallback"></a><span data-ttu-id="90cae-316">EncoderFallback または DecoderFallback からの派生</span><span class="sxs-lookup"><span data-stu-id="90cae-316">Deriving from EncoderFallback or DecoderFallback</span></span>

<span data-ttu-id="90cae-317">カスタム フォールバック ソリューションを実装するには、エンコード操作の場合は [EncoderFallback](xref:System.Text.EncoderFallback)、デコード操作の場合は [DecoderFallback](xref:System.Text.DecoderFallback) を継承するクラスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90cae-317">To implement a custom fallback solution, you must create a class that inherits from [EncoderFallback](xref:System.Text.EncoderFallback) for encoding operations, and from [DecoderFallback](xref:System.Text.DecoderFallback) for decoding operations.</span></span> <span data-ttu-id="90cae-318">これらのクラスのインスタンスは [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) メソッドに渡され、エンコーディング クラスとフォールバックの実装の仲介役として機能します。</span><span class="sxs-lookup"><span data-stu-id="90cae-318">Instances of these classes are passed to the [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) method and serve as the intermediary between the encoding class and the fallback implementation.</span></span>

<span data-ttu-id="90cae-319">エンコーダーまたはデコーダーのカスタム フォールバック ソリューションを作成するときには、次のメンバーを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90cae-319">When you create a custom fallback solution for an encoder or decoder, you must implement the following members:</span></span>

* <span data-ttu-id="90cae-320">[EncoderFallback.MaxCharCount](xref:System.Text.EncoderFallback.MaxCharCount) プロパティまたは [DecoderFallback.MaxCharCount](xref:System.Text.DecoderFallback.MaxCharCount) プロパティ。最適、置換、例外の各フォールバックで単一の文字を置き換えるために返すことのできる文字の最大数を返します。</span><span class="sxs-lookup"><span data-stu-id="90cae-320">The [EncoderFallback.MaxCharCount](xref:System.Text.EncoderFallback.MaxCharCount) or [DecoderFallback.MaxCharCount](xref:System.Text.DecoderFallback.MaxCharCount) property, which returns the maximum possible number of characters that the best-fit, replacement, or exception fallback can return to replace a single character.</span></span> <span data-ttu-id="90cae-321">カスタム例外フォールバックの場合は&0; になります。</span><span class="sxs-lookup"><span data-stu-id="90cae-321">For a custom exception fallback, its value is zero.</span></span> 

* <span data-ttu-id="90cae-322">[EncoderFallback.CreateFallbackBuffer](xref:System.Text.EncoderFallback.CreateFallbackBuffer) メソッドまたは [DecoderFallback.CreateFallbackBuffer](xref:System.Text.DecoderFallback.CreateFallbackBuffer) メソッド。[EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) または [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) のカスタム実装を返します。</span><span class="sxs-lookup"><span data-stu-id="90cae-322">The [EncoderFallback.CreateFallbackBuffer](xref:System.Text.EncoderFallback.CreateFallbackBuffer) or [DecoderFallback.CreateFallbackBuffer](xref:System.Text.DecoderFallback.CreateFallbackBuffer) method, which returns your custom [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) or [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) implementation.</span></span> <span data-ttu-id="90cae-323">このメソッドは、エンコーダーで正しくエンコードできない文字が初めて検出されたとき、またはデコーダーで正しくデコードできないバイトが初めて検出されたときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="90cae-323">The method is called by the encoder when it encounters the first character that it is unable to successfully encode, or by the decoder when it encounters the first byte that it is unable to successfully decode.</span></span>

### <a name="deriving-from-encoderfallbackbuffer-or-decoderfallbackbuffer"></a><span data-ttu-id="90cae-324">EncoderFallbackBuffer または DecoderFallbackBuffer からの派生</span><span class="sxs-lookup"><span data-stu-id="90cae-324">Deriving from EncoderFallbackBuffer or DecoderFallbackBuffer</span></span>

<span data-ttu-id="90cae-325">カスタム フォールバック ソリューションを実装するには、エンコード操作の場合は [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer)、デコード操作の場合は [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) を継承するクラスも作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90cae-325">To implement a custom fallback solution, you must also create a class that inherits from [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) for encoding operations, and from [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) for decoding operations.</span></span> <span data-ttu-id="90cae-326">これらのクラスのインスタンスは、[EncoderFallback](xref:System.Text.EncoderFallback) クラスおよび [DecoderFallback](xref:System.Text.DecoderFallback) クラスの `CreateFallbackBuffer` メソッドによって返されます。</span><span class="sxs-lookup"><span data-stu-id="90cae-326">Instances of these classes are returned by the `CreateFallbackBuffer` method of the [EncoderFallback](xref:System.Text.EncoderFallback) and [DecoderFallback](xref:System.Text.DecoderFallback) classes.</span></span> <span data-ttu-id="90cae-327">[EncoderFallback.CreateFallbackBuffer](xref:System.Text.EncoderFallback.CreateFallbackBuffer) メソッドは、エンコーダーでエンコードできない文字が初めて検出されたときに呼び出され、[DecoderFallback.CreateFallbackBuffer](xref:System.Text.DecoderFallback.CreateFallbackBuffer) メソッドは、デコーダーでデコードできないバイトが検出されたときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="90cae-327">The [EncoderFallback.CreateFallbackBuffer](xref:System.Text.EncoderFallback.CreateFallbackBuffer) method is called by the encoder when it encounters the first character that it is not able to encode, and the [DecoderFallback.CreateFallbackBuffer](xref:System.Text.DecoderFallback.CreateFallbackBuffer) method is called by the decoder when it encounters one or more bytes that it is not able to decode.</span></span> <span data-ttu-id="90cae-328">[EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) クラスと[DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) クラスは、フォールバックの実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="90cae-328">The [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) and [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) classes provide the fallback implementation.</span></span> <span data-ttu-id="90cae-329">各インスタンスは、エンコードできない文字またはデコードできないバイト シーケンスを置き換えるフォールバック文字を含むバッファーを表します。</span><span class="sxs-lookup"><span data-stu-id="90cae-329">Each instance represents a buffer that contains the fallback characters that will replace the character that cannot be encoded or the byte sequence that cannot be decoded.</span></span>

<span data-ttu-id="90cae-330">エンコーダーまたはデコーダーのカスタム フォールバック ソリューションを作成するときには、次のメンバーを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90cae-330">When you create a custom fallback solution for an encoder or decoder, you must implement the following members:</span></span>

* <span data-ttu-id="90cae-331">[EncoderFallbackBuffer.Fallback](xref:System.Text.EncoderFallbackBuffer.%23ctor) メソッドまたは [DecoderFallbackBuffer.Fallback](xref:System.Text.DecoderFallbackBuffer.Fallback(System.Byte[],System.Int32)) メソッド。</span><span class="sxs-lookup"><span data-stu-id="90cae-331">The [EncoderFallbackBuffer.Fallback](xref:System.Text.EncoderFallbackBuffer.%23ctor) or [DecoderFallbackBuffer.Fallback](xref:System.Text.DecoderFallbackBuffer.Fallback(System.Byte[],System.Int32)) method.</span></span> <span data-ttu-id="90cae-332">[EncoderFallbackBuffer.Fallback](xref:System.Text.EncoderFallbackBuffer.Fallback(System.Char,System.Char,System.Int32)) は、エンコーダーによって呼び出され、エンコードできない文字に関する情報をフォールバック バッファーに提供します。</span><span class="sxs-lookup"><span data-stu-id="90cae-332">[EncoderFallbackBuffer.Fallback](xref:System.Text.EncoderFallbackBuffer.Fallback(System.Char,System.Char,System.Int32)) is called by the encoder to provide the fallback buffer with information about the character that it cannot encode.</span></span> <span data-ttu-id="90cae-333">エンコードされる文字はサロゲート ペアである場合もあるため、このメソッドはオーバーロードされます。</span><span class="sxs-lookup"><span data-stu-id="90cae-333">Because the character to be encoded may be a surrogate pair, this method is overloaded.</span></span> <span data-ttu-id="90cae-334">最初のオーバーロードには、エンコードされる文字と、その文字列内のインデックスが渡されます。</span><span class="sxs-lookup"><span data-stu-id="90cae-334">One overload is passed the character to be encoded and its index in the string.</span></span> <span data-ttu-id="90cae-335">2 番目のオーバーロードには、上位および下位のサロゲートと、その文字列内のインデックスが渡されます。</span><span class="sxs-lookup"><span data-stu-id="90cae-335">The second overload is passed the high and low surrogate along with its index in the string.</span></span> <span data-ttu-id="90cae-336">[DecoderFallbackBuffer.Fallback](xref:System.Text.DecoderFallbackBuffer.Fallback(System.Byte[],System.Int32)) メソッドは、デコーダーによって呼び出され、デコードできないバイトに関する情報をフォールバック バッファーに提供します。</span><span class="sxs-lookup"><span data-stu-id="90cae-336">The [DecoderFallbackBuffer.Fallback](xref:System.Text.DecoderFallbackBuffer.Fallback(System.Byte[],System.Int32)) method is called by the decoder to provide the fallback buffer with information about the bytes that it cannot decode.</span></span> <span data-ttu-id="90cae-337">このメソッドには、デコードできないバイト配列と、最初のバイトのインデックスが渡されます。</span><span class="sxs-lookup"><span data-stu-id="90cae-337">This method is passed an array of bytes that it cannot decode, along with the index of the first byte.</span></span> <span data-ttu-id="90cae-338">フォールバック メソッドは、フォールバック バッファーが最適な文字または置換文字を提供できる場合は `true`、それ以外の場合は `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="90cae-338">The fallback method should return `true` if the fallback buffer can supply a best-fit or replacement character or characters; otherwise, it should return `false`.</span></span> <span data-ttu-id="90cae-339">例外フォールバックの場合は例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="90cae-339">For an exception fallback, the fallback method should throw an exception.</span></span>

* <span data-ttu-id="90cae-340">[EncoderFallbackBuffer.GetNextChar](xref:System.Text.EncoderFallbackBuffer.GetNextChar) メソッドまたは [DecoderFallbackBuffer.GetNextChar](xref:System.Text.DecoderFallbackBuffer.GetNextChar) メソッド。フォールバック バッファーから次の文字を取得するために、エンコーダーまたはデコーダーによって繰り返し呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="90cae-340">The [EncoderFallbackBuffer.GetNextChar](xref:System.Text.EncoderFallbackBuffer.GetNextChar) or [DecoderFallbackBuffer.GetNextChar](xref:System.Text.DecoderFallbackBuffer.GetNextChar) method, which is called repeatedly by the encoder or decoder to get the next character from the fallback buffer.</span></span> <span data-ttu-id="90cae-341">すべてのフォールバック文字を返し終わったら、このメソッドは U+0000 を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="90cae-341">When all fallback characters have been returned, the method should return U+0000.</span></span> 

* <span data-ttu-id="90cae-342">[EncoderFallbackBuffer.Remaining](xref:System.Text.EncoderFallbackBuffer.Remaining) プロパティまたは [DecoderFallbackBuffer.Remaining](xref:System.Text.DecoderFallbackBuffer.Remaining) プロパティ。フォールバック バッファー内の残りの文字数を返します。</span><span class="sxs-lookup"><span data-stu-id="90cae-342">The [EncoderFallbackBuffer.Remaining](xref:System.Text.EncoderFallbackBuffer.Remaining) or [DecoderFallbackBuffer.Remaining](xref:System.Text.DecoderFallbackBuffer.Remaining) property, which returns the number of characters remaining in the fallback buffer.</span></span>

* <span data-ttu-id="90cae-343">[EncoderFallbackBuffer.MovePrevious](xref:System.Text.EncoderFallbackBuffer.MovePrevious) メソッドまたは [DecoderFallbackBuffer.MovePrevious](xref:System.Text.DecoderFallbackBuffer.MovePrevious) メソッド。フォールバック バッファー内の現在の位置を前の文字に移動します。</span><span class="sxs-lookup"><span data-stu-id="90cae-343">The [EncoderFallbackBuffer.MovePrevious](xref:System.Text.EncoderFallbackBuffer.MovePrevious) or [DecoderFallbackBuffer.MovePrevious](xref:System.Text.DecoderFallbackBuffer.MovePrevious) method, which moves the current position in the fallback buffer to the previous character.</span></span>

* <span data-ttu-id="90cae-344">[EncoderFallbackBuffer.Reset](xref:System.Text.EncoderFallbackBuffer.Reset) メソッドまたは [DecoderFallbackBuffer.Reset](xref:System.Text.DecoderFallbackBuffer.Reset) メソッド。フォールバック バッファーを再初期化します。</span><span class="sxs-lookup"><span data-stu-id="90cae-344">The [EncoderFallbackBuffer.Reset](xref:System.Text.EncoderFallbackBuffer.Reset) or [DecoderFallbackBuffer.Reset](xref:System.Text.DecoderFallbackBuffer.Reset) method, which reinitializes the fallback buffer.</span></span>

<span data-ttu-id="90cae-345">フォールバックの実装が最適フォールバックまたは置換フォールバックの場合は、[EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) と [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) の派生クラスで、2 つのプライベート インスタンス フィールド (バッファー内の正確な文字数と、次に返される文字のインデックス) も保持します。</span><span class="sxs-lookup"><span data-stu-id="90cae-345">If the fallback implementation is a best-fit fallback or a replacement fallback, the classes derived from [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) and [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) also maintain two private instance fields: the exact number of characters in the buffer; and the index of the next character in the buffer to return.</span></span>

### <a name="an-encoderfallback-example"></a><span data-ttu-id="90cae-346">EncoderFallback の例</span><span class="sxs-lookup"><span data-stu-id="90cae-346">An EncoderFallback example</span></span>

<span data-ttu-id="90cae-347">前の例では、置換フォールバックを使用して、対応する ASCII 文字がない Unicode 文字をアスタリスク (\*) に置き換えました。</span><span class="sxs-lookup"><span data-stu-id="90cae-347">An earlier example used replacement fallback to replace Unicode characters that did not correspond to ASCII characters with an asterisk (\*).</span></span> <span data-ttu-id="90cae-348">次の例では、代わりに最適フォールバックのカスタム実装を使用して、非 ASCII 文字のマッピングを改善しています。</span><span class="sxs-lookup"><span data-stu-id="90cae-348">The following example uses a custom best-fit fallback implementation instead to provide a better mapping of non-ASCII characters.</span></span>

<span data-ttu-id="90cae-349">次のコードでは、[EncoderFallback](xref:System.Text.EncoderFallback) から派生する `CustomMapper` という名前のクラスを定義して、非 ASCII 文字の最適マッピングを処理します。</span><span class="sxs-lookup"><span data-stu-id="90cae-349">The following code defines a class named `CustomMapper` that is derived from [EncoderFallback](xref:System.Text.EncoderFallback) to handle the best-fit mapping of non-ASCII characters.</span></span> <span data-ttu-id="90cae-350">このクラスの `CreateFallbackBuffer` メソッドは、[EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) の実装を提供する `CustomMapperFallbackBuffer` オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="90cae-350">Its `CreateFallbackBuffer` method returns a `CustomMapperFallbackBuffer` object, which provides the [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) implementation.</span></span> <span data-ttu-id="90cae-351">`CustomMapper` クラスは、[Dictionary&lt;TKey, TValue&gt;](xref:System.Collections.Generic.Dictionary%602) オブジェクトを使用して、サポートされていない Unicode 文字 (キー値) と、それらに対応する 8 ビット文字とのマッピングを格納します (64 ビット整数の 2 つの連続するバイトに格納されます)。</span><span class="sxs-lookup"><span data-stu-id="90cae-351">The `CustomMapper` class uses a [Dictionary&lt;TKey, TValue&gt;](xref:System.Collections.Generic.Dictionary%602) object to store the mappings of unsupported Unicode characters (the key value) and their corresponding 8-bit characters (which are stored in two consecutive bytes in a 64-bit integer).</span></span> <span data-ttu-id="90cae-352">このマッピングをフォールバック バッファーで使用できるようにするには、`CustomMapper` のインスタンスを `CustomMapperFallbackBuffer` のクラス コンストラクターにパラメーターとして渡します。</span><span class="sxs-lookup"><span data-stu-id="90cae-352">To make this mapping available to the fallback buffer, the `CustomMapper` instance is passed as a parameter to the `CustomMapperFallbackBuffer` class constructor.</span></span> <span data-ttu-id="90cae-353">最も長いマッピングは Unicode 文字 U+221E に対応する文字列 "INF" なので、`MaxCharCount` プロパティは 3 を返します。</span><span class="sxs-lookup"><span data-stu-id="90cae-353">Because the longest mapping is the string "INF" for the Unicode character U+221E, the `MaxCharCount` property returns 3.</span></span> 

```csharp
public class CustomMapper : EncoderFallback
{
   public string DefaultString;
   internal Dictionary<ushort, ulong> mapping;

   public CustomMapper() : this("*")
   {   
   }

   public CustomMapper(string defaultString)
   {
      this.DefaultString = defaultString;

      // Create table of mappings
      mapping = new Dictionary<ushort, ulong>();
      mapping.Add(0x24C8, 0x53);
      mapping.Add(0x2075, 0x35);
      mapping.Add(0x221E, 0x49004E0046);
   }

   public override EncoderFallbackBuffer CreateFallbackBuffer()
   {
      return new CustomMapperFallbackBuffer(this);
   }

   public override int MaxCharCount
   {
      get { return 3; }
   } 
}
```

```vb
Public Class CustomMapper : Inherits EncoderFallback
   Public DefaultString As String
   Friend mapping As Dictionary(Of UShort, ULong)

   Public Sub New()
      Me.New("?")
   End Sub

   Public Sub New(ByVal defaultString As String)
      Me.DefaultString = defaultString

      ' Create table of mappings
      mapping = New Dictionary(Of UShort, ULong)
      mapping.Add(&H24C8, &H53)
      mapping.Add(&H2075, &H35)
      mapping.Add(&H221E, &H49004E0046)
   End Sub

   Public Overrides Function CreateFallbackBuffer() As System.Text.EncoderFallbackBuffer
      Return New CustomMapperFallbackBuffer(Me)
   End Function

   Public Overrides ReadOnly Property MaxCharCount As Integer
      Get
         Return 3
      End Get
   End Property
End Class
```

<span data-ttu-id="90cae-354">次のコードでは、[EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) から派生する `CustomMapperFallbackBuffer` クラスを定義しています。</span><span class="sxs-lookup"><span data-stu-id="90cae-354">The following code defines the `CustomMapperFallbackBuffer` class, which is derived from [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer).</span></span> <span data-ttu-id="90cae-355">`CustomMapper` インスタンスで定義されている、最適マッピングを含むディクショナリは、クラス コンストラクターから取得できます。</span><span class="sxs-lookup"><span data-stu-id="90cae-355">The dictionary that contains best-fit mappings and that is defined in the `CustomMapper` instance is available from its class constructor.</span></span> <span data-ttu-id="90cae-356">このクラスの `Fallback` メソッドは、ASCII エンコーダーでエンコードできない Unicode 文字がマッピング ディクショナリで定義されている場合は `true` を返し、それ以外の場合は `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="90cae-356">Its `Fallback` method returns `true` if any of the Unicode characters that the ASCII encoder cannot encode are defined in the mapping dictionary; otherwise, it returns `false`.</span></span> <span data-ttu-id="90cae-357">フォールバックのたびに、プライベート変数 `count` は返される残りの文字数を示し、プライベート変数 `index` は次に返される文字の文字列バッファー内 (`charsToReturn` 内) の位置を示します。</span><span class="sxs-lookup"><span data-stu-id="90cae-357">For each fallback, the private `count` variable indicates the number of characters that remain to be returned, and the private `index` variable indicates the position in the string buffer, `charsToReturn`, of the next character to return.</span></span> 

```csharp
public class CustomMapperFallbackBuffer : EncoderFallbackBuffer
{
   int count = -1;                   // Number of characters to return
   int index = -1;                   // Index of character to return
   CustomMapper fb; 
   string charsToReturn; 

   public CustomMapperFallbackBuffer(CustomMapper fallback)
   {
      this.fb = fallback;
   }

   public override bool Fallback(char charUnknownHigh, char charUnknownLow, int index)
   {
      // Do not try to map surrogates to ASCII.
      return false;
   }

   public override bool Fallback(char charUnknown, int index)
   {
      // Return false if there are already characters to map.
      if (count >= 1) return false;

      // Determine number of characters to return.
      charsToReturn = String.Empty;

      ushort key = Convert.ToUInt16(charUnknown);
      if (fb.mapping.ContainsKey(key)) {
         byte[] bytes = BitConverter.GetBytes(fb.mapping[key]);
         int ctr = 0;
         foreach (var byt in bytes) {
            if (byt > 0) {
               ctr++;
               charsToReturn += (char) byt;
            }
         }
         count = ctr;
      }
      else {
         // Return default.
         charsToReturn = fb.DefaultString;
         count = 1;
      }
      this.index = charsToReturn.Length - 1;

      return true;
   }

   public override char GetNextChar()
   {
      // We'll return a character if possible, so subtract from the count of chars to return.
      count--;
      // If count is less than zero, we've returned all characters.
      if (count < 0) 
         return '\u0000';

      this.index--;
      return charsToReturn[this.index + 1];
   }

   public override bool MovePrevious()
   {
      // Original: if count >= -1 and pos >= 0
      if (count >= -1) {
         count++;
         return true;
      }
      else {
         return false;
      }
   }

   public override int Remaining 
   {
      get { return count < 0 ? 0 : count; }
   }

   public override void Reset()
   {
      count = -1;
      index = -1;
   }
}
```

```vb
Public Class CustomMapperFallbackBuffer : Inherits EncoderFallbackBuffer

   Dim count As Integer = -1        ' Number of characters to return
   Dim index As Integer = -1        ' Index of character to return
   Dim fb As CustomMapper
   Dim charsToReturn As String

   Public Sub New(ByVal fallback As CustomMapper)
      MyBase.New()
      Me.fb = fallback
   End Sub

   Public Overloads Overrides Function Fallback(ByVal charUnknownHigh As Char, ByVal charUnknownLow As Char, ByVal index As Integer) As Boolean
      ' Do not try to map surrogates to ASCII.
      Return False
   End Function

   Public Overloads Overrides Function Fallback(ByVal charUnknown As Char, ByVal index As Integer) As Boolean
      ' Return false if there are already characters to map.
      If count >= 1 Then Return False

      ' Determine number of characters to return.
      charsToReturn = String.Empty

      Dim key As UShort = Convert.ToUInt16(charUnknown)
      If fb.mapping.ContainsKey(key) Then
         Dim bytes() As Byte = BitConverter.GetBytes(fb.mapping.Item(key))
         Dim ctr As Integer
         For Each byt In bytes
            If byt > 0 Then
               ctr += 1
               charsToReturn += Chr(byt)
            End If
         Next
         count = ctr
      Else
         ' Return default.
         charsToReturn = fb.DefaultString
         count = 1
      End If
      Me.index = charsToReturn.Length - 1

      Return True
   End Function

   Public Overrides Function GetNextChar() As Char
      ' We'll return a character if possible, so subtract from the count of chars to return.
      count -= 1
      ' If count is less than zero, we've returned all characters.
      If count < 0 Then Return ChrW(0)

      Me.index -= 1
      Return charsToReturn(Me.index + 1)
   End Function

   Public Overrides Function MovePrevious() As Boolean
      ' Original: if count >= -1 and pos >= 0
      If count >= -1 Then
         count += 1
         Return True
      Else
         Return False
      End If
   End Function

   Public Overrides ReadOnly Property Remaining As Integer
      Get
         Return If(count < 0, 0, count)
      End Get
   End Property

   Public Overrides Sub Reset()
      count = -1
      index = -1
   End Sub
End Class
```

<span data-ttu-id="90cae-358">次のコードでは、`CustomMapper` オブジェクトをインスタンス化して、そのインスタンスを [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) メソッドに渡しています。</span><span class="sxs-lookup"><span data-stu-id="90cae-358">The following code then instantiates the `CustomMapper` object and passes an instance of it to the [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) method.</span></span> <span data-ttu-id="90cae-359">出力を見るとわかるように、この最適フォールバックの実装では、元の文字列の&3; つの非 ASCII 文字が正しく処理されます。</span><span class="sxs-lookup"><span data-stu-id="90cae-359">The output indicates that the best-fit fallback implementation successfully handles the three non-ASCII characters in the original string.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Text;

class Program
{
   static void Main()
   {
      Encoding enc = Encoding.GetEncoding("us-ascii", new CustomMapper(), new DecoderExceptionFallback());

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      for (int ctr = 0; ctr <= str1.Length - 1; ctr++) {
         Console.Write("{0} ", Convert.ToUInt16(str1[ctr]).ToString("X4"));
         if (ctr == str1.Length - 1) 
            Console.WriteLine();
      }
      Console.WriteLine();

      // Encode the original string using the ASCII encoder.
      byte[] bytes = enc.GetBytes(str1);
      Console.Write("Encoded bytes: ");
      foreach (var byt in bytes)
         Console.Write("{0:X2} ", byt);

      Console.WriteLine("\n");

      // Decode the ASCII bytes.
      string str2 = enc.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      }
   }
}
```

```vb
Imports System.Text
Imports System.Collections.Generic

Module Module1

   Sub Main()
      Dim enc As Encoding = Encoding.GetEncoding("us-ascii", New CustomMapper(), New DecoderExceptionFallback())

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&H24C8), ChrW(&H2075), ChrW(&H221E))
      Console.WriteLine(str1)
      For ctr As Integer = 0 To str1.Length - 1
         Console.Write("{0} ", Convert.ToUInt16(str1(ctr)).ToString("X4"))
         If ctr = str1.Length - 1 Then Console.WriteLine()
      Next
      Console.WriteLine()

      ' Encode the original string using the ASCII encoder.
      Dim bytes() As Byte = enc.GetBytes(str1)
      Console.Write("Encoded bytes: ")
      For Each byt In bytes
         Console.Write("{0:X2} ", byt)
      Next
      Console.WriteLine()
      Console.WriteLine()

      ' Decode the ASCII bytes.
      Dim str2 As String = enc.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
         Console.WriteLine()
      End If
   End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="90cae-360">関連項目</span><span class="sxs-lookup"><span data-stu-id="90cae-360">See also</span></span>

[<span data-ttu-id="90cae-361">System.Text.Encoder</span><span class="sxs-lookup"><span data-stu-id="90cae-361">System.Text.Encoder</span></span>](xref:System.Text.Encoder)

[<span data-ttu-id="90cae-362">System.Text.EncoderFallback</span><span class="sxs-lookup"><span data-stu-id="90cae-362">System.Text.EncoderFallback</span></span>](xref:System.Text.EncoderFallback)

[<span data-ttu-id="90cae-363">System.Text.Decoder</span><span class="sxs-lookup"><span data-stu-id="90cae-363">System.Text.Decoder</span></span>](xref:System.Text.Decoder)

[<span data-ttu-id="90cae-364">System.Text.DecoderFallback</span><span class="sxs-lookup"><span data-stu-id="90cae-364">System.Text.DecoderFallback</span></span>](xref:System.Text.DecoderFallback)

[<span data-ttu-id="90cae-365">System.Text.Encoding</span><span class="sxs-lookup"><span data-stu-id="90cae-365">System.Text.Encoding</span></span>](xref:System.Text.Encoding)





