---
title: 402 - StartSignpostEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e5be126-765d-4ac9-88e7-008e9ef4f0e5
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c0cd786f78336be50ad2ef5447f74b92b2abbdc7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="402---startsignpostevent"></a>402 - StartSignpostEvent
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|402|  
|キーワード|トラブルシューティング|  
|レベル|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  
 このイベントは、エンド ツー エンド アクティビティの開始を示します。 ここにはアクティビティの名前が指定されています。  
  
## <a name="message"></a>メッセージ  
 アクティビティの境界  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|Extended Data|`xs:string`|アクティビティの名前。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
