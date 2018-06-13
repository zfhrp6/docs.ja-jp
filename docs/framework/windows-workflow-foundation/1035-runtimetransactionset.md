---
title: 1035 - RuntimeTransactionSet
ms.date: 03/30/2017
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
ms.openlocfilehash: 198e11dd94b0ad5cdc1e01c3611280754ca081d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510035"
---
# <a name="1035---runtimetransactionset"></a>1035 - RuntimeTransactionSet
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|1035|  
|キーワード|WFRuntime|  
|レベル|詳細|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  
 アクティビティがランタイムのトランザクションを設定したことを示します。  
  
## <a name="message"></a>メッセージ  
 Activity '%1'、DisplayName によってランタイム トランザクションが設定されました: '%2'、InstanceId: '%3' です。  実行の分離 Activity '%4'、DisplayName: '%5'、InstanceId: '%6' です。  
  
## <a name="details"></a>説明  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|アクティビティ|xs:string|アクティビティの型名。|  
|DisplayName|xs:string|アクティビティの表示名。|  
|InstanceId|xs:string|アクティビティのインスタンス ID。|  
|IsolatedActivity|xs:string|トランザクションが分離されるアクティビティの型の名前。|  
|IsolatedActivityDisplayName|xs:string|トランザクションが分離されるアクティビティの表示名。|  
|IsolatedActivityInstanceId|xs:string|トランザクションが分離されるアクティビティのインスタンスの ID。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
