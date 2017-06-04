---
title: "プロパティ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a941c53f-fc97-42c2-8832-0fb9f1d55c06
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# プロパティ
*プロパティ*は、[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)および[複合型](../../../../docs/framework/data/adonet/complex-type.md)に不可欠な構成要素です。  プロパティは、エンティティ型または複合型のインスタンスに含まれるデータの形と特性を定義します。  概念モデルのプロパティは、クラスに定義されるプロパティに似ています。  クラスのプロパティがクラスの構造を定義し、オブジェクトに関する情報を伝達するのと同様に、概念モデルのプロパティはエンティティ型の構造を定義し、エンティティ型のインスタンスに関する情報を伝達します。  
  
> [!NOTE]
>  このトピックで説明するプロパティは、ナビゲーション プロパティとは異なります。  詳細については、「[ナビゲーション プロパティ](../../../../docs/framework/data/adonet/navigation-property.md)」を参照してください。  
  
 プロパティの定義には、次の情報が含まれます。  
  
-   プロパティ名。  \(必須\)  
  
-   プロパティの型。  \(必須\)  
  
-   一連の[ファセット](../../../../docs/framework/data/adonet/facet.md)。  \(オプション\)。  
  
 プロパティには、プリミティブ データ \(文字列、整数、ブール値など\) または構造化データ \(複合型\) を含めることができます。  プリミティブ型のプロパティは、スカラー プロパティとも呼ばれます。  詳細については、「[Entity Data Model: プリミティブ データ型](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)」を参照してください。  
  
> [!NOTE]
>  複合型自体に、複合型のプロパティを指定することができます。  
  
## 例  
 下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。  各エンティティ型には、いくつかのプロパティがありますが、ダイアグラムには各プロパティの型情報が示されていません。  [エンティティ キー](../../../../docs/framework/data/adonet/entity-key.md)のプロパティには、"\(キー\)" と示されています。  
  
 ![モデル例](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) では、概念スキーマ定義言語 \([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)\) と呼ばれるドメイン固有言語 \(DSL\) を使用して概念モデルを定義します。  次の CSDL は、`Book` エンティティ型 \(上のダイアグラムに示されたように\) を定義し、XML 属性により各プロパティの型と名前を示しています。  ファセット `Nullable` \(省略可能\) も XML 属性により定義されています。  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 ダイアグラムに示されたいずれかのプロパティが複合型のプロパティであることも考えられます。  たとえば、`Publisher` エンティティ型の `Address` プロパティは、`StreetAddress`、`City`、`StateOrProvince`、`Country`、`PostalCode` などいくつかのスカラー プロパティから構成された複合型のプロパティである可能性があります。  このような複合型の CSDL 表現は、次のようになります。  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
## 参照  
 [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)