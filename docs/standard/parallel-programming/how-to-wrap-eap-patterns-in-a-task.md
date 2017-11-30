---
title: "方法: タスクに EAP パターンをラップする"
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
helpviewer_keywords: tasks, how to wrap EAP patterns
ms.assetid: f11ed467-af2f-4504-8a2e-299a6c36d44e
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ae9d90c9bb3d0e8d315cbef510cdfe1b54e66da4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-wrap-eap-patterns-in-a-task"></a><span data-ttu-id="f6f18-102">方法: タスクに EAP パターンをラップする</span><span class="sxs-lookup"><span data-stu-id="f6f18-102">How to: Wrap EAP Patterns in a Task</span></span>
<span data-ttu-id="f6f18-103">次の例を使用して 1 つのタスクとイベント ベースの非同期パターン (EAP) の操作の任意の順序を公開する方法を示しています、<xref:System.Threading.Tasks.TaskCompletionSource%601>です。</span><span class="sxs-lookup"><span data-stu-id="f6f18-103">The following example shows how to expose an arbitrary sequence of Event-Based Asynchronous Pattern (EAP) operations as one task by using a <xref:System.Threading.Tasks.TaskCompletionSource%601>.</span></span> <span data-ttu-id="f6f18-104">使用する方法も示します、<xref:System.Threading.CancellationToken>メソッドを呼び出す、組み込みの取り消しで、<xref:System.Net.WebClient>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f6f18-104">The example also shows how to use a <xref:System.Threading.CancellationToken> to invoke the built-in cancellation methods on the <xref:System.Net.WebClient> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6f18-105">例</span><span class="sxs-lookup"><span data-stu-id="f6f18-105">Example</span></span>  
 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="f6f18-106">関連項目</span><span class="sxs-lookup"><span data-stu-id="f6f18-106">See Also</span></span>  
 [<span data-ttu-id="f6f18-107">TPL と従来の .NET Framework 非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="f6f18-107">TPL and Traditional .NET Framework Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)
