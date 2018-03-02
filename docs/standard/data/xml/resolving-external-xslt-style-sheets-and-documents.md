---
title: "外部の XSLT スタイル シートとドキュメントの解決"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 920cfe3b-d525-4bb2-abf6-9431651f9cf9
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 85176c45b768d1e8fe9efc408fd644bf33aa8c05
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="resolving-external-xslt-style-sheets-and-documents"></a><span data-ttu-id="a4f21-102">外部の XSLT スタイル シートとドキュメントの解決</span><span class="sxs-lookup"><span data-stu-id="a4f21-102">Resolving External XSLT Style Sheets and Documents</span></span>
<span data-ttu-id="a4f21-103">変換中には、外部リソースの解決が必要になるときがあります。</span><span class="sxs-lookup"><span data-stu-id="a4f21-103">There are several times during a transformation when you may need to resolve external resources.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4f21-104"><xref:System.Xml.Xsl.XslTransform> では、[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] クラスが廃止されています。</span><span class="sxs-lookup"><span data-stu-id="a4f21-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="a4f21-105"><xref:System.Xml.Xsl.XslCompiledTransform> クラスを使用して XSLT (Extensible Stylesheet Language for Transformations) 変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="a4f21-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
 <span data-ttu-id="a4f21-106">変換中には、外部リソースの解決が必要になるときがあります。</span><span class="sxs-lookup"><span data-stu-id="a4f21-106">There are several times during a transformation when you may need to resolve external resources:</span></span>  
  
-   <span data-ttu-id="a4f21-107"><xref:System.Xml.Xsl.XslTransform.Load%2A> メソッドの実行時における外部スタイル シートの検索。</span><span class="sxs-lookup"><span data-stu-id="a4f21-107">During the <xref:System.Xml.Xsl.XslTransform.Load%2A> to locate an external style sheet.</span></span>  
  
-   <span data-ttu-id="a4f21-108"><xref:System.Xml.Xsl.XslTransform.Load%2A> メソッドの実行時におけるスタイル シート内の `<xsl:include>` 要素または `<xsl:import>` 要素の解決。</span><span class="sxs-lookup"><span data-stu-id="a4f21-108">During <xref:System.Xml.Xsl.XslTransform.Load%2A> to resolve any `<xsl:include>` or `<xsl:import>` elements found in the style sheet.</span></span>  
  
-   <span data-ttu-id="a4f21-109"><xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドの実行時におけるすべての `document()` 関数の解決。</span><span class="sxs-lookup"><span data-stu-id="a4f21-109">During <xref:System.Xml.Xsl.XslTransform.Transform%2A> to resolve any `document()` functions.</span></span>  
  
## <a name="using-the-xmlresolver-class"></a><span data-ttu-id="a4f21-110">XmlResolver クラスの使い方</span><span class="sxs-lookup"><span data-stu-id="a4f21-110">Using the XmlResolver Class</span></span>  
 <span data-ttu-id="a4f21-111">ネットワーク リソースにアクセスするのに認証が必要な場合は、<xref:System.Xml.Xsl.XslTransform.Load%2A> パラメーターを持っている <xref:System.Xml.XmlResolver> メソッドを使用して、必要な資格情報プロパティが設定された <xref:System.Xml.XmlResolver> オブジェクトを渡します。</span><span class="sxs-lookup"><span data-stu-id="a4f21-111">If authentication is required to access a network resource, use the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that have an <xref:System.Xml.XmlResolver> parameter to pass the <xref:System.Xml.XmlResolver> object, which has the necessary credential properties set.</span></span>  
  
 <span data-ttu-id="a4f21-112">独自の <xref:System.Xml.XmlResolver> を使用する場合や、異なる資格情報を指定する必要がある場合は、次の表に示すように、解決する必要のある外部リソースの処理に応じて、適切な作業を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4f21-112">If you have a custom <xref:System.Xml.XmlResolver> that you want to use, or if you need to specify different credentials, the following table lists the task required, depending on when the external resource needs resolution.</span></span>  
  
|<span data-ttu-id="a4f21-113">解決する必要のある処理</span><span class="sxs-lookup"><span data-stu-id="a4f21-113">What process requires resolution</span></span>|<span data-ttu-id="a4f21-114">必要な作業タスク</span><span class="sxs-lookup"><span data-stu-id="a4f21-114">Task required</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="a4f21-115"><xref:System.Xml.Xsl.XslTransform.Load%2A> メソッドの実行時におけるスタイル シートの検索。</span><span class="sxs-lookup"><span data-stu-id="a4f21-115">During <xref:System.Xml.Xsl.XslTransform.Load%2A> to locate the style sheet.</span></span>|<span data-ttu-id="a4f21-116">スタイル シートが資格情報を必要とするリソース上にある場合は、<xref:System.Xml.Xsl.XslTransform.Load%2A> をパラメーターとして受け取るオーバーロードされた <xref:System.Xml.XmlResolver> メソッドを指定します。</span><span class="sxs-lookup"><span data-stu-id="a4f21-116">Specify the overloaded <xref:System.Xml.Xsl.XslTransform.Load%2A> method that takes, as a parameter, an <xref:System.Xml.XmlResolver> if the style sheet is on a resource that requires credentials.</span></span>|  
|<span data-ttu-id="a4f21-117"><xref:System.Xml.Xsl.XslTransform.Load%2A> メソッドの実行時における `<xsl:include>` または `<xsl:import>` の解決。</span><span class="sxs-lookup"><span data-stu-id="a4f21-117">During <xref:System.Xml.Xsl.XslTransform.Load%2A> to resolve `<xsl:include>` or `<xsl:import>`.</span></span>|<span data-ttu-id="a4f21-118"><xref:System.Xml.Xsl.XslTransform.Load%2A> をパラメーターとして受け取るオーバーロードされた <xref:System.Xml.XmlResolver> メソッドを指定します。</span><span class="sxs-lookup"><span data-stu-id="a4f21-118">Specify the overloaded <xref:System.Xml.Xsl.XslTransform.Load%2A> method that takes, as a parameter, an <xref:System.Xml.XmlResolver>.</span></span> <span data-ttu-id="a4f21-119"><xref:System.Xml.XmlResolver> を使用して、`import` ステートメントまたは `include` ステートメントが参照しているスタイル シートを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="a4f21-119">The <xref:System.Xml.XmlResolver> is used to load the style sheets referenced by the `import` or `include` statements.</span></span> <span data-ttu-id="a4f21-120">`null` を渡すと、外部リソースは解決されません。</span><span class="sxs-lookup"><span data-stu-id="a4f21-120">If you pass in `null`, the external resources are not resolved.</span></span>|  
|<span data-ttu-id="a4f21-121">変換中のすべての `document()` 関数の解決。</span><span class="sxs-lookup"><span data-stu-id="a4f21-121">During a transformation to resolve any `document()` functions.</span></span>|<span data-ttu-id="a4f21-122"><xref:System.Xml.XmlResolver> 引数を受け取る <xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドを使用して、変換中に <xref:System.Xml.XmlResolver> を指定します。</span><span class="sxs-lookup"><span data-stu-id="a4f21-122">Specify the <xref:System.Xml.XmlResolver> during the transformation by using the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method that takes an <xref:System.Xml.XmlResolver> argument.</span></span>|  
  
 <span data-ttu-id="a4f21-123">`document()` 関数は、入力ストリームで提供される XML 初期データの他に、スタイル シートから別の XML リソースを取得します。</span><span class="sxs-lookup"><span data-stu-id="a4f21-123">The `document()` function retrieves other XML resources from a style sheet, in addition to the initial XML data provided by the input stream.</span></span> <span data-ttu-id="a4f21-124">この関数には別の場所にある XML データを含めることができるため、<xref:System.Xml.XmlResolver> 値が設定された `null` を <xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドに渡すと、`document()` 関数は実行されません。</span><span class="sxs-lookup"><span data-stu-id="a4f21-124">Since this function allows the inclusion of XML data that can be located elsewhere, an <xref:System.Xml.XmlResolver> with a `null` value supplied to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method prevents the `document()` function from executing.</span></span> <span data-ttu-id="a4f21-125">`document()` 関数を使用する場合は、適切なアクセス許可セットを取得したうえで、<xref:System.Xml.Xsl.XslTransform.Transform%2A> をパラメーターとして受け取る <xref:System.Xml.XmlResolver> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="a4f21-125">If you want to use the `document()` function, use the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method that takes an <xref:System.Xml.XmlResolver> as a parameter, in addition to having the appropriate permission set.</span></span>  
  
 <span data-ttu-id="a4f21-126"><xref:System.Xml.Xsl.XslTransform.Load%2A> メソッドと、このメソッドでの <xref:System.Xml.XmlResolver> の使い方の詳細については、「<xref:System.Xml.Xsl.XslTransform.Load%28System.String%2CSystem.Xml.XmlResolver%29?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4f21-126">For more information on the <xref:System.Xml.Xsl.XslTransform.Load%2A> method and its use of the <xref:System.Xml.XmlResolver>, see <xref:System.Xml.Xsl.XslTransform.Load%28System.String%2CSystem.Xml.XmlResolver%29?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="a4f21-127"><xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドを呼び出すと、読み込み時に指定された証拠に基づいてアクセス許可が計算され、そのアクセス許可セットが変換処理全体に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="a4f21-127">When the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is called, permissions are calculated against the evidence provided at load time, and that permission set is assigned to the entire transformation process.</span></span> <span data-ttu-id="a4f21-128">`document()` 関数で、アクセス許可セットにないアクセス許可を必要とする処理を実行しようとすると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="a4f21-128">If the `document()` function attempts to initiate an action that requires permissions not found in the set, an exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4f21-129">参照</span><span class="sxs-lookup"><span data-stu-id="a4f21-129">See Also</span></span>  
 [<span data-ttu-id="a4f21-130">XslTransform クラスを使用した XSLT 変換</span><span class="sxs-lookup"><span data-stu-id="a4f21-130">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [<span data-ttu-id="a4f21-131">XslTransform クラスによる XSLT プロセッサの実装</span><span class="sxs-lookup"><span data-stu-id="a4f21-131">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [<span data-ttu-id="a4f21-132">XslTransform からの出力</span><span class="sxs-lookup"><span data-stu-id="a4f21-132">Outputs from an XslTransform</span></span>](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md)  
 [<span data-ttu-id="a4f21-133">異なるストアでの XSLT 変換</span><span class="sxs-lookup"><span data-stu-id="a4f21-133">XSLT Transformations Over Different Stores</span></span>](../../../../docs/standard/data/xml/xslt-transformations-over-different-stores.md)  
 [<span data-ttu-id="a4f21-134">スタイル シート パラメーターと拡張オブジェクト用の XsltArgumentList</span><span class="sxs-lookup"><span data-stu-id="a4f21-134">XsltArgumentList for Style Sheet Parameters and Extension Objects</span></span>](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md)  
 [<span data-ttu-id="a4f21-135">\<msxsl:script> を使用した XSLT スタイルシートのスクリプト</span><span class="sxs-lookup"><span data-stu-id="a4f21-135">XSLT Stylesheet Scripting Using \<msxsl:script></span></span>](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md)  
 [<span data-ttu-id="a4f21-136">msxsl:node-set() 関数のサポート</span><span class="sxs-lookup"><span data-stu-id="a4f21-136">Support for the msxsl:node-set() Function</span></span>](../../../../docs/standard/data/xml/support-for-the-msxsl-node-set-function.md)  
 [<span data-ttu-id="a4f21-137">変換における XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a4f21-137">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [<span data-ttu-id="a4f21-138">変換における XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="a4f21-138">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [<span data-ttu-id="a4f21-139">XslTransform への XPathDocument の入力</span><span class="sxs-lookup"><span data-stu-id="a4f21-139">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [<span data-ttu-id="a4f21-140">XslTransform への XmlDataDocument の入力</span><span class="sxs-lookup"><span data-stu-id="a4f21-140">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [<span data-ttu-id="a4f21-141">XslTransform への XmlDocument の入力</span><span class="sxs-lookup"><span data-stu-id="a4f21-141">XmlDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
