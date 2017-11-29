---
title: "方法 : Windows フォーム LinkLabel コントロールの表示形式を変更する"
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
- LinkLabel properties
- LinkLabel control [Windows Forms], changing appearance of links
- links [Windows Forms], changing appearance
- examples [Windows Forms], LinkLabel control
- LinkLabel control [Windows Forms], examples
ms.assetid: fdc5854f-5162-4457-8cbe-1042feb2d132
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 42aaef183178e7170d3046b4c5daefc8647f7cc1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a><span data-ttu-id="38985-102">方法 : Windows フォーム LinkLabel コントロールの表示形式を変更する</span><span class="sxs-lookup"><span data-stu-id="38985-102">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>
<span data-ttu-id="38985-103">によって表示されるテキストを変更することができます、<xref:System.Windows.Forms.LinkLabel>さまざまな目的に合わせてコントロール。</span><span class="sxs-lookup"><span data-stu-id="38985-103">You can change the text displayed by the <xref:System.Windows.Forms.LinkLabel> control to suit a variety of purposes.</span></span> <span data-ttu-id="38985-104">たとえば、下線付きで特定の色で表示するテキストを設定してテキストをクリックすることができます、ユーザーに示すためによくあることを勧めします。</span><span class="sxs-lookup"><span data-stu-id="38985-104">For example, it is common practice to indicate to the user that text can be clicked by setting the text to appear in a specific color with an underline.</span></span> <span data-ttu-id="38985-105">ユーザーは、テキストをクリックすると、異なる色に色を変更します。</span><span class="sxs-lookup"><span data-stu-id="38985-105">After the user clicks the text, the color changes to a different color.</span></span> <span data-ttu-id="38985-106">この動作を制御するには、5 つの異なるプロパティを設定することができます。 <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>、 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>、 <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>、 <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>、および<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="38985-106">To control this behavior, you can set five different properties: the <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, and <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> properties.</span></span>  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a><span data-ttu-id="38985-107">LinkLabel コントロールの外観を変更するには</span><span class="sxs-lookup"><span data-stu-id="38985-107">To change the appearance of a LinkLabel control</span></span>  
  
1.  <span data-ttu-id="38985-108">設定、<xref:System.Windows.Forms.LinkLabel.LinkColor%2A>と<xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>色のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="38985-108">Set the <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> and <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> properties to the colors you want.</span></span>  
  
     <span data-ttu-id="38985-109">これにいずれかのプログラムから、またはデザイン時に、**プロパティ**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="38985-109">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    ' You can set the color using decimal values for red, green, and blue  
    LinkLabel1.LinkColor = Color.FromArgb(0, 0, 255)  
    ' Or you can set the color using defined constants  
    LinkLabel1.VisitedLinkColor = Color.Purple  
    ```  
  
    ```csharp  
    // You can set the color using decimal values for red, green, and blue  
    linkLabel1.LinkColor = Color.FromArgb(0, 0, 255);  
    // Or you can set the color using defined constants  
    linkLabel1.VisitedLinkColor = Color.Purple;  
    ```  
  
    ```cpp  
    // You can set the color using decimal values for red, green, and blue  
    linkLabel1->LinkColor = Color::FromArgb(0, 0, 255);  
    // Or you can set the color using defined constants  
    linkLabel1->VisitedLinkColor = Color::Purple;  
    ```  
  
2.  <span data-ttu-id="38985-110">設定、<xref:System.Windows.Forms.LinkLabel.Text%2A>プロパティに適切なキャプション。</span><span class="sxs-lookup"><span data-stu-id="38985-110">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>  
  
     <span data-ttu-id="38985-111">これにいずれかのプログラムから、またはデザイン時に、**プロパティ**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="38985-111">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3.  <span data-ttu-id="38985-112">設定、<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>プロパティのキャプションのどの部分がリンクとして示されます。</span><span class="sxs-lookup"><span data-stu-id="38985-112">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span>  
  
     <span data-ttu-id="38985-113"><xref:System.Windows.Forms.LinkLabel.LinkArea%2A>値を表示、 <xref:System.Windows.Forms.LinkArea> 2 つの数値、文字の開始位置と文字数を含むです。</span><span class="sxs-lookup"><span data-stu-id="38985-113">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> value is represented with a <xref:System.Windows.Forms.LinkArea> containing two numbers, the starting character position and the number of characters.</span></span> <span data-ttu-id="38985-114">これにいずれかのプログラムから、またはデザイン時に、**プロパティ**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="38985-114">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4.  <span data-ttu-id="38985-115">設定、<xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>プロパティを<xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>、 <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>、または<xref:System.Windows.Forms.LinkBehavior.NeverUnderline>です。</span><span class="sxs-lookup"><span data-stu-id="38985-115">Set the <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> property to <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, or <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.</span></span>  
  
     <span data-ttu-id="38985-116">設定されている場合<xref:System.Windows.Forms.LinkBehavior.HoverUnderline>、によって決まりますキャプションの一部<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>にポインターを置いたときに下線のみです。</span><span class="sxs-lookup"><span data-stu-id="38985-116">If it is set to <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, the part of the caption determined by <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> will only be underlined when the pointer rests on it.</span></span>  
  
5.  <span data-ttu-id="38985-117"><xref:System.Windows.Forms.LinkLabel.LinkClicked> 、イベント ハンドラーを設定、<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="38985-117">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, set the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="38985-118">リンクにアクセスすると、色で通常の何らかの方法でその外観を変更することを共通であります。</span><span class="sxs-lookup"><span data-stu-id="38985-118">When a link has been visited, it is common practice to change its appearance in some way, usually by color.</span></span> <span data-ttu-id="38985-119">指定された色に変更は、<xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="38985-119">The text will change to the color specified by the <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> property.</span></span>  
  
    ```vb  
    Protected Sub LinkLabel1_LinkClicked (ByVal sender As Object, _  
       ByVal e As EventArgs) Handles LinkLabel1.LinkClicked  
       ' Change the color of the link text  
       ' by setting LinkVisited to True.  
       LinkLabel1.LinkVisited = True  
       ' Then do whatever other action is appropriate  
    End Sub  
    ```  
  
    ```csharp  
    protected void LinkLabel1_LinkClicked(object sender, System.EventArgs e)  
    {  
       // Change the color of the link text by setting LinkVisited   
       // to True.  
       linkLabel1.LinkVisited = true;  
       // Then do whatever other action is appropriate  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void linkLabel1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)  
       {  
          // Change the color of the link text by setting LinkVisited   
          // to True.  
          linkLabel1->LinkVisited = true;  
          // Then do whatever other action is appropriate  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="38985-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="38985-120">See Also</span></span>  
 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>  
 <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>  
 <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>  
 <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>  
 [<span data-ttu-id="38985-121">LinkLabel コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="38985-121">LinkLabel Control Overview</span></span>](../../../../docs/framework/winforms/controls/linklabel-control-overview-windows-forms.md)  
 [<span data-ttu-id="38985-122">方法: Windows フォーム LinkLabel コントロールでオブジェクトまたは Web ページにリンクする</span><span class="sxs-lookup"><span data-stu-id="38985-122">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>](../../../../docs/framework/winforms/controls/link-to-an-object-or-web-page-with-wf-linklabel-control.md)  
 [<span data-ttu-id="38985-123">LinkLabel コントロール</span><span class="sxs-lookup"><span data-stu-id="38985-123">LinkLabel Control</span></span>](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)
