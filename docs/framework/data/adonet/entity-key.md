---
title: "エンティティ キー | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0d447a6d-fa7a-4db0-8e7a-fd45e385fca0
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# エンティティ キー
*エンティティ キー*とは、ID を確認するために使用する[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)の[プロパティ](../../../../docs/framework/data/adonet/property.md)または一連のプロパティです。  エンティティ キーを構成するプロパティは、デザイン時に選択されます。  エンティティ キー プロパティの値は、実行時に[エンティティ セット](../../../../docs/framework/data/adonet/entity-set.md)内でエンティティ型のインスタンスを一意に識別する必要があります。  エンティティ キーを構成するプロパティには、エンティティ セット内のインスタンスの一意性を保証するものを選択する必要があります。  
  
 エンティティ キーを構成する一連のプロパティには、次の要件があります。  
  
-   エンティティ セット内では、2 つ以上のエンティティ キーを同じにすることができません。  つまり、エンティティ セット内の 2 つのエンティティに対して、キーを構成するすべてのプロパティの値を同じにすることができません。  ただし、エンティティ キーを構成する一部 \(すべてではなく\) の値は同じにすることができます。  
  
-   エンティティ キーは、null 値が許可されない不変[プリミティブ型のプロパティ](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)で構成する必要があります。  
  
-   エンティティ型のエンティティ キーを構成するプロパティは、変更できません。  エンティティ型に対して複数のエンティティ キーを許可することはできません。代理キーはサポートされていません。  
  
-   エンティティが継承階層に含まれる場合、ルート エンティティには、エンティティ キーを構成するすべてのプロパティを含める必要があり、そのエンティティ キーをルート エンティティ型に定義する必要があります。  詳細については、「[Entity Data Model: 継承](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)」を参照してください。  
  
## 例  
 下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。  各エンティティ型のエンティティ キーを構成するプロパティには、"\(キー\)" と示されています。  `Author` エンティティ型には、`Name` と `Address` の 2 つのプロパティで構成されるエンティティ キーが含まれます。  
  
 ![モデル例](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) では、概念スキーマ定義言語 \([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)\) と呼ばれるドメイン固有言語 \(DSL\) を使用して概念モデルを定義します。  次の CSDL は、上のダイアグラムに示された `Book` エンティティ型を定義します。  エンティティ キーは、エンティティ型の `ISBN` プロパティを参照して定義されています。  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 国際標準図書番号 \(ISBN\) は書籍を一意に識別するものであるため、`ISBN` プロパティは、エンティティ キーに適しています。  
  
 次の CSDL は、上のダイアグラムに示された `Author` エンティティ型を定義します。  エンティティ キーは、`Name` と `Address` の 2 つのプロパティで構成されています。  
  
 [!code-xml[EDM_Example_Model#CompositeKeyExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#compositekeyexample)]  
  
 同じ名前の 2 人の著者が同じ住所に住む可能性は低いため、エンティティ キーに `Name` および `Address` を使用するのは妥当な選択になります。  ただし、エンティティ キーのこの選択では、エンティティ セット内のエンティティ キーの一意性を絶対的に保証することはできません。  この場合には、`AuthorId` などのプロパティを追加して、著者を一意に識別することが推奨されます。  
  
## 参照  
 [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)