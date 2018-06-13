---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: f3474fc1bb0ed0d11df6289ed6470447d815f5ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33475752"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a>System.ServiceModel.Channels.ConnectionPoolCloseException
この接続プールの接続を閉じている間に例外が発生しました。  
  
## <a name="description"></a>説明  
 このエラー レベルのトレースは、Windows Communication Foundation (WCF) の接続プール機能によって使用される接続プールを閉じているときにエラーが発生したことを示します。 このエラーの原因としては、プールされた接続を閉じることに失敗した、またはプールされた接続で CloseTimeout が設定されていることが考えられます。 この例外がスローされると、このプール内でまだ閉じられていない接続はすべて中断され、他のプールにある閉じられていない接続は破棄されます。  
  
## <a name="see-also"></a>関連項目  
 [トレース](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [トレースを使用したアプリケーションのトラブルシューティング](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [管理と診断](../../../../../docs/framework/wcf/diagnostics/index.md)
