---
title: "アソシエーション セット | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# アソシエーション セット
*アソシエーション セット*は、同じ型の[アソシエーション](../../../../docs/framework/data/adonet/association-type.md) インスタンスの論理コンテナーです。  アソシエーション セットは、データ モデリング構造ではなく、データ構造やリレーションシップを表しません。  アソシエーション セットは、アソシエーション インスタンスをグループ化してデータ ストアにマップするための、ホスト環境またはストレージ環境 \(共通言語ランタイムや SQL Server データベースなど\) の構造を提供します。  
  
 アソシエーション セットは、[エンティティ セット](../../../../docs/framework/data/adonet/entity-set.md)とアソシエーション セットの論理グループである[エンティティ コンテナー](../../../../docs/framework/data/adonet/entity-container.md)内に定義します。  
  
 アソシエーション セットの定義には、次の情報が含まれます。  
  
-   アソシエーション セット名。  \(必須\)  
  
-   インスタンスを含むアソシエーション。  \(必須\)  
  
-   2 つの[アソシエーション セット End](../../../../docs/framework/data/adonet/association-set-end.md)。  
  
## 例  
 下のダイアグラムは、`PublishedBy` および `WrittenBy` という 2 つのアソシエーションの概念モデルを示しています。  このダイアグラムにはアソシエーション セットに関する情報が示されていませんが、次のダイアグラムはこのモデルに基づくアソシエーション セットとエンティティ セットの例を示しています。  
  
 ![モデル例](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 次の例は、上の概念モデルに基づくアソシエーション セット\(`PublishedBy`\) と 2 つのエンティティ セット \(`Books` および `Publishers`\) を示しています。  `Books` エンティティ セット内の Bi は、実行時の `Book` エンティティ型インスタンスを表します。  同様に、Pj は、`Publishers` エンティティ セット内の `Publisher` インスタンスを表します。  BiPj は、`PublishedBy` アソシエーション セット内にある `PublishedBy` アソシエーションのインスタンスを表します。  
  
 ![例の設定](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) では、概念スキーマ定義言語 \([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)\) と呼ばれるドメイン固有言語 \(DSL\) を使用して概念モデルを定義します。  次の CSDL は、上のダイアグラムの各アソシエーションに対して 1 つのアソシエーション セットを持つエンティティ コンテナーを定義しています。  各アソシエーション セットの名前とアソシエーションは、XML 属性で定義しています。  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 2 つのアソシエーション セットが同じ[アソシエーション セット End](../../../../docs/framework/data/adonet/association-set-end.md) を共有していない限り、アソシエーションごとに複数のアソシエーション セットを定義できます。  次の CSDL は、`WrittenBy` アソシエーションの 2 つのアソシエーション セットを含むエンティティ コンテナーを定義しています。  `Book` エンティティ型と `Author` エンティティ型には複数のエンティティ セットが定義され、同じアソシエーション セット End を共有するアソシエーション セットがないことに注意してください。  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## 参照  
 [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)   
 [外部キーのプロパティ](../../../../docs/framework/data/adonet/foreign-key-property.md)