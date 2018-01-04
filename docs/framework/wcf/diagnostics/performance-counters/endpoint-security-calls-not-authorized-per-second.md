---
title: "エンドポイント : 1 秒あたりの承認されていないセキュリティ呼び出し"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 2700e46f2061818dda95b8e3977c13b62e15481b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a>エンドポイント : 1 秒あたりの承認されていないセキュリティ呼び出し
カウンター名 : 1 秒あたりの承認されていないセキュリティ呼び出し。  
  
## <a name="description"></a>説明  
 有効なユーザーから適切な保護を適用して送信されたが、特定のタスクの実行がユーザーに許可されていない、受信メッセージの 1 秒あたりの数です。  
  
 このカウンターは <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> メソッドで `false` が返された場合にインクリメントされます。  
  
 このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
