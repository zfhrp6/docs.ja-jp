---
title: "アソシエーション End の多重度"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0d66c141b83402b011fdebbb04c0b2a9adc5ec29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="association-end-multiplicity"></a>アソシエーション End の多重度
*アソシエーション end の多重度*の数を定義[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)インスタンスの一方の end に存在できる、[アソシエーション](../../../../docs/framework/data/adonet/association-type.md)です。  
  
 アソシエーション End の多重度には、次のいずれかの値を指定できます。  
  
-   1 (1): アソシエーション End に 1 つのエンティティ型のインスタンスが存在することを示します。  
  
-   0 または 1 (0..1): アソシエーション End に 0 または 1 つのエンティティ型のインスタンスが存在することを示します。  
  
-   多数 (*): アソシエーション End に 0、1 つ、または複数のエンティティ型のインスタンスが存在することを示します。  
  
 アソシエーションは、多くの場合、そのアソシエーション End の多重度により特徴付けられます。 たとえば、アソシエーション End の多重度が 1 (1) と多数 (*) の場合、アソシエーションは一対多のアソシエーションと呼ばれます。 次の例で、`PublishedBy` アソシエーションは一対多のアソシエーションです (出版社が多くの書籍を出版し、書籍は 1 社の出版社により出版されます)。 `WrittenBy` アソシエーションは多対多のアソシエーションです (書籍の著者が複数の場合があり、著者は複数の書籍を執筆することができます)。  
  
## <a name="example"></a>例  
 下のダイアグラムは、`PublishedBy` および `WrittenBy` という 2 つのアソシエーションの概念モデルを示しています。 `PublishedBy` アソシエーションのアソシエーション End は `Book` および `Publisher` のエンティティ型です。 `Publisher` End の多重度は 1 (1) で、`Book` End の多重度は多数 (*) です。  
  
 ![モデルの例](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 ADO.NET Entity Framework 概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。 次の CSDL は、上のダイアグラムに示された `PublishedBy` アソシエーションを定義しています。  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>参照  
 [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
