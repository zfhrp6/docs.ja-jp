---
title: "チュートリアル : ステータス バー情報の実行時更新"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- status bars [Windows Forms], updating at run time
- status bars [Windows Forms], refreshing panels
- StatusBar control [Windows Forms], refreshing panels
- panels [Windows Forms], refreshing status bar
ms.assetid: cc2abb06-c082-49f7-a5a3-2fd1bbcb58d1
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6c67aa303f375734408201ce15d1c3db3dc32c8e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a><span data-ttu-id="dfeab-102">チュートリアル : ステータス バー情報の実行時更新</span><span class="sxs-lookup"><span data-stu-id="dfeab-102">Walkthrough: Updating Status Bar Information at Run Time</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="dfeab-103"><xref:System.Windows.Forms.StatusStrip>と<xref:System.Windows.Forms.ToolStripStatusLabel>コントロールの置換し、する機能を追加、<xref:System.Windows.Forms.StatusBar>と<xref:System.Windows.Forms.StatusBarPanel>コントロールですただし、、<xref:System.Windows.Forms.StatusBar>と<xref:System.Windows.Forms.StatusBarPanel>場合、旧バージョンとの互換性と将来の使用の両方のコントロールが保持されますします。選択します。</span><span class="sxs-lookup"><span data-stu-id="dfeab-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="dfeab-104">多くの場合、アプリケーションの状態の変化や他のユーザー操作に基づいて、ステータス バー パネルの内容を実行時に動的に更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dfeab-104">Often, a program will call for you to update the contents of status bar panels dynamically at run time, based on changes to application state or other user interaction.</span></span> <span data-ttu-id="dfeab-105">これは、CapsLock、NumLock、ScrollLock などのキーが有効化されたことをユーザーに通知したり、便利な情報として日付や時刻を表示したりするための一般的な方法です。</span><span class="sxs-lookup"><span data-stu-id="dfeab-105">This is a common way to signal users that keys such as the CAPS LOCK, NUM LOCK, or SCROLL LOCK are enabled, or to provide the date or a clock as a convenient reference.</span></span>  
  
 <span data-ttu-id="dfeab-106">次の例では、インスタンスを使用して、<xref:System.Windows.Forms.StatusBarPanel>クロックをホストするクラス。</span><span class="sxs-lookup"><span data-stu-id="dfeab-106">In the following example, you will use an instance of the <xref:System.Windows.Forms.StatusBarPanel> class to host a clock.</span></span>  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a><span data-ttu-id="dfeab-107">ステータス バーを更新できる状態にするには</span><span class="sxs-lookup"><span data-stu-id="dfeab-107">To get the status bar ready for updating</span></span>  
  
1.  <span data-ttu-id="dfeab-108">新しい Windows フォームを作成します。</span><span class="sxs-lookup"><span data-stu-id="dfeab-108">Create a new Windows form.</span></span>  
  
2.  <span data-ttu-id="dfeab-109">フォームに <xref:System.Windows.Forms.StatusBar> コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="dfeab-109">Add a <xref:System.Windows.Forms.StatusBar> control to your form.</span></span> <span data-ttu-id="dfeab-110">詳細については、「[方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dfeab-110">For details, see [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
3.  <span data-ttu-id="dfeab-111">ステータス バー パネルを追加、<xref:System.Windows.Forms.StatusBar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="dfeab-111">Add a status bar panel to your <xref:System.Windows.Forms.StatusBar> control.</span></span> <span data-ttu-id="dfeab-112">詳細については、「[方法 : StatusBar コントロールにパネルを追加する](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dfeab-112">For details, see [How to: Add Panels to a StatusBar Control](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md).</span></span>  
  
4.  <span data-ttu-id="dfeab-113"><xref:System.Windows.Forms.StatusBar>をフォームに追加したコントロールの設定、<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="dfeab-113">For the <xref:System.Windows.Forms.StatusBar> control you added to your form, set the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true`.</span></span>  
  
5.  <span data-ttu-id="dfeab-114">Windows フォームに追加<xref:System.Windows.Forms.Timer>コンポーネントをフォームにします。</span><span class="sxs-lookup"><span data-stu-id="dfeab-114">Add a Windows Forms <xref:System.Windows.Forms.Timer> component to the form.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dfeab-115">Windows フォーム<xref:System.Windows.Forms.Timer?displayProperty=nameWithType>コンポーネントが Windows フォームの環境用に設計されています。</span><span class="sxs-lookup"><span data-stu-id="dfeab-115">The Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="dfeab-116">サーバー環境に適したタイマーが必要な場合は、「[サーバー ベースのタイマーの概要](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dfeab-116">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span></span>  
  
6.  <span data-ttu-id="dfeab-117"><xref:System.Windows.Forms.Timer.Enabled%2A> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="dfeab-117">Set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>  
  
7.  <span data-ttu-id="dfeab-118">設定、<xref:System.Windows.Forms.Timer.Interval%2A>のプロパティ、 <xref:System.Windows.Forms.Timer> 30000 に設定します。</span><span class="sxs-lookup"><span data-stu-id="dfeab-118">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property of the <xref:System.Windows.Forms.Timer> to 30000.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dfeab-119"><xref:System.Windows.Forms.Timer.Interval%2A>のプロパティ、<xref:System.Windows.Forms.Timer>コンポーネントは、正確な時刻が表示される時刻に反映されることを確認に 30 秒 (30,000 ミリ秒) に設定されています。</span><span class="sxs-lookup"><span data-stu-id="dfeab-119">The <xref:System.Windows.Forms.Timer.Interval%2A> property of the <xref:System.Windows.Forms.Timer> component is set to 30 seconds (30,000 milliseconds) to ensure that an accurate time is reflected in the time displayed.</span></span>  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a><span data-ttu-id="dfeab-120">タイマーを実装してステータス バーを更新するには</span><span class="sxs-lookup"><span data-stu-id="dfeab-120">To implement the timer to update the status bar</span></span>  
  
1.  <span data-ttu-id="dfeab-121">イベント ハンドラーに次のコードを挿入、<xref:System.Windows.Forms.Timer>のパネルを更新するコンポーネント、<xref:System.Windows.Forms.StatusBar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="dfeab-121">Insert the following code into the event handler of the <xref:System.Windows.Forms.Timer> component to update the panel of the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
    ```vb  
    Private Sub Timer1_Tick(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Timer1.Tick  
       StatusBar1.Panels(0).Text = Now.ToShortTimeString  
    End Sub  
    ```  
  
    ```csharp  
    private void timer1_Tick(object sender, System.EventArgs e)  
    {  
       statusBar1.Panels[0].Text = DateTime.Now.ToShortTimeString();  
    }  
    ```  
  
    ```cpp  
    private:  
      System::Void timer1_Tick(System::Object ^ sender,  
        System::EventArgs ^ e)  
      {  
        statusBar1->Panels[0]->Text =  
          DateTime::Now.ToShortTimeString();  
      }  
    ```  
  
     <span data-ttu-id="dfeab-122">この時点で、アプリケーションを実行して、ステータス バー パネルで実行される時計を確認できる状態になります。</span><span class="sxs-lookup"><span data-stu-id="dfeab-122">At this point, you are ready to run the application and observe the clock running in the status bar panel.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="dfeab-123">アプリケーションをテストするには</span><span class="sxs-lookup"><span data-stu-id="dfeab-123">To test the application</span></span>  
  
1.  <span data-ttu-id="dfeab-124">アプリケーションをデバッグし、F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="dfeab-124">Debug the application and press F5 to run it.</span></span> <span data-ttu-id="dfeab-125">デバッグの詳細については、「[Visual Studio でのデバッグ](/visualstudio/debugger/debugging-in-visual-studio)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dfeab-125">For details about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dfeab-126">ステータス バーに時計が表示されるまでに約 30 秒かかります。</span><span class="sxs-lookup"><span data-stu-id="dfeab-126">It will take approximately 30 seconds for the clock to appear in the status bar.</span></span> <span data-ttu-id="dfeab-127">これは、できるだけ正確な時刻を取得するためです。</span><span class="sxs-lookup"><span data-stu-id="dfeab-127">This is to get the most accurate time possible.</span></span> <span data-ttu-id="dfeab-128">逆に、すぐに表示される、時計をするためには、することができますの値を減らして、<xref:System.Windows.Forms.Timer.Interval%2A>プロパティが、前の手順の手順 7 に設定します。</span><span class="sxs-lookup"><span data-stu-id="dfeab-128">Conversely, to make the clock appear sooner, you can reduce the value of the <xref:System.Windows.Forms.Timer.Interval%2A> property you set in step 7 in the previous procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfeab-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="dfeab-129">See Also</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [<span data-ttu-id="dfeab-130">方法: StatusBar コントロールにパネルを追加する</span><span class="sxs-lookup"><span data-stu-id="dfeab-130">How to: Add Panels to a StatusBar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md)  
 [<span data-ttu-id="dfeab-131">方法: Windows フォームの StatusBar コントロールでクリックされたパネルを確認する</span><span class="sxs-lookup"><span data-stu-id="dfeab-131">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)  
 [<span data-ttu-id="dfeab-132">StatusBar コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="dfeab-132">StatusBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)
