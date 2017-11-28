---
title: 1026 - ScheduleTransactionContextWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d5f86ba-ec21-4129-a726-5432e425384c
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4d881f1be4e809cf45f100b966d6013ae8fa88f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1026---scheduletransactioncontextworkitem"></a>1026 - ScheduleTransactionContextWorkItem
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|1026|  
|キーワード|WFRuntime|  
|レベル|詳細|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  
 TransactionContextWorkItem がスケジュールされていることを示します。  
  
## <a name="message"></a>メッセージ  
 Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対して TransactionContextWorkItem がスケジュールされました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|アクティビティ|xs:string|アクティビティの型名。|  
|DisplayName|xs:string|アクティビティの表示名。|  
|InstanceId|xs:string|アクティビティのインスタンス ID。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
