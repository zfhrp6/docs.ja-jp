---
title: "要素のテキストの推論"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 00a66a1f995ac4d705af2bf39993cb387e3bf25d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="inferring-element-text"></a>要素のテキストの推論
要素のテキストが含まれています (要素の属性を持つ) や、繰り返される要素など、名前の新しい列をテーブルとして推論される子要素が存在しない場合**TableName_Text**要素に対して推論されるテーブルに追加されます。 要素に含まれているテキストはテーブルの行に追加され、新しい列に格納されます。 **ColumnMapping**新しい列のプロパティが設定されます**MappingType.SimpleContent**です。  
  
 たとえば、次のような XML があるとします。  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 推論プロセスという名前のテーブルが生成されます**Element1** 2 つの列を含む: **attr1**と**Element1_Text**です。 **ColumnMapping**のプロパティ、 **attr1**列に設定されます**MappingType.Attribute**です。 **ColumnMapping**のプロパティ、 **Element1_Text**列に設定されます**MappingType.SimpleContent**です。  
  
 **データセット:** DocumentElement  
  
 **Table:** Element1  
  
|attr1|Element1_Text|  
|-----------|--------------------|  
|value1|Text1|  
  
 要素にテキストだけでなく、テキストを含む子の要素も含まれている場合は、その要素に含まれているテキストを格納するための列はテーブルに追加されません。 要素に含まれるテキストは無視されますが、子の要素のテキストはテーブルの行に追加されます。 たとえば、次のような XML があるとします。  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 推論プロセスという名前のテーブルが生成されます**Element1**という 1 つの列を持つ**ChildElement1**です。 テキスト、 **ChildElement1**要素は、テーブルの行に含まれます。 その他のテキストは無視されます。 **ColumnMapping**のプロパティ、 **ChildElement1**列に設定されます**MappingType.Element**です。  
  
 **データセット:** DocumentElement  
  
 **Table:** Element1  
  
|ChildElement1|  
|-------------------|  
|Text2|  
  
## <a name="see-also"></a>参照  
 [XML からの DataSet リレーショナル構造の推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [XML からの DataSet の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [XML の DataSet スキーマ情報の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
