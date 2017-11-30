---
title: "方法: 複数のキャンセル要求を待機する"
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
- cancellation tokens, joining
- LinkedTokenSource, how to
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 36cf338a15ad3f7d234f902c50a2dbb1b2e95847
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a>方法: 複数のキャンセル要求を待機する
この例では、いずれかのトークンが要求した場合、操作をキャンセルできるように、2 つのキャンセル トークンを同時にリッスンする方法を示します。  
  
> [!NOTE]
>  [マイ コードのみ] が有効になっている場合、Visual Studio では、例外をスローする行で処理が中断され、"ユーザー コードで処理されない例外" に関するエラー メッセージが表示されることがあります。 このエラーは問題にはなりません。 F5 キーを押して、処理が中断された箇所から続行し、以下の例に示す例外処理動作を確認できます。 Visual Studio の最初のエラーの処理は中断を防ぐために下にある [マイ コードのみ] チェック ボックスをオフにだけ**ツール、オプション、デバッグ、一般的な**します。  
  
## <a name="example"></a>例  
 次の例で、<xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A>メソッドを使用して 2 つのトークンを 1 つのトークンに結合します。 これにより、1 つのキャンセルをトークンを引数として受け取らないメソッドに渡されるトークン。 この例では、メソッドが、クラスおよびクラス内で生成されるトークンの外部から渡された両方のトークンを観察する必要があります、一般的なシナリオを示します。  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 リンクのトークンがスローした場合、<xref:System.OperationCanceledException>例外に渡されるトークンは、先行タスクのトークンのいずれかのないリンク トークンです。 どちらのトークンが取り消されましたを特定するのには、直接先行タスクのトークンのステータスを確認します。  
  
 この例では<xref:System.AggregateException>をスローすることはないためここではキャッチされますが、実際のシナリオでその他の例外だけでなく<xref:System.OperationCanceledException>、タスク デリゲートからスローされるでラップされます、<xref:System.OperationCanceledException>です。  
  
## <a name="see-also"></a>関連項目  
 [マネージ スレッドのキャンセル](../../../docs/standard/threading/cancellation-in-managed-threads.md)
