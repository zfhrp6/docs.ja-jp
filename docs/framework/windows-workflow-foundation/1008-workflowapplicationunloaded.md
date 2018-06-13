---
title: 1008 - WorkflowApplicationUnloaded
ms.date: 03/30/2017
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
ms.openlocfilehash: c7c22e6e4270a3fc3e91e1711db5da9bd5a378b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509562"
---
# <a name="1008---workflowapplicationunloaded"></a>1008 - WorkflowApplicationUnloaded
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|1008|  
|キーワード|WFRuntime|  
|レベル|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  
 ワークフロー アプリケーションがアンロードしたことを示します。  
  
## <a name="message"></a>メッセージ  
 WorkflowInstance ID: '%1' がアンロードされました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|ワークフローのインスタンス ID|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
