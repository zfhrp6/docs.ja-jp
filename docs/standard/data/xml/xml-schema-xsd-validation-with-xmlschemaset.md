---
title: "XmlSchemaSet による XML スキーマ (XSD) 検証"
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
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 99e2f66a1aedafe316ab65ae302113ea553146ed
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a><span data-ttu-id="3f19f-102">XmlSchemaSet による XML スキーマ (XSD) 検証</span><span class="sxs-lookup"><span data-stu-id="3f19f-102">XML Schema (XSD) Validation with XmlSchemaSet</span></span>
<span data-ttu-id="3f19f-103">XML ドキュメントは、<xref:System.Xml.Schema.XmlSchemaSet> の XML スキーマ定義言語 (XSD) スキーマを基準として検証できます。</span><span class="sxs-lookup"><span data-stu-id="3f19f-103">XML documents can be validated against an XML schema definition language (XSD) schema in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
## <a name="validating-xml-documents"></a><span data-ttu-id="3f19f-104">XML ドキュメントの検証</span><span class="sxs-lookup"><span data-stu-id="3f19f-104">Validating XML Documents</span></span>  
 <span data-ttu-id="3f19f-105">XML ドキュメントは、<xref:System.Xml.XmlReader.Create%2A> クラスの <xref:System.Xml.XmlReader> メソッドを使用して検証します。</span><span class="sxs-lookup"><span data-stu-id="3f19f-105">XML documents are validated by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class.</span></span> <span data-ttu-id="3f19f-106">XML ドキュメントを検証するには、XML ドキュメントの検証に使用する XML スキーマ定義言語 (XSD) スキーマを持つ <xref:System.Xml.XmlReaderSettings> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="3f19f-106">To validate an XML document, construct an <xref:System.Xml.XmlReaderSettings> object that contains an XML schema definition language (XSD) schema with which to validate the XML document.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f19f-107">[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) を使用する際、<xref:System.Xml.Schema> 名前空間に含まれる拡張メソッドによって、XSD ファイルを基準として XML ツリーを簡単に検証することができます。</span><span class="sxs-lookup"><span data-stu-id="3f19f-107">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XSD file when using [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span></span> <span data-ttu-id="3f19f-108">LINQ to XML を使用した XML ドキュメントの検証に関する詳細については、「[方法: XSD を使用して検証する](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f19f-108">For more information on validating XML documents with LINQ to XML, see [How to: Validate Using XSD](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b).</span></span>  
  
 <span data-ttu-id="3f19f-109">独立したスキーマまたはスキーマのセット (<xref:System.Xml.Schema.XmlSchemaSet> を使用) を <xref:System.Xml.Schema.XmlSchemaSet> に追加するには、そのどちらかを <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> の <xref:System.Xml.Schema.XmlSchemaSet> メソッドにパラメーターとして渡します。</span><span class="sxs-lookup"><span data-stu-id="3f19f-109">An individual schema or a set of schemas (as an <xref:System.Xml.Schema.XmlSchemaSet>) can be added to an <xref:System.Xml.Schema.XmlSchemaSet> by passing either one as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="3f19f-110">ドキュメントを検証する際には、ドキュメントの対象名前空間がスキーマ セット内のスキーマの対象名前空間と一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f19f-110">Note that when validating a document the target namespace of the document must match the target namespace of the schema in the schema set.</span></span>  
  
 <span data-ttu-id="3f19f-111">XML ドキュメントのサンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="3f19f-111">The following is an example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 <span data-ttu-id="3f19f-112">XML ドキュメントのサンプルを検証するスキーマを次に示します。</span><span class="sxs-lookup"><span data-stu-id="3f19f-112">The following is the schema that validates the example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 <span data-ttu-id="3f19f-113">以下のコード サンプルでは、<xref:System.Xml.Schema.XmlSchemaSet> オブジェクトの <xref:System.Xml.XmlReaderSettings.Schemas%2A><xref:System.Xml.XmlReaderSettings> プロパティに上記のスキーマが追加されます。</span><span class="sxs-lookup"><span data-stu-id="3f19f-113">In the code example that follows, the schema above is added to the <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> property of the <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="3f19f-114"><xref:System.Xml.XmlReaderSettings> オブジェクトは、上記の XML ドキュメントを検証する <xref:System.Xml.XmlReader.Create%2A> オブジェクトの <xref:System.Xml.XmlReader> メソッドにパラメーターとして渡されます。</span><span class="sxs-lookup"><span data-stu-id="3f19f-114">The <xref:System.Xml.XmlReaderSettings> object is passed as a parameter to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object, which validates the XML document above.</span></span>  
  
 <span data-ttu-id="3f19f-115"><xref:System.Xml.XmlReaderSettings.ValidationType%2A> オブジェクトの <xref:System.Xml.XmlReaderSettings> プロパティが `Schema` に設定されて、<xref:System.Xml.XmlReader.Create%2A> オブジェクトの <xref:System.Xml.XmlReader> メソッドによる XML ドキュメントの検証が行われます。</span><span class="sxs-lookup"><span data-stu-id="3f19f-115">The <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property of the <xref:System.Xml.XmlReaderSettings> object is set to `Schema` to enforce validation of the XML document by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="3f19f-116">XML のドキュメントおよびスキーマの検証中に発見されたエラーによって発生する <xref:System.Xml.Schema.ValidationEventHandler> イベントまたは <xref:System.Xml.XmlReaderSettings> イベントを処理するために、<xref:System.Xml.Schema.XmlSeverityType.Warning> オブジェクトに <xref:System.Xml.Schema.XmlSeverityType.Error> を追加します。</span><span class="sxs-lookup"><span data-stu-id="3f19f-116">A <xref:System.Xml.Schema.ValidationEventHandler> is added to the <xref:System.Xml.XmlReaderSettings> object to handle any <xref:System.Xml.Schema.XmlSeverityType.Warning> or <xref:System.Xml.Schema.XmlSeverityType.Error> events raised by errors found during the validation process of both the XML document and the schema.</span></span>  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3f19f-117">参照</span><span class="sxs-lookup"><span data-stu-id="3f19f-117">See Also</span></span>  
 [<span data-ttu-id="3f19f-118">スキーマをコンパイルするための XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="3f19f-118">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [<span data-ttu-id="3f19f-119">XML スキーマの使用</span><span class="sxs-lookup"><span data-stu-id="3f19f-119">Working with XML Schemas</span></span>](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
