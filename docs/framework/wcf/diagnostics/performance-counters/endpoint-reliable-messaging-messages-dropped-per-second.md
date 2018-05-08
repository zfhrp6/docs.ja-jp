---
title: 'エンドポイント: 信頼できるメッセージの 1 秒あたりの破棄されたメッセージ'
ms.date: 03/30/2017
ms.assetid: ea3c4fc0-1e0f-4863-8879-57bc6c113018
ms.openlocfilehash: a87e5fef0c13e239959a386f108af3c4cebae7f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="endpoint-reliable-messaging-messages-dropped-per-second"></a>エンドポイント: 信頼できるメッセージの 1 秒あたりの破棄されたメッセージ
カウンター名 : 1 秒あたりに破棄された信頼できるメッセージ セッション  
  
## <a name="description"></a>説明  
 このエンドポイントで 1 秒間に破棄された信頼できるメッセージング メッセージの合計数です。  
  
 このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
