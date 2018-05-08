---
title: 1 秒あたりのキューに置かれた有害メッセージ
ms.date: 03/30/2017
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
ms.openlocfilehash: 6407cce120f5d534f88a12591ea2ad09bb5130d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="queued-poison-messages-per-second"></a>1 秒あたりのキューに置かれた有害メッセージ
カウンター名 : 1 秒あたりのキューに置かれた有害メッセージ  
  
## <a name="description"></a>説明  
 このサービスでキューに置かれたトランスポートによって 1 秒あたりに有害とマークされたメッセージの数です。  
  
 このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
