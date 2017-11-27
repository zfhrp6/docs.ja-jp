---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b09d7fc476d5eed7f7c534fdde46cb18eeac30d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a>System.ServiceModel.Channels.PeerNodeAuthenticationFailure
潜在的な近隣ノードとのセキュリティ ハンドシェイクに失敗しました。  
  
## <a name="description"></a>説明  
 このトレースは、セキュリティで保護された近隣との接続を確立するときに行われます。 これは、資格情報が十分でないか間違っている場合に発生します。  
  
 PeerChannel では、トークンの種類として、強力な識別手段である X.509 証明書だけを認識します。X.509 証明書は、実装可能な認証および承認の種類に基づいて強力な ID モデルを提供します。 PeerChannel では、パスワードを使用した簡単なアプリケーションもサポートしています。 パスワードは、セッションへのエントリを許可する目的でのみ使用できます。パスワードを使用して、メッセージの認証を行うことはできません。 これは、ピア グループで共有する共通鍵トークンをソース認証に使用することは困難かつ不適切であるためです。  
  
## <a name="troubleshooting"></a>トラブルシューティング  
 すべての近隣ノードに適切なセキュリティ資格情報があることを確認します。  
  
## <a name="see-also"></a>関連項目  
 [ピア チャネルのセキュリティ](../../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [トレース](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [トレースを使用して、アプリケーションのトラブルシューティング](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [管理と診断](../../../../../docs/framework/wcf/diagnostics/index.md)
