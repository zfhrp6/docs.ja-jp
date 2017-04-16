---
title: "Entity Data Model: 名前空間 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Entity Data Model: 名前空間
Entity Data Model \(EDM\) の名前空間は、[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)、[複合型](../../../../docs/framework/data/adonet/complex-type.md)、および[アソシエーション](../../../../docs/framework/data/adonet/association-type.md)の抽象コンテナーです。  EDM の名前空間はプログラミング言語の名前空間と似ており、その中に含まれるオブジェクトのコンテキストを指定し、同じ名前を持つ \(しかし、別の名前空間に含まれる\) オブジェクトを明確に区別する手段になります。  
  
## 例  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) では、概念スキーマ定義言語 \([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)\) と呼ばれるドメイン固有言語 \(DSL\) を使用して概念モデルを定義します。  次の CSDL コードは、名前空間を使用して異なる概念モデルに定義された型を識別します。  この例は、`ExtendedBooksModel` 名前空間からインポートされた複合型のプロパティ \(`Address`\) を持つエンティティ型 \(`Publisher`\) を定義します。  `Using` 要素は、名前空間がインポートされていることを示します。  さらに、`Address` プロパティの型は、完全修飾名 \(`ExtendedBooksModel.Address`\) で定義されており、この型が `ExtendedBooksModel` 名前空間で定義されていることを示します。  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## 参照  
 [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)