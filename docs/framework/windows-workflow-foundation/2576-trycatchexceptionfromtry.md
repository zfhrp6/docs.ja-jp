---
title: 2576 - TryCatchExceptionFromTry
ms.date: 03/30/2017
ms.assetid: 47e48973-b17c-4a16-8338-c84b54aa0a6e
ms.openlocfilehash: cdc48a1a08e997f7bc6a0ad6b93aa13640af9ed3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512696"
---
# <a name="2576---trycatchexceptionfromtry"></a>2576 - TryCatchExceptionFromTry
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|2576|  
|キーワード|WFActivities|  
|レベル|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  
 TryCatch アクティビティが例外をキャッチしたことを示します。  
  
## <a name="message"></a>メッセージ  
 TryCatch アクティビティ '%1' は、型 '%2' の例外をキャッチしました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|DisplayName|xs:string|アクティビティの表示名。|  
|例外|xs:string|例外の型名。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
