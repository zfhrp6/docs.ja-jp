---
title: '方法: アプリケーションの起動時または終了時にメッセージをログに記録する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: 80b07e67cb307d461e63df9f94c9d0962eb6374a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a><span data-ttu-id="ebba8-102">方法: アプリケーションの起動時または終了時にメッセージをログに記録する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ebba8-102">How to: Log Messages When the Application Starts or Shuts Down (Visual Basic)</span></span>
<span data-ttu-id="ebba8-103">`My.Application.Log` オブジェクトおよび `My.Log` オブジェクトを使用すると、アプリケーション内で発生したイベントに関する情報をログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="ebba8-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="ebba8-104">この例では、 `My.Application.Log.WriteEntry` イベントおよび `Startup` イベントで `Shutdown` メソッドを使用してトレース情報を書き込む方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ebba8-104">This example shows how to use the `My.Application.Log.WriteEntry` method with the `Startup` and `Shutdown` events to write tracing information.</span></span>  
  
### <a name="to-access-the-applications-event-handler-code"></a><span data-ttu-id="ebba8-105">アプリケーションのイベント ハンドラー コードにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="ebba8-105">To access the application's event-handler code</span></span>  
  
1.  <span data-ttu-id="ebba8-106">**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="ebba8-106">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ebba8-107">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebba8-107">On the **Project** menu, choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="ebba8-108">**[アプリケーション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebba8-108">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="ebba8-109">**[アプリケーション イベントの表示]** をクリックしてコード エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="ebba8-109">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="ebba8-110">ApplicationEvents.vb ファイルが開かれます。</span><span class="sxs-lookup"><span data-stu-id="ebba8-110">This opens the ApplicationEvents.vb file.</span></span>  
  
### <a name="to-log-messages-when-the-application-starts"></a><span data-ttu-id="ebba8-111">アプリケーションの起動時にメッセージをログに記録するには</span><span class="sxs-lookup"><span data-stu-id="ebba8-111">To log messages when the application starts</span></span>  
  
1.  <span data-ttu-id="ebba8-112">コード エディターで ApplicationEvents.vb ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="ebba8-112">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="ebba8-113">**[全般]** メニューの **[MyApplication イベント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebba8-113">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2.  <span data-ttu-id="ebba8-114">**[宣言]** メニューの **[スタートアップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebba8-114">On the **Declarations** menu, choose **Startup**.</span></span>  
  
     <span data-ttu-id="ebba8-115">アプリケーションでは、メイン アプリケーションの実行前に <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="ebba8-115">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> event before the main application runs.</span></span>  
  
3.  <span data-ttu-id="ebba8-116">`My.Application.Log.WriteEntry` イベント ハンドラーに `Startup` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="ebba8-116">Add the `My.Application.Log.WriteEntry` method to the `Startup` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_1.vb)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a><span data-ttu-id="ebba8-117">アプリケーションの終了時にメッセージをログに記録するには</span><span class="sxs-lookup"><span data-stu-id="ebba8-117">To log messages when the application shuts down</span></span>  
  
1.  <span data-ttu-id="ebba8-118">コード エディターで ApplicationEvents.vb ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="ebba8-118">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="ebba8-119">**[全般]** メニューの **[MyApplication イベント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebba8-119">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2.  <span data-ttu-id="ebba8-120">**[宣言]** メニューの **[シャットダウン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebba8-120">On the **Declarations** menu, choose **Shutdown**.</span></span>  
  
     <span data-ttu-id="ebba8-121">アプリケーションでは、メイン アプリケーションが実行された後、終了前に <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="ebba8-121">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> event after the main application runs, but before it shuts down.</span></span>  
  
3.  <span data-ttu-id="ebba8-122">`My.Application.Log.WriteEntry` イベント ハンドラーに `Shutdown` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="ebba8-122">Add the `My.Application.Log.WriteEntry` method to the `Shutdown` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#2](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="ebba8-123">例</span><span class="sxs-lookup"><span data-stu-id="ebba8-123">Example</span></span>  
 <span data-ttu-id="ebba8-124">**プロジェクト デザイナー** を使用して、コード エディターでアプリケーション イベントにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="ebba8-124">You can use the **Project Designer** to access the application events in the Code Editor.</span></span> <span data-ttu-id="ebba8-125">詳細については、「[[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ebba8-125">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#3](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ebba8-126">参照</span><span class="sxs-lookup"><span data-stu-id="ebba8-126">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 <span data-ttu-id="ebba8-127">[[アプリケーション] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="ebba8-127">[Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)</span></span>  
 [<span data-ttu-id="ebba8-128">アプリケーション ログの使用</span><span class="sxs-lookup"><span data-stu-id="ebba8-128">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
