---
title: 1041 - WorkflowApplicationPersistableIdle
ms.date: 03/30/2017
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
ms.openlocfilehash: 07be0ae603443a1ef06cb539bba7b227d7b3e325
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509668"
---
# <a name="1041---workflowapplicationpersistableidle"></a>1041 - WorkflowApplicationPersistableIdle
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|1041|  
|キーワード|WFRuntime|  
|レベル|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  
 ワークフロー アプリケーションがアイドル状態のままであることを示します。 ワークフロー アプリケーションはアイドル状態または永続化されます。  
  
## <a name="message"></a>メッセージ  
 WorkflowApplication Id: '%1' には、アイドル状態のままです。  次の操作が実行されます: %n%n 2 です。  
  
## <a name="details"></a>説明  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|WorkflowApplicationId|xs:string|ワークフロー アプリケーション ID|  
|ActionTaken|xs:string|ワークフロー アプリケーションで実行されるアクション。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
