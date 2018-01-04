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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cd70b4154a388ecb30518f03773d2a296258d7b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelshttpsclientcertificatenotpresent"></a><span data-ttu-id="41d48-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span><span class="sxs-lookup"><span data-stu-id="41d48-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span></span>
<span data-ttu-id="41d48-103">クライアント証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="41d48-103">Client certificate is required.</span></span> <span data-ttu-id="41d48-104">要求内で証明書が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="41d48-104">No certificate was found in the request.</span></span>  
  
## <a name="description"></a><span data-ttu-id="41d48-105">説明</span><span class="sxs-lookup"><span data-stu-id="41d48-105">Description</span></span>  
 <span data-ttu-id="41d48-106">このトレースは、HTTPS リスナーがクライアント証明書に関連付けられていない HTTPS 要求を受信したことを示します。</span><span class="sxs-lookup"><span data-stu-id="41d48-106">This trace indicates that the HTTPS listener received an HTTPS request that was not associated with a client certificate.</span></span> <span data-ttu-id="41d48-107">リスナーはすべての HTTPS 要求においてクライアント証明書を必要とするように構成されているため、リスナーによるクライアントの信頼性の検証は失敗します。</span><span class="sxs-lookup"><span data-stu-id="41d48-107">Since the listener was configured to require client certificates on all HTTPS requests, the listener failed to validate the client’s authenticity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41d48-108">参照</span><span class="sxs-lookup"><span data-stu-id="41d48-108">See Also</span></span>  
 [<span data-ttu-id="41d48-109">トレース</span><span class="sxs-lookup"><span data-stu-id="41d48-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="41d48-110">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="41d48-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="41d48-111">管理と診断</span><span class="sxs-lookup"><span data-stu-id="41d48-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
