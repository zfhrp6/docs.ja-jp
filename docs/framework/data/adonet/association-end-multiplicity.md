---
title: "アソシエーション End の多重度"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0d66c141b83402b011fdebbb04c0b2a9adc5ec29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="association-end-multiplicity"></a><span data-ttu-id="59838-102">アソシエーション End の多重度</span><span class="sxs-lookup"><span data-stu-id="59838-102">association end multiplicity</span></span>
<span data-ttu-id="59838-103">*アソシエーション end の多重度*の数を定義[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)インスタンスの一方の end に存在できる、[アソシエーション](../../../../docs/framework/data/adonet/association-type.md)です。</span><span class="sxs-lookup"><span data-stu-id="59838-103">*Association end multiplicity* defines the number of [entity type](../../../../docs/framework/data/adonet/entity-type.md) instances that can be at one end of an [association](../../../../docs/framework/data/adonet/association-type.md).</span></span>  
  
 <span data-ttu-id="59838-104">アソシエーション End の多重度には、次のいずれかの値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="59838-104">An association end multiplicity can have one of the following values:</span></span>  
  
-   <span data-ttu-id="59838-105">1 (1): アソシエーション End に 1 つのエンティティ型のインスタンスが存在することを示します。</span><span class="sxs-lookup"><span data-stu-id="59838-105">one (1): Indicates that exactly one entity type instance exists at the association end.</span></span>  
  
-   <span data-ttu-id="59838-106">0 または 1 (0..1): アソシエーション End に 0 または 1 つのエンティティ型のインスタンスが存在することを示します。</span><span class="sxs-lookup"><span data-stu-id="59838-106">zero or one (0..1): Indicates that zero or one entity type instances exist at the association end.</span></span>  
  
-   <span data-ttu-id="59838-107">多数 (*): アソシエーション End に 0、1 つ、または複数のエンティティ型のインスタンスが存在することを示します。</span><span class="sxs-lookup"><span data-stu-id="59838-107">many (*): Indicates that zero, one, or more entity type instances exist at the association end.</span></span>  
  
 <span data-ttu-id="59838-108">アソシエーションは、多くの場合、そのアソシエーション End の多重度により特徴付けられます。</span><span class="sxs-lookup"><span data-stu-id="59838-108">An association is often characterized by its association end multiplicities.</span></span> <span data-ttu-id="59838-109">たとえば、アソシエーション End の多重度が 1 (1) と多数 (*) の場合、アソシエーションは一対多のアソシエーションと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="59838-109">For example, if the ends of an association have multiplicities one (1) and many (*), the association is called a one-to-many association.</span></span> <span data-ttu-id="59838-110">次の例で、`PublishedBy` アソシエーションは一対多のアソシエーションです (出版社が多くの書籍を出版し、書籍は 1 社の出版社により出版されます)。</span><span class="sxs-lookup"><span data-stu-id="59838-110">In the example below, the `PublishedBy` association is a one-to-many association (a publisher publishes many books and a book is published by one publisher).</span></span> <span data-ttu-id="59838-111">`WrittenBy` アソシエーションは多対多のアソシエーションです (書籍の著者が複数の場合があり、著者は複数の書籍を執筆することができます)。</span><span class="sxs-lookup"><span data-stu-id="59838-111">The `WrittenBy` association is a many-to-many association (a book can have multiple authors and an author can write multiple books).</span></span>  
  
## <a name="example"></a><span data-ttu-id="59838-112">例</span><span class="sxs-lookup"><span data-stu-id="59838-112">Example</span></span>  
 <span data-ttu-id="59838-113">下のダイアグラムは、`PublishedBy` および `WrittenBy` という 2 つのアソシエーションの概念モデルを示しています。</span><span class="sxs-lookup"><span data-stu-id="59838-113">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="59838-114">`PublishedBy` アソシエーションのアソシエーション End は `Book` および `Publisher` のエンティティ型です。</span><span class="sxs-lookup"><span data-stu-id="59838-114">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="59838-115">`Publisher` End の多重度は 1 (1) で、`Book` End の多重度は多数 (*) です。</span><span class="sxs-lookup"><span data-stu-id="59838-115">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (*).</span></span>  
  
 <span data-ttu-id="59838-116">![モデルの例](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="59838-116">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="59838-117">ADO.NET Entity Framework 概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="59838-117">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="59838-118">次の CSDL は、上のダイアグラムに示された `PublishedBy` アソシエーションを定義しています。</span><span class="sxs-lookup"><span data-stu-id="59838-118">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="59838-119">参照</span><span class="sxs-lookup"><span data-stu-id="59838-119">See Also</span></span>  
 [<span data-ttu-id="59838-120">Entity Data Model キーの概念</span><span class="sxs-lookup"><span data-stu-id="59838-120">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="59838-121">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="59838-121">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
