---
title: 1146 - FlowchartSwitchCase
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 274e9209-1720-4512-a615-e742f00895f4
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 68c1c4c881e7b963618679a86622b7f8ab961681
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1146---flowchartswitchcase"></a>1146 - FlowchartSwitchCase
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|1146|  
|キーワード|WFActivities|  
|レベル|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  
 フローチャート スイッチで、どの例が選択されたかを示します。  
  
## <a name="message"></a>メッセージ  
 フローチャート '%1'/FlowSwitch - Case '%2' が選択されました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|FlowChart|xs:string|FlowChart の表示名。|  
|Case|xs:string|選択したスイッチに示します。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
