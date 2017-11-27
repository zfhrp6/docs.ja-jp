---
title: "アソシエーション型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 476a92979ff0dc6292e64ce5514cc600a9dee50a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="association-type"></a>アソシエーション型
*アソシエーション型*(アソシエーションとも呼ばれます) は、Entity Data Model (EDM) でのリレーションシップを記述するための基本的なビルド ブロックです。 概念モデルのアソシエーションが 2 つの間のリレーションシップを表す[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)(など`Customer`と`Order`)。 アプリケーションでは、アソシエーションのインスタンスが特定のアソシエーション (`Customer` のインスタンスと `Order` のインスタンスの間のアソシエーションなど) を表します。 アソシエーション インスタンスはで論理的にグループ化、[アソシエーション セット](../../../../docs/framework/data/adonet/association-set.md)です。  
  
 アソシエーションの定義には、次の情報が含まれます。  
  
-   一意の名前  (必須)  
  
-   2 つ[アソシエーション end](../../../../docs/framework/data/adonet/association-end.md)リレーションシップのエンティティ型ごとに 1 つです。 (必須)  
  
    > [!NOTE]
    >  アソシエーションは、2 つ以上のエンティティ型のリレーションシップを表すことができません。 しかし、各アソシエーション End に同じエンティティ型を指定することによって、アソシエーションで自己リレーションシップを定義できます。  
  
-   A[参照整合性制約](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)です。 (オプション)。  
  
 各アソシエーション end を指定する必要があります、[アソシエーション end の多重度](../../../../docs/framework/data/adonet/association-end-multiplicity.md)アソシエーションの 1 つの end に存在できるエンティティ型のインスタンスの数を示すです。 アソシエーション End の多重度には、1 (1)、ゼロか 1 (0..1)、または多数 (*) の値を指定することができます。 アソシエーションの一方の end のエンティティ型のインスタンスからアクセスできます[ナビゲーション プロパティ](../../../../docs/framework/data/adonet/navigation-property.md)または公開されている場合、エンティティ型で外部キーです。 詳細については、次を参照してください。 [Entity Data Model: 外部キー](../../../../docs/framework/data/adonet/foreign-key-property.md)です。  
  
## <a name="example"></a>例  
 下のダイアグラムは、`PublishedBy` および `WrittenBy` という 2 つのアソシエーションの概念モデルを示しています。 `PublishedBy` アソシエーションのアソシエーション End は `Book` および `Publisher` のエンティティ型です。 `Publisher` End の多重度は 1 (1) で、`Book` End の多重度は多数 (*) です。これは、出版社が多くの書籍を出版し、書籍は 1 社の出版社により出版されることを示します。  
  
 ![モデルの例](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。 次の CSDL は、上のダイアグラムに示された `PublishedBy` アソシエーションを定義しています。  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>関連項目  
 [エンティティ データ モデルの主要な概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [エンティティ データ モデル](../../../../docs/framework/data/adonet/entity-data-model.md)
