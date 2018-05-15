---
title: エンティティ コンテナー
ms.date: 03/30/2017
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
ms.openlocfilehash: ed2123629c61b179e07e86effa0c39d9a3222b62
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="entity-container"></a><span data-ttu-id="bcbc8-102">エンティティ コンテナー</span><span class="sxs-lookup"><span data-stu-id="bcbc8-102">entity container</span></span>
<span data-ttu-id="bcbc8-103">*エンティティ コンテナー*の論理的なグループは、[エンティティ セット](../../../../docs/framework/data/adonet/entity-set.md)、[アソシエーション セット](../../../../docs/framework/data/adonet/association-set.md)、および[関数インポート](../../../../docs/framework/data/adonet/model-declared-function.md)です。</span><span class="sxs-lookup"><span data-stu-id="bcbc8-103">An *entity container* is a logical grouping of [entity sets](../../../../docs/framework/data/adonet/entity-set.md), [association sets](../../../../docs/framework/data/adonet/association-set.md), and [function imports](../../../../docs/framework/data/adonet/model-declared-function.md).</span></span>  
  
 <span data-ttu-id="bcbc8-104">概念モデルで定義するエンティティ コンテナーは、次の条件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcbc8-104">The following must be true of an entity container defined in a conceptual model:</span></span>  
  
-   <span data-ttu-id="bcbc8-105">1 つ以上のエンティティ コンテナーを各概念モデルに定義すること。</span><span class="sxs-lookup"><span data-stu-id="bcbc8-105">At least one entity container must be defined in each conceptual model.</span></span>  
  
-   <span data-ttu-id="bcbc8-106">各概念モデル内のエンティティ コンテナー名が一意であること。</span><span class="sxs-lookup"><span data-stu-id="bcbc8-106">The entity container must have a unique name within each conceptual model.</span></span>  
  
 <span data-ttu-id="bcbc8-107">エンティティ コンテナーは、1 つ以上の名前空間に定義されたエンティティ型またはアソシエーションを使用するエンティティ セットまたはアソシエーション セットを定義できます。</span><span class="sxs-lookup"><span data-stu-id="bcbc8-107">An entity container can define entity sets or association sets that use entity types or associations defined in one or more namespaces.</span></span> <span data-ttu-id="bcbc8-108">詳細については、次を参照してください。 [Entity Data Model: 名前空間](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md)です。</span><span class="sxs-lookup"><span data-stu-id="bcbc8-108">For more information, see [Entity Data Model: Namespaces](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcbc8-109">例</span><span class="sxs-lookup"><span data-stu-id="bcbc8-109">Example</span></span>  
 <span data-ttu-id="bcbc8-110">下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。</span><span class="sxs-lookup"><span data-stu-id="bcbc8-110">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  <span data-ttu-id="bcbc8-111">詳細については、次の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bcbc8-111">See the next example for more information.</span></span>  
  
 <span data-ttu-id="bcbc8-112">![モデルの例](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="bcbc8-112">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="bcbc8-113">ダイアグラムにはエンティティ コンテナー情報が示されていませんが、概念モデルにはエンティティ コンテナーを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcbc8-113">Although the diagram does not convey entity container information, the conceptual model must define an entity container.</span></span> <span data-ttu-id="bcbc8-114">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)概念スキーマ定義言語と呼ばれる DSL を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="bcbc8-114">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="bcbc8-115">次の CSDL は、上のダイアグラムに示された概念モデルのエンティティ コンテナーを定義しています。</span><span class="sxs-lookup"><span data-stu-id="bcbc8-115">The following CSDL defines an entity container for the conceptual model shown in the diagram above.</span></span> <span data-ttu-id="bcbc8-116">エンティティ コンテナー名は XML 属性に定義されています。</span><span class="sxs-lookup"><span data-stu-id="bcbc8-116">Note that the entity container name is defined in an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="bcbc8-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="bcbc8-117">See Also</span></span>  
 [<span data-ttu-id="bcbc8-118">Entity Data Model キーの概念</span><span class="sxs-lookup"><span data-stu-id="bcbc8-118">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="bcbc8-119">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="bcbc8-119">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
