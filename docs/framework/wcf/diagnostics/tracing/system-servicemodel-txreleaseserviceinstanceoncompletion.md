---
title: System.ServiceModel.TxReleaseServiceInstanceOnCompletion
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e167bad3-861f-43e4-9e78-9c275cf64a29
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 93bdcebc4fe37dd8aa52861b1ee358ceefa6c716
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodeltxreleaseserviceinstanceoncompletion"></a><span data-ttu-id="e19dd-102">System.ServiceModel.TxReleaseServiceInstanceOnCompletion</span><span class="sxs-lookup"><span data-stu-id="e19dd-102">System.ServiceModel.TxReleaseServiceInstanceOnCompletion</span></span>
<span data-ttu-id="e19dd-103">ReleaseServiceInstanceOnTransactionComplete の ServiceBehaviorAttribute が true に設定されていたので、トランザクション '{0}' の完了時にサービス インスタンスが解放されました。</span><span class="sxs-lookup"><span data-stu-id="e19dd-103">The service instance was released on the completion of the transaction '{0}' because the ReleaseServiceInstanceOnTransactionComplete ServiceBehaviorAttribute was set to true.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e19dd-104">説明</span><span class="sxs-lookup"><span data-stu-id="e19dd-104">Description</span></span>  
 <span data-ttu-id="e19dd-105">現在のアクティブなトランザクションが完了して現在のサービス インスタンスが解放されるか破棄され、ReleaseServiceInstanceOnTransactionComplete が `true` に設定されると、トレースされます。</span><span class="sxs-lookup"><span data-stu-id="e19dd-105">Traced when the current service instance is released or disposed due to the completion of the current active transaction and ReleaseServiceInstanceOnTransactionComplete is set to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e19dd-106">関連項目</span><span class="sxs-lookup"><span data-stu-id="e19dd-106">See Also</span></span>  
 [<span data-ttu-id="e19dd-107">トレース</span><span class="sxs-lookup"><span data-stu-id="e19dd-107">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="e19dd-108">トレースを使用して、アプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="e19dd-108">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="e19dd-109">管理と診断</span><span class="sxs-lookup"><span data-stu-id="e19dd-109">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
