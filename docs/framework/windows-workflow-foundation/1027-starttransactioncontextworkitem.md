---
title: 1027 - StartTransactionContextWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 116ae5ec-b9d5-4231-824e-270d00eea7b8
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: be35a4d478f4f2af0921cac942ebb95d6aed38d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1027---starttransactioncontextworkitem"></a>1027 - StartTransactionContextWorkItem
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|1027|  
|キーワード|WFRuntime|  
|レベル|詳細|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  
 TransactionContextWorkItem が実行を開始していることを示します。  
  
## <a name="message"></a>メッセージ  
 Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の TransactionContextWorkItem の実行を開始しています。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|アクティビティ|xs:string|アクティビティの型名。|  
|DisplayName|xs:string|アクティビティの表示名。|  
|InstanceId|xs:string|アクティビティのインスタンス ID。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
