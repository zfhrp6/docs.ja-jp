---
title: XmlSchemaCollection スキーマのコンパイル
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d64443f213603b1f5db9c256acc88e998e3f009a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571486"
---
# <a name="xmlschemacollection-schema-compilation"></a><span data-ttu-id="10656-102">XmlSchemaCollection スキーマのコンパイル</span><span class="sxs-lookup"><span data-stu-id="10656-102">XmlSchemaCollection Schema Compilation</span></span>
<span data-ttu-id="10656-103">**XmlSchemaCollection** は、XDR (XML-Data Reduced) スキーマや XML スキーマ定義言語 (XSD) スキーマを格納および検証できるキャッシュ (ライブラリ) です。</span><span class="sxs-lookup"><span data-stu-id="10656-103">The **XmlSchemaCollection** is a cache or library where XML-Data Reduced (XDR) and XML Schema definition language (XSD) schemas can be stored and validated.</span></span> <span data-ttu-id="10656-104">**XmlSchemaCollection** は、ファイルや URL からスキーマにアクセスしなくて済むようにスキーマをメモリにキャッシュすることによって、パフォーマンスの向上を図ります。</span><span class="sxs-lookup"><span data-stu-id="10656-104">**XmlSchemaCollection** improves performance by caching schemas in memory instead of accessing them from a file or URL.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10656-105">**XmlSchemaCollection** クラスには XDR スキーマと XML スキーマの両方が格納されますが、**XmlSchema** オブジェクトを受け取ったり返したりするメソッドおよびプロパティは XML スキーマのみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="10656-105">Although the **XmlSchemaCollection** class stores both XDR schemas and XML Schemas, any method and property that takes or returns an **XmlSchema** object supports XML Schemas only.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="10656-106"><xref:System.Xml.Schema.XmlSchemaCollection> クラスは廃止されており、<xref:System.Xml.Schema.XmlSchemaSet> クラスに置き換えられています。</span><span class="sxs-lookup"><span data-stu-id="10656-106">The <xref:System.Xml.Schema.XmlSchemaCollection> class is now obsolete and has been replaced with the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span> <span data-ttu-id="10656-107"><xref:System.Xml.Schema.XmlSchemaSet> クラスの詳細については、「[スキーマをコンパイルするための XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10656-107">For more information about the <xref:System.Xml.Schema.XmlSchemaSet> class see, [XmlSchemaSet for Schema Compilation](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span></span>  
  
## <a name="add-schemas-to-the-collection"></a><span data-ttu-id="10656-108">コレクションへのスキーマの追加</span><span class="sxs-lookup"><span data-stu-id="10656-108">Add Schemas to the Collection</span></span>  
 <span data-ttu-id="10656-109">スキーマを **XmlSchemaCollection** に読み込むには、そのコレクションの **Add** メソッドを使用します。読み込み時に、スキーマは名前空間 URI に関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="10656-109">Schemas are loaded to the collection using the **Add** method of **XmlSchemaCollection**, at which time the schema is associated with a namespace URI.</span></span> <span data-ttu-id="10656-110">XML スキーマの場合、通常、この名前空間 URI がスキーマのターゲット名前空間になります。</span><span class="sxs-lookup"><span data-stu-id="10656-110">For XML Schemas, the namespace URI will typically be the target namespace for the schema.</span></span> <span data-ttu-id="10656-111">また、XDR スキーマの場合は、この名前空間 URI は、スキーマがコレクションに追加されたときに指定された名前空間です。</span><span class="sxs-lookup"><span data-stu-id="10656-111">For XDR schemas, the namespace URI is the namespace specified when the schema was added to the collection.</span></span>  
  
## <a name="check-for-a-schema-in-the-collection"></a><span data-ttu-id="10656-112">コレクション内のスキーマの確認</span><span class="sxs-lookup"><span data-stu-id="10656-112">Check for a Schema in the Collection</span></span>  
 <span data-ttu-id="10656-113">スキーマがコレクション内にあるかどうかを確認するには、**Contains** メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="10656-113">You can check to see if a schema is in the collection by using the **Contains** method.</span></span> <span data-ttu-id="10656-114">**Contains** メソッドは、**XmlSchema** オブジェクト (XML スキーマ専用) またはスキーマに関連付けられた名前空間 URI を表す文字列 (XML スキーマと XDR スキーマ用) のいずれかを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="10656-114">The **Contains** method takes either an **XmlSchema** object (for XML Schemas only) or a string representing the namespace URI associated with the schema (for XML Schemas and XDR schemas).</span></span>  
  
## <a name="retrieve-a-schema-from-the-collection"></a><span data-ttu-id="10656-115">コレクションからのスキーマの取得</span><span class="sxs-lookup"><span data-stu-id="10656-115">Retrieve a Schema from the Collection</span></span>  
 <span data-ttu-id="10656-116">コレクションからスキーマを取得するには、**Item** プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="10656-116">You can retrieve a schema from the collection by using the **Item** property.</span></span> <span data-ttu-id="10656-117">**Item** プロパティは、スキーマに関連付けられた名前空間 URI (通常は、そのスキーマのターゲット名前空間) を表す文字列を受け取り、**XmlSchema** オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="10656-117">The **Item** property takes a string representing the namespace URI associated with the schema, typically its target namespace, and returns an **XmlSchema** object.</span></span> <span data-ttu-id="10656-118">**Item** プロパティは、XML スキーマにだけ適用されます。</span><span class="sxs-lookup"><span data-stu-id="10656-118">The **Item** property applies to XML Schemas only.</span></span> <span data-ttu-id="10656-119">XDR スキーマの場合は、使用できるオブジェクト モデルがないため、戻り値は常に null 参照です。</span><span class="sxs-lookup"><span data-stu-id="10656-119">The return value is always a null reference for XDR schemas because they do not have an object model available.</span></span>  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a><span data-ttu-id="10656-120">XmlSchemaCollection を使用した XML ドキュメントの検証</span><span class="sxs-lookup"><span data-stu-id="10656-120">Validate XML Documents Using XmlSchemaCollection</span></span>  
 <span data-ttu-id="10656-121">**XmlSchemaCollection** を使用して XML インスタンス ドキュメントを検証するには、**XmlSchemaCollection** オブジェクトを作成し、開発者が作成したスキーマをそのコレクションに追加し、**XmlValidatingReader** の **Schemas** プロパティを設定して、作成した **XmlSchemaCollection** をその **XmlValidatingReader** に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="10656-121">You can validate an XML instance document using an **XmlSchemaCollection** by creating the **XmlSchemaCollection** object, adding your schemas to the collection, and setting the **Schemas** property on the **XmlValidatingReader** to assign the created **XmlSchemaCollection** to the **XmlValidatingReader**.</span></span>  
  
### <a name="improved-performance"></a><span data-ttu-id="10656-122">パフォーマンスの向上</span><span class="sxs-lookup"><span data-stu-id="10656-122">Improved Performance</span></span>  
 <span data-ttu-id="10656-123">同じスキーマを基準として複数のドキュメントを検証する場合は、**XmlSchemaCollection** を使用することをお勧めします。このコレクションを使用すると、そのスキーマをメモリ内にキャッシュしてパフォーマンスの向上を図ることができます。</span><span class="sxs-lookup"><span data-stu-id="10656-123">It is recommended, if you are validating more than one document against the same schema, that you use the **XmlSchemaCollection** because it provides better performance by caching schemas in memory.</span></span>  
  
 <span data-ttu-id="10656-124">**XmlSchemaCollection** オブジェクトを作成し、そのコレクションにスキーマを追加し、**Schemas** プロパティを設定するコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="10656-124">The following code example creates the **XmlSchemaCollection** object, adds schemas to the collection, and sets the **Schemas** property.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="10656-125">参照</span><span class="sxs-lookup"><span data-stu-id="10656-125">See Also</span></span>  
 [<span data-ttu-id="10656-126">XmlSchemaCollection を使用した XDR 検証</span><span class="sxs-lookup"><span data-stu-id="10656-126">XDR Validation with XmlSchemaCollection</span></span>](../../../../docs/standard/data/xml/xdr-validation-with-xmlschemacollection.md)  
 [<span data-ttu-id="10656-127">XmlSchemaCollection を使用した XML スキーマ (XSD) 検証</span><span class="sxs-lookup"><span data-stu-id="10656-127">XML Schema (XSD) Validation with XmlSchemaCollection</span></span>](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemacollection.md)
