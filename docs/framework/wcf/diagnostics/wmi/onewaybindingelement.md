---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: ee7cfed20234175ba54dd25dbbbab4615c1ed7af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485758"
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
