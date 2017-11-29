---
title: 1006 - WorkflowApplicationUnhandledException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a03809be5e5d61c505e295e2f769a0298f770f7f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1006---workflowapplicationunhandledexception"></a>1006 - WorkflowApplicationUnhandledException
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|1006|  
|キーワード|WFRuntime|  
|レベル|Error|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  
 ワークフロー アプリケーションでハンドルされない例外が検出されたことを示します。  
  
## <a name="message"></a>メッセージ  
 WorkflowInstance Id: '%1' はハンドルされない例外が発生しました。  例外の発生元 Activity '%2'、DisplayName: '%3' です。  次の操作が実行されます: %n%n 4 です。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|ワークフローのインスタンス ID|  
|例外|`xs:string`|例外の詳細|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
