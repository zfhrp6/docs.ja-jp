---
title: 1 秒あたりの呼び出し回数
ms.date: 03/30/2017
ms.assetid: 0efb5a94-d83b-4793-b529-6fcbedb65c43
ms.openlocfilehash: 04eb5deaf8e6eb09be4e0bf404bec11b8ce84427
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="calls-per-second"></a>1 秒あたりの呼び出し回数
カウンター名 : 1 秒あたりの呼び出し回数  
  
## <a name="description"></a>説明  
 この操作が 1 秒あたりに呼び出される回数です。  
  
 このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
