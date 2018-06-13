---
title: 'エンドポイント : 1 秒あたりの承認されていないセキュリティ呼び出し'
ms.date: 03/30/2017
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0fd7c3ab7abcc374c4ef89f9f5a0650647cf97a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33471705"
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a>エンドポイント : 1 秒あたりの承認されていないセキュリティ呼び出し
カウンター名 : 1 秒あたりの承認されていないセキュリティ呼び出し。  
  
## <a name="description"></a>説明  
 有効なユーザーから適切な保護を適用して送信されたが、特定のタスクの実行がユーザーに許可されていない、受信メッセージの 1 秒あたりの数です。  
  
 このカウンターは <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> メソッドで `false` が返された場合にインクリメントされます。  
  
 このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
