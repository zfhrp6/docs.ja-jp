---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c7a134a60656c6ee237203b69e1bce40656f13d2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="ace07-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="ace07-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>
<span data-ttu-id="ace07-103">この接続プールの接続を閉じている間に例外が発生しました。</span><span class="sxs-lookup"><span data-stu-id="ace07-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ace07-104">説明</span><span class="sxs-lookup"><span data-stu-id="ace07-104">Description</span></span>  
 <span data-ttu-id="ace07-105">このエラー レベルのトレースは、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] が使用している接続プールのエラーにより、接続プールを閉じている間にエラーが発生したことを示しています。</span><span class="sxs-lookup"><span data-stu-id="ace07-105">This error level trace indicates that an error has occurred while closing the connection pools used by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]’s connection pooling feature.</span></span> <span data-ttu-id="ace07-106">このエラーの原因としては、プールされた接続を閉じることに失敗した、またはプールされた接続で CloseTimeout が設定されていることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="ace07-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="ace07-107">この例外がスローされると、このプール内でまだ閉じられていない接続はすべて中断され、他のプールにある閉じられていない接続は破棄されます。</span><span class="sxs-lookup"><span data-stu-id="ace07-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ace07-108">参照</span><span class="sxs-lookup"><span data-stu-id="ace07-108">See Also</span></span>  
 [<span data-ttu-id="ace07-109">トレース</span><span class="sxs-lookup"><span data-stu-id="ace07-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="ace07-110">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="ace07-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="ace07-111">管理と診断</span><span class="sxs-lookup"><span data-stu-id="ace07-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
