---
title: System.ServiceModel.Channels.HttpsClientCertificateNotPresent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b13ef1b6-e340-401d-93ca-2710c3842205
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1808015cd310e64ac05e9827a229112ddd76a80f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelshttpsclientcertificatenotpresent"></a><span data-ttu-id="22258-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span><span class="sxs-lookup"><span data-stu-id="22258-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span></span>
<span data-ttu-id="22258-103">クライアント証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="22258-103">Client certificate is required.</span></span> <span data-ttu-id="22258-104">要求内で証明書が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="22258-104">No certificate was found in the request.</span></span>  
  
## <a name="description"></a><span data-ttu-id="22258-105">説明</span><span class="sxs-lookup"><span data-stu-id="22258-105">Description</span></span>  
 <span data-ttu-id="22258-106">このトレースは、HTTPS リスナーがクライアント証明書に関連付けられていない HTTPS 要求を受信したことを示します。</span><span class="sxs-lookup"><span data-stu-id="22258-106">This trace indicates that the HTTPS listener received an HTTPS request that was not associated with a client certificate.</span></span> <span data-ttu-id="22258-107">リスナーはすべての HTTPS 要求においてクライアント証明書を必要とするように構成されているため、リスナーによるクライアントの信頼性の検証は失敗します。</span><span class="sxs-lookup"><span data-stu-id="22258-107">Since the listener was configured to require client certificates on all HTTPS requests, the listener failed to validate the client’s authenticity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22258-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="22258-108">See Also</span></span>  
 [<span data-ttu-id="22258-109">トレース</span><span class="sxs-lookup"><span data-stu-id="22258-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="22258-110">トレースを使用して、アプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="22258-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="22258-111">管理と診断</span><span class="sxs-lookup"><span data-stu-id="22258-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
