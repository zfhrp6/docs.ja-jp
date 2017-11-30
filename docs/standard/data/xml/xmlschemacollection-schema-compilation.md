---
title: "XmlSchemaCollection スキーマのコンパイル"
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
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 901c3fdc8fdc80cc7c3bf13170646de857a5e009
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xmlschemacollection-schema-compilation"></a><span data-ttu-id="a535c-102">XmlSchemaCollection スキーマのコンパイル</span><span class="sxs-lookup"><span data-stu-id="a535c-102">XmlSchemaCollection Schema Compilation</span></span>
<span data-ttu-id="a535c-103">**XmlSchemaCollection**がキャッシュまたはライブラリ Xml-data Reduced (XDR) スキーマと XML スキーマ定義言語 (XSD) スキーマを格納および検証できます。</span><span class="sxs-lookup"><span data-stu-id="a535c-103">The **XmlSchemaCollection** is a cache or library where XML-Data Reduced (XDR) and XML Schema definition language (XSD) schemas can be stored and validated.</span></span> <span data-ttu-id="a535c-104">**XmlSchemaCollection**ファイルまたは URL からそれらにアクセスする代わりに、メモリ内のスキーマをキャッシュすることによってパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="a535c-104">**XmlSchemaCollection** improves performance by caching schemas in memory instead of accessing them from a file or URL.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a535c-105">ただし、 **XmlSchemaCollection**クラスは、XDR スキーマと XML スキーマ、メソッドおよびプロパティを受け取るかを返しますの両方を格納、 **XmlSchema**オブジェクトをサポートしている XML スキーマのみです。</span><span class="sxs-lookup"><span data-stu-id="a535c-105">Although the **XmlSchemaCollection** class stores both XDR schemas and XML Schemas, any method and property that takes or returns an **XmlSchema** object supports XML Schemas only.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a535c-106"><xref:System.Xml.Schema.XmlSchemaCollection> クラスは廃止されており、<xref:System.Xml.Schema.XmlSchemaSet> クラスに置き換えられています。</span><span class="sxs-lookup"><span data-stu-id="a535c-106">The <xref:System.Xml.Schema.XmlSchemaCollection> class is now obsolete and has been replaced with the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span> <span data-ttu-id="a535c-107">詳細については、<xref:System.Xml.Schema.XmlSchemaSet>クラス」を参照して[スキーマのコンパイルのための XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)です。</span><span class="sxs-lookup"><span data-stu-id="a535c-107">For more information about the <xref:System.Xml.Schema.XmlSchemaSet> class see, [XmlSchemaSet for Schema Compilation](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span></span>  
  
## <a name="add-schemas-to-the-collection"></a><span data-ttu-id="a535c-108">コレクションへのスキーマの追加</span><span class="sxs-lookup"><span data-stu-id="a535c-108">Add Schemas to the Collection</span></span>  
 <span data-ttu-id="a535c-109">使用してコレクションにスキーマが読み込まれて、**追加**メソッドの**XmlSchemaCollection**時に、スキーマは名前空間 URI に関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="a535c-109">Schemas are loaded to the collection using the **Add** method of **XmlSchemaCollection**, at which time the schema is associated with a namespace URI.</span></span> <span data-ttu-id="a535c-110">XML スキーマの場合、通常、この名前空間 URI がスキーマのターゲット名前空間になります。</span><span class="sxs-lookup"><span data-stu-id="a535c-110">For XML Schemas, the namespace URI will typically be the target namespace for the schema.</span></span> <span data-ttu-id="a535c-111">また、XDR スキーマの場合は、この名前空間 URI は、スキーマがコレクションに追加されたときに指定された名前空間です。</span><span class="sxs-lookup"><span data-stu-id="a535c-111">For XDR schemas, the namespace URI is the namespace specified when the schema was added to the collection.</span></span>  
  
## <a name="check-for-a-schema-in-the-collection"></a><span data-ttu-id="a535c-112">コレクション内のスキーマの確認</span><span class="sxs-lookup"><span data-stu-id="a535c-112">Check for a Schema in the Collection</span></span>  
 <span data-ttu-id="a535c-113">使用して、スキーマがコレクション内かどうかを確認することができます、 **Contains**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="a535c-113">You can check to see if a schema is in the collection by using the **Contains** method.</span></span> <span data-ttu-id="a535c-114">**Contains**メソッドは、いずれか、 **XmlSchema** (XML スキーマおよび XDR スキーマ) のスキーマに関連付けられているオブジェクト (XML スキーマ専用) または名前空間 URI を表す文字列。</span><span class="sxs-lookup"><span data-stu-id="a535c-114">The **Contains** method takes either an **XmlSchema** object (for XML Schemas only) or a string representing the namespace URI associated with the schema (for XML Schemas and XDR schemas).</span></span>  
  
## <a name="retrieve-a-schema-from-the-collection"></a><span data-ttu-id="a535c-115">コレクションからのスキーマの取得</span><span class="sxs-lookup"><span data-stu-id="a535c-115">Retrieve a Schema from the Collection</span></span>  
 <span data-ttu-id="a535c-116">使用して、コレクションからスキーマを取得することができます、**項目**プロパティです。</span><span class="sxs-lookup"><span data-stu-id="a535c-116">You can retrieve a schema from the collection by using the **Item** property.</span></span> <span data-ttu-id="a535c-117">**項目**プロパティが、スキーマでは、通常その対象名前空間に関連付けられた URI 名前空間を表す文字列を受け取り、返します、 **XmlSchema**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a535c-117">The **Item** property takes a string representing the namespace URI associated with the schema, typically its target namespace, and returns an **XmlSchema** object.</span></span> <span data-ttu-id="a535c-118">**項目**プロパティは XML スキーマにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="a535c-118">The **Item** property applies to XML Schemas only.</span></span> <span data-ttu-id="a535c-119">XDR スキーマの場合は、使用できるオブジェクト モデルがないため、戻り値は常に null 参照です。</span><span class="sxs-lookup"><span data-stu-id="a535c-119">The return value is always a null reference for XDR schemas because they do not have an object model available.</span></span>  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a><span data-ttu-id="a535c-120">XmlSchemaCollection を使用した XML ドキュメントの検証</span><span class="sxs-lookup"><span data-stu-id="a535c-120">Validate XML Documents Using XmlSchemaCollection</span></span>  
 <span data-ttu-id="a535c-121">使用して XML インスタンス ドキュメントを検証することができます、 **XmlSchemaCollection**作成することで、 **XmlSchemaCollection**オブジェクト、スキーマをコレクションに追加し、設定、**スキーマ**プロパティを**XmlValidatingReader**を割り当てる、作成した**XmlSchemaCollection**を**XmlValidatingReader**です。</span><span class="sxs-lookup"><span data-stu-id="a535c-121">You can validate an XML instance document using an **XmlSchemaCollection** by creating the **XmlSchemaCollection** object, adding your schemas to the collection, and setting the **Schemas** property on the **XmlValidatingReader** to assign the created **XmlSchemaCollection** to the **XmlValidatingReader**.</span></span>  
  
### <a name="improved-performance"></a><span data-ttu-id="a535c-122">パフォーマンスの向上</span><span class="sxs-lookup"><span data-stu-id="a535c-122">Improved Performance</span></span>  
 <span data-ttu-id="a535c-123">お勧め、同一のスキーマに対して 1 つ以上のドキュメントを検証する場合を使用すること、 **XmlSchemaCollection**メモリ内のスキーマをキャッシュすることによってパフォーマンスが向上が用意されているためです。</span><span class="sxs-lookup"><span data-stu-id="a535c-123">It is recommended, if you are validating more than one document against the same schema, that you use the **XmlSchemaCollection** because it provides better performance by caching schemas in memory.</span></span>  
  
 <span data-ttu-id="a535c-124">次のコード例を作成、 **XmlSchemaCollection**オブジェクトは、このコレクションにスキーマを追加し、設定、**スキーマ**プロパティです。</span><span class="sxs-lookup"><span data-stu-id="a535c-124">The following code example creates the **XmlSchemaCollection** object, adds schemas to the collection, and sets the **Schemas** property.</span></span>  
  
```vb  
Dim tr as XmlTextReader = new XmlTextReader("Books.xml")  
Dim vr as XmlValidatingReader = new XmlValidatingReader(tr)  
Dim xsc as XmlSchemaCollection = new XmlSchemaCollection  
xsc.Add("urn:bookstore-schema", "Books.xsd")  
vr.Schemas.Add(xsc)  
```  
  
```csharp  
XmlTextReader tr = new XmlTextReader("Books.xml");  
XmlValidatingReader vr = new XmlValidatingReader(tr);  
XmlSchemaCollection xsc = new XmlSchemaCollection();  
xsc.Add("urn:bookstore-schema", "Books.xsd");    
vr.Schemas.Add(xsc);  
```  
  
## <a name="see-also"></a><span data-ttu-id="a535c-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="a535c-125">See Also</span></span>  
 [<span data-ttu-id="a535c-126">XmlSchemaCollection を使用した XDR 検証</span><span class="sxs-lookup"><span data-stu-id="a535c-126">XDR Validation with XmlSchemaCollection</span></span>](../../../../docs/standard/data/xml/xdr-validation-with-xmlschemacollection.md)  
 [<span data-ttu-id="a535c-127">XmlSchemaCollection を使用した XML スキーマ (XSD) 検証</span><span class="sxs-lookup"><span data-stu-id="a535c-127">XML Schema (XSD) Validation with XmlSchemaCollection</span></span>](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemacollection.md)
