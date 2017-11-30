---
title: "方法: タスクから値を返す"
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
helpviewer_keywords: tasks, how to return a value
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ade2aadc7d76c12c633f84eeb9eced7a637d5df9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-return-a-value-from-a-task"></a>方法: タスクから値を返す
この例では、<xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> の型を使用して <xref:System.Threading.Tasks.Task%601.Result%2A> プロパティから値を返す方法を示します。 C:\Users\Public\Pictures\Sample Pictures\ ディレクトリが存在している必要があり、それがファイルを含んでいる必要があります。  
  
## <a name="example"></a>例  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 <xref:System.Threading.Tasks.Task%601.Result%2A> プロパティは、タスクが終了するまで呼び出し元のスレッドをブロックします。  
  
 1 つの結果を渡す方法を表示する<xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>継続タスクを参照してください。[を使用して継続タスクをタスクの連結](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md)です。  
  
## <a name="see-also"></a>関連項目  
 [タスク ベースの非同期プログラミング](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)  
 [PLINQ および TPL のラムダ式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
