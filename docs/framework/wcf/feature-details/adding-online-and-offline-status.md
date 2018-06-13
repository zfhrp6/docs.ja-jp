---
title: オンライン ステータスとオフライン ステータスの追加
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: fb19614c1975c5634a81ca2f40edb145b724cd1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488105"
---
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="506c8-102">オンライン ステータスとオフライン ステータスの追加</span><span class="sxs-lookup"><span data-stu-id="506c8-102">Adding Online and Offline Status</span></span>
<span data-ttu-id="506c8-103">多くの場合、アプリケーションではピア チャネル接続のステータスについて明確な詳細情報を監視することが重要です。</span><span class="sxs-lookup"><span data-stu-id="506c8-103">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="506c8-104">この情報は、`GetProperty` インターフェイスの実装で <xref:System.ServiceModel.IOnlineStatus> メソッドを呼び出すことで取得できます。</span><span class="sxs-lookup"><span data-stu-id="506c8-104">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="506c8-105">このインターフェイスを実装するオブジェクトは、接続ステータスを監視したり、`OnOnline` や `OnOffline` などのイベント ハンドラーを登録したりできるため、オンライン ステータスに変化があると即座に反応できます。</span><span class="sxs-lookup"><span data-stu-id="506c8-105">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="506c8-106">ピア チャネル インフラストラクチャでは、クライアントが少なくとも 1 つのピアに接続されているとオンラインと見なされ、そうでない場合はオフラインと見なされます。</span><span class="sxs-lookup"><span data-stu-id="506c8-106">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="506c8-107">このことは、開発中のアプリケーションをデバッグする際や、エンド ユーザーに詳細情報を表示する際に特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="506c8-107">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="506c8-108">オンライン イベント ハンドラーでは、メッセージを送信する前に、まず、ノードが開いていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="506c8-108">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="506c8-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="506c8-109">See Also</span></span>  
 [<span data-ttu-id="506c8-110">ピア チャネル アプリケーションの構築</span><span class="sxs-lookup"><span data-stu-id="506c8-110">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
