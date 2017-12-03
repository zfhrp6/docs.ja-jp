---
title: Binding2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b9e44d161e1229db9145f4ed7e337396bbd98c68
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="binding"></a>バインド
wmi バインディング  
  
## <a name="syntax"></a>構文  
  
```  
class Binding  
{  
  BindingElement BindingElements[];  
  datetime CloseTimeout;  
  string Name;  
  string Namespace;  
  datetime OpenTimeout;  
  datetime ReceiveTimeout;  
  string Scheme;  
  datetime SendTimeout;  
};  
```  
  
## <a name="methods"></a>メソッド  
 Binding クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 Binding クラスには、次のプロパティがあります。  
  
### <a name="bindingelements"></a>BindingElements  
 データ型 : BindingElement 配列  
  
 アクセスの種類 : 読み取り専用  
  
 バインディングによって実装されるバインド要素のコレクションです。  
  
### <a name="closetimeout"></a>CloseTimeout  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 クローズ操作が完了するまで待機する時間です。  
  
### <a name="name"></a>名前  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 バインディングの名前。  
  
### <a name="namespace"></a>名前空間  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 バインディングの XML 名前空間。  
  
### <a name="opentimeout"></a>OpenTimeout  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 オープン操作が完了するまで待機する時間です。  
  
### <a name="receivetimeout"></a>ReceiveTimeout  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 受信操作が完了するまで待機する時間です。  
  
### <a name="scheme"></a>Scheme  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 このバインディングに組み込まれているチャネルおよびリスナー ファクトリによって使用される URI トランスポート スキームです。  
  
### <a name="sendtimeout"></a>SendTimeout  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 送信操作が完了するまで待機する時間です。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Channels.Binding>
