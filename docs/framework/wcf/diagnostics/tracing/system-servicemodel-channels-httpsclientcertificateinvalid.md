---
title: System.ServiceModel.Channels.HttpsClientCertificateInvalid
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8884dda1-fa0e-4d2a-8079-7042c51b64ef
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e798c0be052dc0d7987d99263117bf21a93ba9c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelshttpsclientcertificateinvalid"></a><span data-ttu-id="7a232-102">System.ServiceModel.Channels.HttpsClientCertificateInvalid</span><span class="sxs-lookup"><span data-stu-id="7a232-102">System.ServiceModel.Channels.HttpsClientCertificateInvalid</span></span>
<span data-ttu-id="7a232-103">クライアント証明書が無効です。</span><span class="sxs-lookup"><span data-stu-id="7a232-103">Client certificate is invalid.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7a232-104">説明</span><span class="sxs-lookup"><span data-stu-id="7a232-104">Description</span></span>  
 <span data-ttu-id="7a232-105">このトレースは、HTTPS リスナーが、クライアントによって提供された証明書が無効であることを検出したことを示します。</span><span class="sxs-lookup"><span data-stu-id="7a232-105">This trace indicates that the certificate provided by the client was found to be invalid by the HTTPS listener.</span></span> <span data-ttu-id="7a232-106">HTTPS リスナーは、この証明書を使用してクライアントの信頼性を検証しようとしていました。</span><span class="sxs-lookup"><span data-stu-id="7a232-106">The HTTPS listener was attempting to validate the authenticity of the client using this certificate.</span></span> <span data-ttu-id="7a232-107">サービスをホストしているサーバーによって証明書の証明機関が認識されないと、証明書は無効になります。</span><span class="sxs-lookup"><span data-stu-id="7a232-107">A certificate could be invalid if its Certificate Authority is not recognized by the server hosting the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a232-108">参照</span><span class="sxs-lookup"><span data-stu-id="7a232-108">See Also</span></span>  
 [<span data-ttu-id="7a232-109">トレース</span><span class="sxs-lookup"><span data-stu-id="7a232-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="7a232-110">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="7a232-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="7a232-111">管理と診断</span><span class="sxs-lookup"><span data-stu-id="7a232-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
