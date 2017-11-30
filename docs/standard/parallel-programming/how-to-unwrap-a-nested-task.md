---
title: "方法: 入れ子のタスクのラップを解除する"
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
helpviewer_keywords: tasks, how to unwrap nested tasks
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2da3de912abb693c4342e1ede02f273348e4b571
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-unwrap-a-nested-task"></a><span data-ttu-id="3036d-102">方法: 入れ子のタスクのラップを解除する</span><span class="sxs-lookup"><span data-stu-id="3036d-102">How to: Unwrap a Nested Task</span></span>
<span data-ttu-id="3036d-103">メソッドからタスクを返すを待機または次の例で示すように、そのタスクから継続します。</span><span class="sxs-lookup"><span data-stu-id="3036d-103">You can return a task from a method, and then wait on or continue from that task, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 <span data-ttu-id="3036d-104">前の例で、<xref:System.Threading.Tasks.Task%601.Result%2A>プロパティの型は`string`(`String` Visual Basic で)。</span><span class="sxs-lookup"><span data-stu-id="3036d-104">In the previous example, the <xref:System.Threading.Tasks.Task%601.Result%2A> property is of type `string` (`String` in Visual Basic).</span></span>  
  
 <span data-ttu-id="3036d-105">ただし、一部のシナリオは、別のタスク内のタスクを作成し、入れ子のタスクを返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="3036d-105">However, in some scenarios, you might want to create a task within another task, and then return the nested task.</span></span> <span data-ttu-id="3036d-106">ここで、`TResult`外側のタスクの自体がタスク。</span><span class="sxs-lookup"><span data-stu-id="3036d-106">In this case, the `TResult` of the enclosing task is itself a task.</span></span> <span data-ttu-id="3036d-107">結果のプロパティは、次の例で、 `Task<Task<string>>` (C#) または`Task(Of Task(Of String))`Visual Basic でします。</span><span class="sxs-lookup"><span data-stu-id="3036d-107">In the following example, the Result property is a `Task<Task<string>>` in C# or `Task(Of Task(Of String))` in Visual Basic.</span></span>  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 <span data-ttu-id="3036d-108">外側のタスクのラップを解除し、元のタスクを取得するコードを記述することはできますが、その<xref:System.Threading.Tasks.Task%601.Result%2A>プロパティこのようなコードは、簡単に書き込むため例外とキャンセル要求を処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3036d-108">Although it is possible to write code to unwrap the outer task and retrieve the original task and its <xref:System.Threading.Tasks.Task%601.Result%2A> property, such code is not easy to write because you must handle exceptions and also cancellation requests.</span></span> <span data-ttu-id="3036d-109">このような状況のことをお勧めのいずれかを使用すること、<xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>拡張メソッドを次の例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="3036d-109">In this situation, we recommend that you use one of the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods, as shown in the following example.</span></span>  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <span data-ttu-id="3036d-110"><xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>メソッドは、いずれかに変換するために使用できます`Task<Task>`または`Task<Task<TResult>>`(`Task(Of Task)`または`Task(Of Task(Of TResult))`Visual Basic で) に、`Task`または`Task<TResult>`(`Task(Of TResult)` Visual Basic で)。</span><span class="sxs-lookup"><span data-stu-id="3036d-110">The <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> methods can be used to transform any `Task<Task>` or `Task<Task<TResult>>` (`Task(Of Task)` or `Task(Of Task(Of TResult))` in Visual Basic) to a `Task` or `Task<TResult>` (`Task(Of TResult)` in Visual Basic).</span></span> <span data-ttu-id="3036d-111">完全に、新しいタスクは、内側の入れ子になったタスクを表し、キャンセル状態とすべての例外が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3036d-111">The new task fully represents the inner nested task, and includes cancellation state and all exceptions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3036d-112">例</span><span class="sxs-lookup"><span data-stu-id="3036d-112">Example</span></span>  
 <span data-ttu-id="3036d-113">次の例で使用する方法、<xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>拡張メソッド。</span><span class="sxs-lookup"><span data-stu-id="3036d-113">The following example demonstrates how to use the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods.</span></span>  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="3036d-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="3036d-114">See Also</span></span>  
 <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>  
 [<span data-ttu-id="3036d-115">タスク ベースの非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="3036d-115">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
