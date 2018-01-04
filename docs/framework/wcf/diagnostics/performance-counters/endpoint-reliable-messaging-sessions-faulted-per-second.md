---
title: "エンドポイント : 1 秒あたりのエラーとなった信頼できるメッセージ セッション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9ae808a-7e1f-46b0-9560-d5a866be6d6e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fd75dd054fd16278a1b908eecbfc3f2d03e762ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint-reliable-messaging-sessions-faulted-per-second"></a>エンドポイント : 1 秒あたりのエラーとなった信頼できるメッセージ セッション
カウンター名 : 1 秒あたりのエラーとなった信頼できるメッセージ セッション  
  
## <a name="description"></a>説明  
 1 秒以内にこのエンドポイントでエラーになった信頼できるメッセージ セッション数。  
  
 このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
