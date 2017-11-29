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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7f3963fe28ccaf55b3946254e395b770619c8f22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelmessageclosedagain"></a><span data-ttu-id="44dfb-102">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="44dfb-102">System.ServiceModel.MessageClosedAgain</span></span>
<span data-ttu-id="44dfb-103">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="44dfb-103">System.ServiceModel.MessageClosedAgain</span></span>  
  
## <a name="description"></a><span data-ttu-id="44dfb-104">説明</span><span class="sxs-lookup"><span data-stu-id="44dfb-104">Description</span></span>  
 <span data-ttu-id="44dfb-105">メッセージがもう一度閉じられました。</span><span class="sxs-lookup"><span data-stu-id="44dfb-105">A message was closed again.</span></span>  
  
 <span data-ttu-id="44dfb-106">メッセージを閉じることができるのは一度だけです。</span><span class="sxs-lookup"><span data-stu-id="44dfb-106">A message should be closed only once.</span></span> <span data-ttu-id="44dfb-107">このトレースがユーザー拡張コード内で出力されている場合は、ユーザー拡張コードは既に閉じられているメッセージをさらに閉じようとしていることが示されています。</span><span class="sxs-lookup"><span data-stu-id="44dfb-107">If this trace is being emitted in user extension code, it indicates that the user extension code is closing a message that has already been closed.</span></span> <span data-ttu-id="44dfb-108">このトレースが製品のコード内で出力されている場合は、ユーザー拡張コードがメッセージを閉じるのが早すぎる可能性があることが示されています。</span><span class="sxs-lookup"><span data-stu-id="44dfb-108">If this trace is being emitted through product code, it indicates that the user extension code could potentially be closing a message too early.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44dfb-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="44dfb-109">See Also</span></span>  
 [<span data-ttu-id="44dfb-110">トレース</span><span class="sxs-lookup"><span data-stu-id="44dfb-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="44dfb-111">トレースを使用して、アプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="44dfb-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="44dfb-112">管理と診断</span><span class="sxs-lookup"><span data-stu-id="44dfb-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
