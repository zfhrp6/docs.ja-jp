---
title: "方法: キャンセル要求のコールバックを登録する"
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
helpviewer_keywords: cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 85b15ed610d80958ac9d7e3762ac8ea7b781b8d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a>方法: キャンセル要求のコールバックを登録する
次の例は、れるデリゲートを登録する方法を示しています。 ときに呼び出されます、<xref:System.Threading.CancellationToken.IsCancellationRequested%2A>プロパティが呼び出されたため true になる<xref:System.Threading.CancellationTokenSource.Cancel%2A>トークンを作成したオブジェクトにします。 この方法は、統合キャンセル フレームワークをネイティブにはサポートしていない非同期操作を取り消す場合や、非同期操作の終了を待機している可能性のあるメソッドのブロックを解除する場合に使用できます。  
  
> [!NOTE]
>  [マイ コードのみ] が有効になっている場合、Visual Studio では、例外をスローする行で処理が中断され、"ユーザー コードで処理されない例外" に関するエラー メッセージが表示されることがあります。 このエラーは問題にはなりません。 F5 キーを押して、処理が中断された箇所から続行し、以下の例に示す例外処理動作を確認できます。 Visual Studio の最初のエラーの処理は中断を防ぐために下にある [マイ コードのみ] チェック ボックスをオフにだけ**ツール、オプション、デバッグ、一般的な**します。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Net.WebClient.CancelAsync%2A> メソッドを、キャンセル トークンを通じてキャンセルが要求されたときに呼び出されるメソッドとして登録します。  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 コールバックを登録するときにキャンセルが既に要求されていても、コールバックは必ず呼び出されます。 このような場合、進行中の非同期操作がないと <xref:System.Net.WebClient.CancelAsync%2A> メソッドは何も実行しないので、このメソッドの呼び出しは常に安全です。  
  
## <a name="see-also"></a>関連項目  
 [マネージ スレッドのキャンセル](../../../docs/standard/threading/cancellation-in-managed-threads.md)
