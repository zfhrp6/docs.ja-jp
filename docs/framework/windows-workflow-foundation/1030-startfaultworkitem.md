---
title: 1030 - StartFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b25dbd5ced96b8e9ca3ef51e4de841a6238d2cbc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1030---startfaultworkitem"></a>1030 - StartFaultWorkItem
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|1030|  
|キーワード|WFRuntime|  
|レベル|詳細|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  
 FaultWorkItem が実行を開始していることを示します。  
  
## <a name="message"></a>メッセージ  
 Activity '%1'、DisplayName FaultWorkItem の実行を開始: '%2'、InstanceId: '%3' です。  Activity '%4'、DisplayName: '%5'、InstanceId: '%6' から例外が伝達されました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|FaultActivity|xs:string|エラーとなったアクティビティの型名。|  
|FaultActivityDisplayName|xs:string|エラーとなったアクティビティの表示名。|  
|FaultActivityInstanceId|xs:string|エラーとなったアクティビティのインスタンス ID。|  
|ExceptionActivity|xs:string|例外をスローしたアクティビティの型名。|  
|ExceptionActivityDisplayName|xs:string|例外をスローしたアクティビティの表示名。|  
|ExceptionActivityInstanceId|xs:string|例外をスローしたアクティビティのインスタンス ID。|  
|例外|xs:string|例外の詳細|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
