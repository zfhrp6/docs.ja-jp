---
title: "アソシエーション End"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7ceb6d40a47c73c4580a8fc33acc3c395a2c5a06
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="association-end"></a>アソシエーション End
*アソシエーション end*を識別、[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)の一方の end に、[アソシエーション](../../../../docs/framework/data/adonet/association-type.md)とエンティティの数をアソシエーションの end に存在できるインスタンスを入力します。 アソシエーション End はアソシエーションの一部として定義され、アソシエーションには必ず 2 つのアソシエーション End が必要です。 [ナビゲーション プロパティ](../../../../docs/framework/data/adonet/navigation-property.md)他の 1 つのアソシエーション end から移動できるようにします。  
  
 アソシエーション End の定義には、次の情報が含まれます。  
  
-   アソシエーションに含まれるエンティティ型の 1 つ。 (必須)  
  
    > [!NOTE]
    >  アソシエーションでは、各アソシエーション End に同じエンティティ型を指定することができます。 これにより、自己アソシエーションが作成されます。  
  
-   [アソシエーション end の多重度](../../../../docs/framework/data/adonet/association-end-multiplicity.md)アソシエーションの 1 つの end に存在できるエンティティ型のインスタンスの数を示すです。 アソシエーション End の多重度には、1 (1)、ゼロか 1 (0..1)、または多数 (*) の値を指定することができます。  
  
-   アソシエーション End の名前。 (オプション)。  
  
-   アソシエーション End に実行する CASCADE ON DELETE などの操作の情報。 (オプション)。  
  
## <a name="example"></a>例  
 下のダイアグラムは、`PublishedBy` および `WrittenBy` という 2 つのアソシエーションの概念モデルを示しています。 `PublishedBy` アソシエーションのアソシエーション End は `Book` および `Publisher` のエンティティ型です。 `Publisher` End の多重度は 1 (1) で、`Book` End の多重度は多数 (*) です。これは、出版社が多くの書籍を出版し、書籍は 1 社の出版社により出版されることを示します。  
  
 ![モデルの例](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 ADO.NET Entity Framework 概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。 次の CSDL は、上のダイアグラムに示された `PublishedBy` アソシエーションを定義します。 各アソシエーション End の型、名前、および多重度は、XML 属性 (それぞれ `Type` 属性、`Role` 属性、および `Multiplicity` 属性) で指定されます。 アソシエーション End に実行する操作に関するオプション情報は、XML 要素 (`OnDelete` 要素) に指定します。 この場合、出版社を削除すると、関連付けられたすべての書籍も削除されます。  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a>関連項目  
 [エンティティ データ モデルの主要な概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [エンティティ データ モデル](../../../../docs/framework/data/adonet/entity-data-model.md)
