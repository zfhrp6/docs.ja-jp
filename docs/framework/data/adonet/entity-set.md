---
title: エンティティ セット
ms.date: 03/30/2017
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
ms.openlocfilehash: 5a8b4bdac2d0cb2065438bb390c002fcb690b1f6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="entity-set"></a><span data-ttu-id="69e49-102">エンティティ セット</span><span class="sxs-lookup"><span data-stu-id="69e49-102">entity set</span></span>
<span data-ttu-id="69e49-103">*エンティティ セット*の論理的なコンテナーは、のインスタンス、[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)とそのエンティティ型から派生した任意の型のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="69e49-103">An *entity set* is a logical container for instances of an [entity type](../../../../docs/framework/data/adonet/entity-type.md) and instances of any type derived from that entity type.</span></span> <span data-ttu-id="69e49-104">(派生型については、次を参照してください[Entity Data Model: 継承](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)。)。エンティティ型とエンティティ セットの関係は、リレーショナル データベースの行とテーブルの関係に似ており、エンティティ型は行のようにデータ構造を表し、エンティティ セットにはテーブルのように構造のインスタンスが格納されます。</span><span class="sxs-lookup"><span data-stu-id="69e49-104">(For information about derived types, see [Entity Data Model: Inheritance](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).) The relationship between an entity type and an entity set is analogous to the relationship between a row and a table in a relational database: Like a row, an entity type describes data structure, and, like a table, an entity set contains instances of a given structure.</span></span> <span data-ttu-id="69e49-105">エンティティ セットは、データ モデリング構造ではなく、データ構造を表しません。</span><span class="sxs-lookup"><span data-stu-id="69e49-105">An entity set is not a data modeling construct; it does not describe the structure of data.</span></span> <span data-ttu-id="69e49-106">エンティティ セットは、エンティティ型のインスタンスをグループ化してデータ ストアにマップするための、ホスト環境またはストレージ環境 (共通言語ランタイムや SQL Server データベースなど) の構造を提供します。</span><span class="sxs-lookup"><span data-stu-id="69e49-106">Instead, an entity set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group entity type instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="69e49-107">内のエンティティ セットが定義されている、[エンティティ コンテナー](../../../../docs/framework/data/adonet/entity-container.md)、エンティティ セットの論理的なグループであると[アソシエーション セット](../../../../docs/framework/data/adonet/association-set.md)です。</span><span class="sxs-lookup"><span data-stu-id="69e49-107">An entity set is defined within an [entity container](../../../../docs/framework/data/adonet/entity-container.md), which is a logical grouping of entity sets and [association sets](../../../../docs/framework/data/adonet/association-set.md).</span></span>  
  
 <span data-ttu-id="69e49-108">エンティティ型のインスタンスがエンティティ セット内に存在できるようにするには、次の条件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="69e49-108">For an entity type instance to exist in an entity set, the following must be true:</span></span>  
  
-   <span data-ttu-id="69e49-109">インスタンスの型がエンティティ セットの基本になるエンティティ型と同じであるか、インスタンスの型がエンティティ型のサブタイプであること。</span><span class="sxs-lookup"><span data-stu-id="69e49-109">The type of the instance is either the same as the entity type on which the entity set is based, or the type of the instance is a subtype of the entity type.</span></span>  
  
-   <span data-ttu-id="69e49-110">[エンティティ キー](../../../../docs/framework/data/adonet/entity-key.md)インスタンスは、エンティティ セット内で一意です。</span><span class="sxs-lookup"><span data-stu-id="69e49-110">The [entity key](../../../../docs/framework/data/adonet/entity-key.md) for the instance is unique within the entity set.</span></span>  
  
-   <span data-ttu-id="69e49-111">インスタンスが他のエンティティ セットに存在しないこと。</span><span class="sxs-lookup"><span data-stu-id="69e49-111">The instance does not exist in any other entity set.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="69e49-112">同じエンティティ型を使用して複数のエンティティ セットを定義できますが、特定のエンティティ型のインスタンスは、1 つのエンティティ セット内のみに存在できます。</span><span class="sxs-lookup"><span data-stu-id="69e49-112">Multiple entity sets can be defined using the same entity type, but an instance of a given entity type can only exist in one entity set.</span></span>  
  
 <span data-ttu-id="69e49-113">概念モデルの各エンティティ型にはエンティティ セットを定義する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="69e49-113">You do not have to define an entity set for each entity type in a conceptual model.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69e49-114">例</span><span class="sxs-lookup"><span data-stu-id="69e49-114">Example</span></span>  
 <span data-ttu-id="69e49-115">下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。</span><span class="sxs-lookup"><span data-stu-id="69e49-115">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 <span data-ttu-id="69e49-116">![モデルの例](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="69e49-116">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="69e49-117">次のダイアグラムには、上の概念モデルに基づく 2 つのエンティティ セット (`Books` および `Publishers`) と、アソシエーション セット(`PublishedBy`) を示しています。</span><span class="sxs-lookup"><span data-stu-id="69e49-117">The following diagram shows two entity sets (`Books` and `Publishers`) and an association set (`PublishedBy`) based on the conceptual model shown above.</span></span> <span data-ttu-id="69e49-118">Bi、`Books`エンティティ セットのインスタンスを表し、`Book`実行時にエンティティ型。</span><span class="sxs-lookup"><span data-stu-id="69e49-118">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="69e49-119">同様に、Pj を表す、`Publisher`インスタンス、`Publishers`エンティティ セット。</span><span class="sxs-lookup"><span data-stu-id="69e49-119">Similarly, Pj represent a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="69e49-120">BiPj がのインスタンスを表し、`PublishedBy`のアソシエーション、`PublishedBy`アソシエーション セット。</span><span class="sxs-lookup"><span data-stu-id="69e49-120">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 <span data-ttu-id="69e49-121">![例の設定](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span><span class="sxs-lookup"><span data-stu-id="69e49-121">![Sets Example](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span></span>  
  
 <span data-ttu-id="69e49-122">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="69e49-122">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="69e49-123">次の CSDL は、上の概念モデルに示された各エンティティ型に対して 1 つのエンティティ セットを持つエンティティ コンテナーを定義しています。</span><span class="sxs-lookup"><span data-stu-id="69e49-123">The following CSDL defines an entity container with one entity set for each entity type in the conceptual model shown above.</span></span> <span data-ttu-id="69e49-124">各エンティティ セットの名前とエンティティ型は、XML 属性で定義されています。</span><span class="sxs-lookup"><span data-stu-id="69e49-124">Note that the name and entity type for each entity set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="69e49-125">型ごとに複数のエンティティ セット (Multiple-Entity-Sets-per-Type: MEST) を定義できます。</span><span class="sxs-lookup"><span data-stu-id="69e49-125">It is possible to define multiple entity sets per type (MEST).</span></span> <span data-ttu-id="69e49-126">次の CSDL は、`Book` エンティティ型のエンティティ セットを 2 つ持つエンティティ コンテナーを定義しています。</span><span class="sxs-lookup"><span data-stu-id="69e49-126">The following CSDL defines an entity container with two entity sets for the `Book` entity type:</span></span>  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a><span data-ttu-id="69e49-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="69e49-127">See Also</span></span>  
 [<span data-ttu-id="69e49-128">Entity Data Model キーの概念</span><span class="sxs-lookup"><span data-stu-id="69e49-128">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="69e49-129">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="69e49-129">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
