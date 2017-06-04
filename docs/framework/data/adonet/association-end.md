---
title: "アソシエーション End | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# アソシエーション End
*アソシエーション End* は、[アソシエーション](../../../../docs/framework/data/adonet/association-type.md)の一方の End にある[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)と、アソシエーションのその End に存在できるエンティティ型のインスタンス数を特定します。  アソシエーション End はアソシエーションの一部として定義され、アソシエーションには必ず 2 つのアソシエーション End が必要です。  [ナビゲーション プロパティ](../../../../docs/framework/data/adonet/navigation-property.md)は、一方のアソシエーション End から他方のアソシエーション End へのナビゲーションを可能にします。  
  
 アソシエーション End の定義には、次の情報が含まれます。  
  
-   アソシエーションに含まれるエンティティ型の 1 つ。  \(必須\)  
  
    > [!NOTE]
    >  アソシエーションでは、各アソシエーション End に同じエンティティ型を指定することができます。  これにより、自己アソシエーションが作成されます。  
  
-   アソシエーションの 1 つの End に存在できるエンティティ型のインスタンス数を示す[アソシエーション End の多重度](../../../../docs/framework/data/adonet/association-end-multiplicity.md)。  アソシエーション End の多重度には、1 \(1\)、ゼロか 1 \(0..1\)、または多数 \(\*\) の値を指定することができます。  
  
-   アソシエーション End の名前。  \(オプション\)。  
  
-   アソシエーション End に実行する CASCADE ON DELETE などの操作の情報。  \(オプション\)。  
  
## 例  
 下のダイアグラムは、`WrittenBy` および `PublishedBy` という 2 つのアソシエーションの概念モデルを示しています。  `PublishedBy` アソシエーションのアソシエーション End は `Book` および `Publisher` のエンティティ型です。  `Publisher` End の多重度は 1 \(1\) で、`Book` End の多重度は多数 \(\*\) です。これは、出版社が多くの書籍を出版し、書籍は 1 社の出版社により出版されることを示します。  
  
 ![モデル例](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 ADO.NET Entity Framework では、概念スキーマ定義言語 \([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)\) と呼ばれるドメイン固有言語 \(DSL\) を使用して概念モデルを定義します。  次の CSDL は、上のダイアグラムに示された `PublishedBy` アソシエーションを定義します。  各アソシエーション End の型、名前、および多重度は、XML 属性 \(それぞれ `Type` 属性、`Role` 属性、および `Multiplicity` 属性\) で指定されます。  アソシエーション End に実行する操作に関するオプション情報は、XML 要素 \(`OnDelete` 要素\) に指定します。  この場合、出版社を削除すると、関連付けられたすべての書籍も削除されます。  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## 参照  
 [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)