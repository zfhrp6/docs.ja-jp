---
title: 1018 - StartCancelActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68b4fa1d-eee6-4a2a-8c16-7e9d89f08ab9
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f74a133a685699bcefc014269a9ecb3ebea4e505
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1018---startcancelactivityworkitem"></a>1018 - StartCancelActivityWorkItem
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|1018|  
|キーワード|WFRuntime|  
|レベル|詳細|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  
 CancelActivityWorkItem が実行を開始していることを示します。  
  
## <a name="message"></a>メッセージ  
 Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の CancelActivityWorkItem の実行を開始しています。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|アクティビティ|xs:string|アクティビティの型名。|  
|DisplayName|xs:string|アクティビティの表示名。|  
|InstanceId|xs:string|アクティビティのインスタンス ID。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
