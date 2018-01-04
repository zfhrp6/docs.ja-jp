---
title: 1014 - ScheduleCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a80406ce56000703555f7834714222e03d2b65f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="1014---schedulecompletionworkitem"></a>1014 - ScheduleCompletionWorkItem
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|1014|  
|キーワード|WFRuntime|  
|レベル|詳細|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  
 CompletionWorkItem がスケジュールされていることを示します。  
  
## <a name="message"></a>メッセージ  
 親 Activity '%1'、DisplayName に対して CompletionWorkItem がスケジュールされました: '%2'、InstanceId: '%3' です。  Activity '%4'、DisplayName: '%5'、InstanceId: '%6' が完了しました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|ParentActivity|xs:string|親アクティビティの型名。|  
|ParentDisplayName|xs:string|親アクティビティの表示名。|  
|ParentInstanceId|xs:string|親アクティビティのインスタンス ID。|  
|CompletedActivity|xs:string|完了したアクティビティの型名。|  
|CompletedActivityDisplayName|xs:string|完了したアクティビティの表示名。|  
|CompletedActivityInstanceId|xs:string|完了したアクティビティのインスタンス ID。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
