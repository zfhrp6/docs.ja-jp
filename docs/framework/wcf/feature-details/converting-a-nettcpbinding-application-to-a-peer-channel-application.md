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
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a><span data-ttu-id="d2bb4-102">NetTcpBinding アプリケーションからピア チャネル アプリケーションへの変換</span><span class="sxs-lookup"><span data-stu-id="d2bb4-102">Converting a NetTcpBinding Application to a Peer Channel Application</span></span>
<span data-ttu-id="d2bb4-103">[!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] を使用するクライアント間の接続は、その接続パラメーターを記述するバインディングを使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="d2bb4-103">You can create connections between clients using the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] by using bindings that describe the parameters of the connection.</span></span> <span data-ttu-id="d2bb4-104">ピアツーピア接続を使用するように [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アプリケーションを変換するには、クライアントを接続するときにこのテクノロジをサポートするバインディングが必要です。</span><span class="sxs-lookup"><span data-stu-id="d2bb4-104">Converting a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] application to use peer-to-peer connections requires a binding that supports this technology when making client connections.</span></span> <span data-ttu-id="d2bb4-105">ピア チャネルには、<xref:System.ServiceModel.NetPeerTcpBinding> と呼ばれるバインディングが用意されています。このバインディングは、<xref:System.ServiceModel.NetTcpBinding> と同じような方法で使用できます。</span><span class="sxs-lookup"><span data-stu-id="d2bb4-105">Peer Channel provides a binding called <xref:System.ServiceModel.NetPeerTcpBinding>, which you can use in a similar way to the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="d2bb4-106">主な違いは、リゾルバー サービスの仕様とセキュリティ設定の定義です。</span><span class="sxs-lookup"><span data-stu-id="d2bb4-106">Key differences include specifying a resolver service and defining security settings.</span></span>  
  
 <span data-ttu-id="d2bb4-107">アプリケーションでリゾルバーとセキュリティの既定の設定を使用する場合、通常のクライアント/サーバー ベースのアプリケーションは、アプリケーションの構成ファイルでバインディング名を "NetTcpBinding" から "NetPeerTcpBinding" に変更するだけで、ピア チャネルを使用するように変換できます。アプリケーションのコード ベースを変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d2bb4-107">If an application is using the default resolver and security settings, converting a normal client/server-based application to use Peer Channel entails changing the name of the binding from "NetTcpBinding" to "NetPeerTcpBinding" in the application’s configuration file—you do not have to change the application code base.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2bb4-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2bb4-108">See Also</span></span>  
 [<span data-ttu-id="d2bb4-109">ピア チャネル アプリケーションの構築</span><span class="sxs-lookup"><span data-stu-id="d2bb4-109">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)  
 [<span data-ttu-id="d2bb4-110">システム標準のバインディング</span><span class="sxs-lookup"><span data-stu-id="d2bb4-110">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
