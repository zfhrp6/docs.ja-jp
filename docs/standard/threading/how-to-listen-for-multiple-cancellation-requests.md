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
# <a name="how-to-listen-for-multiple-cancellation-requests"></a><span data-ttu-id="b90a5-102">方法: 複数のキャンセル要求を待機する</span><span class="sxs-lookup"><span data-stu-id="b90a5-102">How to: Listen for Multiple Cancellation Requests</span></span>
<span data-ttu-id="b90a5-103">この例では、いずれかのトークンが要求した場合、操作をキャンセルできるように、2 つのキャンセル トークンを同時にリッスンする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b90a5-103">This example shows how to listen to two cancellation tokens simultaneously so that you can cancel an operation if either token requests it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b90a5-104">[マイ コードのみ] が有効になっている場合、Visual Studio では、例外をスローする行で処理が中断され、"ユーザー コードで処理されない例外" に関するエラー メッセージが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="b90a5-104">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="b90a5-105">このエラーは問題にはなりません。</span><span class="sxs-lookup"><span data-stu-id="b90a5-105">This error is benign.</span></span> <span data-ttu-id="b90a5-106">F5 キーを押して、処理が中断された箇所から続行し、以下の例に示す例外処理動作を確認できます。</span><span class="sxs-lookup"><span data-stu-id="b90a5-106">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="b90a5-107">Visual Studio の最初のエラーの処理は中断を防ぐために下にある [マイ コードのみ] チェック ボックスをオフにだけ**ツール、オプション、デバッグ、一般的な**します。</span><span class="sxs-lookup"><span data-stu-id="b90a5-107">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b90a5-108">例</span><span class="sxs-lookup"><span data-stu-id="b90a5-108">Example</span></span>  
 <span data-ttu-id="b90a5-109">次の例で、<xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A>メソッドを使用して 2 つのトークンを 1 つのトークンに結合します。</span><span class="sxs-lookup"><span data-stu-id="b90a5-109">In the following example, the <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> method is used to join two tokens into one token.</span></span> <span data-ttu-id="b90a5-110">これにより、1 つのキャンセルをトークンを引数として受け取らないメソッドに渡されるトークン。</span><span class="sxs-lookup"><span data-stu-id="b90a5-110">This enables the token to be passed to methods that take just one cancellation token as an argument.</span></span> <span data-ttu-id="b90a5-111">この例では、メソッドが、クラスおよびクラス内で生成されるトークンの外部から渡された両方のトークンを観察する必要があります、一般的なシナリオを示します。</span><span class="sxs-lookup"><span data-stu-id="b90a5-111">The example demonstrates a common scenario in which a method must observe both a token passed in from outside the class, and a token generated inside the class.</span></span>  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 <span data-ttu-id="b90a5-112">リンクのトークンがスローした場合、<xref:System.OperationCanceledException>例外に渡されるトークンは、先行タスクのトークンのいずれかのないリンク トークンです。</span><span class="sxs-lookup"><span data-stu-id="b90a5-112">When the linked token throws an <xref:System.OperationCanceledException>, the token that is passed to the exception is the linked token, not either of the predecessor tokens.</span></span> <span data-ttu-id="b90a5-113">どちらのトークンが取り消されましたを特定するのには、直接先行タスクのトークンのステータスを確認します。</span><span class="sxs-lookup"><span data-stu-id="b90a5-113">To determine which of the tokens was canceled, check the status of the predecessor tokens directly.</span></span>  
  
 <span data-ttu-id="b90a5-114">この例では<xref:System.AggregateException>をスローすることはないためここではキャッチされますが、実際のシナリオでその他の例外だけでなく<xref:System.OperationCanceledException>、タスク デリゲートからスローされるでラップされます、<xref:System.OperationCanceledException>です。</span><span class="sxs-lookup"><span data-stu-id="b90a5-114">In this example, <xref:System.AggregateException> should never be thrown, but it is caught here because in real-world scenarios any other exceptions besides <xref:System.OperationCanceledException> that are thrown from the task delegate are wrapped in a <xref:System.OperationCanceledException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b90a5-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="b90a5-115">See Also</span></span>  
 [<span data-ttu-id="b90a5-116">マネージ スレッドのキャンセル</span><span class="sxs-lookup"><span data-stu-id="b90a5-116">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
