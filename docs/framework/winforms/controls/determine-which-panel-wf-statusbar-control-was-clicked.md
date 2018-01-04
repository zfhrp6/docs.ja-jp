---
title: "方法 : Windows フォームの StatusBar コントロールでクリックされたパネルを確認する"
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
- status bars [Windows Forms], determining panel clicked
- panels [Windows Forms], determining clicked
- StatusBar control [Windows Forms], coding panel click events
- StatusBar control [Windows Forms], determining panel clicked
- PanelClick event [Windows Forms], determining panel clicked
- Panel control [Windows Forms], determining click
ms.assetid: d14c6092-04b2-4a07-8ddf-0dd11277ff5f
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a91ad8c28bae7d517a9e13937d5de340b1b6a605
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a><span data-ttu-id="7d5bd-102">方法 : Windows フォームの StatusBar コントロールでクリックされたパネルを確認する</span><span class="sxs-lookup"><span data-stu-id="7d5bd-102">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="7d5bd-103"><xref:System.Windows.Forms.StatusStrip>と<xref:System.Windows.Forms.ToolStripStatusLabel>コントロールの置換し、する機能を追加、<xref:System.Windows.Forms.StatusBar>と<xref:System.Windows.Forms.StatusBarPanel>コントロールですただし、、<xref:System.Windows.Forms.StatusBar>と<xref:System.Windows.Forms.StatusBarPanel>場合、旧バージョンとの互換性と将来の使用の両方のコントロールが保持されますします。選択します。</span><span class="sxs-lookup"><span data-stu-id="7d5bd-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="7d5bd-104">プログラムを[StatusBar コントロール](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md)コントロールにユーザーのクリックに応答を内の case ステートメントを使用して、<xref:System.Windows.Forms.StatusBar.PanelClick>イベント。</span><span class="sxs-lookup"><span data-stu-id="7d5bd-104">To program the [StatusBar Control](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) control to respond to user clicks, use a case statement within the <xref:System.Windows.Forms.StatusBar.PanelClick> event.</span></span> <span data-ttu-id="7d5bd-105">イベントには、クリックされたへの参照を含む引数 (パネルの引数) が含まれる<xref:System.Windows.Forms.StatusBarPanel>です。</span><span class="sxs-lookup"><span data-stu-id="7d5bd-105">The event contains an argument (the panel argument), which contains a reference to the clicked <xref:System.Windows.Forms.StatusBarPanel>.</span></span> <span data-ttu-id="7d5bd-106">この参照を使用して、クリックされたパネルのインデックスを確認し、それに応じたプログラミングできます。</span><span class="sxs-lookup"><span data-stu-id="7d5bd-106">Using this reference, you can determine the index of the clicked panel, and program accordingly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7d5bd-107">いることを確認、<xref:System.Windows.Forms.StatusBar>コントロールの<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>プロパティに設定されている`true`です。</span><span class="sxs-lookup"><span data-stu-id="7d5bd-107">Ensure that the <xref:System.Windows.Forms.StatusBar> control's <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property is set to `true`.</span></span>  
  
### <a name="to-determine-which-panel-was-clicked"></a><span data-ttu-id="7d5bd-108">クリックしてされたパネルを決定するには</span><span class="sxs-lookup"><span data-stu-id="7d5bd-108">To determine which panel was clicked</span></span>  
  
1.  <span data-ttu-id="7d5bd-109"><xref:System.Windows.Forms.StatusBar.PanelClick>イベント ハンドラーを使用して、 `Select Case` (で[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]) または`switch case`([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]または[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) ステートメントを確認するには、インデックス イベントの引数でクリックされたパネルのクリックしてされたパネルを確認します。</span><span class="sxs-lookup"><span data-stu-id="7d5bd-109">In the <xref:System.Windows.Forms.StatusBar.PanelClick> event handler, use a `Select Case` (in [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]) or `switch case` ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] or [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) statement to determine which panel was clicked by examining the index of the clicked panel in the event arguments.</span></span>  
  
     <span data-ttu-id="7d5bd-110">次のコード例のフォームに存在することが必要です、<xref:System.Windows.Forms.StatusBar>コントロール、 `StatusBar1`、および 2 つ<xref:System.Windows.Forms.StatusBarPanel>オブジェクト、`StatusBarPanel1`と`StatusBarPanel2`です。</span><span class="sxs-lookup"><span data-stu-id="7d5bd-110">The following code example requires the presence, on the form, of a <xref:System.Windows.Forms.StatusBar> control, `StatusBar1`, and two <xref:System.Windows.Forms.StatusBarPanel> objects, `StatusBarPanel1` and `StatusBarPanel2`.</span></span>  
  
    ```vb  
    Private Sub StatusBar1_PanelClick(ByVal sender As System.Object, ByVal e As System.Windows.Forms.StatusBarPanelClickEventArgs) Handles StatusBar1.PanelClick  
       Select Case StatusBar1.Panels.IndexOf(e.StatusBarPanel)  
         Case 0  
           MessageBox.Show("You have clicked Panel One.")  
         Case 1  
           MessageBox.Show("You have clicked Panel Two.")  
       End Select  
    End Sub  
    ```  
  
    ```csharp  
    private void statusBar1_PanelClick(object sender,   
    System.Windows.Forms.StatusBarPanelClickEventArgs e)  
    {  
       switch (statusBar1.Panels.IndexOf(e.StatusBarPanel))  
       {  
          case 0 :  
             MessageBox.Show("You have clicked Panel One.");  
             break;  
          case 1 :  
             MessageBox.Show("You have clicked Panel Two.");  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void statusBar1_PanelClick(System::Object ^  sender,  
          System::Windows::Forms::StatusBarPanelClickEventArgs ^  e)  
       {  
          switch (statusBar1->Panels->IndexOf(e->StatusBarPanel))  
          {  
             case 0 :  
                MessageBox::Show("You have clicked Panel One.");  
                break;  
             case 1 :  
                MessageBox::Show("You have clicked Panel Two.");  
                break;  
          }  
       }  
    ```  
  
     <span data-ttu-id="7d5bd-111">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) フォームのコンストラクターに次のコードを挿入してイベント ハンドラーを登録します。</span><span class="sxs-lookup"><span data-stu-id="7d5bd-111">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.statusBar1.PanelClick += new   
       System.Windows.Forms.StatusBarPanelClickEventHandler   
       (this.statusBar1_PanelClick);  
    ```  
  
    ```cpp  
    this->statusBar1->PanelClick += gcnew  
       System::Windows::Forms::StatusBarPanelClickEventHandler  
       (this, &Form1::statusBar1_PanelClick);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7d5bd-112">参照</span><span class="sxs-lookup"><span data-stu-id="7d5bd-112">See Also</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [<span data-ttu-id="7d5bd-113">方法: ステータス バー パネルのサイズを設定する</span><span class="sxs-lookup"><span data-stu-id="7d5bd-113">How to: Set the Size of Status-Bar Panels</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-size-of-status-bar-panels.md)  
 [<span data-ttu-id="7d5bd-114">チュートリアル: ステータス バー情報の実行時更新</span><span class="sxs-lookup"><span data-stu-id="7d5bd-114">Walkthrough: Updating Status Bar Information at Run Time</span></span>](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)  
 [<span data-ttu-id="7d5bd-115">StatusBar コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="7d5bd-115">StatusBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)
