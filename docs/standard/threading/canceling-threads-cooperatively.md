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
# <a name="canceling-threads-cooperatively"></a>スレッドの協調的な取り消し
[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]より前のバージョンの .NET Framework には、開始されたスレッドを協調的に取り消す手段は組み込まれていませんでした。 ただし、[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] では、<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> オブジェクトや PLINQ クエリを取り消す場合と同様に、取り消しトークンを使用してスレッドを取り消すことができます。 <xref:System.Threading.Thread?displayProperty=nameWithType> クラスには取り消しトークンのサポートは組み込まれていませんが、<xref:System.Threading.Thread> デリゲートを受け取る <xref:System.Threading.ParameterizedThreadStart> コンストラクターを使用して、トークンをスレッド プロシージャに渡すことができます。 この方法を次の例に示します。  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a>参照  
 [スレッドの使用とスレッド処理](../../../docs/standard/threading/using-threads-and-threading.md)
