---
title: "アソシエーション型 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# アソシエーション型
*アソシエーション型* \(アソシエーションとも呼ばれます\) は、Entity Data Model \(EDM\) でリレーションシップを記述するために不可欠な構成要素です。  概念モデルでは、アソシエーションが 2 つの[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md) \(`Customer` や `Order` など\) の間のリレーションシップを表します。  アプリケーションでは、アソシエーションのインスタンスが特定のアソシエーション \(`Customer` のインスタンスと `Order` のインスタンスの間のアソシエーションなど\) を表します。  アソシエーション インスタンスは、[アソシエーション セット](../../../../docs/framework/data/adonet/association-set.md)に論理的にグループ化されます。  
  
 アソシエーションの定義には、次の情報が含まれます。  
  
-   一意の名前   \(必須\)  
  
-   2 つの[アソシエーション End](../../../../docs/framework/data/adonet/association-end.md) \(リレーションシップを構成する各エンティティ型に 1 つずつ\)。  \(必須\)  
  
    > [!NOTE]
    >  アソシエーションは、2 つ以上のエンティティ型のリレーションシップを表すことができません。  しかし、各アソシエーション End に同じエンティティ型を指定することによって、アソシエーションで自己リレーションシップを定義できます。  
  
-   [参照整合性制約](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)。  \(オプション\)。  
  
 各アソシエーション End には、アソシエーションの 1 つの End に存在できるエンティティ型のインスタンス数を示す[アソシエーション End の多重度](../../../../docs/framework/data/adonet/association-end-multiplicity.md)を指定する必要があります。  アソシエーション End の多重度には、1 \(1\)、ゼロか 1 \(0..1\)、または多数 \(\*\) の値を指定することができます。  アソシエーションの 1 つの End にあるエンティティ型のインスタンスには、エンティティ型で公開されている場合、[ナビゲーション プロパティ](../../../../docs/framework/data/adonet/navigation-property.md)または外部キーからアクセスできます。  詳細については、「[Entity Data Model: 外部キー](../../../../docs/framework/data/adonet/foreign-key-property.md)」を参照してください。  
  
## 例  
 下のダイアグラムは、`WrittenBy` および `PublishedBy` という 2 つのアソシエーションの概念モデルを示しています。  `PublishedBy` アソシエーションのアソシエーション End は `Book` および `Publisher` のエンティティ型です。  `Publisher` End の多重度は 1 \(1\) で、`Book` End の多重度は多数 \(\*\) です。これは、出版社が多くの書籍を出版し、書籍は 1 社の出版社により出版されることを示します。  
  
 ![モデル例](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) では、概念スキーマ定義言語 \([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)\) と呼ばれるドメイン固有言語 \(DSL\) を使用して概念モデルを定義します。  次の CSDL は、上のダイアグラムに示された `PublishedBy` アソシエーションを定義しています。  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## 参照  
 [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)