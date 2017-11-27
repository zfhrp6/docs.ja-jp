---
title: "信頼できるメッセージの 1 秒あたりの破棄されたメッセージ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a11b0b80-b242-48e1-b0bb-7f756db5486b
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 06df77ae14dbe4980ae54cc09a0822f59731bf1c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="reliable-messaging-messages-dropped-per-second"></a>信頼できるメッセージの 1 秒あたりの破棄されたメッセージ
カウンター名 : 1 秒あたりに破棄された信頼できるメッセージ セッション  
  
## <a name="description"></a>説明  
 このサービスで 1 秒間に破棄された信頼できるメッセージング メッセージの合計数です。  
  
 このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
