---
title: "NetTcpBinding アプリケーションからピア チャネル アプリケーションへの変換"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d52b005013e9728cfcdb43ad289984018b90d27c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a>NetTcpBinding アプリケーションからピア チャネル アプリケーションへの変換
[!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] を使用するクライアント間の接続は、その接続パラメーターを記述するバインディングを使用して作成できます。 ピアツーピア接続を使用するように [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アプリケーションを変換するには、クライアントを接続するときにこのテクノロジをサポートするバインディングが必要です。 ピア チャネルには、<xref:System.ServiceModel.NetPeerTcpBinding> と呼ばれるバインディングが用意されています。このバインディングは、<xref:System.ServiceModel.NetTcpBinding> と同じような方法で使用できます。 主な違いは、リゾルバー サービスの仕様とセキュリティ設定の定義です。  
  
 アプリケーションでリゾルバーとセキュリティの既定の設定を使用する場合、通常のクライアント/サーバー ベースのアプリケーションは、アプリケーションの構成ファイルでバインディング名を "NetTcpBinding" から "NetPeerTcpBinding" に変更するだけで、ピア チャネルを使用するように変換できます。アプリケーションのコード ベースを変更する必要はありません。  
  
## <a name="see-also"></a>関連項目  
 [ピア チャネル アプリケーションの構築](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)  
 [システム標準のバインディング](../../../../docs/framework/wcf/system-provided-bindings.md)
