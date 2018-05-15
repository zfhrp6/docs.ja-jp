---
title: エンティティ型
ms.date: 03/30/2017
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
ms.openlocfilehash: c694f29d36988ea52aeca650cf2bba2c50c91e89
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="entity-type"></a><span data-ttu-id="91ef7-102">エンティティ型</span><span class="sxs-lookup"><span data-stu-id="91ef7-102">entity type</span></span>
<span data-ttu-id="91ef7-103">*エンティティ型*は Entity Data Model (EDM) でのデータの構造を記述するための基本的なビルド ブロックです。</span><span class="sxs-lookup"><span data-stu-id="91ef7-103">The *entity type* is the fundamental building block for describing the structure of data with the Entity Data Model (EDM).</span></span> <span data-ttu-id="91ef7-104">概念モデルでのエンティティ型は、顧客や注文のように、トップレベル概念の構造を表します。</span><span class="sxs-lookup"><span data-stu-id="91ef7-104">In a conceptual model, an entity type represents the structure of top-level concepts, such as customers or orders.</span></span> <span data-ttu-id="91ef7-105">エンティティ型は、エンティティ型のインスタンスのテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="91ef7-105">An entity type is a template for entity type instances.</span></span> <span data-ttu-id="91ef7-106">各テンプレートには、次の情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="91ef7-106">Each template contains the following information:</span></span>  
  
-   <span data-ttu-id="91ef7-107">一意の名前 </span><span class="sxs-lookup"><span data-stu-id="91ef7-107">A unique name.</span></span> <span data-ttu-id="91ef7-108">(必須) </span><span class="sxs-lookup"><span data-stu-id="91ef7-108">(Required.)</span></span>  
  
-   <span data-ttu-id="91ef7-109">[エンティティ キー](../../../../docs/framework/data/adonet/entity-key.md) 1 つまたは複数のプロパティで定義します。</span><span class="sxs-lookup"><span data-stu-id="91ef7-109">An [entity key](../../../../docs/framework/data/adonet/entity-key.md) defined by one or more properties.</span></span> <span data-ttu-id="91ef7-110">(必須) </span><span class="sxs-lookup"><span data-stu-id="91ef7-110">(Required.)</span></span>  
  
-   <span data-ttu-id="91ef7-111">データの形式で[プロパティ](../../../../docs/framework/data/adonet/property.md)です。</span><span class="sxs-lookup"><span data-stu-id="91ef7-111">Data in the form of [properties](../../../../docs/framework/data/adonet/property.md).</span></span> <span data-ttu-id="91ef7-112">(省略可能) </span><span class="sxs-lookup"><span data-stu-id="91ef7-112">(Optional.)</span></span>  
  
-   <span data-ttu-id="91ef7-113">[ナビゲーション プロパティ](../../../../docs/framework/data/adonet/navigation-property.md)から 1 つのナビゲーションを可能にする[終了](../../../../docs/framework/data/adonet/association-end.md)の[アソシエーション](../../../../docs/framework/data/adonet/association-type.md)もう一方の end にします。</span><span class="sxs-lookup"><span data-stu-id="91ef7-113">[Navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) that allow for navigation from one [end](../../../../docs/framework/data/adonet/association-end.md) of an [association](../../../../docs/framework/data/adonet/association-type.md) to the other end.</span></span> <span data-ttu-id="91ef7-114">(オプション)。</span><span class="sxs-lookup"><span data-stu-id="91ef7-114">(Optional)</span></span>  
  
 <span data-ttu-id="91ef7-115">アプリケーションでは、エンティティ型のインスタンスが特定のオブジェクト (特定の顧客や注文など) を表します。</span><span class="sxs-lookup"><span data-stu-id="91ef7-115">In an application, an instance of an entity type represents a specific object (such as a specific customer or order).</span></span> <span data-ttu-id="91ef7-116">エンティティ型の各インスタンスを一意にいる必要があります[エンティティ キー](../../../../docs/framework/data/adonet/entity-key.md)内で、[エンティティ セット](../../../../docs/framework/data/adonet/entity-set.md)です。</span><span class="sxs-lookup"><span data-stu-id="91ef7-116">Each instance of an entity type must have a unique [entity key](../../../../docs/framework/data/adonet/entity-key.md) within an [entity set](../../../../docs/framework/data/adonet/entity-set.md).</span></span>  
  
 <span data-ttu-id="91ef7-117">2 つのエンティティ型のインスタンスは、型が同じであり、エンティティ キーの値が等しい場合にのみ、等価のインスタンスと見なされます。</span><span class="sxs-lookup"><span data-stu-id="91ef7-117">Two entity type instances are considered equal only if they are of the same type and the values of their entity keys are the same.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91ef7-118">例</span><span class="sxs-lookup"><span data-stu-id="91ef7-118">Example</span></span>  
 <span data-ttu-id="91ef7-119">下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。</span><span class="sxs-lookup"><span data-stu-id="91ef7-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`:</span></span>  
  
 <span data-ttu-id="91ef7-120">![モデルの例](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="91ef7-120">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="91ef7-121">各エンティティ型のエンティティ キーを構成するプロパティには、"(キー)" と示されています。</span><span class="sxs-lookup"><span data-stu-id="91ef7-121">Note that the properties of each entity type that make up its entity key are denoted with "(Key)".</span></span>  
  
 <span data-ttu-id="91ef7-122">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="91ef7-122">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="91ef7-123">次の CSDL は、上のダイアグラムに示された `Book` エンティティ型を定義しています。</span><span class="sxs-lookup"><span data-stu-id="91ef7-123">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a><span data-ttu-id="91ef7-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="91ef7-124">See Also</span></span>  
 [<span data-ttu-id="91ef7-125">Entity Data Model キーの概念</span><span class="sxs-lookup"><span data-stu-id="91ef7-125">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="91ef7-126">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="91ef7-126">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [<span data-ttu-id="91ef7-127">facet</span><span class="sxs-lookup"><span data-stu-id="91ef7-127">facet</span></span>](../../../../docs/framework/data/adonet/facet.md)
