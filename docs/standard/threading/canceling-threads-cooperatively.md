---
title: "スレッドの協調的な取り消し"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threads, cancellation
ms.assetid: d2d6d5fd-e263-4fa0-847b-2fc3e0d82337
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 334cbcf8b4a888dbac5962c0fd668673e15e0e29
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="canceling-threads-cooperatively"></a><span data-ttu-id="7b646-102">スレッドの協調的な取り消し</span><span class="sxs-lookup"><span data-stu-id="7b646-102">Canceling Threads Cooperatively</span></span>
<span data-ttu-id="7b646-103">[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]より前のバージョンの .NET Framework には、開始されたスレッドを協調的に取り消す手段は組み込まれていませんでした。</span><span class="sxs-lookup"><span data-stu-id="7b646-103">Prior to the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the .NET Framework provided no built-in way to cancel a thread cooperatively after it was started.</span></span> <span data-ttu-id="7b646-104">ただし、[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] では、<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> オブジェクトや PLINQ クエリを取り消す場合と同様に、取り消しトークンを使用してスレッドを取り消すことができます。</span><span class="sxs-lookup"><span data-stu-id="7b646-104">However, in [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use cancellation tokens to cancel threads, just as you can use them to cancel <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or PLINQ queries.</span></span> <span data-ttu-id="7b646-105"><xref:System.Threading.Thread?displayProperty=nameWithType> クラスには取り消しトークンのサポートは組み込まれていませんが、<xref:System.Threading.Thread> デリゲートを受け取る <xref:System.Threading.ParameterizedThreadStart> コンストラクターを使用して、トークンをスレッド プロシージャに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="7b646-105">Although the <xref:System.Threading.Thread?displayProperty=nameWithType> class does not offer built-in support for cancellation tokens, you can pass a token to a thread procedure by using the <xref:System.Threading.Thread> constructor that takes a <xref:System.Threading.ParameterizedThreadStart> delegate.</span></span> <span data-ttu-id="7b646-106">この方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="7b646-106">The following example demonstrates how to do this.</span></span>  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="7b646-107">参照</span><span class="sxs-lookup"><span data-stu-id="7b646-107">See Also</span></span>  
 [<span data-ttu-id="7b646-108">スレッドの使用とスレッド処理</span><span class="sxs-lookup"><span data-stu-id="7b646-108">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
