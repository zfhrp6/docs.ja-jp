---
title: "オンライン ステータスとオフライン ステータスの追加"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1a9f4cf65febd955e69d81f8dbb8f97aaa24e68c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="72fb9-102">オンライン ステータスとオフライン ステータスの追加</span><span class="sxs-lookup"><span data-stu-id="72fb9-102">Adding Online and Offline Status</span></span>
<span data-ttu-id="72fb9-103">多くの場合、アプリケーションではピア チャネル接続のステータスについて明確な詳細情報を監視することが重要です。</span><span class="sxs-lookup"><span data-stu-id="72fb9-103">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="72fb9-104">この情報は、`GetProperty` インターフェイスの実装で <xref:System.ServiceModel.IOnlineStatus> メソッドを呼び出すことで取得できます。</span><span class="sxs-lookup"><span data-stu-id="72fb9-104">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="72fb9-105">このインターフェイスを実装するオブジェクトは、接続ステータスを監視したり、`OnOnline` や `OnOffline` などのイベント ハンドラーを登録したりできるため、オンライン ステータスに変化があると即座に反応できます。</span><span class="sxs-lookup"><span data-stu-id="72fb9-105">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="72fb9-106">ピア チャネル インフラストラクチャでは、クライアントが少なくとも 1 つのピアに接続されているとオンラインと見なされ、そうでない場合はオフラインと見なされます。</span><span class="sxs-lookup"><span data-stu-id="72fb9-106">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="72fb9-107">このことは、開発中のアプリケーションをデバッグする際や、エンド ユーザーに詳細情報を表示する際に特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="72fb9-107">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72fb9-108">オンライン イベント ハンドラーでは、メッセージを送信する前に、まず、ノードが開いていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="72fb9-108">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72fb9-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="72fb9-109">See Also</span></span>  
 [<span data-ttu-id="72fb9-110">ピア チャネル アプリケーションの構築</span><span class="sxs-lookup"><span data-stu-id="72fb9-110">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
