---
title: エンティティ キー
ms.date: 03/30/2017
ms.assetid: 0d447a6d-fa7a-4db0-8e7a-fd45e385fca0
ms.openlocfilehash: 6b4e3c6876aa3de1661d680d79caa3116550e073
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764997"
---
# <a name="entity-key"></a>エンティティ キー
*エンティティ キー*は、[プロパティ](../../../../docs/framework/data/adonet/property.md)または一連のプロパティの[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)id を判断するために使用されます。 エンティティ キーを構成するプロパティは、デザイン時に選択されます。 エンティティのキー プロパティの値は、内のエンティティ型インスタンスを一意に識別する必要があります、[エンティティ セット](../../../../docs/framework/data/adonet/entity-set.md)実行時にします。 エンティティ キーを構成するプロパティには、エンティティ セット内のインスタンスの一意性を保証するものを選択する必要があります。  
  
 エンティティ キーを構成する一連のプロパティには、次の要件があります。  
  
-   エンティティ セット内では、2 つ以上のエンティティ キーを同じにすることができません。 つまり、エンティティ セット内の 2 つのエンティティに対して、キーを構成するすべてのプロパティの値を同じにすることができません。 ただし、エンティティ キーを構成する一部 (すべてではなく) の値は同じにすることができます。  
  
-   エンティティ キー必要がありますの非 null 値が、変更できないセットから成る[プリミティブ型のプロパティ](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)です。  
  
-   エンティティ型のエンティティ キーを構成するプロパティは、変更できません。 エンティティ型に対して複数のエンティティ キーを許可することはできません。代理キーはサポートされていません。  
  
-   エンティティが継承階層に含まれる場合、ルート エンティティには、エンティティ キーを構成するすべてのプロパティを含める必要があり、そのエンティティ キーをルート エンティティ型に定義する必要があります。 詳細については、次を参照してください。 [Entity Data Model: 継承](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)です。  
  
## <a name="example"></a>例  
 下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。 各エンティティ型のエンティティ キーを構成するプロパティには、"(キー)" と示されています。 `Author` エンティティ型には、`Name` と `Address` の 2 つのプロパティで構成されるエンティティ キーが含まれます。  
  
 ![モデルの例](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。 次の CSDL は、上のダイアグラムに示された `Book` エンティティ型を定義します。 エンティティ キーは、エンティティ型の `ISBN` プロパティを参照して定義されています。  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 国際標準図書番号 (ISBN) は書籍を一意に識別するものであるため、`ISBN` プロパティは、エンティティ キーに適しています。  
  
 次の CSDL は、上のダイアグラムに示された `Author` エンティティ型を定義します。 エンティティ キーは、`Name` と `Address` の 2 つのプロパティで構成されています。  
  
 [!code-xml[EDM_Example_Model#CompositeKeyExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#compositekeyexample)]  
  
 同じ名前の 2 人の著者が同じ住所に住む可能性は低いため、エンティティ キーに `Name` および `Address` を使用するのは妥当な選択になります。 ただし、エンティティ キーのこの選択では、エンティティ セット内のエンティティ キーの一意性を絶対的に保証することはできません。 この場合には、`AuthorId` などのプロパティを追加して、著者を一意に識別することが推奨されます。  
  
## <a name="see-also"></a>関連項目  
 [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
