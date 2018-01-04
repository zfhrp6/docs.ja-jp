---
title: "Single 同時実行モードでメッセージを順番に処理する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c50381c678a84f5602d08342d02dbf44316994c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a><span data-ttu-id="101b1-102">Single 同時実行モードでメッセージを順番に処理する</span><span class="sxs-lookup"><span data-stu-id="101b1-102">Ordered Processing of Messages in Single Concurrency Mode</span></span>
<span data-ttu-id="101b1-103">基になるチャネルがセッションフルでない限り、WCF は、メッセージが処理される順序に関する保証はありません。</span><span class="sxs-lookup"><span data-stu-id="101b1-103">WCF makes no guarantees about the order in which messages are processed, unless the underlying channel is sessionful.</span></span>  <span data-ttu-id="101b1-104">インスタンスの順序でメッセージを処理する、セッションの多いチャネルではない MsmqInputChannel を使用する WCF サービスは失敗します。</span><span class="sxs-lookup"><span data-stu-id="101b1-104">For instance, a WCF service that uses MsmqInputChannel, which is not a sessionful channel, will fail to process messages in order.</span></span> <span data-ttu-id="101b1-105">状況によっては、開発者可能性があります順番に処理動作をしますが、セッションを使用するには。</span><span class="sxs-lookup"><span data-stu-id="101b1-105">There are some circumstances where a developer may want the in order processing behavior but not want to use sessions.</span></span> <span data-ttu-id="101b1-106">このトピックでは、サービスが Single 同時実行モードで実行されている場合にこの動作を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="101b1-106">This topic describes how to configure this behavior when a service is running in Single Concurrency Mode.</span></span>  
  
## <a name="in-order-message-processing"></a><span data-ttu-id="101b1-107">順番に従ったメッセージの処理</span><span class="sxs-lookup"><span data-stu-id="101b1-107">In-order Message Processing</span></span>  
 <span data-ttu-id="101b1-108"><xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> という名前の新しい属性が <xref:System.ServiceModel.ServiceBehaviorAttribute> に追加されました。</span><span class="sxs-lookup"><span data-stu-id="101b1-108">A new attribute called <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> has been added to the <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span></span> <span data-ttu-id="101b1-109"><xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> を true に設定し、<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> を <xref:System.ServiceModel.ConcurrencyMode.Single> に設定すると、サービスに送信されたメッセージは順番に処理されます。</span><span class="sxs-lookup"><span data-stu-id="101b1-109">When <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> is set to true and <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to <xref:System.ServiceModel.ConcurrencyMode.Single> messages sent to the service will be processed in order.</span></span> <span data-ttu-id="101b1-110">次のコードは、これらの属性の設定方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="101b1-110">The following code snippet illustrates how to set these attributes.</span></span>  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 <span data-ttu-id="101b1-111"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> をその他の値に設定すると、<xref:System.InvalidOperationException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="101b1-111">If <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to any other value, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="101b1-112">参照</span><span class="sxs-lookup"><span data-stu-id="101b1-112">See Also</span></span>  
 [<span data-ttu-id="101b1-113">セッション、インスタンス化、および同時実行</span><span class="sxs-lookup"><span data-stu-id="101b1-113">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [<span data-ttu-id="101b1-114">同時実行</span><span class="sxs-lookup"><span data-stu-id="101b1-114">Concurrency</span></span>](../../../../docs/framework/wcf/samples/concurrency.md)
