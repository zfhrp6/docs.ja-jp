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
# <a name="how-to-unwrap-a-nested-task"></a>方法: 入れ子のタスクのラップを解除する
メソッドからタスクを返すを待機または次の例で示すように、そのタスクから継続します。  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 前の例で、<xref:System.Threading.Tasks.Task%601.Result%2A>プロパティの型は`string`(`String` Visual Basic で)。  
  
 ただし、一部のシナリオは、別のタスク内のタスクを作成し、入れ子のタスクを返す必要があります。 ここで、`TResult`外側のタスクの自体がタスク。 結果のプロパティは、次の例で、 `Task<Task<string>>` (C#) または`Task(Of Task(Of String))`Visual Basic でします。  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 外側のタスクのラップを解除し、元のタスクを取得するコードを記述することはできますが、その<xref:System.Threading.Tasks.Task%601.Result%2A>プロパティこのようなコードは、簡単に書き込むため例外とキャンセル要求を処理する必要があります。 このような状況のことをお勧めのいずれかを使用すること、<xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>拡張メソッドを次の例で示すようにします。  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>メソッドは、いずれかに変換するために使用できます`Task<Task>`または`Task<Task<TResult>>`(`Task(Of Task)`または`Task(Of Task(Of TResult))`Visual Basic で) に、`Task`または`Task<TResult>`(`Task(Of TResult)` Visual Basic で)。 完全に、新しいタスクは、内側の入れ子になったタスクを表し、キャンセル状態とすべての例外が含まれています。  
  
## <a name="example"></a>例  
 次の例で使用する方法、<xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>拡張メソッド。  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>  
 [タスク ベースの非同期プログラミング](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
