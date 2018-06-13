---
title: 3503 - DuplicateCorrelationQuery
ms.date: 03/30/2017
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
ms.openlocfilehash: 37a689b30b0bcab9124472deb98627afbe30dfee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511401"
---
# <a name="3503---duplicatecorrelationquery"></a>3503 - DuplicateCorrelationQuery
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|3503|  
|キーワード|WFServices|  
|レベル|警告|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  
 重複する CorrelationQuery が見つかったことを示します。 相関の計算時には、重複するクエリは使用されません。  
  
## <a name="message"></a>メッセージ  
 Where='%1' で重複する CorrelationQuery が見つかりました。 相関の計算時には、この重複するクエリは使用されません。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|Where|xs:string|関連付けクエリの Where 部分。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
