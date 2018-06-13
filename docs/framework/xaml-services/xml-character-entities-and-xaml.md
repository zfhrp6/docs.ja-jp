---
title: XML 文字エンティティと XAML
ms.date: 03/30/2017
f1_keywords:
- '&'
- '&amp'
- '&gt'
- '&lt'
helpviewer_keywords:
- XAML [XAML Services], special characters
- ampersand (&) [XAML Services]
- special characters [XAML Services]
- apostrophe (') [XAML Services]
- greater-than (>) character [XAML Services]
- XAML [XAML Services], quotation mark (")
- XAML [XAML Services], apostrophe (')
- '& (ampersand) [XAML Services]'
- XAML [XAML Services], & (ampersand)
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- less-than (<) character [XAML Services]
ms.assetid: 6896d0ce-74f7-420a-9ab4-de9bbf390e8d
ms.openlocfilehash: 5ef489498cdc8716f7599124138f9ecf8945ac9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564769"
---
# <a name="xml-character-entities-and-xaml"></a><span data-ttu-id="7418a-102">XML 文字エンティティと XAML</span><span class="sxs-lookup"><span data-stu-id="7418a-102">XML Character Entities and XAML</span></span>
<span data-ttu-id="7418a-103">XAML は、特殊文字に、XML で定義される文字エンティティを使用します。</span><span class="sxs-lookup"><span data-stu-id="7418a-103">XAML uses character entities defined in XML for special characters.</span></span> <span data-ttu-id="7418a-104">ここでは、いくつかの特定の文字エンティティ、および XAML における他の XML の概念に関する一般的な考慮事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="7418a-104">This topic describes some specific character entities and general considerations for other XML concepts in XAML.</span></span>  
  
<a name="character_entities_and_escaping_issues_that_are_unique_to_xaml"></a>   
## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a><span data-ttu-id="7418a-105">XAML に固有の文字のエンティティとエスケープの問題</span><span class="sxs-lookup"><span data-stu-id="7418a-105">Character Entities and Escaping Issues That Are Unique to XAML</span></span>  
 <span data-ttu-id="7418a-106">XAML マークアップでは、一般に、XML で定義されているものと同じ文字エンティティおよびエスケープ シーケンスを使用します。</span><span class="sxs-lookup"><span data-stu-id="7418a-106">XAML markup typically uses the same character entities and escape sequences that are defined in XML.</span></span>  
  
 <span data-ttu-id="7418a-107">大きな違いは、XAML では中かっこ ({ と }) が意味を持つ点です。中かっこで囲まれた文字シーケンスは、マークアップ拡張機能として解釈する必要があることを XAML プロセッサに通知します。</span><span class="sxs-lookup"><span data-stu-id="7418a-107">The main exception is that braces ({ and }) have significance in XAML because these characters inform a XAML processor that a character sequence enclosed by braces must be interpreted as a markup extension.</span></span> <span data-ttu-id="7418a-108">マークアップ拡張機能について詳しくは、「 [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7418a-108">For more information about markup extensions, see [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).</span></span>  
  
 <span data-ttu-id="7418a-109">ただし、XML ではなく XAML に固有のエスケープ シーケンスを使用すると、中かっこをリテラル文字として表示できます。</span><span class="sxs-lookup"><span data-stu-id="7418a-109">However, you can still display the braces as literal characters by using an escape sequence that is particular to XAML instead of XML.</span></span> <span data-ttu-id="7418a-110">詳細については、次を参照してください。 [ {}エスケープ シーケンスのマークアップ拡張機能](escape-sequence-markup-extension.md)します。</span><span class="sxs-lookup"><span data-stu-id="7418a-110">For more information, see [{} Escape Sequence - Markup Extension](escape-sequence-markup-extension.md).</span></span>  
  
 <span data-ttu-id="7418a-111">なお、円記号 (\\) が必要としない、エスケープ シーケンスを文字列として処理されます。</span><span class="sxs-lookup"><span data-stu-id="7418a-111">Note that a backslash (\\) does not require an escape sequence when it is handled as a string.</span></span>  
  
<a name="xml_character_entities"></a>   
## <a name="xml-character-entities"></a><span data-ttu-id="7418a-112">XML 文字エンティティ</span><span class="sxs-lookup"><span data-stu-id="7418a-112">XML Character Entities</span></span>  
 <span data-ttu-id="7418a-113">前に述べたように、XAML マークアップを記述するときに一般的に使用する文字エンティティおよびエスケープ シーケンスの大半は、XML で定義されています。</span><span class="sxs-lookup"><span data-stu-id="7418a-113">As mentioned previously, most character entities and escape sequences that are typically used to write XAML markup are defined by XML.</span></span> <span data-ttu-id="7418a-114">このトピックでは、こうしたエンティティの一覧は示しません。エンティティの詳細なリファレンスについては、XML 仕様などの外部ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7418a-114">This topic does not provide the complete list of these entities; a detailed reference for the entities can be found in external documentation, such as in XML specifications.</span></span> <span data-ttu-id="7418a-115">ただし、このトピックでは、便宜を考えて、XAML マークアップでよく使用する XML 文字エンティティを抜粋した一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="7418a-115">However, for convenience, this topic lists some of the specific XML character entities that are typically used in XAML markup.</span></span>  
  
|<span data-ttu-id="7418a-116">文字</span><span class="sxs-lookup"><span data-stu-id="7418a-116">Character</span></span>|<span data-ttu-id="7418a-117">エンティティ</span><span class="sxs-lookup"><span data-stu-id="7418a-117">Entity</span></span>|<span data-ttu-id="7418a-118">メモ</span><span class="sxs-lookup"><span data-stu-id="7418a-118">Notes</span></span>|  
|---------------|------------|-----------|  
|<span data-ttu-id="7418a-119">& (アンパサンド)</span><span class="sxs-lookup"><span data-stu-id="7418a-119">& (ampersand)</span></span>|<span data-ttu-id="7418a-120">\&amp;</span><span class="sxs-lookup"><span data-stu-id="7418a-120">\&amp;</span></span>|<span data-ttu-id="7418a-121">属性値および要素の内容の両方に対して使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7418a-121">Must be used both for attribute values and for content of an element.</span></span>|  
|<span data-ttu-id="7418a-122">> (大なり記号)</span><span class="sxs-lookup"><span data-stu-id="7418a-122">> (greater-than character)</span></span>|<span data-ttu-id="7418a-123">\&gt;</span><span class="sxs-lookup"><span data-stu-id="7418a-123">\&gt;</span></span>|<span data-ttu-id="7418a-124">属性値に対しては使用する必要があります。要素の内容に対しては、前に < がない限りは、> を使用できます。</span><span class="sxs-lookup"><span data-stu-id="7418a-124">Must be used for an attribute value, but > is acceptable as the content of an element as long as < does not precede it.</span></span>|  
|<span data-ttu-id="7418a-125">< (小なり記号)</span><span class="sxs-lookup"><span data-stu-id="7418a-125">< (less-than character)</span></span>|<span data-ttu-id="7418a-126">\&lt;</span><span class="sxs-lookup"><span data-stu-id="7418a-126">\&lt;</span></span>|<span data-ttu-id="7418a-127">属性値に対して使用する必要がありますが、\<が同じくらい要素のコンテンツとして許容される > それに従っていません。</span><span class="sxs-lookup"><span data-stu-id="7418a-127">Must be used for an attribute value, but \< is acceptable as the content of an element as long as > does not follow it.</span></span>|  
|<span data-ttu-id="7418a-128">" (二重引用符)</span><span class="sxs-lookup"><span data-stu-id="7418a-128">" (straight quotation mark)</span></span>|<span data-ttu-id="7418a-129">\&quot;</span><span class="sxs-lookup"><span data-stu-id="7418a-129">\&quot;</span></span>|<span data-ttu-id="7418a-130">属性値に対しては使用する必要があります。要素の内容としては、二重引用符 (") も受け入れられます、</span><span class="sxs-lookup"><span data-stu-id="7418a-130">Must be used for an attribute value, but a straight quotation mark (") is acceptable as the content of an element.</span></span> <span data-ttu-id="7418a-131">属性値は、単一引用符 (') と二重引用符 (") のどちらかで囲むことができます。最初に使用したほうの引用符が、属性値を囲む文字になり、もう一方の引用符は値の中でリテラルとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="7418a-131">Note that attribute values may be enclosed either by a single straight quotation mark (') or by a straight quotation mark ("); whichever character appears first defines the attribute value enclosure, and the alternative quote can then be used as a literal within the value.</span></span>|  
|<span data-ttu-id="7418a-132">' (単一引用符)</span><span class="sxs-lookup"><span data-stu-id="7418a-132">' (single straight quotation mark)</span></span>|<span data-ttu-id="7418a-133">\&apos;</span><span class="sxs-lookup"><span data-stu-id="7418a-133">\&apos;</span></span>|<span data-ttu-id="7418a-134">属性値に対しては使用する必要があります。要素の内容としては、単一引用符 (') も受け入れられます、</span><span class="sxs-lookup"><span data-stu-id="7418a-134">Must be used for an attribute value, but a single straight quotation mark (') is acceptable as the content of an element.</span></span> <span data-ttu-id="7418a-135">属性値は、単一引用符 (') と二重引用符 (") のどちらかで囲むことができます。最初に使用したほうの引用符が、属性値を囲む文字になり、もう一方の引用符は値の中でリテラルとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="7418a-135">Note that attribute values may be enclosed either by a single straight quotation mark (') or by a straight quotation mark ("); whichever character appears first defines the attribute value enclosure, and the alternative quote can then be used as a literal within the value.</span></span>|  
|<span data-ttu-id="7418a-136">(数値と文字の対応付け)</span><span class="sxs-lookup"><span data-stu-id="7418a-136">(numeric character mappings)</span></span>|<span data-ttu-id="7418a-137">&#*[整数]*; または & #x *[16 進数]* です。</span><span class="sxs-lookup"><span data-stu-id="7418a-137">&#*[integer]*; or &#x *[hex]*;</span></span>|<span data-ttu-id="7418a-138">XAML では、アクティブなエンコーディングに応じた数値と文字の対応付けがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="7418a-138">XAML supports numeric character mappings into the encoding that is active.</span></span>|  
|<span data-ttu-id="7418a-139">(改行しないスペース)</span><span class="sxs-lookup"><span data-stu-id="7418a-139">(nonbreaking space)</span></span>|<span data-ttu-id="7418a-140">&\#160;(utf-8 エンコードを想定)</span><span class="sxs-lookup"><span data-stu-id="7418a-140">&\#160; (assuming UTF-8 encoding)</span></span>|<span data-ttu-id="7418a-141">フロー ドキュメントの要素、または WPF の <xref:System.Windows.Controls.TextBox> などのテキストを受け取る要素では、マークアップからの改行しないスペースの正規化は行われません。これには、`xml:space="default"` の場合も含まれます。</span><span class="sxs-lookup"><span data-stu-id="7418a-141">For flow document elements, or elements that take text such as the WPF <xref:System.Windows.Controls.TextBox>, nonbreaking spaces are not normalized out of the markup, even for `xml:space="default"`.</span></span> <span data-ttu-id="7418a-142">(詳細については、次を参照してください[XAML での空白の処理](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)。)。</span><span class="sxs-lookup"><span data-stu-id="7418a-142">(For more information, see [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).)</span></span>|  
  
<a name="xml_comment_format"></a>   
## <a name="xml-comment-format"></a><span data-ttu-id="7418a-143">XML のコメントの書式</span><span class="sxs-lookup"><span data-stu-id="7418a-143">XML Comment Format</span></span>  
 <span data-ttu-id="7418a-144">XAML では、XML のコメントの書式を使用します。つまり、コメントの先頭は `<!--` で表し、コメントの末尾は `-->,` で表します。コメントの中に `--` というシーケンスを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="7418a-144">XAML uses the XML comment format: the start of the comment is `<!--`, the end of comment is `-->,` and the sequence `--` must not occur within the comment.</span></span>  
  
<a name="xml_processing_instructions"></a>   
## <a name="xml-processing-instructions"></a><span data-ttu-id="7418a-145">XML 処理命令</span><span class="sxs-lookup"><span data-stu-id="7418a-145">XML Processing Instructions</span></span>  
 <span data-ttu-id="7418a-146">XAML では、XML 仕様に従って XML 処理命令が処理されます。つまり、命令は必ず素通しされます。</span><span class="sxs-lookup"><span data-stu-id="7418a-146">XAML handles XML processing instructions according to XML specifications, which state that the instructions must be passed through.</span></span> <span data-ttu-id="7418a-147">.NET Framework XAML サービスで XAML 処理では、処理命令は使用しません。</span><span class="sxs-lookup"><span data-stu-id="7418a-147">XAML processing in .NET Framework XAML Services  does not use any processing instructions.</span></span> <span data-ttu-id="7418a-148">XAML を使用する他の既存のフレームワークでも、XAML の処理命令は使用されません。</span><span class="sxs-lookup"><span data-stu-id="7418a-148">Other existing frameworks that use XAML also do not use processing instructions from XAML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7418a-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="7418a-149">See Also</span></span>  
 [<span data-ttu-id="7418a-150">XAML の概要 (WPF)</span><span class="sxs-lookup"><span data-stu-id="7418a-150">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="7418a-151">マークアップ拡張機能と WPF XAML</span><span class="sxs-lookup"><span data-stu-id="7418a-151">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="7418a-152">XamlName の文法</span><span class="sxs-lookup"><span data-stu-id="7418a-152">XamlName Grammar</span></span>](../../../docs/framework/xaml-services/xamlname-grammar.md)  
 [<span data-ttu-id="7418a-153">XAML での空白の処理</span><span class="sxs-lookup"><span data-stu-id="7418a-153">Whitespace Processing in XAML</span></span>](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)
