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
helpviewer_keywords: threads, cancellation
ms.assetid: d2d6d5fd-e263-4fa0-847b-2fc3e0d82337
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 482f48b347af1a4f76231abcb15abc2f4dba168b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="canceling-threads-cooperatively"></a>スレッドの協調的な取り消し
[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]より前のバージョンの .NET Framework には、開始されたスレッドを協調的に取り消す手段は組み込まれていませんでした。 ただし、 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]、それらを使用するには [キャンセル] を同様に、スレッドを取り消すキャンセル トークンを使用できます<xref:System.Threading.Tasks.Task?displayProperty=nameWithType>オブジェクトや PLINQ クエリ。 <xref:System.Threading.Thread?displayProperty=nameWithType>クラスはキャンセル トークンの組み込みサポートを提供しないを使用して、トークンをスレッド プロシージャに渡すことができます、<xref:System.Threading.Thread>を受け取るコンス トラクター、<xref:System.Threading.ParameterizedThreadStart>を委任します。 この方法を次の例に示します。  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a>関連項目  
 [スレッドの使用とスレッド処理](../../../docs/standard/threading/using-threads-and-threading.md)
