---
title: TcpTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b9aa7e0d9eaba0181b17b44da1bf871c10af814
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
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
