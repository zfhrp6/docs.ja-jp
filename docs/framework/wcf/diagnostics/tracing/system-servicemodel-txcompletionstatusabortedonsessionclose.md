---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1e9ab5af359b833452664f534e3627f477246fa6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a>System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
指定されたトランザクションは、セッションが終了したときにまだ完了しておらず、TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute が false に設定されているため、中止されました。  
  
## <a name="description"></a>説明  
 現在のアクティブなセッションが終了した時点でトランザクションが完了しておらず、TransactionAutoCompleteOnSessionClose が `false` に設定されている場合にトレースされます。  
  
## <a name="troubleshooting"></a>トラブルシューティング  
 このトレースは、アプリケーションに調査が必要なバグが含まれている可能性があることを示します。  
  
## <a name="see-also"></a>関連項目  
 [トレース](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [トレースを使用して、アプリケーションのトラブルシューティング](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [管理と診断](../../../../../docs/framework/wcf/diagnostics/index.md)
