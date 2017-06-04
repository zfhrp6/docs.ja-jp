---
title: "エンティティ セット | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# エンティティ セット
*エンティティ セット*は、[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)のインスタンスと、そのエンティティ型から派生するあらゆる型のインスタンスの論理コンテナーです   \(派生型の詳細については、「[Entity Data Model: 継承](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)」を参照してください\)。エンティティ型とエンティティ セットの関係は、リレーショナル データベースの行とテーブルの関係に似ており、エンティティ型は行のようにデータ構造を表し、エンティティ セットにはテーブルのように構造のインスタンスが格納されます。  エンティティ セットは、データ モデリング構造ではなく、データ構造を表しません。  エンティティ セットは、エンティティ型のインスタンスをグループ化してデータ ストアにマップするための、ホスト環境またはストレージ環境 \(共通言語ランタイムや SQL Server データベースなど\) の構造を提供します。  
  
 エンティティ セットは、エンティティ セットと[アソシエーション セット](../../../../docs/framework/data/adonet/association-set.md)の論理グループである[エンティティ コンテナー](../../../../docs/framework/data/adonet/entity-container.md)内に定義します。  
  
 エンティティ型のインスタンスがエンティティ セット内に存在できるようにするには、次の条件を満たしている必要があります。  
  
-   インスタンスの型がエンティティ セットの基本になるエンティティ型と同じであるか、インスタンスの型がエンティティ型のサブタイプであること。  
  
-   インスタンスの[エンティティ キー](../../../../docs/framework/data/adonet/entity-key.md)がエンティティ セット内で一意であること。  
  
-   インスタンスが他のエンティティ セットに存在しないこと。  
  
    > [!NOTE]
    >  同じエンティティ型を使用して複数のエンティティ セットを定義できますが、特定のエンティティ型のインスタンスは、1 つのエンティティ セット内のみに存在できます。  
  
 概念モデルの各エンティティ型にはエンティティ セットを定義する必要がありません。  
  
## 例  
 下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。  
  
 ![モデル例](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 次のダイアグラムには、上の概念モデルに基づく 2 つのエンティティ セット \(`Books` および `Publishers`\) と、アソシエーション セット\(`PublishedBy`\) を示しています。  `Books` エンティティ セット内の Bi は、実行時の `Book` エンティティ型インスタンスを表します。  同様に、Pj は、`Publishers` エンティティ セットの `Publisher` インスタンスを表します。  BiPj は、`PublishedBy` アソシエーション セット内にある `PublishedBy` アソシエーションのインスタンスを表します。  
  
 ![例の設定](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) では、概念スキーマ定義言語 \([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)\) と呼ばれるドメイン固有言語 \(DSL\) を使用して概念モデルを定義します。  次の CSDL は、上の概念モデルに示された各エンティティ型に対して 1 つのエンティティ セットを持つエンティティ コンテナーを定義しています。  各エンティティ セットの名前とエンティティ型は、XML 属性で定義されています。  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 型ごとに複数のエンティティ セット \(Multiple\-Entity\-Sets\-per\-Type: MEST\) を定義できます。  次の CSDL は、`Book` エンティティ型のエンティティ セットを 2 つ持つエンティティ コンテナーを定義しています。  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## 参照  
 [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)