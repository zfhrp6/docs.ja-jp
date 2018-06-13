---
title: エンティティ セット
ms.date: 03/30/2017
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
ms.openlocfilehash: 5a8b4bdac2d0cb2065438bb390c002fcb690b1f6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764139"
---
# <a name="entity-set"></a>エンティティ セット
*エンティティ セット*の論理的なコンテナーは、のインスタンス、[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)とそのエンティティ型から派生した任意の型のインスタンス。 (派生型については、次を参照してください[Entity Data Model: 継承](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)。)。エンティティ型とエンティティ セットの関係は、リレーショナル データベースの行とテーブルの関係に似ており、エンティティ型は行のようにデータ構造を表し、エンティティ セットにはテーブルのように構造のインスタンスが格納されます。 エンティティ セットは、データ モデリング構造ではなく、データ構造を表しません。 エンティティ セットは、エンティティ型のインスタンスをグループ化してデータ ストアにマップするための、ホスト環境またはストレージ環境 (共通言語ランタイムや SQL Server データベースなど) の構造を提供します。  
  
 内のエンティティ セットが定義されている、[エンティティ コンテナー](../../../../docs/framework/data/adonet/entity-container.md)、エンティティ セットの論理的なグループであると[アソシエーション セット](../../../../docs/framework/data/adonet/association-set.md)です。  
  
 エンティティ型のインスタンスがエンティティ セット内に存在できるようにするには、次の条件を満たしている必要があります。  
  
-   インスタンスの型がエンティティ セットの基本になるエンティティ型と同じであるか、インスタンスの型がエンティティ型のサブタイプであること。  
  
-   [エンティティ キー](../../../../docs/framework/data/adonet/entity-key.md)インスタンスは、エンティティ セット内で一意です。  
  
-   インスタンスが他のエンティティ セットに存在しないこと。  
  
    > [!NOTE]
    >  同じエンティティ型を使用して複数のエンティティ セットを定義できますが、特定のエンティティ型のインスタンスは、1 つのエンティティ セット内のみに存在できます。  
  
 概念モデルの各エンティティ型にはエンティティ セットを定義する必要がありません。  
  
## <a name="example"></a>例  
 下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。  
  
 ![モデルの例](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 次のダイアグラムには、上の概念モデルに基づく 2 つのエンティティ セット (`Books` および `Publishers`) と、アソシエーション セット(`PublishedBy`) を示しています。 Bi、`Books`エンティティ セットのインスタンスを表し、`Book`実行時にエンティティ型。 同様に、Pj を表す、`Publisher`インスタンス、`Publishers`エンティティ セット。 BiPj がのインスタンスを表し、`PublishedBy`のアソシエーション、`PublishedBy`アソシエーション セット。  
  
 ![例の設定](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。 次の CSDL は、上の概念モデルに示された各エンティティ型に対して 1 つのエンティティ セットを持つエンティティ コンテナーを定義しています。 各エンティティ セットの名前とエンティティ型は、XML 属性で定義されています。  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 型ごとに複数のエンティティ セット (Multiple-Entity-Sets-per-Type: MEST) を定義できます。 次の CSDL は、`Book` エンティティ型のエンティティ セットを 2 つ持つエンティティ コンテナーを定義しています。  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a>関連項目  
 [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
