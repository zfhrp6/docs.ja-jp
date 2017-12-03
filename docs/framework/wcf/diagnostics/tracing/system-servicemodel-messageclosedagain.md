---
title: System.ServiceModel.MessageClosedAgain
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec4a0acc70f1878756776d7ed8e8d8e5ee64035f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelmessageclosedagain"></a><span data-ttu-id="ec8b8-102">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="ec8b8-102">System.ServiceModel.MessageClosedAgain</span></span>
<span data-ttu-id="ec8b8-103">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="ec8b8-103">System.ServiceModel.MessageClosedAgain</span></span>  
  
## <a name="description"></a><span data-ttu-id="ec8b8-104">説明</span><span class="sxs-lookup"><span data-stu-id="ec8b8-104">Description</span></span>  
 <span data-ttu-id="ec8b8-105">メッセージがもう一度閉じられました。</span><span class="sxs-lookup"><span data-stu-id="ec8b8-105">A message was closed again.</span></span>  
  
 <span data-ttu-id="ec8b8-106">メッセージを閉じることができるのは一度だけです。</span><span class="sxs-lookup"><span data-stu-id="ec8b8-106">A message should be closed only once.</span></span> <span data-ttu-id="ec8b8-107">このトレースがユーザー拡張コード内で出力されている場合は、ユーザー拡張コードは既に閉じられているメッセージをさらに閉じようとしていることが示されています。</span><span class="sxs-lookup"><span data-stu-id="ec8b8-107">If this trace is being emitted in user extension code, it indicates that the user extension code is closing a message that has already been closed.</span></span> <span data-ttu-id="ec8b8-108">このトレースが製品のコード内で出力されている場合は、ユーザー拡張コードがメッセージを閉じるのが早すぎる可能性があることが示されています。</span><span class="sxs-lookup"><span data-stu-id="ec8b8-108">If this trace is being emitted through product code, it indicates that the user extension code could potentially be closing a message too early.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec8b8-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="ec8b8-109">See Also</span></span>  
 [<span data-ttu-id="ec8b8-110">トレース</span><span class="sxs-lookup"><span data-stu-id="ec8b8-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="ec8b8-111">トレースを使用して、アプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="ec8b8-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="ec8b8-112">管理と診断</span><span class="sxs-lookup"><span data-stu-id="ec8b8-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
