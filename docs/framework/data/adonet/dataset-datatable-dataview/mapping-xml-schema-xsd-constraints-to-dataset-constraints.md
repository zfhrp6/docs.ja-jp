---
title: XML スキーマ (XSD) 制約の DataSet 制約への割り当て
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: 0a23e7a7ab6456125559ffd8fa19ffa5eba9335d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="82989-102">XML スキーマ (XSD) 制約の DataSet 制約への割り当て</span><span class="sxs-lookup"><span data-stu-id="82989-102">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="82989-103">XML スキーマ定義言語 (XSD) を使用すると、定義する要素と属性で制約を指定できます。</span><span class="sxs-lookup"><span data-stu-id="82989-103">The XML Schema definition language (XSD) allows constraints to be specified on the elements and attributes it defines.</span></span> <span data-ttu-id="82989-104">内のリレーショナル スキーマに XML スキーマをマップするとき、 <xref:System.Data.DataSet>、XML スキーマの制約は、テーブルや列内で適切なリレーショナル制約にマップされて、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="82989-104">When mapping an XML Schema to relational schema in a <xref:System.Data.DataSet>, XML Schema constraints are mapped to appropriate relational constraints on the tables and columns within the **DataSet**.</span></span>  
  
 <span data-ttu-id="82989-105">このセクションでは、次の XML スキーマの制約の割り当てについて説明します。</span><span class="sxs-lookup"><span data-stu-id="82989-105">This section discusses the mapping of the following XML Schema constraints:</span></span>  
  
-   <span data-ttu-id="82989-106">使用して指定される unique 制約、**一意**要素。</span><span class="sxs-lookup"><span data-stu-id="82989-106">The uniqueness constraint specified using the **unique** element.</span></span>  
  
-   <span data-ttu-id="82989-107">使用して指定されたキーの制約、**キー**要素。</span><span class="sxs-lookup"><span data-stu-id="82989-107">The key constraint specified using the **key** element.</span></span>  
  
-   <span data-ttu-id="82989-108">使用して指定されるキー参照制約、 **keyref**要素。</span><span class="sxs-lookup"><span data-stu-id="82989-108">The keyref constraint specified using the **keyref** element.</span></span>  
  
 <span data-ttu-id="82989-109">要素または属性に対して制約を指定することにより、同じスキーマに基づくあらゆるドキュメントで、その要素の値について特定の制限を適用できます。</span><span class="sxs-lookup"><span data-stu-id="82989-109">By using a constraint on an element or attribute, you specify certain restrictions on the values of the element in any instance of the document.</span></span> <span data-ttu-id="82989-110">たとえば、キー制約を**CustomerID**の子要素、**顧客**スキーマ内の要素には、ことを示しますの値、 **CustomerID**子要素にする必要があります任意のドキュメント インスタンス内で一意で null 値は許可されていません。</span><span class="sxs-lookup"><span data-stu-id="82989-110">For example, a key constraint on a **CustomerID** child element of a **Customer** element in the schema indicates that the values of the **CustomerID** child element must be unique in any document instance, and that null values are not allowed.</span></span>  
  
 <span data-ttu-id="82989-111">さらに、ドキュメント内のリレーションシップを確立するために、ドキュメント内の要素および属性間に制約を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="82989-111">Constraints can also be specified between elements and attributes in a document, in order to establish a relationship within the document.</span></span> <span data-ttu-id="82989-112">ドキュメント内で制約を指定するためにスキーマ内で key 制約または keyref 制約を使用すると、ドキュメントの要素と属性間にリレーションシップを持つことになります。</span><span class="sxs-lookup"><span data-stu-id="82989-112">The key and keyref constraints are used in the schema to specify the constraints within the document, resulting in a relationship between document elements and attributes.</span></span>  
  
 <span data-ttu-id="82989-113">マッピング プロセス内で作成されたテーブルに適切な制約にこれらのスキーマの制約を変換する、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="82989-113">The mapping process converts these schema constraints into appropriate constraints on the tables created within the **DataSet**.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="82989-114">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="82989-114">In This Section</span></span>  
 [<span data-ttu-id="82989-115">XML スキーマ (XSD) の UNIQUE 制約の DataSet 制約への割り当て</span><span class="sxs-lookup"><span data-stu-id="82989-115">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="82989-116">Unique 制約を作成するために使用する XML スキーマの要素について説明します、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="82989-116">Describes the XML Schema elements used to create unique constraints in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="82989-117">XML スキーマ (XSD) のキー制約の DataSet 制約への割り当て</span><span class="sxs-lookup"><span data-stu-id="82989-117">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="82989-118">キー制約 (一意制約は null 値が許可されていません) を作成するために使用する XML スキーマの要素について説明します、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="82989-118">Describes the XML Schema elements used to create key constraints (unique constraints where null values are not allowed) in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="82989-119">XML スキーマ (XSD) のキー参照制約の DataSet 制約への割り当て</span><span class="sxs-lookup"><span data-stu-id="82989-119">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="82989-120">参照で (外部キー) 制約の作成に使用する XML スキーマ要素について説明します、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="82989-120">Describes the XML Schema elements used to create keyref (foreign key) constraints in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="82989-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="82989-121">Related Sections</span></span>  
 [<span data-ttu-id="82989-122">XML スキーマ (XSD) からの DataSet リレーショナル構造の派生</span><span class="sxs-lookup"><span data-stu-id="82989-122">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="82989-123">リレーショナル構造体、またはスキーマについて説明します、**データセット**XSD スキーマから作成します。</span><span class="sxs-lookup"><span data-stu-id="82989-123">Describes the relational structure, or schema, of a **DataSet** that is created from XSD schema.</span></span>  
  
 [<span data-ttu-id="82989-124">XML スキーマ (XSD) からの DataSet リレーションの生成</span><span class="sxs-lookup"><span data-stu-id="82989-124">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="82989-125">テーブルの列間のリレーションを作成するために使用する XML スキーマの要素について説明します、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="82989-125">Describes the XML Schema elements used to create relations between table columns in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82989-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="82989-126">See Also</span></span>  
 [<span data-ttu-id="82989-127">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="82989-127">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
