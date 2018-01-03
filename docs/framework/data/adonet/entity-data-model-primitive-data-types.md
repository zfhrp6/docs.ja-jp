---
title: "Entity Data Model: プリミティブ データ型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7635168e-0566-4fdd-8391-7941b0d9f787
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e9bf1298a5e3fbac82a931abcfb0919238d81bfb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="entity-data-model-primitive-data-types"></a>Entity Data Model: プリミティブ データ型
Entity Data Model (EDM) は、一連の定義に使用される抽象プリミティブ データ型 (文字列、ブール値、Int32 など) をサポートしている[プロパティ](../../../../docs/framework/data/adonet/property.md)概念モデルでします。 これらのプリミティブ データ型は、SQL Server データベースや共通言語ランタイム (CLR) などのストレージ環境またはホスト環境でサポートされる、実際のプリミティブ データ型のプロキシです。 EDM では、プリミティブ データ型に対する演算や変換のセマンティクスを定義していません。これらのセマンティクスは、ストレージ環境またはホスト環境で定義されます。 通常、EDM のプリミティブ データ型は、ストレージ環境またはホスト環境の対応プリミティブ データ型にマップされます。 Entity Framework が、EDM のプリミティブ型を SQL Server データ型にマップする方法については、次を参照してください。 [Entity Framework 用 SqlClient](../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)です。  
  
> [!NOTE]
>  EDM では、プリミティブ データ型のコレクションをサポートしていません。  
  
 EDM の構造化されたデータ型については、次を参照してください。[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)と[複合型](../../../../docs/framework/data/adonet/complex-type.md)です。  
  
## <a name="primitive-data-types-supported-in-the-entity-data-model"></a>Entity Data Model でサポートされるプリミティブ データ型  
 下の表は、EDM でサポートされるプリミティブ データ型の一覧を示します。 テーブルの一覧も、[ファセット](../../../../docs/framework/data/adonet/facet.md)各プリミティブ データ型に適用することがあります。  
  
|プリミティブ データ型|説明|使用できるファセット|  
|-------------------------|-----------------|-----------------------|  
|2 項|バイナリ データを格納します。|MaxLength、FixedLength、Nullable、Default|  
|Boolean|`true` または `false` の値を格納します。|Nullable、Default|  
|Byte|符号なし 8 ビット整数値を格納します。|Precision、Nullable、Default|  
|DateTime|日時を表します。|Precision、Nullable、Default|  
|DateTimeOffset|GMT からのオフセット (分単位) としての日時を格納します。|Precision、Nullable、Default|  
|Decimal (10 進数型)|有効桁数と小数点以下桁数が固定長の数値を格納します。|Precision、Nullable、Default|  
|Double (倍精度浮動小数点型)|15 桁の有効桁数を持つ浮動小数点数を格納します。|Precision、Nullable、Default|  
|Float|7 桁の有効桁数を持つ浮動小数点数を格納します。|Precision、Nullable、Default|  
|Guid|16 バイトの一意識別子を格納します。|Precision、Nullable、Default|  
|Int16|符号付き 16 ビット整数値を格納します。|Precision、Nullable、Default|  
|Int32|符号付き 32 ビット整数値を格納します。|Precision、Nullable、Default|  
|Int64|符号付き 64 ビット整数値を格納します。|Precision、Nullable、Default|  
|SByte|符号付き 8 ビット整数値を格納します。|Precision、Nullable、Default|  
|String|文字データを格納します。|Unicode、FixedLength、MaxLength、Collation、Precision、Nullable、Default|  
|時刻|時刻を格納します。|Precision、Nullable、Default|  
  
## <a name="see-also"></a>参照  
 [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
