---
title: 1040 - InArgumentBound
ms.date: 03/30/2017
ms.assetid: 7dfaad1b-36c0-4575-84c1-31d63b0eaf5d
ms.openlocfilehash: 984372c07ccfb11f2f05d5488fa5ffc95075db41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510196"
---
# <a name="1040---inargumentbound"></a>1040 - InArgumentBound
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|1040|  
|キーワード|WFActivities|  
|レベル|詳細|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  
 In 引数がバインドされたことを示します。  
  
## <a name="message"></a>メッセージ  
 Activity '%2' の引数 '%1' で、DisplayName: '%3'、InstanceId: '%4' が値: %5 にバインドされています。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|InArgument|xs:string|InArgument の名前。|  
|アクティビティ|xs:string|アクティビティの型名。|  
|DisplayName|xs:string|アクティビティの表示名。|  
|InstanceId|xs:string|アクティビティのインスタンス ID。|  
|値|xs:string|InArgument にバインドされた値。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
