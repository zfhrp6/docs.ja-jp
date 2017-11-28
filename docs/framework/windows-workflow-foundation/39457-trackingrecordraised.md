---
title: 39457 - TrackingRecordRaised
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a2731d1-c731-4b79-bb69-016cb69ef481
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3d2e142db5834a6c867970a28ec74e9fceebee16
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="39457---trackingrecordraised"></a>39457 - TrackingRecordRaised
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|39457|  
|キーワード|WFRuntime|  
|レベル|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  
 TrackingRecord が TrackingParticipant に発生したことを示します。  
  
## <a name="message"></a>メッセージ  
 追跡レコード %1 が %2 になりました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|RecordNumber|xs:string|追跡レコード番号。|  
|ParticipantId|xs:string|追跡参加要素|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
