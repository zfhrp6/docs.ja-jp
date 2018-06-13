---
title: System.ServiceModel.MessageClosedAgain
ms.date: 03/30/2017
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
ms.openlocfilehash: 3a73834888ae4a8945bd71492d787e23868fa5e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33480744"
---
# <a name="systemservicemodelmessageclosedagain"></a><span data-ttu-id="3caba-102">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="3caba-102">System.ServiceModel.MessageClosedAgain</span></span>
<span data-ttu-id="3caba-103">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="3caba-103">System.ServiceModel.MessageClosedAgain</span></span>  
  
## <a name="description"></a><span data-ttu-id="3caba-104">説明</span><span class="sxs-lookup"><span data-stu-id="3caba-104">Description</span></span>  
 <span data-ttu-id="3caba-105">メッセージがもう一度閉じられました。</span><span class="sxs-lookup"><span data-stu-id="3caba-105">A message was closed again.</span></span>  
  
 <span data-ttu-id="3caba-106">メッセージを閉じることができるのは一度だけです。</span><span class="sxs-lookup"><span data-stu-id="3caba-106">A message should be closed only once.</span></span> <span data-ttu-id="3caba-107">このトレースがユーザー拡張コード内で出力されている場合は、ユーザー拡張コードは既に閉じられているメッセージをさらに閉じようとしていることが示されています。</span><span class="sxs-lookup"><span data-stu-id="3caba-107">If this trace is being emitted in user extension code, it indicates that the user extension code is closing a message that has already been closed.</span></span> <span data-ttu-id="3caba-108">このトレースが製品のコード内で出力されている場合は、ユーザー拡張コードがメッセージを閉じるのが早すぎる可能性があることが示されています。</span><span class="sxs-lookup"><span data-stu-id="3caba-108">If this trace is being emitted through product code, it indicates that the user extension code could potentially be closing a message too early.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3caba-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="3caba-109">See Also</span></span>  
 [<span data-ttu-id="3caba-110">トレース</span><span class="sxs-lookup"><span data-stu-id="3caba-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="3caba-111">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="3caba-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="3caba-112">管理と診断</span><span class="sxs-lookup"><span data-stu-id="3caba-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
