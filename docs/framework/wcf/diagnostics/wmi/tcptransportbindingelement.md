---
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: e64f689923d95546c8cecdf47c247faf79242ebf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485815"
---
# <a name="tcptransportbindingelement"></a>TcpTransportBindingElement
TcpTransportBindingElement  
  
## <a name="syntax"></a>構文  
  
```  
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a>メソッド  
 TcpTransportBindingElement クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 TcpTransportBindingElement クラスには、次のプロパティがあります。  
  
### <a name="connectionpoolsettings"></a>ConnectionPoolSettings  
 データ型 : TcpConnectionPoolSettings  
  
 アクセスの種類 : 読み取り専用  
  
 接続プールの設定。  
  
### <a name="listenbacklog"></a>ListenBacklog  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 保留可能なキュー内の接続要求の最大数です。  
  
### <a name="portsharingenabled"></a>PortSharingEnabled  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 TCP ポート共有をこの接続で有効にするかどうかを指定するブール値です。  
  
### <a name="teredoenabled"></a>TeredoEnabled  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 Teredo (ファイアウォールの内側にあるクライアントをアドレス指定するためのテクノロジ) を有効にするかどうかを指定するブール値です。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
