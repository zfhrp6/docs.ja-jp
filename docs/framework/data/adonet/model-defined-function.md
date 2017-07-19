---
title: "モデル定義関数 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# モデル定義関数
*モデル定義関数*は、概念モデルで定義される関数です。  モデル定義関数の本体は、[Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) により表現されます。これにより、データ ソースでサポートされる規則または言語に関係なく関数を表現することが可能になります。  
  
 モデル定義関数の定義には、次の情報が含まれます。  
  
-   関数名。  \(必須\)  
  
-   戻り値の型。  \(オプション\)。  
  
    > [!NOTE]
    >  戻り値の型が指定されていない場合、戻り値は void になります。  
  
-   パラメーター情報。  \(オプション\)。  
  
-   関数の本体を定義する [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) 表現。  
  
 モデル定義関数では、出力パラメーターがサポートされません。  この制約は、モデル定義関数を構成できるようにするためにあります。  
  
## 例  
 下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。  
  
 ![公開日付が含まれるモデル](../../../../docs/framework/data/adonet/media/modelwithpublisheddate.gif "ModelWithPublishedDate")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) では、概念スキーマ定義言語 \([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)\) と呼ばれるドメイン固有言語 \(DSL\) を使用して概念モデルを定義します。  次の CSDL は、`Book` \(上のダイアグラムの\) の出版以降の年数を返す概念モデルの関数を定義しています。  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## 参照  
 [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)   
 [Entity Data Model: プリミティブ データ型](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)