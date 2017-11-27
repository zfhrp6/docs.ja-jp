---
title: "Entity Framework 用 SqlClient の型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c8a3a3e794941c2713af0e5b098bd7f8d783eb4c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="sqlclient-for-entity-frameworktypes"></a>Entity Framework 用 SqlClient の型
.NET Framework Data Provider for SQL Server (SqlClient) プロバイダー マニフェスト ファイルには、プロバイダー プリミティブ型のリスト、それぞれの型のファセット、概念モデルとストレージ モデルのプリミティブ型とのマッピング、および概念モデルとストレージ モデルのプリミティブ型間での昇格と変換の規則が含まれています。  
  
 次の表は、SQL Server 2008 用の種類を示します[!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)]、および[!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]データベースとどのようにこれらの型マップに概念モデルの種類。 いくつかの新しい型が SQL Server の新しいバージョンで導入されており、これらの型は SQL Server の古いバージョンではサポートされていません。 これらの型については次の表で説明します。  
  
|プロバイダー型の<br /><br /> name|プロバイダー型の<br /><br /> 属性|`EDMSimpleType`<br /><br /> name|ファセット|  
|----------------------------|----------------------------------|------------------------------|------------|  
|`bit`|適用なし|`Edm.Boolean`|該当なし|  
|`tinyint`|該当なし|`Edm.Byte`|該当なし|  
|`smallint`|該当なし|`Edm.Int16`|該当なし|  
|`int`|該当なし|`Edm.Int32`|該当なし|  
|`bigint`|該当なし|`Edm.Int64`|該当なし|  
|`float`|該当なし|`Edm.Double`|該当なし|  
|`real`|該当なし|`Edm.Double`|該当なし|  
|`decimal`|適用なし|`Edm.Decimal`|有効桁数。<br /><br /> -最小値: 1<br /><br /> -最大: 38<br /><br /> -既定値: 18<br /><br /> -定数: False<br /><br /> スケール:<br /><br /> -最小値: 0<br /><br /> -最大: 38<br /><br /> -既定値: 0<br /><br /> -定数: False|  
|`numeric`|適用なし|`Edm.Decimal`|有効桁数。<br /><br /> -最小値: 1<br /><br /> -最大: 38<br /><br /> -既定値: 18<br /><br /> -定数: False<br /><br /> スケール:<br /><br /> -最小値: 0<br /><br /> -最大: 38<br /><br /> -既定値: 0<br /><br /> -定数: False|  
|`smallmoney`|適用なし|`Edm.Decimal`|有効桁数。<br /><br /> -既定値: 10<br /><br /> -定数: True<br /><br /> スケール:<br /><br /> -既定値: 4<br /><br /> -定数: True|  
|`money`|適用なし|`Edm.Decimal`|有効桁数。<br /><br /> -既定値: 19<br /><br /> -定数: True<br /><br /> スケール:<br /><br /> -既定値: 4<br /><br /> -定数: True|  
|`binary`|適用なし|`Edm.Binary`|MaxLength:<br /><br /> -最小値: 1<br /><br /> -最大: 8000<br /><br /> -既定値: 8000<br /><br /> -定数: False<br /><br /> FixedLength:<br /><br /> -既定値: True<br /><br /> -定数: True|  
|`varbinary`|適用なし|`Edm.Binary`|MaxLength:<br /><br /> -最小値: 1<br /><br /> -最大: 8000<br /><br /> -既定値: 8000<br /><br /> -定数: False<br /><br /> FixedLength:<br /><br /> -既定値: False<br /><br /> -定数: True|  
|`varbinary(max)`<br /><br /> 注: この型はではサポートされていません[!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]です。|適用なし|`Edm.Binary`|MaxLength:<br /><br /> -既定値: 214748364780<br /><br /> -定数: True<br /><br /> FixedLength:<br /><br /> -既定値: False<br /><br /> -定数: True|  
|`image`|適用なし|`Edm.Binary`|MaxLength:<br /><br /> -既定値: 2,147, 483,647<br /><br /> -定数: True<br /><br /> FixedLength:<br /><br /> -既定値: False<br /><br /> -定数: True|  
|`timestamp`|適用なし|`Edm.Binary`|MaxLength:<br /><br /> -既定値: 8<br /><br /> -定数: True<br /><br /> FixedLength:<br /><br /> -既定値: True<br /><br /> -定数: True|  
|`rowversion`|適用なし|`Edm.Binary`|MaxLength:<br /><br /> -既定値: 8<br /><br /> -定数: True<br /><br /> FixedLength:<br /><br /> -既定値: True<br /><br /> -定数: True|  
|`smalldatetime`|適用なし|`Edm.DateTime`|有効桁数。<br /><br /> -既定値: 0<br /><br /> -定数: True|  
|`datetime`|適用なし|`Edm.DateTime`|有効桁数。<br /><br /> -既定値: 3<br /><br /> -定数: True|  
|`date`<br /><br /> 注: この型は、SQL Server 2005 および SQL Server 2000 ではサポートされていません。|適用なし|`Edm.DateTime`|有効桁数。<br /><br /> -既定値: 0<br /><br /> -定数: False|  
|`time`<br /><br /> 注: この型は、SQL Server 2005 および SQL Server 2000 ではサポートされていません。|適用なし|`Edm.Time`|有効桁数。<br /><br /> -既定値: 7<br /><br /> -定数: False|  
|`datetime2`<br /><br /> 注: この型は、SQL Server 2005 および SQL Server 2000 ではサポートされていません。|適用なし|`Edm.DateTime`|有効桁数。<br /><br /> -既定値: 7<br /><br /> -定数: False|  
|`datetimeoffset`<br /><br /> 注: この型は、SQL Server 2005 および SQL Server 2000 ではサポートされていません。|適用なし|`Edm.DateTimeOffset`|有効桁数。<br /><br /> -既定値: 7<br /><br /> -定数: False|  
|`nvarchar`<br /><br /> 注: この型はではサポートされていません[!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]です。|適用なし|`Edm.String`|MaxLength:<br /><br /> -最小値: 1<br /><br /> -最大: 4000<br /><br /> -既定値: 4000<br /><br /> -定数: False<br /><br /> Unicode:<br /><br /> -既定値: True<br /><br /> -定数: True<br /><br /> FixedLength:<br /><br /> -既定値: False<br /><br /> -定数: True|  
|`varchar`<br /><br /> 注: この型はではサポートされていません[!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]です。|適用なし|`Edm.String`|MaxLength:<br /><br /> -最小値: 1<br /><br /> -最大: 8000<br /><br /> -既定値: 8000<br /><br /> -定数: False<br /><br /> Unicode:<br /><br /> -既定値: False<br /><br /> -定数: True<br /><br /> FixedLength:<br /><br /> -既定値: False<br /><br /> -定数: True|  
|`char`|適用なし|`Edm.String`|MaxLength:<br /><br /> -最小値: 1<br /><br /> -最大: 8000<br /><br /> -既定値: 8000<br /><br /> -定数: False<br /><br /> Unicode:<br /><br /> -既定値: False<br /><br /> -定数: True<br /><br /> FixedLength:<br /><br /> -既定値: True<br /><br /> -定数: True|  
|`nchar`|適用なし|`Edm.String`|MaxLength:<br /><br /> -最小値: 1<br /><br /> -最大: 4000<br /><br /> -既定値: 4000<br /><br /> -定数: False<br /><br /> Unicode:<br /><br /> -既定値: True<br /><br /> -定数: True<br /><br /> FixedLength:<br /><br /> -既定値: True<br /><br /> -定数: True|  
|`varchar`(`max`)|適用なし|`Edm.String`|MaxLength:<br /><br /> -既定値: 2,147, 483,647<br /><br /> -定数: True<br /><br /> Unicode:<br /><br /> -既定値: False<br /><br /> -定数: True<br /><br /> FixedLength:<br /><br /> -既定値: False<br /><br /> -定数: True|  
|`nvarchar`(`max`)|適用なし|`Edm.String`|MaxLength:<br /><br /> -既定値: 1073741823<br /><br /> -定数: True<br /><br /> Unicode:<br /><br /> -既定値: True<br /><br /> -定数: True<br /><br /> FixedLength:<br /><br /> -既定値: False<br /><br /> -定数: True|  
|`ntext`|等しいかどうか比較可能な: False<br /><br /> 順序を比較できる: False|`Edm.String`|MaxLength:<br /><br /> -既定値: 1073741823<br /><br /> -定数: True<br /><br /> Unicode:<br /><br /> -既定値: False<br /><br /> -定数: True<br /><br /> FixedLength:<br /><br /> -既定値: False<br /><br /> -定数: True|  
|`text`|等しいかどうか比較可能な: False<br /><br /> 順序を比較できる: False|`Edm.String`|MaxLength:<br /><br /> -既定値: 2,147, 483,647<br /><br /> -定数: True<br /><br /> Unicode:<br /><br /> -既定値: False<br /><br /> -定数: True<br /><br /> FixedLength:<br /><br /> -既定値: False<br /><br /> -定数: True|  
|`Unique`<br /><br /> `identifier`|等しいかどうか比較可能な: True<br /><br /> 順序を比較できる: True|`Edm.Guid`|適用なし|  
|`xml`|等しいかどうか比較可能な: False<br /><br /> 順序を比較できる: False|`Edm.String`|MaxLength:<br /><br /> -既定値: 1073741823<br /><br /> -定数: True<br /><br /> Unicode:<br /><br /> -既定値: True<br /><br /> -定数: True<br /><br /> FixedLength:<br /><br /> -既定値: False<br /><br /> -定数: True|  
  
## <a name="see-also"></a>関連項目  
 [CSDL、SSDL、および MSL 仕様](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
