---
title: 'トラブルシューティング: ログ リスナー (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: 54c3ed0f607edf992fa3c40a8e6214252740587c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="troubleshooting-log-listeners-visual-basic"></a><span data-ttu-id="9da66-102">トラブルシューティング: ログ リスナー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9da66-102">Troubleshooting: Log Listeners (Visual Basic)</span></span>
<span data-ttu-id="9da66-103">`My.Application.Log` オブジェクトおよび `My.Log` オブジェクトを使用すると、アプリケーション内で発生したイベントに関する情報をログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="9da66-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span>  
  
 <span data-ttu-id="9da66-104">これらのメッセージをどのログ リスナーが受け取るかを確認するには、「[チュートリアル : My.Application.Log による情報の書き込み先の確認](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9da66-104">To determine which log listeners receive those messages, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="9da66-105">`Log` オブジェクトでログ フィルターを使って、ログに記録される情報の量を制限できます。</span><span class="sxs-lookup"><span data-stu-id="9da66-105">The `Log` object can use log filtering to limit the amount of information that it logs.</span></span> <span data-ttu-id="9da66-106">フィルターが正しく構成されていない場合、ログに誤った情報が含まれる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9da66-106">If the filters are misconfigured, the logs might contain the wrong information.</span></span> <span data-ttu-id="9da66-107">フィルターについて詳しくは、「[チュートリアル: My.Application.Log の出力をフィルター処理する](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9da66-107">For more information about filtering, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>  
  
 <span data-ttu-id="9da66-108">一方、ログが正しく構成されていない場合は、現在の構成についてさらに情報が必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="9da66-108">However, if a log is configured incorrectly, you may need more information about its current configuration.</span></span> <span data-ttu-id="9da66-109">ログの高度な `TraceSource` プロパティを使って、この情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="9da66-109">You can get to this information through the log's advanced `TraceSource` property.</span></span>  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a><span data-ttu-id="9da66-110">コードで Log オブジェクトのログ リスナーを特定するには</span><span class="sxs-lookup"><span data-stu-id="9da66-110">To determine the log listeners for the Log object in code</span></span>  
  
1.  <span data-ttu-id="9da66-111">コード ファイルの先頭に <xref:System.Diagnostics> 名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="9da66-111">Import the <xref:System.Diagnostics> namespace at the beginning of the code file.</span></span> <span data-ttu-id="9da66-112">詳細については、「[Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9da66-112">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#13](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_1.vb)]  
  
2.  <span data-ttu-id="9da66-113">各ログ リスナーの情報で構成される文字列を返す関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="9da66-113">Create a function that returns a string consisting of information for each of the log's listeners.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#14](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_2.vb)]  
  
3.  <span data-ttu-id="9da66-114">ログのトレース リスナーのコレクションを `GetListeners` 関数に渡し、戻り値を表示します。</span><span class="sxs-lookup"><span data-stu-id="9da66-114">Pass the collection of the log's trace listeners to the `GetListeners` function, and display the return value.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#19](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_3.vb)]  
  
     <span data-ttu-id="9da66-115">詳細については、「<xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9da66-115">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9da66-116">参照</span><span class="sxs-lookup"><span data-stu-id="9da66-116">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [<span data-ttu-id="9da66-117">アプリケーション ログの使用</span><span class="sxs-lookup"><span data-stu-id="9da66-117">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="9da66-118">チュートリアル : My.Application.Log による情報の書き込み先の確認</span><span class="sxs-lookup"><span data-stu-id="9da66-118">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
