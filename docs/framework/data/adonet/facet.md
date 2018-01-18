---
title: facet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91c4e6aa-3e54-4b6c-a38a-abf27808cc85
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 23346fe2095cea2b3f0d705c7d6d8914c35c06f7
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="facet"></a>facet
A*ファセット*詳細プリミティブ型のプロパティ定義を追加するために使用します。 A[プロパティ](../../../../docs/framework/data/adonet/property.md)定義には、プロパティの型に関する情報が含まれていますが、多くの場合より詳しい情報が必要です。 たとえば、概念モデルのエンティティ型に、値を null に設定できない `String` 型のプロパティが含まれる場合があります。 ファセットにより、このレベルの詳細を指定することができます。  
  
 下の表は、EDM でサポートされるファセットについて説明しています。  
  
> [!NOTE]
>  ファセットの正確な値と動作は、EDM の実装を使用するランタイム環境によって決まります。  
  
|ファセット|説明|対象|  
|-----------|-----------------|----------------|  
|`Collation`|プロパティの値に対して比較と順序付け操作を行うときに使用する照合シーケンス (または並べ替え順序) を指定します。|`String`|  
|`ConcurrencyMode`|プロパティの値をオプティミスティック同時実行制御チェックに使用することを指定します。|すべてのプリミティブ型のプロパティ|  
|`Default`|インスタンス化で値が指定されない場合のプロパティの既定値を指定します。|すべてのプリミティブ型のプロパティ|  
|`FixedLength`|プロパティ値の長さを可変とすることができるかどうかを指定します。|`Binary`, `String`|  
|`MaxLength`|プロパティ値の最大長を指定します。|`Binary`, `String`|  
|`Nullable`|プロパティに null 値を指定できるかどうかを指定します。|すべてのプリミティブ型のプロパティ|  
|`Precision`|`Decimal` 型のプロパティには、プロパティ値の桁数を指定します。 `Time` 型、`DateTime` 型、および `DateTimeOffset` 型のプロパティには、プロパティ値の秒の小数点以下の有効桁数を指定します。|`DateTime`, `DateTimeOffset`, `Decimal`, `Time`,|  
|`Scale`|プロパティ値の小数点の右側の桁数を指定します。|Decimal (10 進数型)|  
|`Unicode`|プロパティ値を Unicode として保存するかどうかを指定します。|`String`|  
  
## <a name="example"></a>例  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。 次の CSDL は `Book` エンティティ型を定義しています。 ファセットは XML 属性として実装されています。 ファセット値は、プロパティ値を null に設定できないことと、`Scale` プロパティの `Precision` と `Revision` がそれぞれ 29 に設定されることを示します。  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a>参照  
 [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
