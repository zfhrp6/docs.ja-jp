---
title: サービス
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: 0cfeb178e26f6c93e29210accf5d7866cc1fca02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487148"
---
# <a name="service"></a>サービス
サービス  
  
## <a name="syntax"></a>構文  
  
```  
class Service  
{  
  string BaseAddresses[];  
  Behavior Behaviors[];  
  string ConfigurationName;  
  string CounterInstanceName;  
  string DistinguishedName;  
  string Extensions[];  
  string Metadata[];  
  string Name;  
  string Namespace;  
  datetime Opened;  
  Channel OutgoingChannels[];  
  sint32 ProcessId;  
};  
```  
  
## <a name="methods"></a>メソッド  
 Service クラスで定義されているメソッドはありません。  
  
## <a name="properties"></a>プロパティ  
 Service クラスには次のプロパティがあります。  
  
### <a name="baseaddresses"></a>BaseAddresses  
 データ型 : string array  
  
 アクセスの種類 : 読み取り専用  
  
 サービスによって使用されるベース アドレスです。  
  
### <a name="behaviors"></a>ビヘイビアー  
 データ型 : Behavior array  
  
 アクセスの種類 : 読み取り専用  
  
 このサービスに関連付けられている動作です。  
  
### <a name="configurationname"></a>ConfigurationName  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 ServiceElement_BehaviorConfiguration  
  
### <a name="counterinstancename"></a>CounterInstanceName  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 サービスのパフォーマンス カウンターのインスタンスのインスタンス名です。  
  
### <a name="distinguishedname"></a>DistinguishedName  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 アドレスでのサービス名です。  
  
### <a name="extensions"></a>拡張機能  
 データ型 : string array  
  
 アクセスの種類 : 読み取り専用  
  
 サービス インスタンスの拡張に対するインスタンス コンテキストです。  
  
### <a name="metadata"></a>メタデータ  
 データ型 : string array  
  
 アクセスの種類 : 読み取り専用  
  
 サービス メタデータの設定です。  
  
### <a name="name"></a>名前  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 このサービスの一意の名前。  
  
### <a name="namespace"></a>名前空間  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 サービスの名前空間です。  
  
### <a name="opened"></a>Opened  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 サービスが開かれた時刻です。  
  
### <a name="outgoingchannels"></a>OutgoingChannels  
 データ型 : Channel 配列  
  
 アクセスの種類 : 読み取り専用  
  
 サービス インスタンスから送信しているチャネルです。  
  
### <a name="processid"></a>ProcessId  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 サービスをホストするプロセスのプロセス ID です。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|
