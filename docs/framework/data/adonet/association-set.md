---
title: "関連付けセット"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: db293cbc636d0ae4e532f24b2852444395f603c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="association-set"></a><span data-ttu-id="23a82-102">関連付けセット</span><span class="sxs-lookup"><span data-stu-id="23a82-102">association set</span></span>
<span data-ttu-id="23a82-103">*アソシエーション セット*の論理コンテナー[アソシエーション](../../../../docs/framework/data/adonet/association-type.md)同じ型のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="23a82-103">An *association set* is a logical container for [association](../../../../docs/framework/data/adonet/association-type.md) instances of the same type.</span></span> <span data-ttu-id="23a82-104">アソシエーション セットは、データ モデリング構造ではなく、データ構造やリレーションシップを表しません。</span><span class="sxs-lookup"><span data-stu-id="23a82-104">An association set is not a data modeling construct; that is, it does not describe the structure of data or relationships.</span></span> <span data-ttu-id="23a82-105">アソシエーション セットは、アソシエーション インスタンスをグループ化してデータ ストアにマップするための、ホスト環境またはストレージ環境 (共通言語ランタイムや SQL Server データベースなど) の構造を提供します。</span><span class="sxs-lookup"><span data-stu-id="23a82-105">Instead, an association set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group association instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="23a82-106">アソシエーション セットが内で定義されている、[エンティティ コンテナー](../../../../docs/framework/data/adonet/entity-container.md)の論理的なグループは[エンティティ セット](../../../../docs/framework/data/adonet/entity-set.md)とアソシエーション セット。</span><span class="sxs-lookup"><span data-stu-id="23a82-106">An association set is defined within an [entity container](../../../../docs/framework/data/adonet/entity-container.md), which is a logical grouping of [entity sets](../../../../docs/framework/data/adonet/entity-set.md) and association sets.</span></span>  
  
 <span data-ttu-id="23a82-107">アソシエーション セットの定義には、次の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="23a82-107">A definition for an association set contains the following information:</span></span>  
  
-   <span data-ttu-id="23a82-108">アソシエーション セット名。</span><span class="sxs-lookup"><span data-stu-id="23a82-108">The association set name.</span></span> <span data-ttu-id="23a82-109">(必須)</span><span class="sxs-lookup"><span data-stu-id="23a82-109">(Required)</span></span>  
  
-   <span data-ttu-id="23a82-110">インスタンスを含むアソシエーション。</span><span class="sxs-lookup"><span data-stu-id="23a82-110">The association of which it will contain instances.</span></span> <span data-ttu-id="23a82-111">(必須)</span><span class="sxs-lookup"><span data-stu-id="23a82-111">(Required)</span></span>  
  
-   <span data-ttu-id="23a82-112">2 つ[アソシエーション セット end](../../../../docs/framework/data/adonet/association-set-end.md)です。</span><span class="sxs-lookup"><span data-stu-id="23a82-112">Two [association set ends](../../../../docs/framework/data/adonet/association-set-end.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="23a82-113">例</span><span class="sxs-lookup"><span data-stu-id="23a82-113">Example</span></span>  
 <span data-ttu-id="23a82-114">下のダイアグラムは、`PublishedBy` および `WrittenBy` という 2 つのアソシエーションの概念モデルを示しています。</span><span class="sxs-lookup"><span data-stu-id="23a82-114">The diagram below shows a conceptual model with two associations: `PublishedBy`, and `WrittenBy`.</span></span> <span data-ttu-id="23a82-115">このダイアグラムにはアソシエーション セットに関する情報が示されていませんが、次のダイアグラムはこのモデルに基づくアソシエーション セットとエンティティ セットの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="23a82-115">Although information about association sets is not conveyed in the diagram, the next diagram shows an example of association sets and entity sets based on this model.</span></span>  
  
 <span data-ttu-id="23a82-116">![モデルの例](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="23a82-116">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="23a82-117">次の例は、上の概念モデルに基づくアソシエーション セット(`PublishedBy`) と 2 つのエンティティ セット (`Books` および `Publishers`) を示しています。</span><span class="sxs-lookup"><span data-stu-id="23a82-117">The following example shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="23a82-118">Bi、`Books`エンティティ セットのインスタンスを表し、`Book`実行時にエンティティ型。</span><span class="sxs-lookup"><span data-stu-id="23a82-118">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="23a82-119">同様に、Pj を表す、`Publisher`インスタンス、`Publishers`エンティティ セット。</span><span class="sxs-lookup"><span data-stu-id="23a82-119">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="23a82-120">BiPj がのインスタンスを表し、`PublishedBy`のアソシエーション、`PublishedBy`アソシエーション セット。</span><span class="sxs-lookup"><span data-stu-id="23a82-120">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 <span data-ttu-id="23a82-121">![例の設定](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span><span class="sxs-lookup"><span data-stu-id="23a82-121">![Sets Example](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span></span>  
  
 <span data-ttu-id="23a82-122">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="23a82-122">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="23a82-123">次の CSDL は、上のダイアグラムの各アソシエーションに対して 1 つのアソシエーション セットを持つエンティティ コンテナーを定義しています。</span><span class="sxs-lookup"><span data-stu-id="23a82-123">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="23a82-124">各アソシエーション セットの名前とアソシエーションは、XML 属性で定義しています。</span><span class="sxs-lookup"><span data-stu-id="23a82-124">Note that the name and association for each association set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="23a82-125">関連付けのない 2 つのアソシエーション セットの共有と同じくらいごとに複数の関連付けセットを定義することは、[アソシエーション セット end](../../../../docs/framework/data/adonet/association-set-end.md)です。</span><span class="sxs-lookup"><span data-stu-id="23a82-125">It is possible to define multiple association sets per association, as long as no two association sets share an [association set end](../../../../docs/framework/data/adonet/association-set-end.md).</span></span> <span data-ttu-id="23a82-126">次の CSDL は、`WrittenBy` アソシエーションの 2 つのアソシエーション セットを含むエンティティ コンテナーを定義しています。</span><span class="sxs-lookup"><span data-stu-id="23a82-126">The following CSDL defines an entity container with two association sets for the `WrittenBy` association.</span></span> <span data-ttu-id="23a82-127">`Book` エンティティ型と `Author` エンティティ型には複数のエンティティ セットが定義され、同じアソシエーション セット End を共有するアソシエーション セットがないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="23a82-127">Notice that multiple entity sets have been defined for the `Book` and `Author` entity types and that no association set shares an association set end.</span></span>  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a><span data-ttu-id="23a82-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="23a82-128">See Also</span></span>  
 [<span data-ttu-id="23a82-129">エンティティ データ モデルの主要な概念</span><span class="sxs-lookup"><span data-stu-id="23a82-129">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="23a82-130">エンティティ データ モデル</span><span class="sxs-lookup"><span data-stu-id="23a82-130">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [<span data-ttu-id="23a82-131">外部キーのプロパティ</span><span class="sxs-lookup"><span data-stu-id="23a82-131">foreign key property</span></span>](../../../../docs/framework/data/adonet/foreign-key-property.md)
