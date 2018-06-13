---
title: 1013 - CompleteExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 31fc57b3-ef2f-48f0-a5de-b4e2c5c9ded7
ms.openlocfilehash: c1ff62bb4143bb798ea7adb7c3fee539ef68bc37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509575"
---
# <a name="1013---completeexecuteactivityworkitem"></a>1013 - CompleteExecuteActivityWorkItem
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|1013|  
|キーワード|WFRuntime|  
|レベル|詳細|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  
 ExecuteActivityWorkItem が完了したことを示します  
  
## <a name="message"></a>メッセージ  
 Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の ExecuteActivityWorkItem が完了しました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|アクティビティ|xs:string|アクティビティの型名。|  
|DisplayName|xs:string|アクティビティの表示名。|  
|InstanceId|xs:string|アクティビティのインスタンス ID。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
