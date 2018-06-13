---
title: DataSet スキーマの推論プロセスの概要
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: 9bcc5ce1574eed60d2ef1aa35bdafe8c6050e44c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760272"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a>DataSet スキーマの推論プロセスの概要
推論プロセスでは、まず、テーブルとして推論する XML ドキュメントの要素を決定します。 XML ドキュメントの残りの要素から、それらのテーブルの列が推論によって決定されます。 入れ子状のテーブルの場合は、入れ子になった <xref:System.Data.DataRelation> オブジェクトと <xref:System.Data.ForeignKeyConstraint> オブジェクトが生成されます。  
  
 推論規則について、次に簡単に説明します。  
  
-   属性を持つ要素は、テーブルとして推論されます。  
  
-   子要素を持つ要素は、テーブルとして推論されます。  
  
-   繰り返し出現する要素は、単一のテーブルとして推論されます。  
  
-   ドキュメント (ルート) 要素に属性がなく、列として推論される子要素もない場合、その要素は <xref:System.Data.DataSet> として推論されます。 それ以外の場合は、ドキュメント要素はテーブルとして推論されます。  
  
-   属性は、列として推論されます。  
  
-   属性または子要素を持たず、繰り返し出現することもない要素は、列として推論されます。  
  
-   推論されたその他の要素内で入れ子になったテーブルとして推論される要素のテーブルとして、入れ子になった**DataRelation** 2 つのテーブル間に作成されます。 新しいプライマリ キーの列が名前付き**TableName_Id**が両方のテーブルに追加されで使用される、 **DataRelation**です。 A **ForeignKeyConstraint**間を使用して 2 つのテーブルが作成、 **TableName_Id**列です。  
  
-   新しい列の名前は、要素のテーブルとして推論されると、テキストは含まれていない子要素を持つ**TableName_Text**の各要素のテキストを作成します。 テーブルとして推論される要素にテキストだけでなく、子要素もある場合、テキストは無視されます。  
  
## <a name="see-also"></a>関連項目  
 [XML からの DataSet リレーショナル構造の推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [XML からの DataSet の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [XML の DataSet スキーマ情報の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
