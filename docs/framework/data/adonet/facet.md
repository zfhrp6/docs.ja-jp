---
title: "ファセット | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 91c4e6aa-3e54-4b6c-a38a-abf27808cc85
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# ファセット
*ファセット*は、プリミティブ型のプロパティ定義の詳細を追加するために使用します。  [プロパティ](../../../../docs/framework/data/adonet/property.md)定義には、プロパティの型の情報が含まれますが、多くの場合、より詳しい情報が必要になります。  たとえば、概念モデルのエンティティ型に、値を null に設定できない `String` 型のプロパティが含まれる場合があります。  ファセットにより、このレベルの詳細を指定することができます。  
  
 下の表は、EDM でサポートされるファセットについて説明しています。  
  
> [!NOTE]
>  ファセットの正確な値と動作は、EDM の実装を使用するランタイム環境によって決まります。  
  
|ファセット|説明|対象|  
|-----------|--------|--------|  
|`Collation`|プロパティの値に対して比較と順序付け操作を行うときに使用する照合シーケンス \(または並べ替え順序\) を指定します。|`String`|  
|`ConcurrencyMode`|プロパティの値をオプティミスティック同時実行制御チェックに使用することを指定します。|すべてのプリミティブ型のプロパティ|  
|`Default`|インスタンス化で値が指定されない場合のプロパティの既定値を指定します。|すべてのプリミティブ型のプロパティ|  
|`FixedLength`|プロパティ値の長さを可変とすることができるかどうかを指定します。|`Binary`, `String`|  
|`MaxLength`|プロパティ値の最大長を指定します。|`Binary`, `String`|  
|`Nullable`|プロパティに null 値を指定できるかどうかを指定します。|すべてのプリミティブ型のプロパティ|  
|`Precision`|`Decimal` 型のプロパティには、プロパティ値の桁数を指定します。  `Time` 型、`DateTime` 型、および `DateTimeOffset` 型のプロパティには、プロパティ値の秒の小数点以下の有効桁数を指定します。|`DateTime`, `DateTimeOffset`, `Decimal`, `Time`,|  
|`Scale`|プロパティ値の小数点の右側の桁数を指定します。|Decimal \(10 進数型\)|  
|`Unicode`|プロパティ値を Unicode として保存するかどうかを指定します。|`String`|  
  
## 例  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) では、概念スキーマ定義言語 \([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)\) と呼ばれるドメイン固有言語 \(DSL\) を使用して概念モデルを定義します。  次の CSDL は `Book` エンティティ型を定義しています。  ファセットは XML 属性として実装されています。  ファセット値は、プロパティ値を null に設定できないことと、`Revision` プロパティの `Scale` と `Precision` がそれぞれ 29 に設定されることを示します。  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## 参照  
 [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)