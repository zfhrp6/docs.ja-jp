---
title: 参照整合性制約
ms.date: 03/30/2017
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
ms.openlocfilehash: a4d63e07da0c75b8a0369933fccfc0cc66fcc40b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352640"
---
# <a name="referential-integrity-constraint"></a><span data-ttu-id="974bf-102">参照整合性制約</span><span class="sxs-lookup"><span data-stu-id="974bf-102">referential integrity constraint</span></span>
<span data-ttu-id="974bf-103">A*参照整合性制約*Entity Data Model (EDM) では、リレーショナル データベースの参照整合性制約に似ています。</span><span class="sxs-lookup"><span data-stu-id="974bf-103">A *referential integrity constraint* in the Entity Data Model (EDM) is similar to a referential integrity constraint in a relational database.</span></span> <span data-ttu-id="974bf-104">データベース テーブルから列 (または列) が、別のテーブルの主キーを参照できるように、同じ方法で、[プロパティ](../../../../docs/framework/data/adonet/property.md)(またはプロパティ) の[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)参照できる、[エンティティ キー](../../../../docs/framework/data/adonet/entity-key.md)別のエンティティ型。</span><span class="sxs-lookup"><span data-stu-id="974bf-104">In the same way that a column (or columns) from a database table can reference the primary key of another table, a [property](../../../../docs/framework/data/adonet/property.md) (or properties) of an [entity type](../../../../docs/framework/data/adonet/entity-type.md) can reference the [entity key](../../../../docs/framework/data/adonet/entity-key.md) of another entity type.</span></span> <span data-ttu-id="974bf-105">参照されるエンティティ型が呼び出される、*プリンシパル end*制約のです。</span><span class="sxs-lookup"><span data-stu-id="974bf-105">The entity type that is referenced is called the *principal end* of the constraint.</span></span> <span data-ttu-id="974bf-106">プリンシパル end を参照するエンティティ型が呼び出される、*依存 end*制約のです。</span><span class="sxs-lookup"><span data-stu-id="974bf-106">The entity type that references the principal end is called the *dependent end* of the constraint.</span></span>  
  
 <span data-ttu-id="974bf-107">参照整合性制約がの一部として定義されている、[アソシエーション](../../../../docs/framework/data/adonet/association-type.md)2 つのエンティティ型の間です。</span><span class="sxs-lookup"><span data-stu-id="974bf-107">A referential integrity constraint is defined as part of an [association](../../../../docs/framework/data/adonet/association-type.md) between two entity types.</span></span> <span data-ttu-id="974bf-108">参照整合性制約の定義には、次の情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="974bf-108">The definition for a referential integrity constraint specifies the following information:</span></span>  
  
-   <span data-ttu-id="974bf-109">制約のプリンシパル End。</span><span class="sxs-lookup"><span data-stu-id="974bf-109">The principal end of the constraint.</span></span> <span data-ttu-id="974bf-110">(エンティティ キーが依存 End により参照されるエンティティ型)</span><span class="sxs-lookup"><span data-stu-id="974bf-110">(An entity type whose entity key is referenced by the dependent end.)</span></span>  
  
-   <span data-ttu-id="974bf-111">プリンシパル End のエンティティ キー。</span><span class="sxs-lookup"><span data-stu-id="974bf-111">The entity key of the principal end.</span></span>  
  
-   <span data-ttu-id="974bf-112">制約の依存 End。</span><span class="sxs-lookup"><span data-stu-id="974bf-112">The dependent end of the constraint.</span></span> <span data-ttu-id="974bf-113">(プリンシパル End のエンティティ キーを参照するプロパティを持つエンティティ型)</span><span class="sxs-lookup"><span data-stu-id="974bf-113">(An entity type that has a property or properties that reference the entity key of the principal end.)</span></span>  
  
-   <span data-ttu-id="974bf-114">依存 End の参照プロパティ。</span><span class="sxs-lookup"><span data-stu-id="974bf-114">The referencing property or properties of the dependent end.</span></span>  
  
 <span data-ttu-id="974bf-115">EDM の参照整合性制約の目的は、常に有効なアソシエーションが存在することを確認するためです。</span><span class="sxs-lookup"><span data-stu-id="974bf-115">The purpose of referential integrity constraints in the EDM is to ensure that valid associations always exist.</span></span> <span data-ttu-id="974bf-116">詳細については、次を参照してください。[外部キー プロパティ](../../../../docs/framework/data/adonet/foreign-key-property.md)です。</span><span class="sxs-lookup"><span data-stu-id="974bf-116">For more information, see [foreign key property](../../../../docs/framework/data/adonet/foreign-key-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="974bf-117">例</span><span class="sxs-lookup"><span data-stu-id="974bf-117">Example</span></span>  
 <span data-ttu-id="974bf-118">下のダイアグラムは、`WrittenBy` および `PublishedBy` という 2 つのアソシエーションの概念モデルを示しています。</span><span class="sxs-lookup"><span data-stu-id="974bf-118">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span> <span data-ttu-id="974bf-119">`Book` エンティティ型には、`PublisherId` というプロパティがあります。`Publisher` アソシエーションに参照整合性制約を定義するときに、このプロパティは `PublishedBy` エンティティ型のエンティティ キーを参照します。</span><span class="sxs-lookup"><span data-stu-id="974bf-119">The `Book` entity type has a property, `PublisherId`, that references the entity key of the `Publisher` entity type when you define a referential integrity constraint on the `PublishedBy` association.</span></span>  
  
 <span data-ttu-id="974bf-120">![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")</span><span class="sxs-lookup"><span data-stu-id="974bf-120">![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")</span></span>  
  
 <span data-ttu-id="974bf-121">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="974bf-121">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="974bf-122">次の CSDL は、上の概念モデルに示された `PublishedBy` アソシエーションの参照整合性制約を定義しています。</span><span class="sxs-lookup"><span data-stu-id="974bf-122">The following CSDL defines a referential integrity constraint on the `PublishedBy` association shown in the conceptual model above.</span></span>  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a><span data-ttu-id="974bf-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="974bf-123">See Also</span></span>  
 [<span data-ttu-id="974bf-124">Entity Data Model キーの概念</span><span class="sxs-lookup"><span data-stu-id="974bf-124">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="974bf-125">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="974bf-125">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
