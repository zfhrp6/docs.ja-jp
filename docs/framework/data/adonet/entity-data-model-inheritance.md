---
title: "Entity Data Model: 継承"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42c7ef24-710a-4af9-8493-cd41c399ecb0
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6e6207087524a1ec1201511a91a810f02449e610
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="entity-data-model-inheritance"></a><span data-ttu-id="534d6-102">Entity Data Model: 継承</span><span class="sxs-lookup"><span data-stu-id="534d6-102">Entity Data Model: Inheritance</span></span>
<span data-ttu-id="534d6-103">Entity Data Model (EDM) の継承をサポートしている[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)です。</span><span class="sxs-lookup"><span data-stu-id="534d6-103">The Entity Data Model (EDM) supports inheritance for [entity types](../../../../docs/framework/data/adonet/entity-type.md).</span></span> <span data-ttu-id="534d6-104">EDM の継承は、オブジェクト指向プログラミング言語におけるクラスの継承に似ています。</span><span class="sxs-lookup"><span data-stu-id="534d6-104">Inheritance in the EDM is similar to inheritance for classes in object-oriented programming languages.</span></span> <span data-ttu-id="534d6-105">オブジェクト指向言語でクラスでは、概念モデルで定義できます、エンティティ型と同じように (、*派生型*) 別のエンティティ型から継承する (、*基本型*)。</span><span class="sxs-lookup"><span data-stu-id="534d6-105">Like with classes in object-oriented languages, in a conceptual model you can define an entity type (a *derived type*) that inherits from another entity type (the *base type*).</span></span> <span data-ttu-id="534d6-106">ただし、オブジェクト指向プログラミングのクラスとは異なり、概念モデルで、派生型常にすべてを継承、[プロパティ](../../../../docs/framework/data/adonet/property.md)と[ナビゲーション プロパティ](../../../../docs/framework/data/adonet/navigation-property.md)の基本型です。</span><span class="sxs-lookup"><span data-stu-id="534d6-106">However, unlike classes in object-oriented programming, in a conceptual model the derived type always inherits all the [properties](../../../../docs/framework/data/adonet/property.md) and [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) of the base type.</span></span> <span data-ttu-id="534d6-107">派生型の継承プロパティは、オーバーライドできません。</span><span class="sxs-lookup"><span data-stu-id="534d6-107">You cannot override inherited properties in a derived type.</span></span>  
  
 <span data-ttu-id="534d6-108">概念モデルでは、派生型が別の派生型を継承する継承階層を構築することができます。</span><span class="sxs-lookup"><span data-stu-id="534d6-108">In a conceptual model you can build inheritance hierarchies in which a derived type inherits from another derived type.</span></span> <span data-ttu-id="534d6-109">階層 (派生型ではない階層内の 1 つの型) の上部にある型が呼び出される、*ルート型*です。</span><span class="sxs-lookup"><span data-stu-id="534d6-109">The type at the top of the hierarchy (the one type in the hierarchy that is not a derived type) is called the *root type*.</span></span> <span data-ttu-id="534d6-110">継承階層で、[エンティティ キー](../../../../docs/framework/data/adonet/entity-key.md)ルート型で定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="534d6-110">In an inheritance hierarchy, the [entity key](../../../../docs/framework/data/adonet/entity-key.md) must be defined on the root type.</span></span>  
  
 <span data-ttu-id="534d6-111">複数の型から派生型を継承する継承階層を構築することはできません。</span><span class="sxs-lookup"><span data-stu-id="534d6-111">You cannot build inheritance hierarchies in which a derived type inherits from more than one type.</span></span> <span data-ttu-id="534d6-112">たとえば、`Book` エンティティ型の概念モデルでは、それぞれ `FictionBook` から継承する派生型、`NonFictionBook` および `Book` を定義することができます。</span><span class="sxs-lookup"><span data-stu-id="534d6-112">For example, in a conceptual model with a `Book` entity type, you could define derived types `FictionBook` and `NonFictionBook` that each inherit from `Book`.</span></span> <span data-ttu-id="534d6-113">しかし、`FictionBook` 型と `NonFictionBook` 型の両方から継承する型を定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="534d6-113">However, you could not then define a type that inherits from both the `FictionBook` and `NonFictionBook` types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="534d6-114">例</span><span class="sxs-lookup"><span data-stu-id="534d6-114">Example</span></span>  
 <span data-ttu-id="534d6-115">下のダイアグラムは、`Book`、`FictionBook`、`Publisher`、および `Author` という 4 つのエンティティ型の概念モデルを示しています。</span><span class="sxs-lookup"><span data-stu-id="534d6-115">The diagram below shows a conceptual model with four entity types: `Book`, `FictionBook`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="534d6-116">`FictionBook` エンティティ型は、`Book` エンティティ型から継承する派生型です。</span><span class="sxs-lookup"><span data-stu-id="534d6-116">The `FictionBook` entity type is a derived type, inheriting from the `Book` entity type.</span></span> <span data-ttu-id="534d6-117">`FictionBook` 型は、`ISBN (Key)` プロパティ、`Title` プロパティ、および `Revision` プロパティを継承し、`Genre` と呼ばれる追加プロパティを定義します。</span><span class="sxs-lookup"><span data-stu-id="534d6-117">The `FictionBook` type inherits the `ISBN (Key)`, `Title`, and `Revision` properties, and defines an additional property called `Genre`.</span></span>  
  
 <span data-ttu-id="534d6-118">![継承](../../../../docs/framework/data/adonet/media/inheritanceexample.gif "InheritanceExample")</span><span class="sxs-lookup"><span data-stu-id="534d6-118">![Inheritance](../../../../docs/framework/data/adonet/media/inheritanceexample.gif "InheritanceExample")</span></span>  
  
 <span data-ttu-id="534d6-119">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="534d6-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="534d6-120">次の CSDL は、上のダイアグラムに示された `FictionBook` 型を継承する `Book` エンティティ型を定義しています。</span><span class="sxs-lookup"><span data-stu-id="534d6-120">The following CSDL defines an entity type, `FictionBook`, that inherits from the `Book` type (as in the diagram above):</span></span>  
  
 [!code-xml[EDM_Example_Model#DerivedType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books5.edmx#derivedtype)]  
  
## <a name="see-also"></a><span data-ttu-id="534d6-121">参照</span><span class="sxs-lookup"><span data-stu-id="534d6-121">See Also</span></span>  
 [<span data-ttu-id="534d6-122">Entity Data Model キーの概念</span><span class="sxs-lookup"><span data-stu-id="534d6-122">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="534d6-123">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="534d6-123">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
