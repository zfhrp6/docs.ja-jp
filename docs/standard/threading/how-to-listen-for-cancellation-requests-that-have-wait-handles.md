---
title: "方法: 待機ハンドルがあるキャンセル要求を待機する"
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
helpviewer_keywords: cancellation, waiting with wait handles
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1eaa84d924fde63e94c36fab50a809c7c03f075
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a>方法: 待機ハンドルがあるキャンセル要求を待機する
メソッドは、ブロックされた場合は、シグナル状態になるイベントの待機中、キャンセル トークンの値をチェックおよび適切なタイミングで反応できません。 最初の例などのイベントを使用しているときに、この問題を解決する方法を示しています。<xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>統合キャンセル フレームワークをネイティブにサポートしていません。 2 番目の例を使用するより効率的な方法を示しています。 <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>、一元化されたキャンセルをサポートしています。  
  
> [!NOTE]
>  [マイ コードのみ] が有効になっている場合、Visual Studio では、例外をスローする行で処理が中断され、"ユーザー コードで処理されない例外" に関するエラー メッセージが表示されることがあります。 このエラーは問題にはなりません。 F5 キーを押して、処理が中断された箇所から続行し、以下の例に示す例外処理動作を確認できます。 Visual Studio の最初のエラーの処理は中断を防ぐために下にある [マイ コードのみ] チェック ボックスをオフにだけ**ツール、オプション、デバッグ、一般的な**します。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Threading.ManualResetEvent>統合キャンセルをサポートしていない待機ハンドルのブロックを解除する方法について説明します。  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Threading.ManualResetEventSlim>をサポートしているプリミティブがキャンセルを unified 調整のブロックを解除する方法を示します。 同じアプローチをなどその他の軽量な調整プリミティブと共に使用できる<xref:System.Threading.Semaphore>`Slim`と<xref:System.Threading.CountdownEvent>です。  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a>関連項目  
 [マネージ スレッドのキャンセル](../../../docs/standard/threading/cancellation-in-managed-threads.md)
