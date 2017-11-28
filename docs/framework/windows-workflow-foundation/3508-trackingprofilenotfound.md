---
title: 3508 - TrackingProfileNotFound
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fb5636057193fcfb59e5062f6f3833a62b4f3027
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="3508---trackingprofilenotfound"></a>3508 - TrackingProfileNotFound
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|3508|  
|キーワード|WFServices|  
|レベル|詳細|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  
 構成ファイル内に TrackingProfile がないか、または ActivityDefinitionId がプロファイルと一致していないことを示します。  
  
## <a name="message"></a>メッセージ  
 ActivityDefinitionId '%2' の TrackingProfile '%1' が見つかりません。 config ファイルに TrackingProfile がないか、ActivityDefinitionId が一致しません。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|TrackingProfile|xs:string|追跡プロファイルの名前。|  
|ActivityDefinitionId|xs:string|アクティビティ定義 ID。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
