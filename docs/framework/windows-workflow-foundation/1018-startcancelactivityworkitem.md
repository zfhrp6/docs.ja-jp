---
title: 1018 - StartCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 68b4fa1d-eee6-4a2a-8c16-7e9d89f08ab9
ms.openlocfilehash: 8d7045b0a7f31ecfd5dd90f319192bd202804353
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510654"
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
