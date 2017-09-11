---
title: "方法: Visual Basic で例外をログに記録する"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: adf2dc683a139d21f24379efc779d4510a2057eb
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-log-exceptions-in-visual-basic"></a><span data-ttu-id="2a9d8-102">方法: Visual Basic で例外をログに記録する</span><span class="sxs-lookup"><span data-stu-id="2a9d8-102">How to: Log Exceptions in Visual Basic</span></span>
<span data-ttu-id="2a9d8-103">`My.Application.Log` オブジェクトおよび `My.Log` オブジェクトを使用すると、アプリケーション内で発生した例外に関する情報をログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="2a9d8-103">You can use the `My.Application.Log` and `My.Log` objects to log information about exceptions that occur in your application.</span></span> <span data-ttu-id="2a9d8-104">以下の例では、`My.Application.Log.WriteException` メソッドを使用して、明示的にキャッチした例外および未処理の例外をログに記録する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2a9d8-104">These examples show how to use the `My.Application.Log.WriteException` method to log exceptions that you catch explicitly and exceptions that are unhandled.</span></span>  
  
 <span data-ttu-id="2a9d8-105">トレース情報をログに記録するには、`My.Application.Log.WriteEntry` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="2a9d8-105">For logging tracing information, use the `My.Application.Log.WriteEntry` method.</span></span> <span data-ttu-id="2a9d8-106">詳細については、「<xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a9d8-106">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>  
  
### <a name="to-log-a-handled-exception"></a><span data-ttu-id="2a9d8-107">処理した例外をログに記録するには</span><span class="sxs-lookup"><span data-stu-id="2a9d8-107">To log a handled exception</span></span>  
  
1.  <span data-ttu-id="2a9d8-108">例外情報を生成するメソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="2a9d8-108">Create the method that will generate the exception information.</span></span>  
  
     <span data-ttu-id="2a9d8-109">[!code-vb[VbVbalrMyApplicationLog#9](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2a9d8-109">[!code-vb[VbVbalrMyApplicationLog#9](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_1.vb)]</span></span>  
  
2.  <span data-ttu-id="2a9d8-110">`Try...Catch` ブロックを使用して例外をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="2a9d8-110">Use a `Try...Catch` block to catch the exception.</span></span>  
  
     <span data-ttu-id="2a9d8-111">[!code-vb[VbVbalrMyApplicationLog#6](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="2a9d8-111">[!code-vb[VbVbalrMyApplicationLog#6](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_2.vb)]</span></span>  
  
3.  <span data-ttu-id="2a9d8-112">例外が発生する可能性のあるコードを `Try` ブロックに記述します。</span><span class="sxs-lookup"><span data-stu-id="2a9d8-112">Put the code that could generate an exception in the `Try` block.</span></span>  
  
     <span data-ttu-id="2a9d8-113">`Dim` 行と `MsgBox` 行のコメントを解除すると、<xref:System.NullReferenceException> 例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="2a9d8-113">Uncomment the `Dim` and `MsgBox` lines to cause a <xref:System.NullReferenceException> exception.</span></span>  
  
     <span data-ttu-id="2a9d8-114">[!code-vb[VbVbalrMyApplicationLog#7](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="2a9d8-114">[!code-vb[VbVbalrMyApplicationLog#7](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_3.vb)]</span></span>  
  
4.  <span data-ttu-id="2a9d8-115">`Catch` ブロックで、`My.Application.Log.WriteException` メソッドを使用して例外情報を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="2a9d8-115">In the `Catch` block, use the `My.Application.Log.WriteException` method to write the exception information.</span></span>  
  
     <span data-ttu-id="2a9d8-116">[!code-vb[VbVbalrMyApplicationLog#8](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="2a9d8-116">[!code-vb[VbVbalrMyApplicationLog#8](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_4.vb)]</span></span>  
  
     <span data-ttu-id="2a9d8-117">次の例は、処理した例外をログに記録するコード全体を示しています。</span><span class="sxs-lookup"><span data-stu-id="2a9d8-117">The following example shows the complete code for logging a handled exception.</span></span>  
  
     <span data-ttu-id="2a9d8-118">[!code-vb[VbVbalrMyApplicationLog#10](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="2a9d8-118">[!code-vb[VbVbalrMyApplicationLog#10](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_5.vb)]</span></span>  
  
### <a name="to-log-an-unhandled-exception"></a><span data-ttu-id="2a9d8-119">未処理の例外をログに記録するには</span><span class="sxs-lookup"><span data-stu-id="2a9d8-119">To log an unhandled exception</span></span>  
  
1.  <span data-ttu-id="2a9d8-120">**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="2a9d8-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="2a9d8-121">**[プロジェクト]** メニューの **[プロパティ]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a9d8-121">On the **Project** menu, choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="2a9d8-122">**[アプリケーション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a9d8-122">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="2a9d8-123">**[アプリケーション イベントの表示]** をクリックしてコード エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="2a9d8-123">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="2a9d8-124">ApplicationEvents.vb ファイルが開かれます。</span><span class="sxs-lookup"><span data-stu-id="2a9d8-124">This opens the ApplicationEvents.vb file.</span></span>  
  
4.  <span data-ttu-id="2a9d8-125">コード エディターで ApplicationEvents.vb ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="2a9d8-125">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="2a9d8-126">**[全般]** メニューの **[MyApplication イベント]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a9d8-126">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
5.  <span data-ttu-id="2a9d8-127">**[宣言]** メニューの **[UnhandledException]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a9d8-127">On the **Declarations** menu, choose **UnhandledException**.</span></span>  
  
     <span data-ttu-id="2a9d8-128">アプリケーションでは、メイン アプリケーションの実行前に <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="2a9d8-128">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> event before the main application runs.</span></span>  
  
6.  <span data-ttu-id="2a9d8-129">`My.Application.Log.WriteException` イベント ハンドラーに `UnhandledException` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="2a9d8-129">Add the `My.Application.Log.WriteException` method to the `UnhandledException` event handler.</span></span>  
  
     <span data-ttu-id="2a9d8-130">[!code-vb[VbVbalrMyApplicationLog#4](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="2a9d8-130">[!code-vb[VbVbalrMyApplicationLog#4](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_6.vb)]</span></span>  
  
     <span data-ttu-id="2a9d8-131">次の例は、未処理の例外をログに記録するためのコード全体を示しています。</span><span class="sxs-lookup"><span data-stu-id="2a9d8-131">The following example shows the complete code for logging an unhandled exception.</span></span>  
  
     <span data-ttu-id="2a9d8-132">[!code-vb[VbVbalrMyApplicationLog#5](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="2a9d8-132">[!code-vb[VbVbalrMyApplicationLog#5](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_7.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a9d8-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="2a9d8-133">See Also</span></span>  
 <span data-ttu-id="2a9d8-134"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="2a9d8-134"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span></span>   
 <span data-ttu-id="2a9d8-135"><xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span><span class="sxs-lookup"><span data-stu-id="2a9d8-135"><xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>   
 <span data-ttu-id="2a9d8-136"><xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A></span><span class="sxs-lookup"><span data-stu-id="2a9d8-136"><xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A></span></span>   
 <span data-ttu-id="2a9d8-137">[アプリケーション ログの使用](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span><span class="sxs-lookup"><span data-stu-id="2a9d8-137">[Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span></span>  
 <span data-ttu-id="2a9d8-138">[方法: ログ メッセージを書き込む](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) </span><span class="sxs-lookup"><span data-stu-id="2a9d8-138">[How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) </span></span>  
 <span data-ttu-id="2a9d8-139">[チュートリアル : My.Application.Log による情報の書き込み先の確認](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md) </span><span class="sxs-lookup"><span data-stu-id="2a9d8-139">[Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md) </span></span>  
 [<span data-ttu-id="2a9d8-140">チュートリアル : My.Application.Log による情報の書き込み先の変更</span><span class="sxs-lookup"><span data-stu-id="2a9d8-140">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)

