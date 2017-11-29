---
title: "XslCompiledTransform クラスの出力オプション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91ce8cba-386c-411e-bb38-0891a0393c0a
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 61f59c1be3376fb76c91994996840b915cd662ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="output-options-on-the-xslcompiledtransform-class"></a><span data-ttu-id="ae0e6-102">XslCompiledTransform クラスの出力オプション</span><span class="sxs-lookup"><span data-stu-id="ae0e6-102">Output Options on the XslCompiledTransform Class</span></span>
<span data-ttu-id="ae0e6-103">このトピックでは、XSLT で使用できる出力オプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-103">This topic discusses the available XSLT output options.</span></span> <span data-ttu-id="ae0e6-104">出力オプションは、スタイル シート内で、または <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドで指定できます。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-104">You can specify output options in the style sheet, or on the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="xsloutput-element"></a><span data-ttu-id="ae0e6-105">xsl:output 要素</span><span class="sxs-lookup"><span data-stu-id="ae0e6-105">xsl:output Element</span></span>  
 <span data-ttu-id="ae0e6-106">`xsl:output` 要素は出力のオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-106">The `xsl:output` element specifies options for the output.</span></span> <span data-ttu-id="ae0e6-107"><xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドで指定する出力の種類により、`xsl:output` オプションの動作が決定されます。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-107">The output type specified by the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method determines the behavior of the `xsl:output` options.</span></span>  
  
 <span data-ttu-id="ae0e6-108">次の表では、出力の種類がストリームか `xsl:output` の場合に <xref:System.IO.TextWriter> 要素で使用できる各属性の動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-108">The following table describes the behavior for each of the attributes available on the `xsl:output` element when the output type is a stream or a <xref:System.IO.TextWriter>.</span></span>  
  
|<span data-ttu-id="ae0e6-109">属性名</span><span class="sxs-lookup"><span data-stu-id="ae0e6-109">Attribute name</span></span>|<span data-ttu-id="ae0e6-110">動作</span><span class="sxs-lookup"><span data-stu-id="ae0e6-110">Behavior</span></span>|  
|--------------------|--------------|  
|<span data-ttu-id="ae0e6-111">メソッド</span><span class="sxs-lookup"><span data-stu-id="ae0e6-111">method</span></span>|<span data-ttu-id="ae0e6-112">サポートされています。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-112">Supported.</span></span>|  
|<span data-ttu-id="ae0e6-113">version</span><span class="sxs-lookup"><span data-stu-id="ae0e6-113">version</span></span>|<span data-ttu-id="ae0e6-114">無視されます。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-114">Ignored.</span></span> <span data-ttu-id="ae0e6-115">バージョンは常に XML では 1.0、そして HTML では 4.0 です。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-115">The version is always 1.0 for XML and 4.0 for HTML.</span></span>|  
|<span data-ttu-id="ae0e6-116">encoding</span><span class="sxs-lookup"><span data-stu-id="ae0e6-116">encoding</span></span>|<span data-ttu-id="ae0e6-117"><xref:System.IO.TextWriter> への出力時には無視されます。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-117">Ignored when outputting to a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="ae0e6-118"><xref:System.IO.TextWriter.Encoding%2A?displayProperty=nameWithType> プロパティが代わりに使用されます。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-118">The <xref:System.IO.TextWriter.Encoding%2A?displayProperty=nameWithType> property is used instead.</span></span>|  
|<span data-ttu-id="ae0e6-119">omit-xml-declaration</span><span class="sxs-lookup"><span data-stu-id="ae0e6-119">omit-xml-declaration</span></span>|<span data-ttu-id="ae0e6-120">サポートされています。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-120">Supported.</span></span>|  
|<span data-ttu-id="ae0e6-121">スタンドアロン</span><span class="sxs-lookup"><span data-stu-id="ae0e6-121">standalone</span></span>|<span data-ttu-id="ae0e6-122">サポートされています。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-122">Supported.</span></span>|  
|<span data-ttu-id="ae0e6-123">doctype-public</span><span class="sxs-lookup"><span data-stu-id="ae0e6-123">doctype-public</span></span>|<span data-ttu-id="ae0e6-124">サポートされています。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-124">Supported.</span></span>|  
|<span data-ttu-id="ae0e6-125">doctype-system</span><span class="sxs-lookup"><span data-stu-id="ae0e6-125">doctype-system</span></span>|<span data-ttu-id="ae0e6-126">サポートされています。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-126">Supported.</span></span>|  
|<span data-ttu-id="ae0e6-127">cdata-section-elements</span><span class="sxs-lookup"><span data-stu-id="ae0e6-127">cdata-section-elements</span></span>|<span data-ttu-id="ae0e6-128">サポートされています。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-128">Supported.</span></span>|  
|<span data-ttu-id="ae0e6-129">indent</span><span class="sxs-lookup"><span data-stu-id="ae0e6-129">indent</span></span>|<span data-ttu-id="ae0e6-130">サポートされています。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-130">Supported.</span></span>|  
|<span data-ttu-id="ae0e6-131">media-type</span><span class="sxs-lookup"><span data-stu-id="ae0e6-131">media-type</span></span>|<span data-ttu-id="ae0e6-132">サポートされています。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-132">Supported.</span></span>|  
  
#### <a name="sending-output-to-an-xmlwriter"></a><span data-ttu-id="ae0e6-133">XmlWriter への出力の送出</span><span class="sxs-lookup"><span data-stu-id="ae0e6-133">Sending Output to an XmlWriter</span></span>  
 <span data-ttu-id="ae0e6-134">スタイル シートで `xsl:output` 要素が使用され、出力の種類が <xref:System.Xml.XmlWriter> オブジェクトの場合は、<xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> オブジェクトを作成する際に <xref:System.Xml.XmlWriter> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-134">If your style sheet uses the `xsl:output` element and the output type is an <xref:System.Xml.XmlWriter> object, you should use the <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> property when you create the <xref:System.Xml.XmlWriter> object.</span></span> <span data-ttu-id="ae0e6-135"><xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> プロパティは、コンパイル済みスタイル シートの <xref:System.Xml.XmlWriterSettings> 要素から派生した情報を含む `xsl:output` オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-135">The <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> property returns an <xref:System.Xml.XmlWriterSettings> object that contains information derived from the `xsl:output` element of a compiled style sheet.</span></span> <span data-ttu-id="ae0e6-136">この <xref:System.Xml.XmlWriterSettings> オブジェクトを <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> メソッドに渡して、正しい設定の <xref:System.Xml.XmlWriter> オブジェクトを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-136">This <xref:System.Xml.XmlWriterSettings> object can be passed to the <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> method to create an <xref:System.Xml.XmlWriter> object with the correct settings.</span></span>  
  
## <a name="output-types"></a><span data-ttu-id="ae0e6-137">出力の種類</span><span class="sxs-lookup"><span data-stu-id="ae0e6-137">Output Types</span></span>  
 <span data-ttu-id="ae0e6-138">次の一覧では、<xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> コマンドで使用できる出力の種類について説明します。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-138">The following list describes the output types available on the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> command.</span></span>  
  
#### <a name="xmlwriter"></a><span data-ttu-id="ae0e6-139">XmlWriter</span><span class="sxs-lookup"><span data-stu-id="ae0e6-139">XmlWriter</span></span>  
 <span data-ttu-id="ae0e6-140"><xref:System.Xml.XmlWriter> クラスは XML ストリームまたはファイルを書き出します。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-140">The <xref:System.Xml.XmlWriter> class writes out XML streams or files.</span></span> <span data-ttu-id="ae0e6-141"><xref:System.Xml.XmlWriter> クラスを使用して、出力オプションも含め、<xref:System.Xml.XmlWriterSettings> オブジェクトでサポートする機能を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-141">You can specify the features to support on the <xref:System.Xml.XmlWriter> object, including output options, by using the <xref:System.Xml.XmlWriterSettings> class.</span></span> <span data-ttu-id="ae0e6-142"><xref:System.Xml.XmlWriter> クラスは <xref:System.Xml> フレームワークの重要な一部分です。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-142">The <xref:System.Xml.XmlWriter> class is an integral part of the <xref:System.Xml> framework.</span></span> <span data-ttu-id="ae0e6-143">出力結果を別の XML プロセスにパイプラインして送るには、この出力を使用します。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-143">Use this output type to pipeline the output results into another XML process.</span></span>  
  
#### <a name="string"></a><span data-ttu-id="ae0e6-144">String</span><span class="sxs-lookup"><span data-stu-id="ae0e6-144">String</span></span>  
 <span data-ttu-id="ae0e6-145">出力ファイルの URI を指定するには、この出力を使用します。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-145">Use this output type to specify the URI of the output file.</span></span>  
  
#### <a name="stream"></a><span data-ttu-id="ae0e6-146">ストリーム</span><span class="sxs-lookup"><span data-stu-id="ae0e6-146">Stream</span></span>  
 <span data-ttu-id="ae0e6-147">ストリームとは、ファイル、入出力デバイス、プロセス間通信のパイプ、または TCP/IP ソケットなどのバイト シーケンスを抽象化したものです。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-147">A stream is an abstraction of a sequence of bytes, such as a file, an input/output device, an inter-process communication pipe, or a TCP/IP socket.</span></span> <span data-ttu-id="ae0e6-148"><xref:System.IO.Stream> クラスとその派生クラスは、これら各種の入出力にジェネリックな視点を提供し、プログラマがオペレーティング システムや下位のデバイスに固有の詳細を考慮する必要をなくします。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-148">The <xref:System.IO.Stream> class and its derived classes provide a generic view of these different types of input and output, isolating the programmer from the specific details of the operating system and the underlying devices.</span></span>  
  
 <span data-ttu-id="ae0e6-149"><xref:System.IO.FileStream>、<xref:System.IO.MemoryStream>、または出力ストリーム (`Response.OutputStream`) にデータを送るには、この出力の種類を使用します。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-149">Use this output type to send data to a <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, or an output stream (`Response.OutputStream`).</span></span>  
  
#### <a name="textwriter"></a><span data-ttu-id="ae0e6-150">TextWriter</span><span class="sxs-lookup"><span data-stu-id="ae0e6-150">TextWriter</span></span>  
 <span data-ttu-id="ae0e6-151"><xref:System.IO.TextWriter> は、文字シーケンスを書き出します。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-151">The <xref:System.IO.TextWriter> writes sequential characters.</span></span> <span data-ttu-id="ae0e6-152">これは <xref:System.IO.StringWriter> クラスおよび <xref:System.IO.StreamWriter> クラスに実装され、それぞれ文字を文字列に、またはストリームに書き出します。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-152">It is implemented in the <xref:System.IO.StringWriter> and <xref:System.IO.StreamWriter> classes, which write characters to strings or streams, respectively.</span></span> <span data-ttu-id="ae0e6-153">文字列に出力する場合は、この出力の種類を使用します。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-153">Use this output type when you want to output to a string.</span></span>  
  
## <a name="notes"></a><span data-ttu-id="ae0e6-154">メモ</span><span class="sxs-lookup"><span data-stu-id="ae0e6-154">Notes</span></span>  
  
-   <span data-ttu-id="ae0e6-155">空要素タグを書き出すとき、要素名の最後の文字とバック主ラッシュとの間に 1 つのスペースが書かれます。たとえば `<myElement />` です。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-155">When writing out empty tags, a space is written between the last character of the element name and the backslash, `<myElement />` for example.</span></span> <span data-ttu-id="ae0e6-156">これにより、生成された HTML ページが古いブラウザーで正しく表示されます。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-156">This lets older browsers display the generated HTML pages correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae0e6-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae0e6-157">See Also</span></span>  
 [<span data-ttu-id="ae0e6-158">XSLT 変換</span><span class="sxs-lookup"><span data-stu-id="ae0e6-158">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
