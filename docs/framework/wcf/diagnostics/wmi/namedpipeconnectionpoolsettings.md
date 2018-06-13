---
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 3548a1f19672a98ad0fc81eec15d5be29e5170bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486287"
---
# <a name="namedpipeconnectionpoolsettings"></a>NamedPipeConnectionPoolSettings
NamedPipeConnectionPoolSettings  
  
## <a name="syntax"></a>構文  
  
```  
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a>メソッド  
 NamedPipeConnectionPoolSettings クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 NamedPipeConnectionPoolSettings クラスには、次のプロパティがあります。  
  
### <a name="groupname"></a>GroupName  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 バインド要素により使用される接続プールのグループ名。  
  
### <a name="idletimeout"></a>IdleTimeout  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 接続が切断されるまでの最大アイドル時間。  
  
### <a name="maxoutboundconnectionsperendpoint"></a>MaxOutboundConnectionsPerEndpoint  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 クライアント上の各エンドポイントでの発信接続の最大数。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
