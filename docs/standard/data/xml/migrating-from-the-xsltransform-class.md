---
title: "XslTransform クラスからの移行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9404d758-679f-4ffb-995d-3d07d817659e
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b867b2d7eb2f4b1252579bbf1f47430d9a9a48f4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="migrating-from-the-xsltransform-class"></a><span data-ttu-id="04fbf-102">XslTransform クラスからの移行</span><span class="sxs-lookup"><span data-stu-id="04fbf-102">Migrating From the XslTransform Class</span></span>
<span data-ttu-id="04fbf-103">XSLT アーキテクチャで再設計されました、[!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)]を解放します。</span><span class="sxs-lookup"><span data-stu-id="04fbf-103">The XSLT architecture was redesigned in the [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)] release.</span></span> <span data-ttu-id="04fbf-104"><xref:System.Xml.Xsl.XslTransform> クラスは <xref:System.Xml.Xsl.XslCompiledTransform> クラスで置き換えられています。</span><span class="sxs-lookup"><span data-stu-id="04fbf-104">The <xref:System.Xml.Xsl.XslTransform> class has been replaced by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
 <span data-ttu-id="04fbf-105">以降では、<xref:System.Xml.Xsl.XslCompiledTransform> クラスと <xref:System.Xml.Xsl.XslTransform> クラスの主な相違点について説明します。</span><span class="sxs-lookup"><span data-stu-id="04fbf-105">The following sections describe some of the main differences between the <xref:System.Xml.Xsl.XslCompiledTransform> and the <xref:System.Xml.Xsl.XslTransform> classes.</span></span>  
  
## <a name="performance"></a><span data-ttu-id="04fbf-106">パフォーマンス テスト</span><span class="sxs-lookup"><span data-stu-id="04fbf-106">Performance</span></span>  
 <span data-ttu-id="04fbf-107"><xref:System.Xml.Xsl.XslCompiledTransform> クラスでは多くのパフォーマンスの向上が図られています。</span><span class="sxs-lookup"><span data-stu-id="04fbf-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class includes many performance improvements.</span></span> <span data-ttu-id="04fbf-108">新しい XSLT プロセッサは XSLT スタイル シートを、共通言語ランタイム (CLR) が他のプログラム言語で行うのと同様に、共通の中間形式にコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="04fbf-108">The new XSLT processor compiles the XSLT style sheet down to a common intermediate format, similar to what the common language runtime (CLR) does for other programming languages.</span></span> <span data-ttu-id="04fbf-109">いったんスタイル シートがコンパイルされると、それをキャッシュして再利用することができます。</span><span class="sxs-lookup"><span data-stu-id="04fbf-109">Once the style sheet is compiled, it can be cached and reused.</span></span>  
  
 <span data-ttu-id="04fbf-110"><xref:System.Xml.Xsl.XslCompiledTransform> クラスには、このクラスを <xref:System.Xml.Xsl.XslTransform> クラスよりも大幅に高速化する他の最適化も含まれています。</span><span class="sxs-lookup"><span data-stu-id="04fbf-110">The <xref:System.Xml.Xsl.XslCompiledTransform> class also includes other optimizations that make it much faster than the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04fbf-111">全体的なパフォーマンスは <xref:System.Xml.Xsl.XslCompiledTransform> クラスの方が <xref:System.Xml.Xsl.XslTransform> クラスより優れていますが、<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> クラスの <xref:System.Xml.Xsl.XslCompiledTransform> メソッドが変換で初めて呼び出されたときは、<xref:System.Xml.Xsl.XslTransform.Load%2A> クラスの <xref:System.Xml.Xsl.XslTransform> メソッドよりパフォーマンスが劣る場合があります。</span><span class="sxs-lookup"><span data-stu-id="04fbf-111">Although the overall performance of the <xref:System.Xml.Xsl.XslCompiledTransform> class is better than the <xref:System.Xml.Xsl.XslTransform> class, the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslCompiledTransform> class might perform more slowly than the <xref:System.Xml.Xsl.XslTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslTransform> class the first time it is called on a transformation.</span></span> <span data-ttu-id="04fbf-112">これは、XSLT ファイルを読み込む前にコンパイルする必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="04fbf-112">This is because the XSLT file must be compiled before it is loaded.</span></span> <span data-ttu-id="04fbf-113">詳細については、次のブログの投稿を参照してください: [XslCompiledTransform は XslTransform より遅いですか?](http://go.microsoft.com/fwlink/?LinkId=130590)</span><span class="sxs-lookup"><span data-stu-id="04fbf-113">For more information, see the following blog post: [XslCompiledTransform Slower than XslTransform?](http://go.microsoft.com/fwlink/?LinkId=130590)</span></span>  
  
## <a name="security"></a><span data-ttu-id="04fbf-114">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="04fbf-114">Security</span></span>  
 <span data-ttu-id="04fbf-115">既定で、<xref:System.Xml.Xsl.XslCompiledTransform> クラスでは XSLT `document()` 関数と埋め込みスクリプトのサポートが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="04fbf-115">By default, the <xref:System.Xml.Xsl.XslCompiledTransform> class disables support for the XSLT `document()` function and embedded scripting.</span></span> <span data-ttu-id="04fbf-116">これらの機能を有効にするには、機能が有効になっている <xref:System.Xml.Xsl.XsltSettings> オブジェクトを作成し、それを <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="04fbf-116">These features can be enabled by creating an <xref:System.Xml.Xsl.XsltSettings> object that has the features enabled and passing it to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span> <span data-ttu-id="04fbf-117">スクリプト作成を有効にして XSLT 変換を実行する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="04fbf-117">The following example shows how to enable scripting and perform an XSLT transformation.</span></span>  
  
 [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
 [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
 <span data-ttu-id="04fbf-118">詳細については、次を参照してください。 [XSLT のセキュリティに関する考慮事項](../../../../docs/standard/data/xml/xslt-security-considerations.md)です。</span><span class="sxs-lookup"><span data-stu-id="04fbf-118">For more information, see [XSLT Security Considerations](../../../../docs/standard/data/xml/xslt-security-considerations.md).</span></span>  
  
## <a name="new-features"></a><span data-ttu-id="04fbf-119">新機能</span><span class="sxs-lookup"><span data-stu-id="04fbf-119">New Features</span></span>  
  
### <a name="temporary-files"></a><span data-ttu-id="04fbf-120">一時テーブル</span><span class="sxs-lookup"><span data-stu-id="04fbf-120">Temporary Files</span></span>  
 <span data-ttu-id="04fbf-121">XSLT の処理中に一時ファイルが生成されることがあります。</span><span class="sxs-lookup"><span data-stu-id="04fbf-121">Temporary files are sometimes generated during XSLT processing.</span></span> <span data-ttu-id="04fbf-122">スタイル シートにスクリプト ブロックが含まれる場合、またはデバッグ設定を true に設定してスタイル シートをコンパイルした場合、%TEMP% フォルダーに一時ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="04fbf-122">If a style sheet contains script blocks, or if it is compiled with the debug setting set to true, temporary files may be created in the %TEMP% folder.</span></span> <span data-ttu-id="04fbf-123">タイミングの問題で、一部の一時ファイルが削除されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="04fbf-123">There may be instances when some temporary files are not deleted due to timing issues.</span></span> <span data-ttu-id="04fbf-124">たとえば、一時ファイルが現在の AppDomain やデバッガーにより使用されると、<xref:System.CodeDom.Compiler.TempFileCollection> オブジェクトの終了処理でそのファイルを削除できなくなります。</span><span class="sxs-lookup"><span data-stu-id="04fbf-124">For example, if the files are in use by the current AppDomain or by the debugger, the finalizer of the <xref:System.CodeDom.Compiler.TempFileCollection> object will not be able to remove them.</span></span>  
  
 <span data-ttu-id="04fbf-125">クライアントのすべての一時ファイルが削除されるように、<xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> プロパティを使用して追加のクリーンアップを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="04fbf-125">The <xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> property can be used for additional cleanup to make sure that all temporary files are removed from the client.</span></span>  
  
### <a name="support-for-the-xsloutput-element-and-xmlwriter"></a><span data-ttu-id="04fbf-126">xsl:output 要素と XmlWriter のサポート</span><span class="sxs-lookup"><span data-stu-id="04fbf-126">Support for the xsl:output Element and XmlWriter</span></span>  
 <span data-ttu-id="04fbf-127">変換出力が <xref:System.Xml.Xsl.XslTransform> オブジェクトに送られる場合、`xsl:output` クラスでは <xref:System.Xml.XmlWriter> の設定が無視されていました。</span><span class="sxs-lookup"><span data-stu-id="04fbf-127">The <xref:System.Xml.Xsl.XslTransform> class ignored `xsl:output` settings when the transform output was sent to an <xref:System.Xml.XmlWriter> object.</span></span> <span data-ttu-id="04fbf-128"><xref:System.Xml.Xsl.XslCompiledTransform> クラスには、スタイル シートの <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> 要素から取得された出力情報を含む <xref:System.Xml.XmlWriterSettings> オブジェクトを返す `xsl:output` プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="04fbf-128">The <xref:System.Xml.Xsl.XslCompiledTransform> class has an <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> property that returns an <xref:System.Xml.XmlWriterSettings> object containing the output information derived from the `xsl:output` element of the style sheet.</span></span> <span data-ttu-id="04fbf-129"><xref:System.Xml.XmlWriterSettings> オブジェクトを使用して、適切に設定された <xref:System.Xml.XmlWriter> オブジェクトを作成し、それを <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="04fbf-129">The <xref:System.Xml.XmlWriterSettings> object is used to create an <xref:System.Xml.XmlWriter> object with the correct settings that can be passed to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span> <span data-ttu-id="04fbf-130">次の C# コードに、この処理を示します。</span><span class="sxs-lookup"><span data-stu-id="04fbf-130">The following C# code illustrates this behavior:</span></span>  
  
```  
// Create the XslTransform object and load the style sheet.  
XslCompiledTransform xslt = new XslCompiledTransform();  
xslt.Load(stylesheet);  
  
// Load the file to transform.  
XPathDocument doc = new XPathDocument(filename);  
  
// Create the writer.  
XmlWriter writer = XmlWriter.Create(Console.Out, xslt.OutputSettings);  
  
// Transform the file and send the output to the console.  
xslt.Transform(doc, writer);  
writer.Close();  
```  
  
### <a name="debug-option"></a><span data-ttu-id="04fbf-131">デバッグ オプション</span><span class="sxs-lookup"><span data-stu-id="04fbf-131">Debug Option</span></span>  
 <span data-ttu-id="04fbf-132"><xref:System.Xml.Xsl.XslCompiledTransform> クラスによりデバッグ情報を生成できます。この機能を利用して、Microsoft [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] デバッガーを使用してスタイル シートをデバッグすることができます。</span><span class="sxs-lookup"><span data-stu-id="04fbf-132">The <xref:System.Xml.Xsl.XslCompiledTransform> class can generate debug information, which enables you to debug the style sheet with the Microsoft [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] Debugger.</span></span> <span data-ttu-id="04fbf-133">詳細については、「<xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04fbf-133">See <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29> for more information.</span></span>  
  
## <a name="behavioral-differences"></a><span data-ttu-id="04fbf-134">動作の違い</span><span class="sxs-lookup"><span data-stu-id="04fbf-134">Behavioral Differences</span></span>  
  
### <a name="transforming-to-an-xmlreader"></a><span data-ttu-id="04fbf-135">XmlReader への変換</span><span class="sxs-lookup"><span data-stu-id="04fbf-135">Transforming to an XmlReader</span></span>  
 <span data-ttu-id="04fbf-136"><xref:System.Xml.Xsl.XslTransform> クラスには、変換結果を <xref:System.Xml.XmlReader> オブジェクトとして返す Transform オーバーロードが数種類あります。</span><span class="sxs-lookup"><span data-stu-id="04fbf-136">The <xref:System.Xml.Xsl.XslTransform> class has several Transform overloads that return transformation results as an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="04fbf-137">このオーバーロードを使用することで、生成される XML ツリーのシリアル化と逆シリアル化によるオーバーヘッドを生じることなく、変換結果をメモり内表現 (<xref:System.Xml.XmlDocument> または <xref:System.Xml.XPath.XPathDocument>) に読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="04fbf-137">These overloads can be used to load the transformation results into an in-memory representation (such as <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument>) without incurring the overhead of serialization and deserialization of the resulting XML tree.</span></span> <span data-ttu-id="04fbf-138">次の C# コード例で、<xref:System.Xml.XmlDocument> オブジェクトに変換結果を読み込む方法を示します。</span><span class="sxs-lookup"><span data-stu-id="04fbf-138">The following C# code shows how to load the transformation results into an <xref:System.Xml.XmlDocument> object.</span></span>  
  
```  
// Load the style sheet  
XslTransform xslt = new XslTransform();  
xslt.Load("MyStylesheet.xsl");  
  
// Transform input document to XmlDocument for additional processing  
XmlDocument doc = new XmlDocument();  
doc.Load(xslt.Transform(input, (XsltArgumentList)null));  
```  
  
 <span data-ttu-id="04fbf-139"><xref:System.Xml.Xsl.XslCompiledTransform> クラスでは、<xref:System.Xml.XmlReader> オブジェクトへの変換がサポートされません。</span><span class="sxs-lookup"><span data-stu-id="04fbf-139">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not support transforming to an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="04fbf-140">ただし、<xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> メソッドを使用して、生成される XML ツリーを <xref:System.Xml.XmlWriter> から直接読み込むことはできます。</span><span class="sxs-lookup"><span data-stu-id="04fbf-140">However, you can do something similar by using the <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> method to load the resulting XML tree directly from an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="04fbf-141">次の C# コード例では、同じ操作を <xref:System.Xml.Xsl.XslCompiledTransform> を使用して行う方法を示します。</span><span class="sxs-lookup"><span data-stu-id="04fbf-141">The following C# code shows how to accomplish the same task using <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
```  
// Transform input document to XmlDocument for additional processing  
XmlDocument doc = new XmlDocument();  
using (XmlWriter writer = doc.CreateNavigator().AppendChild()) {  
    xslt.Transform(input, (XsltArgumentList)null, writer);  
}  
```  
  
### <a name="discretionary-behavior"></a><span data-ttu-id="04fbf-142">随意動作</span><span class="sxs-lookup"><span data-stu-id="04fbf-142">Discretionary Behavior</span></span>  
 <span data-ttu-id="04fbf-143">W3C 勧告『XSL Transformations (XSLT) Version 1.0』には、対処方法を実装者が決定できる事項があります。</span><span class="sxs-lookup"><span data-stu-id="04fbf-143">The W3C XSL Transformations (XSLT) Version 1.0 Recommendation includes areas in which the implementation provider may decide how to handle a situation.</span></span> <span data-ttu-id="04fbf-144">このような事項は、随意動作と見なされています。</span><span class="sxs-lookup"><span data-stu-id="04fbf-144">These areas are considered to be discretionary behavior.</span></span> <span data-ttu-id="04fbf-145">事項によっては、<xref:System.Xml.Xsl.XslCompiledTransform> クラスと <xref:System.Xml.Xsl.XslTransform> クラスで動作が異なります。</span><span class="sxs-lookup"><span data-stu-id="04fbf-145">There are several areas where the <xref:System.Xml.Xsl.XslCompiledTransform> behaves differently than the <xref:System.Xml.Xsl.XslTransform> class.</span></span> <span data-ttu-id="04fbf-146">詳細については、次を参照してください。[回復可能な XSLT エラー](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)です。</span><span class="sxs-lookup"><span data-stu-id="04fbf-146">For more information, see [Recoverable XSLT Errors](../../../../docs/standard/data/xml/recoverable-xslt-errors.md).</span></span>  
  
### <a name="extension-objects-and-script-functions"></a><span data-ttu-id="04fbf-147">拡張オブジェクトとスクリプト関数</span><span class="sxs-lookup"><span data-stu-id="04fbf-147">Extension Objects and Script Functions</span></span>  
 <span data-ttu-id="04fbf-148"><xref:System.Xml.Xsl.XslCompiledTransform> では、スクリプト関数の使用に関して新たに 2 つの制限が加えられています。</span><span class="sxs-lookup"><span data-stu-id="04fbf-148"><xref:System.Xml.Xsl.XslCompiledTransform> introduces two new restrictions on the use of script functions:</span></span>  
  
-   <span data-ttu-id="04fbf-149">XPath 式からはパブリック メソッドのみを呼び出すことができる。</span><span class="sxs-lookup"><span data-stu-id="04fbf-149">Only public methods may be called from XPath expressions.</span></span>  
  
-   <span data-ttu-id="04fbf-150">オーバーロードは引数の数に基づいて区別される。</span><span class="sxs-lookup"><span data-stu-id="04fbf-150">Overloads are distinguishable from each other based on the number of arguments.</span></span> <span data-ttu-id="04fbf-151">引数の数が同じオーバーロードが複数存在する場合、例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="04fbf-151">If more than one overload has the same number of arguments, an exception will be raised.</span></span>  
  
 <span data-ttu-id="04fbf-152"><xref:System.Xml.Xsl.XslCompiledTransform> では、スクリプト関数へのバインド (メソッド名参照) がコンパイル時に実行されます。XslTranform を利用するスタイル シートを <xref:System.Xml.Xsl.XslCompiledTransform> によって読み込むと、例外が発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="04fbf-152">In <xref:System.Xml.Xsl.XslCompiledTransform>, a binding (method name lookup) to script functions occurs at compile time, and style sheets that worked with XslTranform may cause an exception when they are loaded with <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
 <span data-ttu-id="04fbf-153"><xref:System.Xml.Xsl.XslCompiledTransform> では、`msxsl:using` 要素内に子要素として `msxsl:assembly` および `msxsl:script` を含めることがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="04fbf-153"><xref:System.Xml.Xsl.XslCompiledTransform> supports having `msxsl:using` and `msxsl:assembly` child elements within the `msxsl:script` element.</span></span> <span data-ttu-id="04fbf-154">`msxsl:using` 要素と `msxsl:assembly` 要素を使用して、スクリプト ブロックで使用する追加の名前空間とアセンブリを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="04fbf-154">The `msxsl:using` and `msxsl:assembly` elements are used to declare additional namespaces and assemblies for use in the script block.</span></span> <span data-ttu-id="04fbf-155">参照してください[msxsl:script スクリプト ブロックを使用した](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md)詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="04fbf-155">See [Script Blocks Using msxsl:script](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md) for more information.</span></span>  
  
 <span data-ttu-id="04fbf-156"><xref:System.Xml.Xsl.XslCompiledTransform> では、複数のオーバーロードおよびそれと同数の引数を含む拡張オブジェクトは使用できません。</span><span class="sxs-lookup"><span data-stu-id="04fbf-156"><xref:System.Xml.Xsl.XslCompiledTransform> prohibits extension objects that have multiple overloads with the same number of arguments.</span></span>  
  
### <a name="msxml-functions"></a><span data-ttu-id="04fbf-157">MSXML 関数</span><span class="sxs-lookup"><span data-stu-id="04fbf-157">MSXML Functions</span></span>  
 <span data-ttu-id="04fbf-158"><xref:System.Xml.Xsl.XslCompiledTransform> クラスでは、新しい MSXML 関数のサポートが追加されました。</span><span class="sxs-lookup"><span data-stu-id="04fbf-158">Support for additional MSXML functions have been added to the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="04fbf-159">新しい関数または強化された関数は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="04fbf-159">The following list describes new or improved functionality:</span></span>  
  
-   <span data-ttu-id="04fbf-160">msxsl:node-設定:<xref:System.Xml.Xsl.XslTransform>の引数を必要な[ノードセット関数](http://msdn.microsoft.com/en-us/87b6b3f4-16f4-4fa3-8103-d62a679ac2a7)関数の結果ツリー フラグメント。</span><span class="sxs-lookup"><span data-stu-id="04fbf-160">msxsl:node-set: <xref:System.Xml.Xsl.XslTransform> required the argument of the [node-set Function](http://msdn.microsoft.com/en-us/87b6b3f4-16f4-4fa3-8103-d62a679ac2a7) function to be a result tree fragment.</span></span> <span data-ttu-id="04fbf-161"><xref:System.Xml.Xsl.XslCompiledTransform> クラスでは、この要件がありません。</span><span class="sxs-lookup"><span data-stu-id="04fbf-161">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not have this requirement.</span></span>  
  
-   <span data-ttu-id="04fbf-162">msxsl:version : この関数は、<xref:System.Xml.Xsl.XslCompiledTransform> でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="04fbf-162">msxsl:version: This function is supported in <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
-   <span data-ttu-id="04fbf-163">XPath 拡張関数: [ms:string-関数の比較](http://msdn.microsoft.com/en-us/20616b82-9e27-444c-b714-4f1e09b73aee)、 [ms:utc 関数](http://msdn.microsoft.com/en-us/ef26fc88-84c6-4fb9-9c3b-f2f5264b864f)、 [ms:namespace-uri 関数](http://msdn.microsoft.com/en-us/91f9cabf-ab93-4dbe-9c12-e6a75214f4c7)、 [ms:local-関数の名前](http://msdn.microsoft.com/en-us/10ed60a1-17a9-4d74-8b98-7940ac97c0b5)、 [ms:number 関数](http://msdn.microsoft.com/en-us/b94fc08e-1f31-4f48-b1a8-6d78c1b5d954)、 [ms:format-関数の日付](http://msdn.microsoft.com/en-us/51f35609-89a9-4098-a166-88bf01300bf5)、および[ms:format-関数の時間](http://msdn.microsoft.com/en-us/e5c2df2d-e8fb-4a8f-bfc0-db84ea12a5d5)関数がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="04fbf-163">XPath extension functions: The [ms:string-compare Function](http://msdn.microsoft.com/en-us/20616b82-9e27-444c-b714-4f1e09b73aee), [ms:utc Function](http://msdn.microsoft.com/en-us/ef26fc88-84c6-4fb9-9c3b-f2f5264b864f), [ms:namespace-uri Function](http://msdn.microsoft.com/en-us/91f9cabf-ab93-4dbe-9c12-e6a75214f4c7), [ms:local-name Function](http://msdn.microsoft.com/en-us/10ed60a1-17a9-4d74-8b98-7940ac97c0b5), [ms:number Function](http://msdn.microsoft.com/en-us/b94fc08e-1f31-4f48-b1a8-6d78c1b5d954), [ms:format-date Function](http://msdn.microsoft.com/en-us/51f35609-89a9-4098-a166-88bf01300bf5), and [ms:format-time Function](http://msdn.microsoft.com/en-us/e5c2df2d-e8fb-4a8f-bfc0-db84ea12a5d5) functions are now supported.</span></span>  
  
-   <span data-ttu-id="04fbf-164">スキーマ関連の XPath 拡張関数 : これは、<xref:System.Xml.Xsl.XslCompiledTransform> ではネイティブでサポートされません。</span><span class="sxs-lookup"><span data-stu-id="04fbf-164">Schema-related XPath extension functions: These functions are not supported natively by <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span> <span data-ttu-id="04fbf-165">ただし、拡張関数として実装することはできます。</span><span class="sxs-lookup"><span data-stu-id="04fbf-165">However, they can be implemented as extension functions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04fbf-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="04fbf-166">See Also</span></span>  
 [<span data-ttu-id="04fbf-167">XSLT 変換</span><span class="sxs-lookup"><span data-stu-id="04fbf-167">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [<span data-ttu-id="04fbf-168">XslCompiledTransform クラスの使用</span><span class="sxs-lookup"><span data-stu-id="04fbf-168">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
