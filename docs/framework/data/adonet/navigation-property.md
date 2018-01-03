---
title: "ナビゲーション プロパティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: dc980a2c61be736e2c1d8e52d8f13d0ea5ed09f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="navigation-property"></a><span data-ttu-id="9bbb5-102">ナビゲーション プロパティ</span><span class="sxs-lookup"><span data-stu-id="9bbb5-102">navigation property</span></span>
<span data-ttu-id="9bbb5-103">A*ナビゲーション プロパティ*では、省略可能なプロパティ、[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)から 1 つのナビゲーションを可能にする[終了](../../../../docs/framework/data/adonet/association-end.md)の[アソシエーション](../../../../docs/framework/data/adonet/association-type.md)にその他の終了時刻です。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-103">A *navigation property* is an optional property on an [entity type](../../../../docs/framework/data/adonet/entity-type.md) that allows for navigation from one [end](../../../../docs/framework/data/adonet/association-end.md) of an [association](../../../../docs/framework/data/adonet/association-type.md) to the other end.</span></span> <span data-ttu-id="9bbb5-104">その他のとは異なり[プロパティ](../../../../docs/framework/data/adonet/property.md)、ナビゲーション プロパティがデータを伝達しません。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-104">Unlike other [properties](../../../../docs/framework/data/adonet/property.md), navigation properties do not carry data.</span></span>  
  
 <span data-ttu-id="9bbb5-105">ナビゲーション プロパティの定義には、以下が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-105">A navigation property definition includes the following:</span></span>  
  
-   <span data-ttu-id="9bbb5-106">名前。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-106">A name.</span></span> <span data-ttu-id="9bbb5-107">(必須)</span><span class="sxs-lookup"><span data-stu-id="9bbb5-107">(Required)</span></span>  
  
-   <span data-ttu-id="9bbb5-108">移動対象のアソシエーション。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-108">The association that it navigates.</span></span> <span data-ttu-id="9bbb5-109">(必須)</span><span class="sxs-lookup"><span data-stu-id="9bbb5-109">(Required)</span></span>  
  
-   <span data-ttu-id="9bbb5-110">移動対象のアソシエーションの End。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-110">The ends of the association that it navigates.</span></span> <span data-ttu-id="9bbb5-111">(必須)</span><span class="sxs-lookup"><span data-stu-id="9bbb5-111">(Required)</span></span>  
  
 <span data-ttu-id="9bbb5-112">ナビゲーション プロパティは、アソシエーション End の両方のエンティティ型で省略可能です。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-112">Note that navigation properties are optional on both entity types at the ends of an association.</span></span> <span data-ttu-id="9bbb5-113">1 つのアソシエーション End のエンティティ型にナビゲーション プロパティを定義した場合に、そのアソシエーションの他方の End でもエンティティ型にナビゲーション プロパティを定義する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-113">If you define a navigation property on one entity type at the end of an association, you do not have to define a navigation property on the entity type at the other end of the association.</span></span>  
  
 <span data-ttu-id="9bbb5-114">ナビゲーション プロパティのデータ型は、によって決定されます、[多重度](../../../../docs/framework/data/adonet/association-end-multiplicity.md)、リモートの[アソシエーション end](../../../../docs/framework/data/adonet/association-end.md)です。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-114">The data type of a navigation property is determined by the [multiplicity](../../../../docs/framework/data/adonet/association-end-multiplicity.md) of its remote [association end](../../../../docs/framework/data/adonet/association-end.md).</span></span> <span data-ttu-id="9bbb5-115">たとえば、ナビゲーション プロパティ `OrdersNavProp` が `Customer` エンティティ型に存在し、`Customer` と `Order` の間の一対多のアソシエーションで移動するとします。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-115">For example, suppose a navigation property, `OrdersNavProp`, exists on a `Customer` entity type and navigates a one-to-many association between `Customer` and `Order`.</span></span> <span data-ttu-id="9bbb5-116">ナビゲーション プロパティのリモートのアソシエーション End の多重度が多数 (*) であるため、そのデータ型は (`Order` の) コレクションになります。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-116">Because the remote association end for the navigation property has multiplicity of many (*), its data type is a collection (of `Order`).</span></span> <span data-ttu-id="9bbb5-117">同様に、`CustomerNavProp` エンティティ型にナビゲーション プロパティ、`Order` が存在する場合、リモート End の多重度が (1) であるため、データ型は `Customer` になります。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-117">Similarly, if a navigation property, `CustomerNavProp`, exists on the `Order` entity type, its data type would be `Customer`, because the multiplicity of the remote end is one (1).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bbb5-118">例</span><span class="sxs-lookup"><span data-stu-id="9bbb5-118">Example</span></span>  
 <span data-ttu-id="9bbb5-119">下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="9bbb5-120">Book エンティティ型には、ナビゲーション プロパティ、`Publisher` および `Authors` が定義されています。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-120">Navigation properties, `Publisher` and `Authors`, are defined on the Book entity type.</span></span> <span data-ttu-id="9bbb5-121">Publisher エンティティ型と `Books` エンティティ型には、ナビゲーション プロパティ、`Author` が定義されています。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-121">Navigation property `Books` is defined on both the Publisher entity type and the `Author` entity type.</span></span>  
  
 <span data-ttu-id="9bbb5-122">![ナビゲーション プロパティが含まれるモデル](../../../../docs/framework/data/adonet/media/modelwithnavprops.gif "ModelWithNavProps")</span><span class="sxs-lookup"><span data-stu-id="9bbb5-122">![Model with Navigation Properties](../../../../docs/framework/data/adonet/media/modelwithnavprops.gif "ModelWithNavProps")</span></span>  
  
 <span data-ttu-id="9bbb5-123">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-123">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="9bbb5-124">次の CSDL は、上のダイアグラムに示された `Book` エンティティ型を定義しています。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-124">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 <span data-ttu-id="9bbb5-125">ナビゲーション プロパティの定義に必要な情報を伝達するために、XML 属性が使用されています。属性 `Name` にはプロパティ名が含まれ、`Relationship` には移動対象のアソシエーション名が含まれ、`FromRole` および `ToRole` にはアソシエーション End が含まれています。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-125">Note that XML attributes are used to communicate the information necessary to define a navigation property: The attribute `Name` contains the name of the property, `Relationship` contains the name of the association it navigates, and `FromRole` and `ToRole` contain the ends of the association.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bbb5-126">参照</span><span class="sxs-lookup"><span data-stu-id="9bbb5-126">See Also</span></span>  
 [<span data-ttu-id="9bbb5-127">Entity Data Model キーの概念</span><span class="sxs-lookup"><span data-stu-id="9bbb5-127">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="9bbb5-128">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="9bbb5-128">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
