---
title: "ナビゲーション プロパティ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# ナビゲーション プロパティ
*ナビゲーション プロパティ*は、[アソシエーション](../../../../docs/framework/data/adonet/association-type.md)の 1 つの [End](../../../../docs/framework/data/adonet/association-end.md) から別の End へのナビゲーションを可能にする、[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)の省略可能なプロパティです。  その他の[プロパティ](../../../../docs/framework/data/adonet/property.md)とは異なり、ナビゲーション プロパティはデータを伝達しません。  
  
 ナビゲーション プロパティの定義には、以下が含まれます。  
  
-   名前。  \(必須\)  
  
-   移動対象のアソシエーション。  \(必須\)  
  
-   移動対象のアソシエーションの End。  \(必須\)  
  
 ナビゲーション プロパティは、アソシエーション End の両方のエンティティ型で省略可能です。  1 つのアソシエーション End のエンティティ型にナビゲーション プロパティを定義した場合に、そのアソシエーションの他方の End でもエンティティ型にナビゲーション プロパティを定義する必要はありません。  
  
 ナビゲーション プロパティのデータ型は、リモートの[アソシエーション End](../../../../docs/framework/data/adonet/association-end.md) の[多重度](../../../../docs/framework/data/adonet/association-end-multiplicity.md)により決まります。  たとえば、ナビゲーション プロパティ `OrdersNavProp` が `Customer` エンティティ型に存在し、`Customer` と `Order` の間の一対多のアソシエーションで移動するとします。  ナビゲーション プロパティのリモートのアソシエーション End の多重度が多数 \(\*\) であるため、そのデータ型は \(`Order` の\) コレクションになります。  同様に、`Order` エンティティ型にナビゲーション プロパティ、`CustomerNavProp` が存在する場合、リモート End の多重度が \(1\) であるため、データ型は `Customer` になります。  
  
## 例  
 下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。  Book エンティティ型には、ナビゲーション プロパティ、`Publisher` および `Authors` が定義されています。  Publisher エンティティ型と `Author` エンティティ型には、ナビゲーション プロパティ、`Books` が定義されています。  
  
 ![ナビゲーション プロパティが含まれるモデル](../../../../docs/framework/data/adonet/media/modelwithnavprops.gif "ModelWithNavProps")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) では、概念スキーマ定義言語 \([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)\) と呼ばれるドメイン固有言語 \(DSL\) を使用して概念モデルを定義します。  次の CSDL は、上のダイアグラムに示された `Book` エンティティ型を定義しています。  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 ナビゲーション プロパティの定義に必要な情報を伝達するために、XML 属性が使用されています。属性 `Name` にはプロパティ名が含まれ、`Relationship` には移動対象のアソシエーション名が含まれ、`FromRole` および `ToRole` にはアソシエーション End が含まれています。  
  
## 参照  
 [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)