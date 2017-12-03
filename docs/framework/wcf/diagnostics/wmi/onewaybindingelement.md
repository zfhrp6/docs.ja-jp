---
title: OneWayBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: abaacfb6541d41019a8d0cd6df53913c6b7911f2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="onewaybindingelement"></a>OneWayBindingElement
OneWayBindingElement  
  
## <a name="syntax"></a>構文  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a>メソッド  
 OneWayBindingElement クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 OneWayBindingElement クラスには、次のプロパティがあります。  
  
### <a name="channelpoolsettings"></a>ChannelPoolSettings  
 データ型 : ChannelPoolSettings  
  
 アクセスの種類 : 読み取り専用  
  
 チャネル プールの設定。  
  
### <a name="maxacceptedchannels"></a>MaxAcceptedChannels  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 許可されるチャネルの最大数。  
  
### <a name="packetroutable"></a>PacketRoutable  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 パケットがルーティング可能かどうかを示す値。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
