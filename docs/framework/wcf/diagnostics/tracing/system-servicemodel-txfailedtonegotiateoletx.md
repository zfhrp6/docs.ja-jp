---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 61360eff4f2c403eea98bbc0a2eae36e516b3d7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a>System.ServiceModel.TxFailedToNegotiateOleTx
指定されたコーディネーション コンテキストのための OleTransactions プロトコル ネゴシエーションに失敗しました。  
  
## <a name="description"></a>説明  
 OleTx 情報が添付された受信トランザクションがその OleTx 情報を使用できず、代わりに WS-AT 使用した場合にトレースされます。  
  
## <a name="troubleshooting"></a>トラブルシューティング  
 コンピューター間の MSDTC RPC 通信に潜在的な問題があることを示しています。 これらのトレースが多数ログに記録されている場合は、大幅なパフォーマンス低下が発生している可能性があります。  OleTx が必要ない場合は、WS-AT のレジストリ構成で `OleTxUpgradeEnabled` を 0 に設定してください。  
  
## <a name="see-also"></a>関連項目  
 [トレース](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [トレースを使用して、アプリケーションのトラブルシューティング](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [管理と診断](../../../../../docs/framework/wcf/diagnostics/index.md)
