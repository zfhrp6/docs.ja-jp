---
title: "エンティティ コンテナー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 10e10e0a5891e9383b3a8c6dafa6e19606486b33
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="entity-container"></a>エンティティ コンテナー
*エンティティ コンテナー*の論理的なグループは、[エンティティ セット](../../../../docs/framework/data/adonet/entity-set.md)、[アソシエーション セット](../../../../docs/framework/data/adonet/association-set.md)、および[関数インポート](../../../../docs/framework/data/adonet/model-declared-function.md)です。  
  
 概念モデルで定義するエンティティ コンテナーは、次の条件を満たしている必要があります。  
  
-   1 つ以上のエンティティ コンテナーを各概念モデルに定義すること。  
  
-   各概念モデル内のエンティティ コンテナー名が一意であること。  
  
 エンティティ コンテナーは、1 つ以上の名前空間に定義されたエンティティ型またはアソシエーションを使用するエンティティ セットまたはアソシエーション セットを定義できます。 詳細については、次を参照してください。 [Entity Data Model: 名前空間](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md)です。  
  
## <a name="example"></a>例  
 下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。  詳細については、次の例を参照してください。  
  
 ![モデルの例](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 ダイアグラムにはエンティティ コンテナー情報が示されていませんが、概念モデルにはエンティティ コンテナーを定義する必要があります。 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)概念スキーマ定義言語と呼ばれる DSL を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。 次の CSDL は、上のダイアグラムに示された概念モデルのエンティティ コンテナーを定義しています。 エンティティ コンテナー名は XML 属性に定義されています。  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>参照  
 [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
