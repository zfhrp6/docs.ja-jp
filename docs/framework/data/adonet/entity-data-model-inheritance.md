---
title: "Entity Data Model: 継承 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 42c7ef24-710a-4af9-8493-cd41c399ecb0
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Entity Data Model: 継承
Entity Data Model \(EDM\) は、[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)の継承をサポートしています。  EDM の継承は、オブジェクト指向プログラミング言語におけるクラスの継承に似ています。  オブジェクト指向言語のクラスと同様、概念モデルでは、別のエンティティ型 \(*基本型*\) を継承するエンティティ型 \(*派生型*\) を定義できます。  ただし、オブジェクト指向プログラミングのクラスとは異なり、概念モデルでは、派生型が基本型のすべての[プロパティ](../../../../docs/framework/data/adonet/property.md)と[ナビゲーション プロパティ](../../../../docs/framework/data/adonet/navigation-property.md)を常に継承します。  派生型の継承プロパティは、オーバーライドできません。  
  
 概念モデルでは、派生型が別の派生型を継承する継承階層を構築することができます。  階層の最上位にある型 \(階層内で派生型ではない唯一の型\) は、*ルート型*と呼ばれます。  継承階層では、ルート型に[エンティティ キー](../../../../docs/framework/data/adonet/entity-key.md)を定義する必要があります。  
  
 複数の型から派生型を継承する継承階層を構築することはできません。  たとえば、`Book` エンティティ型の概念モデルでは、それぞれ `Book` から継承する派生型、`FictionBook` および `NonFictionBook` を定義することができます。  しかし、`FictionBook` 型と `NonFictionBook` 型の両方から継承する型を定義することはできません。  
  
## 例  
 下のダイアグラムは、`Book`、`FictionBook`、`Publisher`、および `Author` という 4 つのエンティティ型の概念モデルを示しています。  `FictionBook` エンティティ型は、`Book` エンティティ型から継承する派生型です。  `FictionBook` 型は、`ISBN (Key)` プロパティ、`Title` プロパティ、および `Revision` プロパティを継承し、`Genre` と呼ばれる追加プロパティを定義します。  
  
 ![継承](../../../../docs/framework/data/adonet/media/inheritanceexample.gif "InheritanceExample")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) では、概念スキーマ定義言語 \([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)\) と呼ばれるドメイン固有言語 \(DSL\) を使用して概念モデルを定義します。  次の CSDL は、上のダイアグラムに示された `Book` 型を継承する `FictionBook` エンティティ型を定義しています。  
  
 [!code-xml[EDM_Example_Model#DerivedType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books5.edmx#derivedtype)]  
  
## 参照  
 [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)