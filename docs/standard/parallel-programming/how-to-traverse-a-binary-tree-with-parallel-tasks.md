---
title: "方法: 並列タスクでバイナリ ツリーを走査する"
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
- tasks, how to traverse a tree
ms.assetid: 4265d169-6c69-4f36-b10d-b7ae7f72f4df
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0196d82dd46a105f7cf1db0f9333a5d28afe559b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a><span data-ttu-id="bf1ef-102">方法: 並列タスクでバイナリ ツリーを走査する</span><span class="sxs-lookup"><span data-stu-id="bf1ef-102">How to: Traverse a Binary Tree with Parallel Tasks</span></span>
<span data-ttu-id="bf1ef-103">次の例では、ツリー データ構造を走査する並列タスクを使用する 2 つの方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bf1ef-103">The following example shows two ways in which parallel tasks can be used to traverse a tree data structure.</span></span> <span data-ttu-id="bf1ef-104">ツリー自体の作成は、演習として残しておきます。</span><span class="sxs-lookup"><span data-stu-id="bf1ef-104">The creation of the tree itself is left as an exercise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf1ef-105">例</span><span class="sxs-lookup"><span data-stu-id="bf1ef-105">Example</span></span>  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 <span data-ttu-id="bf1ef-106">示した 2 つのメソッドは、機能的に同等です。</span><span class="sxs-lookup"><span data-stu-id="bf1ef-106">The two methods shown are functionally equivalent.</span></span> <span data-ttu-id="bf1ef-107">タスクを作成して実行するために、<xref:System.Threading.Tasks.TaskFactory.StartNew%2A> メソッドを使用すると、タスクで待機し、例外を処理するために使用するタスクからハンドルを戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="bf1ef-107">By using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> method to create and run the tasks, you get a handle back from the tasks which can be used to wait on the tasks and handle exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf1ef-108">参照</span><span class="sxs-lookup"><span data-stu-id="bf1ef-108">See Also</span></span>  
 [<span data-ttu-id="bf1ef-109">タスク並列ライブラリ (TPL)</span><span class="sxs-lookup"><span data-stu-id="bf1ef-109">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
