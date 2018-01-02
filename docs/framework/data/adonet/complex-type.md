---
title: "複合型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 50b29e5ae0df37238a16ba08898d307918f0b439
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="complex-type"></a><span data-ttu-id="bb57e-102">複合型</span><span class="sxs-lookup"><span data-stu-id="bb57e-102">complex type</span></span>
<span data-ttu-id="bb57e-103">A*複合型*豊富な構造化されたプロパティを定義するためのテンプレートです[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)またはその他の複合型。</span><span class="sxs-lookup"><span data-stu-id="bb57e-103">A *complex type* is a template for defining rich, structured properties on [entity types](../../../../docs/framework/data/adonet/entity-type.md) or on other complex types.</span></span> <span data-ttu-id="bb57e-104">各テンプレートには、以下が含まれています。</span><span class="sxs-lookup"><span data-stu-id="bb57e-104">Each template contains the following:</span></span>  
  
-   <span data-ttu-id="bb57e-105">一意の名前 </span><span class="sxs-lookup"><span data-stu-id="bb57e-105">A unique name.</span></span> <span data-ttu-id="bb57e-106">(必須)</span><span class="sxs-lookup"><span data-stu-id="bb57e-106">(Required)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bb57e-107">複合型の名前は、同じ名前空間のエンティティ型の名前と同じにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="bb57e-107">The name of a complex type cannot be the same as an entity type name within the same namespace.</span></span>  
  
-   <span data-ttu-id="bb57e-108">1 つまたは複数の形式でデータ[プロパティ](../../../../docs/framework/data/adonet/property.md)です。</span><span class="sxs-lookup"><span data-stu-id="bb57e-108">Data in the form of one or more [properties](../../../../docs/framework/data/adonet/property.md).</span></span> <span data-ttu-id="bb57e-109">(省略可能) </span><span class="sxs-lookup"><span data-stu-id="bb57e-109">(Optional.)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bb57e-110">複合型のプロパティには、別の複合型を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="bb57e-110">A property of a complex type can be another complex type.</span></span>  
  
 <span data-ttu-id="bb57e-111">複合型は、プリミティブ型のプロパティまたはその他の複合型の形式でデータ ペイロードを伝達できる点がエンティティ型と似ています。</span><span class="sxs-lookup"><span data-stu-id="bb57e-111">A complex type is similar to an entity type in that a complex type can carry a data payload in the form of primitive type properties or other complex types.</span></span> <span data-ttu-id="bb57e-112">ただし、複合型とエンティティ型の間にはいくつかの重要な違いがあります。</span><span class="sxs-lookup"><span data-stu-id="bb57e-112">However, there are some key differences between complex types and entity types:</span></span>  
  
-   <span data-ttu-id="bb57e-113">複合型には ID がないため、独立して存在することができません。</span><span class="sxs-lookup"><span data-stu-id="bb57e-113">Complex types do not have identities and therefore cannot exist independently.</span></span> <span data-ttu-id="bb57e-114">複合型は、エンティティ型またはその他の複合型のプロパティとしてのみ存在できます。</span><span class="sxs-lookup"><span data-stu-id="bb57e-114">Complex types can only exist as properties on entity types or other complex types.</span></span>  
  
-   <span data-ttu-id="bb57e-115">複合型には参加できません[アソシエーション](../../../../docs/framework/data/adonet/association-type.md)です。</span><span class="sxs-lookup"><span data-stu-id="bb57e-115">Complex types cannot participate in [associations](../../../../docs/framework/data/adonet/association-type.md).</span></span> <span data-ttu-id="bb57e-116">アソシエーションの end にも複雑な型であることができ、したがって[ナビゲーション プロパティ](../../../../docs/framework/data/adonet/navigation-property.md)複合型で定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="bb57e-116">Neither end of an association can be a complex type, and therefore [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) cannot be defined on complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb57e-117">例</span><span class="sxs-lookup"><span data-stu-id="bb57e-117">Example</span></span>  
 <span data-ttu-id="bb57e-118">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="bb57e-118">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="bb57e-119">次の CSDL は、`StreetAddress`、`City`、`StateOrProvince`、`Country`、および `PostalCode` のプリミティブ型のプロパティの複合型 Address を定義しています。</span><span class="sxs-lookup"><span data-stu-id="bb57e-119">The following CSDL defines a complex type, Address, with the primitive type properties `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 <span data-ttu-id="bb57e-120">エンティティ型のプロパティとして複合型 `Address` (上の図) を定義するには、エンティティ型の定義にプロパティの型を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb57e-120">To define the complex type `Address` (above) as a property on an entity type, you must declare the property type in the entity type definition.</span></span> <span data-ttu-id="bb57e-121">次の CSDL は、エンティティ型 (Publisher) に複合型として `Address` プロパティを宣言しています。</span><span class="sxs-lookup"><span data-stu-id="bb57e-121">The following CSDL declares the `Address` property as a complex type on an entity type (Publisher):</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a><span data-ttu-id="bb57e-122">参照</span><span class="sxs-lookup"><span data-stu-id="bb57e-122">See Also</span></span>  
 [<span data-ttu-id="bb57e-123">Entity Data Model キーの概念</span><span class="sxs-lookup"><span data-stu-id="bb57e-123">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="bb57e-124">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="bb57e-124">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
