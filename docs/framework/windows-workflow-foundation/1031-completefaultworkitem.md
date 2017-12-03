---
title: 1031 - CompleteFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5173e61b2479d02dc35c5fcf9ae55634cc8dc7ba
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="1031---completefaultworkitem"></a>1031 - CompleteFaultWorkItem
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|1031|  
|キーワード|WFRuntime|  
|レベル|詳細|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  
 FaultWorkItem が完了したことを示します。  
  
## <a name="message"></a>メッセージ  
 Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の FaultWorkItem が完了しました。 Activity '%4'、DisplayName: '%5'、InstanceId: '%6' から例外が伝達されました。  
  
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
