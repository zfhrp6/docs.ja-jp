---
title: "XslTransform からの出力"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 647f3829f4b26791c063d5646669b2fcb7ab6684
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="outputs-from-an-xsltransform"></a><span data-ttu-id="e3fdd-102">XslTransform からの出力</span><span class="sxs-lookup"><span data-stu-id="e3fdd-102">Outputs from an XslTransform</span></span>
<span data-ttu-id="e3fdd-103">スタイル シートは、`<xsl:output>` ステートメントと `method` 属性を使って出力形式を決定できます。次の表では、<xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドを使用して出力を書き出し、出力形式を <xref:System.IO.Stream> または <xref:System.IO.TextWriter> として宣言した場合に出力形式がどうなるかを説明します。</span><span class="sxs-lookup"><span data-stu-id="e3fdd-103">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3fdd-104"><xref:System.Xml.Xsl.XslTransform> では、[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] クラスが廃止されています。</span><span class="sxs-lookup"><span data-stu-id="e3fdd-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="e3fdd-105"><xref:System.Xml.Xsl.XslCompiledTransform> クラスを使用して XSLT (Extensible Stylesheet Language for Transformations) 変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="e3fdd-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="e3fdd-106">詳細については、「[XslCompiledTransform クラスの使用](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)」と「[XslTransform クラスからの移行](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3fdd-106">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="e3fdd-107">スタイル シートは、`<xsl:output>` ステートメントと `method` 属性を使って出力形式を決定できます。次の表では、<xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドを使用して出力を書き出し、出力形式を <xref:System.IO.Stream> または <xref:System.IO.TextWriter> として宣言した場合に出力形式がどうなるかを説明します。</span><span class="sxs-lookup"><span data-stu-id="e3fdd-107">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="e3fdd-108"><xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドを `<xsl:output>` ステートメントと共に使用して出力の種類を宣言した場合に得られる結果を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="e3fdd-108">The following table describes what happens when an output type is declared by the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method in conjunction with the use of an `<xsl:output>` statement:</span></span>  
  
|<span data-ttu-id="e3fdd-109">\<xsl:output method = > attribute</span><span class="sxs-lookup"><span data-stu-id="e3fdd-109">\<xsl:output method = > attribute</span></span>|<span data-ttu-id="e3fdd-110">結果の形式</span><span class="sxs-lookup"><span data-stu-id="e3fdd-110">Result format</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="e3fdd-111">method="xml"</span><span class="sxs-lookup"><span data-stu-id="e3fdd-111">method="xml"</span></span>|<span data-ttu-id="e3fdd-112">XML</span><span class="sxs-lookup"><span data-stu-id="e3fdd-112">XML</span></span>|  
|<span data-ttu-id="e3fdd-113">method="html"</span><span class="sxs-lookup"><span data-stu-id="e3fdd-113">method="html"</span></span>|<span data-ttu-id="e3fdd-114">HTML</span><span class="sxs-lookup"><span data-stu-id="e3fdd-114">HTML</span></span>|  
|<span data-ttu-id="e3fdd-115">method="text"</span><span class="sxs-lookup"><span data-stu-id="e3fdd-115">method="text"</span></span>|<span data-ttu-id="e3fdd-116">テキスト</span><span class="sxs-lookup"><span data-stu-id="e3fdd-116">Text</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="e3fdd-117">メモ: `<xsl:output>` メソッドの出力が <xref:System.Xml.Xsl.XslTransform.Transform%2A> または <xref:System.Xml.XmlReader> である場合、<xref:System.Xml.XmlWriter> ステートメントは無視されます。</span><span class="sxs-lookup"><span data-stu-id="e3fdd-117">Note: The `<xsl:output>` statement is ignored when the output of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="e3fdd-118"><xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドの出力が <xref:System.IO.Stream> または <xref:System.IO.TextWriter> である場合は、次の属性がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="e3fdd-118">The following attributes are supported when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>:</span></span>  
  
-   <span data-ttu-id="e3fdd-119">encoding\*</span><span class="sxs-lookup"><span data-stu-id="e3fdd-119">encoding\*</span></span>  
  
-   <span data-ttu-id="e3fdd-120">omit-xml-declaration</span><span class="sxs-lookup"><span data-stu-id="e3fdd-120">omit-xml-declaration</span></span>  
  
-   <span data-ttu-id="e3fdd-121">スタンドアロン</span><span class="sxs-lookup"><span data-stu-id="e3fdd-121">standalone</span></span>  
  
-   <span data-ttu-id="e3fdd-122">doctype-public</span><span class="sxs-lookup"><span data-stu-id="e3fdd-122">doctype-public</span></span>  
  
-   <span data-ttu-id="e3fdd-123">doctype-system</span><span class="sxs-lookup"><span data-stu-id="e3fdd-123">doctype-system</span></span>  
  
-   <span data-ttu-id="e3fdd-124">cdata-section-elements</span><span class="sxs-lookup"><span data-stu-id="e3fdd-124">cdata-section-elements</span></span>  
  
-   <span data-ttu-id="e3fdd-125">indent</span><span class="sxs-lookup"><span data-stu-id="e3fdd-125">indent</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e3fdd-126">\*<xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドが出力を <xref:System.IO.TextWriter> に送信する場合、encoding 属性は無視されます。</span><span class="sxs-lookup"><span data-stu-id="e3fdd-126">\*the encoding attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is sending its output to a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="e3fdd-127">その場合は、encoding 属性の代わりに <xref:System.IO.TextWriter> の encoding プロパティが使用されます。</span><span class="sxs-lookup"><span data-stu-id="e3fdd-127">The encoding property on the <xref:System.IO.TextWriter> is used instead.</span></span>  
  
 <span data-ttu-id="e3fdd-128"><xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドの出力が <xref:System.IO.Stream> の場合、次の属性は無視されます。</span><span class="sxs-lookup"><span data-stu-id="e3fdd-128">The following attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream>:</span></span>  
  
-   <span data-ttu-id="e3fdd-129">version : バージョンは常に 1.0 です。</span><span class="sxs-lookup"><span data-stu-id="e3fdd-129">version: the version is always 1.0</span></span>  
  
-   <span data-ttu-id="e3fdd-130">media-type : メディア タイプです。</span><span class="sxs-lookup"><span data-stu-id="e3fdd-130">media-type: the media-type</span></span>  
  
## <a name="escaping-special-characters"></a><span data-ttu-id="e3fdd-131">特殊文字のエスケープ</span><span class="sxs-lookup"><span data-stu-id="e3fdd-131">Escaping Special Characters</span></span>  
 <span data-ttu-id="e3fdd-132">`<xsl:text disable-output-escaping>` 記号の代わりに `<&lt>` を使用するなど、特殊文字を XML 形式にエスケープする必要があるかどうかを示すには、`"<"` タグを使用します。</span><span class="sxs-lookup"><span data-stu-id="e3fdd-132">The `<xsl:text disable-output-escaping>` tag is used to indicate whether or not special characters need to be escaped into an XML form (for example, using `<&lt>` in place of the `"<"` symbol) or left in the present condition.</span></span> <span data-ttu-id="e3fdd-133">`disable-output-escaping` オブジェクトまたは <xref:System.Xml.XmlReader> オブジェクトへの変換では <xref:System.Xml.XmlWriter> 属性が無視されるため、特殊文字はこのタグの影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="e3fdd-133">The `disable-output-escaping` attribute is ignored when transforming to an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter> object and has no effect on special characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3fdd-134">参照</span><span class="sxs-lookup"><span data-stu-id="e3fdd-134">See Also</span></span>  
 [<span data-ttu-id="e3fdd-135">XslTransform クラスによる XSLT プロセッサの実装</span><span class="sxs-lookup"><span data-stu-id="e3fdd-135">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
