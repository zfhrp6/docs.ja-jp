---
title: WPF のグローバリゼーション
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-wpf
ms.topic: article
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e6f39d40284e6212715d85fece545e653ff2e60a
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2018
---
# <a name="globalization-for-wpf"></a><span data-ttu-id="1f8e2-102">WPF のグローバリゼーション</span><span class="sxs-lookup"><span data-stu-id="1f8e2-102">Globalization for WPF</span></span>
<span data-ttu-id="1f8e2-103">このトピックの内容を記述する際に注意する必要がありますのある問題が導入されています[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]グローバル市場向けアプリケーション。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-103">This topic introduces issues that you should be aware of when writing [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications for the global market.</span></span> <span data-ttu-id="1f8e2-104">グローバリゼーションのプログラミング要素がで定義されている[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)]で`System.Globalization`です。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-104">The globalization programming elements are defined in [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] in `System.Globalization`.</span></span>  
  

  
<a name="xaml_globalization"></a>   
## <a name="xaml-globalization"></a><span data-ttu-id="1f8e2-105">XAML グローバリゼーション</span><span class="sxs-lookup"><span data-stu-id="1f8e2-105">XAML Globalization</span></span>  
 [!INCLUDE[TLA#tla_xaml#initcap](../../../../includes/tlasharptla-xamlsharpinitcap-md.md)]<span data-ttu-id="1f8e2-106"> 基づく[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]で定義されているグローバル化のサポートを利用して、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]仕様です。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-106"> is based on [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] and takes advantage of the globalization support defined in the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] specification.</span></span> <span data-ttu-id="1f8e2-107">次のセクションでは、いくつか説明[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]機能を認識しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-107">The following sections describe some [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] features that you should be aware of.</span></span>  
  
<a name="char_reference"></a>   
### <a name="character-references"></a><span data-ttu-id="1f8e2-108">文字参照</span><span class="sxs-lookup"><span data-stu-id="1f8e2-108">Character References</span></span>  
<span data-ttu-id="1f8e2-109">文字参照は、特定の UTF16 コード単位[!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)]文字、10 進数または 16 進数のいずれか。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-109">A character reference gives the UTF16 code unit of the particular [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] character it represents, in either decimal or hexadecimal.</span></span> <span data-ttu-id="1f8e2-110">次の例では、コプト語 CAPITAL LETTER 作成、または 'Ϩ' の参照を 10 進数の文字を示しています。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-110">The following example shows a decimal character reference for the COPTIC CAPITAL LETTER HORI, or 'Ϩ':</span></span>

```
&#1000;
```

<span data-ttu-id="1f8e2-111">次の例では、16 進文字の参照を示します。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-111">The following example shows a hexadecimal character reference.</span></span> <span data-ttu-id="1f8e2-112">持つことに注意してください、 **x** 16 進数の前にします。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-112">Notice that it has an **x** in front of the hexadecimal number.</span></span>

```
&#x3E8;
```

<a name="encoding"></a>   
### <a name="encoding"></a><span data-ttu-id="1f8e2-113">エンコード</span><span class="sxs-lookup"><span data-stu-id="1f8e2-113">Encoding</span></span>  
 <span data-ttu-id="1f8e2-114">サポートされているエンコード[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]は[!INCLUDE[TLA#tla_ascii](../../../../includes/tlasharptla-ascii-md.md)]、 [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] utf-16、および utf-8 です。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-114">The encoding supported by [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] are [!INCLUDE[TLA#tla_ascii](../../../../includes/tlasharptla-ascii-md.md)], [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] UTF-16, and UTF-8.</span></span> <span data-ttu-id="1f8e2-115">先頭には、エンコード ステートメント[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ドキュメント。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-115">The encoding statement is at the beginning of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] document.</span></span> <span data-ttu-id="1f8e2-116">エンコーディング属性が存在せず、バイト順もない場合、パーサーでは既定として UTF-8 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-116">If no encoding attribute exists and there is no byte-order, the parser defaults to UTF-8.</span></span> <span data-ttu-id="1f8e2-117">UTF-8 と UTF-16 は優先エンコードです。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-117">UTF-8 and UTF-16 are the preferred encodings.</span></span> <span data-ttu-id="1f8e2-118">UTF-7 には対応していません。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-118">UTF-7 is not supported.</span></span> <span data-ttu-id="1f8e2-119">次の例での utf-8 エンコードを指定する方法を示します、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイル。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-119">The following example demonstrates how to specify a UTF-8 encoding in a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file.</span></span>  
  
```  
?xml encoding="UTF-8"?  
```  
  
<a name="lang_attrib"></a>   
### <a name="language-attribute"></a><span data-ttu-id="1f8e2-120">言語属性</span><span class="sxs-lookup"><span data-stu-id="1f8e2-120">Language Attribute</span></span>  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]<span data-ttu-id="1f8e2-121"> 使用して[xml:lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md)を要素の language 属性を表します。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-121"> uses [xml:lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) to represent the language attribute of an element.</span></span>  <span data-ttu-id="1f8e2-122">活用するために、<xref:System.Globalization.CultureInfo>クラス、言語属性値がによって定義済みカルチャ名のいずれかを指定する必要があります<xref:System.Globalization.CultureInfo>です。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-122">To take advantage of the <xref:System.Globalization.CultureInfo> class, the language attribute value needs to be one of the culture names predefined by <xref:System.Globalization.CultureInfo>.</span></span> <span data-ttu-id="1f8e2-123">[xml:lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) は要素ツリーで継承可能であり (XML ルールによる継承であり、必ずしも依存関係プロパティの継承によるものではありません)、その既定値は、明示的に割り当てられていない場合、空の文字列になります。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-123">[xml:lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) is inheritable in the element tree (by XML rules, not necessarily because of dependency property inheritance) and its default value is an empty string if it is not assigned explicitly.</span></span>  
  
 <span data-ttu-id="1f8e2-124">言語属性は、方言を指定するときに非常に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-124">The language attribute is very useful for specifying dialects.</span></span> <span data-ttu-id="1f8e2-125">たとえば、フランス語であれば、フランス、ケベック、ベルギー、スイスでスペル、語彙、発音が異なります。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-125">For example, French has different spelling, vocabulary, and pronunciation in France, Quebec, Belgium, and Switzerland.</span></span> <span data-ttu-id="1f8e2-126">中国語、日本語、および韓国語での内のコード ポイントの共有も[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]が表意文字の形状が異なると、まったく異なるフォントを使用します。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-126">Also Chinese, Japanese, and Korean share code points in [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], but the ideographic shapes are different and they use totally different fonts.</span></span>  
  
 <span data-ttu-id="1f8e2-127">次[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]の例では、`fr-CA`カナダ フランス語を指定する言語の属性です。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-127">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example uses the `fr-CA` language attribute to specify Canadian French.</span></span>  
  
```xml  
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>  
```  
  
<a name="unicode"></a>   
### <a name="unicode"></a><span data-ttu-id="1f8e2-128">Unicode</span><span class="sxs-lookup"><span data-stu-id="1f8e2-128">Unicode</span></span>  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]<span data-ttu-id="1f8e2-129"> すべてをサポートしている[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]サロゲートを含む機能します。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-129"> supports all [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] features including surrogates.</span></span> <span data-ttu-id="1f8e2-130">文字セットにマップできる限り[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]はサポートされています。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-130">As long as the character set can be mapped to [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], it is supported.</span></span> <span data-ttu-id="1f8e2-131">たとえば、GB18030 では、一部の文字が中国語、日本語、韓国語 (CFK) の拡張 A および B とサロゲート ペアにマッピングされているため、完全に対応しています。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-131">For example, GB18030 introduces some characters that are mapped to the Chinese, Japanese, and Korean (CFK) extension A and B and surrogate pairs, therefore it is fully supported.</span></span> <span data-ttu-id="1f8e2-132">A[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションを使用できる<xref:System.Globalization.StringInfo>サロゲート ペアがあるかどうかを理解することや、組み合わせ文字なし文字列を操作します。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-132">A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application can use <xref:System.Globalization.StringInfo> to manipulate strings without understanding whether they have surrogate pairs or combining characters.</span></span>  
  
<a name="design_intl_ui_with_xaml"></a>   
## <a name="designing-an-international-user-interface-with-xaml"></a><span data-ttu-id="1f8e2-133">XAML で各国対応ユーザー インターフェイスを設計する</span><span class="sxs-lookup"><span data-stu-id="1f8e2-133">Designing an International User Interface with XAML</span></span>  
 <span data-ttu-id="1f8e2-134">このセクションで説明[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]機能アプリケーションを作成するときに考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-134">This section describes [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] features that you should consider when writing an application.</span></span>  
  
<a name="intl_text"></a>   
### <a name="international-text"></a><span data-ttu-id="1f8e2-135">国際対応テキスト</span><span class="sxs-lookup"><span data-stu-id="1f8e2-135">International Text</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="1f8e2-136"> すべての組み込みの処理が含まれます[!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)]書記体系をサポートします。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-136"> includes built-in processing for all [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] supported writing systems.</span></span>  
  
 <span data-ttu-id="1f8e2-137">現在、次の書体がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-137">The following scripts are currently supported:</span></span>  
  
-   <span data-ttu-id="1f8e2-138">アラビア語</span><span class="sxs-lookup"><span data-stu-id="1f8e2-138">Arabic</span></span>  
  
-   <span data-ttu-id="1f8e2-139">ベンガル語</span><span class="sxs-lookup"><span data-stu-id="1f8e2-139">Bengali</span></span>  
  
-   <span data-ttu-id="1f8e2-140">デバナガリ</span><span class="sxs-lookup"><span data-stu-id="1f8e2-140">Devanagari</span></span>  
  
-   <span data-ttu-id="1f8e2-141">キリル言語</span><span class="sxs-lookup"><span data-stu-id="1f8e2-141">Cyrillic</span></span>  
  
-   <span data-ttu-id="1f8e2-142">ギリシャ語</span><span class="sxs-lookup"><span data-stu-id="1f8e2-142">Greek</span></span>  
  
-   <span data-ttu-id="1f8e2-143">グジャラート語</span><span class="sxs-lookup"><span data-stu-id="1f8e2-143">Gujarati</span></span>  
  
-   <span data-ttu-id="1f8e2-144">グルムキー</span><span class="sxs-lookup"><span data-stu-id="1f8e2-144">Gurmukhi</span></span>  
  
-   <span data-ttu-id="1f8e2-145">ヘブライ語</span><span class="sxs-lookup"><span data-stu-id="1f8e2-145">Hebrew</span></span>  
  
-   <span data-ttu-id="1f8e2-146">表意文字スクリプト</span><span class="sxs-lookup"><span data-stu-id="1f8e2-146">Ideographic scripts</span></span>  
  
-   <span data-ttu-id="1f8e2-147">カナラ語</span><span class="sxs-lookup"><span data-stu-id="1f8e2-147">Kannada</span></span>  
  
-   <span data-ttu-id="1f8e2-148">ラオス語</span><span class="sxs-lookup"><span data-stu-id="1f8e2-148">Lao</span></span>  
  
-   <span data-ttu-id="1f8e2-149">ラテン語</span><span class="sxs-lookup"><span data-stu-id="1f8e2-149">Latin</span></span>  
  
-   <span data-ttu-id="1f8e2-150">マラヤーラム語</span><span class="sxs-lookup"><span data-stu-id="1f8e2-150">Malayalam</span></span>  
  
-   <span data-ttu-id="1f8e2-151">モンゴル語</span><span class="sxs-lookup"><span data-stu-id="1f8e2-151">Mongolian</span></span>  
  
-   <span data-ttu-id="1f8e2-152">オディア語</span><span class="sxs-lookup"><span data-stu-id="1f8e2-152">Odia</span></span>  
  
-   <span data-ttu-id="1f8e2-153">シリア語</span><span class="sxs-lookup"><span data-stu-id="1f8e2-153">Syriac</span></span>  
  
-   <span data-ttu-id="1f8e2-154">タミール語</span><span class="sxs-lookup"><span data-stu-id="1f8e2-154">Tamil</span></span>  
  
-   <span data-ttu-id="1f8e2-155">テルグ語</span><span class="sxs-lookup"><span data-stu-id="1f8e2-155">Telugu</span></span>  
  
-   <span data-ttu-id="1f8e2-156">ターナ</span><span class="sxs-lookup"><span data-stu-id="1f8e2-156">Thaana</span></span>  
  
-   <span data-ttu-id="1f8e2-157">タイ語\*</span><span class="sxs-lookup"><span data-stu-id="1f8e2-157">Thai\*</span></span>  
  
-   <span data-ttu-id="1f8e2-158">チベット語</span><span class="sxs-lookup"><span data-stu-id="1f8e2-158">Tibetan</span></span>  
  
 <span data-ttu-id="1f8e2-159">\* このリリースでは、タイ語テキストを表示し、編集できますが、単語を分割することはできません。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-159">\*In this release the display and editing of Thai text is supported; word breaking is not.</span></span>  
  
 <span data-ttu-id="1f8e2-160">現在、次のスクリプトはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-160">The following scripts are not currently supported:</span></span>  
  
-   <span data-ttu-id="1f8e2-161">クメール語</span><span class="sxs-lookup"><span data-stu-id="1f8e2-161">Khmer</span></span>  
  
-   <span data-ttu-id="1f8e2-162">韓国語の古いハングル</span><span class="sxs-lookup"><span data-stu-id="1f8e2-162">Korean Old Hangul</span></span>  
  
-   <span data-ttu-id="1f8e2-163">ミャンマー</span><span class="sxs-lookup"><span data-stu-id="1f8e2-163">Myanmar</span></span>  
  
-   <span data-ttu-id="1f8e2-164">シンハラ語</span><span class="sxs-lookup"><span data-stu-id="1f8e2-164">Sinhala</span></span>  
  
 <span data-ttu-id="1f8e2-165">すべての書記体系エンジン サポート[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]フォントです。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-165">All the writing system engines support [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] fonts.</span></span> [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]<span data-ttu-id="1f8e2-166"> フォントを含めることができます、[!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]より国際化とハイエンド傍点を文字のフォントをデザインするフォントの作成者を可能にするテーブルをレイアウトします。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-166"> fonts can include the [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] layout tables that enable font creators to design better international and high-end typographic fonts.</span></span> <span data-ttu-id="1f8e2-167">[!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]フォント レイアウト テーブルに関する情報が含まグリフの置換、グリフ配置、理由、およびベースラインは、次の配置、テキスト レイアウトを向上させるためにテキスト処理アプリケーションを有効にするとします。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-167">The [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] font layout tables contain information about glyph substitutions, glyph positioning, justification, and baseline positioning, enabling text-processing applications to improve text layout.</span></span>  
  
 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]<span data-ttu-id="1f8e2-168"> 大規模なグリフの処理は、設定を使用してフォントを許可する[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]エンコードします。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-168"> fonts allow the handling of large glyph sets using [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] encoding.</span></span> <span data-ttu-id="1f8e2-169">このようなエンコードにより、広範な国際対応が可能になり、さまざまなグリフを印刷できます。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-169">Such encoding enables broad international support as well as for typographic glyph variants.</span></span>  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="1f8e2-170"> テキストのレンダリングが電源に[!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)]解決の独立性をサポートするサブ ピクセル テクノロジです。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-170"> text rendering is powered by [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] sub-pixel technology that supports resolution independence.</span></span> <span data-ttu-id="1f8e2-171">これにより読みやすさが大幅に向上し、あらゆる書体で高品質の雑誌スタイルの書面を作成できます。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-171">This significantly improves legibility and provides the ability to support high quality magazine style documents for all scripts.</span></span>  
  
<a name="intl_layout"></a>   
### <a name="international-layout"></a><span data-ttu-id="1f8e2-172">国際対応レイアウト</span><span class="sxs-lookup"><span data-stu-id="1f8e2-172">International Layout</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="1f8e2-173"> では非常に便利な方法で横書きレイアウト、双方向レイアウト、縦書きレイアウトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-173"> provides a very convenient way to support horizontal, bidirectional, and vertical layouts.</span></span> <span data-ttu-id="1f8e2-174">プレゼンテーション フレームワークで、<xref:System.Windows.FrameworkElement.FlowDirection%2A>レイアウトを定義するプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-174">In presentation framework the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property can be used to define layout.</span></span> <span data-ttu-id="1f8e2-175">フローの方向パターン:</span><span class="sxs-lookup"><span data-stu-id="1f8e2-175">The flow direction patterns are:</span></span>  
  
-   <span data-ttu-id="1f8e2-176">*LeftToRight* - ラテン語や東アジア言語などのための横書きレイアウト。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-176">*LeftToRight* - horizontal layout for Latin, East Asian and so forth.</span></span>  
  
-   <span data-ttu-id="1f8e2-177">*RightToLeft* - アラビア語やヘブライ語などのための双方向レイアウト。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-177">*RightToLeft* - bidirectional for Arabic, Hebrew and so forth.</span></span>  
  
<a name="developing_localizable_apps"></a>   
## <a name="developing-localizable-applications"></a><span data-ttu-id="1f8e2-178">ローカライズ可能なアプリケーションの開発</span><span class="sxs-lookup"><span data-stu-id="1f8e2-178">Developing Localizable Applications</span></span>  
 <span data-ttu-id="1f8e2-179">世界中で利用されるアプリケーションを開発するときは、アプリケーションをローカライズ可能にすることを忘れてはなりません。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-179">When you write an application for global consumption you should keep in mind that the application must be localizable.</span></span> <span data-ttu-id="1f8e2-180">後続のトピックで、考慮事項を指摘します。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-180">The following topics point out things to consider.</span></span>  
  
<a name="mui"></a>   
### <a name="multilingual-user-interface"></a><span data-ttu-id="1f8e2-181">多言語ユーザー インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1f8e2-181">Multilingual User Interface</span></span>  
 <span data-ttu-id="1f8e2-182">多言語ユーザー インターフェイス (MUI) は、[!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]の切り替えをサポートして[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]を別の 1 つの言語からです。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-182">Multilingual User Interfaces (MUI) is a [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] support for switching [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] from one language to another.</span></span> <span data-ttu-id="1f8e2-183">A[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションでは、アセンブリのモデルを使用して、MUI をサポートします。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-183">A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application uses the assembly model to support MUI.</span></span> <span data-ttu-id="1f8e2-184">1 つのアプリケーションに言語に依存しないアセンブリと言語に依存するサテライト リソース アセンブリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-184">One application contains language-neutral assemblies as well as language-dependent satellite resource assemblies.</span></span> <span data-ttu-id="1f8e2-185">エントリ ポイントはメイン アセンブリのマネージ .EXE です。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-185">The entry point is a managed .EXE in the main assembly.</span></span>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="1f8e2-186"> リソース ローダーを活用、[!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]のリソースの検索とフォールバックをサポートするためにリソース マネージャー。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-186"> resource loader takes advantage of the [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]'s resource manager to support resource lookup and fallback.</span></span> <span data-ttu-id="1f8e2-187">多言語サテライト アセンブリは同じメイン アセンブリと連動します。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-187">Multiple language satellite assemblies work with the same main assembly.</span></span> <span data-ttu-id="1f8e2-188">読み込まれているリソース アセンブリに依存して、<xref:System.Globalization.CultureInfo.CurrentUICulture%2A>現在のスレッド。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-188">The resource assembly that is loaded depends on the <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> of the current thread.</span></span>  
  
<a name="localizable_ui"></a>   
### <a name="localizable-user-interface"></a><span data-ttu-id="1f8e2-189">ローカライズ可能なユーザー インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1f8e2-189">Localizable User Interface</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="1f8e2-190"> アプリケーションを使用して[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を定義する、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-190"> applications use [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] to define their [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span></span> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]<span data-ttu-id="1f8e2-191"> で開発すると、オブジェクトの階層に一連のプロパティとロジックを指定できます。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-191"> allows developers to specify a hierarchy of objects with a set of properties and logic.</span></span> <span data-ttu-id="1f8e2-192">主な用途[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を開発するが[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションが、これを使用して、任意の階層を指定して[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-192">The primary use of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is to develop [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications but it can be used to specify a hierarchy of any [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objects.</span></span> <span data-ttu-id="1f8e2-193">ほとんどの開発者が使用して[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]がアプリケーションの指定に[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]などのプログラミング言語を使用して[!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)]ユーザーとのやり取りに反応するためです。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-193">Most developers use [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] to specify their application's [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] and use a programming language such as [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] to react to user interaction.</span></span>  
  
 <span data-ttu-id="1f8e2-194">リソースの観点から、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルの言語に依存するについて説明するように設計[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]リソースがあり、したがってその最終的な配信形式が国際対応の言語をサポートするためにローカライズできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-194">From a resource point of view, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file designed to describe a language-dependent [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] is a resource element and therefore its final distribution format must be localizable to support international languages.</span></span> <span data-ttu-id="1f8e2-195">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]多くようにイベントが処理できない[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]アプリケーションには、これを行うコードのブロックが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-195">Because [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] cannot handle events many [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] applications contain blocks of code to do this.</span></span> <span data-ttu-id="1f8e2-196">詳細については、次を参照してください。 [XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)です。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-196">For more information, see [XAML Overview (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).</span></span> <span data-ttu-id="1f8e2-197">コードが除去され、異なるバイナリにコンパイル時に、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルは XAML の BAML 形式にトークンです。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-197">Code is stripped out and compiled into different binaries when a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is tokenized into the BAML form of XAML.</span></span> <span data-ttu-id="1f8e2-198">XAML ファイル、画像、その他の種類の管理対象リソース オブジェクトの BAML 形式はサテライト リソース アセンブリに組み込まれます。サテライト リソース アセンブリに組み込むことで、他の言語にローカライズできます。ローカライズが必要なければ、メイン アセンブリに組み込まれます。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-198">The BAML form of XAML files, images, and other types of managed resource objects are embedded in the satellite resource assembly, which can be localized into other languages, or the main assembly when localization is not required.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="1f8e2-199"> すべてのアプリケーションをサポート、 [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)] [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]リソース文字列テーブル、イメージ、およびなどを含むです。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-199"> applications support all the [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)][!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] resources including string tables, images, and so forth.</span></span>  
  
<a name="building_localizable_apps"></a>   
### <a name="building-localizable-applications"></a><span data-ttu-id="1f8e2-200">ローカライズ可能なアプリケーションの構築</span><span class="sxs-lookup"><span data-stu-id="1f8e2-200">Building Localizable Applications</span></span>  
 <span data-ttu-id="1f8e2-201">ローカライズとは、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]を異なるカルチャ。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-201">Localization means to adapt a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to different cultures.</span></span> <span data-ttu-id="1f8e2-202">させる、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションのローカライズ可能な開発者は、すべてのローカライズ可能なリソースをリソース アセンブリに組み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-202">To make a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application localizable, developers need to build all the localizable resources into a resource assembly.</span></span> <span data-ttu-id="1f8e2-203">リソース アセンブリは、異なる言語にローカライズし、分離コードがリソースの管理を使用して[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]を読み込めません。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-203">The resource assembly is localized into different languages, and the code-behind uses resource management [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] to load.</span></span> <span data-ttu-id="1f8e2-204">必要なファイルのいずれか、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションは、プロジェクト ファイル (.proj)。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-204">One of the files required for a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application is a project file (.proj).</span></span> <span data-ttu-id="1f8e2-205">アプリケーションで使用するすべてのリソースをプロジェクト ファイルに含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-205">All resources that you use in your application should be included in the project file.</span></span> <span data-ttu-id="1f8e2-206">その方法を .csproj ファイルからの次の例で示します。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-206">The following example from a .csproj file shows how to do this.</span></span>  
  
```xml  
<Resource Include="data\picture1.jpg"/>  
<EmbeddedResource Include="data\stringtable.en-US.restext"/>  
```  
  
 <span data-ttu-id="1f8e2-207">使用する、アプリケーションでリソースのインスタンスを作成、<xref:System.Resources.ResourceManager>し、使用するリソースを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-207">To use a resource in your application instantiate a <xref:System.Resources.ResourceManager> and load the resource you want to use.</span></span> <span data-ttu-id="1f8e2-208">この方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-208">The following example demonstrates how to do this.</span></span>  
  
 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]  
  
<a name="using_clickonce"></a>   
## <a name="using-clickonce-with-localized-applications"></a><span data-ttu-id="1f8e2-209">ローカライズされたアプリケーションで ClickOnce を使用する</span><span class="sxs-lookup"><span data-stu-id="1f8e2-209">Using ClickOnce with Localized Applications</span></span>  
 <span data-ttu-id="1f8e2-210">ClickOnce は、新しい Windows フォーム展開テクノロジが付属している[!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-210">ClickOnce is a new Windows Forms deployment technology that will ship with [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)].</span></span> <span data-ttu-id="1f8e2-211">アプリケーションをインストールしたり、Web アプリケーションをアップグレードしたりできます。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-211">It enables application installation and upgrading of Web applications.</span></span> <span data-ttu-id="1f8e2-212">ClickOnce で展開されたアプリケーションがローカライズされると、ローカライズされたカルチャでのみ表示できます。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-212">When an application that was deployed with ClickOnce is localized it can only be viewed on the localized culture.</span></span> <span data-ttu-id="1f8e2-213">たとえば、配置済みのアプリケーションが日本語にローカライズされている場合のみ表示する日本語で[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]英語ではなく[!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-213">For example, if a deployed application is localized to Japanese it can only be viewed on Japanese [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] not on English [!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)].</span></span> <span data-ttu-id="1f8e2-214">これは、問題の英語バージョンを実行する日本語のユーザーの一般的なシナリオになっているため[!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-214">This presents a problem because it is a common scenario for Japanese users to run an English version of [!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)].</span></span>  
  
 <span data-ttu-id="1f8e2-215">この問題の解決策は、非依存言語フォールバック属性を設定することです。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-215">The solution to this problem is setting the neutral language fallback attribute.</span></span> <span data-ttu-id="1f8e2-216">アプリケーション開発者はメイン アセンブリからリソースを任意で削除し、特定のカルチャに対応するサテライト アセンブリでそのリソースを見つけられるように指定できます。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-216">An application developer can optionally remove resources from the main assembly and specify that the resources can be found in a satellite assembly corresponding to a specific culture.</span></span> <span data-ttu-id="1f8e2-217">このプロセスで使用するを制御する、<xref:System.Resources.NeutralResourcesLanguageAttribute>です。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-217">To control this process use the <xref:System.Resources.NeutralResourcesLanguageAttribute>.</span></span> <span data-ttu-id="1f8e2-218">コンス トラクター、<xref:System.Resources.NeutralResourcesLanguageAttribute>クラスを受け取る 1 つ、2 つの署名には、<xref:System.Resources.UltimateResourceFallbackLocation>場所を指定するパラメーターを<xref:System.Resources.ResourceManager>フォールバック リソースを抽出する必要があります: メイン アセンブリまたはサテライト アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-218">The constructor of the <xref:System.Resources.NeutralResourcesLanguageAttribute> class has two signatures, one that takes an <xref:System.Resources.UltimateResourceFallbackLocation> parameter to specify the location where the <xref:System.Resources.ResourceManager> should extract the fallback resources: main assembly or satellite assembly.</span></span> <span data-ttu-id="1f8e2-219">この属性を使用する方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-219">The following example shows how to use the attribute.</span></span> <span data-ttu-id="1f8e2-220">コードがによって、最終フォールバック位置の<xref:System.Resources.ResourceManager>"de"ディレクトリのサブディレクトリに、現在実行中のアセンブリのリソースを検索します。</span><span class="sxs-lookup"><span data-stu-id="1f8e2-220">For the ultimate fallback location, the code causes the <xref:System.Resources.ResourceManager> to look for the resources in the "de" subdirectory of the directory of the currently executing assembly.</span></span>  
  
```  
[assembly: NeutralResourcesLanguageAttribute(  
    "de" , UltimateResourceFallbackLocation.Satellite)]  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f8e2-221">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f8e2-221">See Also</span></span>  
 [<span data-ttu-id="1f8e2-222">WPF のグローバリゼーションおよびローカリゼーションの概要</span><span class="sxs-lookup"><span data-stu-id="1f8e2-222">WPF Globalization and Localization Overview</span></span>](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)
