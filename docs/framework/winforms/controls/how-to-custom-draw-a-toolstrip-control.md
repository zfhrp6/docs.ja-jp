---
title: '方法 : ToolStrip コントロールをカスタム描画する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], custom drawing
- drawing [Windows Forms], owner
- ProfessionalColorTable class [Windows Forms], overriding
- examples [Windows Forms], toolbars
- drawing [Windows Forms], custom
- toolbars [Windows Forms], changing colors
- ToolStrip control [Windows Forms], drawing
- ToolStrip control [Windows Forms], changing colors
- custom drawing
- owner drawing
ms.assetid: 94e7d7bd-a752-441c-b5b3-7acf98881163
ms.openlocfilehash: 09d9654bf1a2670c77a4a3db2eae2ed7ab6dbfec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-custom-draw-a-toolstrip-control"></a><span data-ttu-id="96316-102">方法 : ToolStrip コントロールをカスタム描画する</span><span class="sxs-lookup"><span data-stu-id="96316-102">How to: Custom Draw a ToolStrip Control</span></span>
<span data-ttu-id="96316-103"><xref:System.Windows.Forms.ToolStrip> コントロールに、次のレンダリング (描画) クラスが関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="96316-103">The <xref:System.Windows.Forms.ToolStrip> controls have the following associated rendering (painting) classes:</span></span>  
  
-   <span data-ttu-id="96316-104"><xref:System.Windows.Forms.ToolStripSystemRenderer> は、オペレーティング システムの外観とスタイルを提供します。</span><span class="sxs-lookup"><span data-stu-id="96316-104"><xref:System.Windows.Forms.ToolStripSystemRenderer> provides the appearance and style of your operating system.</span></span>  
  
-   <span data-ttu-id="96316-105"><xref:System.Windows.Forms.ToolStripProfessionalRenderer> は、Microsoft Office の外観とスタイルを提供します。</span><span class="sxs-lookup"><span data-stu-id="96316-105"><xref:System.Windows.Forms.ToolStripProfessionalRenderer> provides the appearance and style of Microsoft Office.</span></span>  
  
-   <span data-ttu-id="96316-106"><xref:System.Windows.Forms.ToolStripRenderer> は、その他の 2 つのレンダリング クラスの抽象基本クラスです。</span><span class="sxs-lookup"><span data-stu-id="96316-106"><xref:System.Windows.Forms.ToolStripRenderer> is the abstract base class for the other two rendering classes.</span></span>  
  
 <span data-ttu-id="96316-107"><xref:System.Windows.Forms.ToolStrip> をカスタムで描画 (オーナー描画) するために、レンダラー クラスの 1 つをオーバーライドして表示ロジックの特定の側面を変更できます。</span><span class="sxs-lookup"><span data-stu-id="96316-107">To custom draw (also known as owner draw) a <xref:System.Windows.Forms.ToolStrip>, you can override one of the renderer classes and change an aspect of the rendering logic.</span></span>  
  
 <span data-ttu-id="96316-108">次の手順は、カスタムの描画のさまざまな側面について説明します。</span><span class="sxs-lookup"><span data-stu-id="96316-108">The following procedures describe various aspects of custom drawing.</span></span>  
  
### <a name="to-switch-between-the-provided-renderers"></a><span data-ttu-id="96316-109">設定されているレンダラー間で切り替えるには</span><span class="sxs-lookup"><span data-stu-id="96316-109">To switch between the provided renderers</span></span>  
  
-   <span data-ttu-id="96316-110"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> プロパティを任意の <xref:System.Windows.Forms.ToolStripRenderMode> の値に設定します。</span><span class="sxs-lookup"><span data-stu-id="96316-110">Set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to the <xref:System.Windows.Forms.ToolStripRenderMode> value you want.</span></span>  
  
     <span data-ttu-id="96316-111"><xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode> と共に、静的な <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> がアプリケーションのレンダラーを決定します。</span><span class="sxs-lookup"><span data-stu-id="96316-111">With <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>, the static <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> determines the renderer for your application.</span></span> <span data-ttu-id="96316-112"><xref:System.Windows.Forms.ToolStripRenderMode> のその他の値は、<xref:System.Windows.Forms.ToolStripRenderMode.Custom>、<xref:System.Windows.Forms.ToolStripRenderMode.Professional>、および <xref:System.Windows.Forms.ToolStripRenderMode.System> です。</span><span class="sxs-lookup"><span data-stu-id="96316-112">The other values of <xref:System.Windows.Forms.ToolStripRenderMode> are <xref:System.Windows.Forms.ToolStripRenderMode.Custom>, <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, and <xref:System.Windows.Forms.ToolStripRenderMode.System>.</span></span>  
  
### <a name="to-change-the-microsoft-officestyle-borders-to-straight"></a><span data-ttu-id="96316-113">Microsoft Office スタイルの境界を直線に変更するには</span><span class="sxs-lookup"><span data-stu-id="96316-113">To change the Microsoft Office–style borders to straight</span></span>  
  
-   <span data-ttu-id="96316-114"><xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType> をオーバーライドしますが、基本クラスは呼び出しません。</span><span class="sxs-lookup"><span data-stu-id="96316-114">Override <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, but do not call the base class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96316-115"><xref:System.Windows.Forms.ToolStripRenderer>、<xref:System.Windows.Forms.ToolStripSystemRenderer>、および <xref:System.Windows.Forms.ToolStripProfessionalRenderer> に対して、このメソッドのバージョンがあります。</span><span class="sxs-lookup"><span data-stu-id="96316-115">There is a version of this method for <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripSystemRenderer>, and <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.</span></span>  
  
### <a name="to-change-the-professionalcolortable"></a><span data-ttu-id="96316-116">ProfessionalColorTable を変更するには</span><span class="sxs-lookup"><span data-stu-id="96316-116">To change the ProfessionalColorTable</span></span>  
  
-   <span data-ttu-id="96316-117"><xref:System.Windows.Forms.ProfessionalColorTable> をオーバーライドして必要な色を変更します。</span><span class="sxs-lookup"><span data-stu-id="96316-117">Override <xref:System.Windows.Forms.ProfessionalColorTable> and change the colors you want.</span></span>  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As _  
    System.EventArgs) Handles Me.Load  
        Dim t As MyColorTable = New MyColorTable  
        ToolStrip1.Renderer = New ToolStripProfessionalRenderer(t)  
    End Sub  
  
    Class MyColorTable   
    Inherits ProfessionalColorTable  
  
    Public Overrides ReadOnly Property ButtonPressedGradientBegin() As Color  
        Get  
            Return Color.Red  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonPressedGradientMiddle() _  
    As System.Drawing.Color  
        Get  
            Return Color.Blue  
        End Get  
            End Property  
  
    Public Overrides ReadOnly Property ButtonPressedGradientEnd() _  
    As System.Drawing.Color  
        Get  
            Return Color.Green  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientBegin() _  
    As Color  
        Get  
            Return Color.Yellow  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientMiddle() As System.Drawing.Color  
        Get  
            Return Color.Orange  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientEnd() _  
    As System.Drawing.Color  
        Get  
            Return Color.Violet  
        End Get  
    End Property  
    End Class  
    ```  
  
### <a name="to-change-the-rendering-for-all-toolstrip-controls-in-your-application"></a><span data-ttu-id="96316-118">アプリケーション内のすべての ToolStrip コントロールのレンダリングを変更するには</span><span class="sxs-lookup"><span data-stu-id="96316-118">To change the rendering for all ToolStrip controls in your application</span></span>  
  
1.  <span data-ttu-id="96316-119"><xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> プロパティを使用して、設定されているレンダラーのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="96316-119">Use the <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> property to choose one of the provided renderers.</span></span>  
  
2.  <span data-ttu-id="96316-120"><xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> を使用して、カスタム レンダラーを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="96316-120">Use <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> to assign a custom renderer.</span></span>  
  
3.  <span data-ttu-id="96316-121"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> が既定値の <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode> に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="96316-121">Ensure that <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> is set to the default value of <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-the-entire-application"></a><span data-ttu-id="96316-122">アプリケーション全体で Microsoft Office の色をオフにするには</span><span class="sxs-lookup"><span data-stu-id="96316-122">To turn off the Microsoft Office colors for the entire application</span></span>  
  
-   <span data-ttu-id="96316-123"><xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> を `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="96316-123">Set <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> to `false`.</span></span>  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-one-toolstrip-control"></a><span data-ttu-id="96316-124">1 つの ToolStrip コントロールで Microsoft Office の色をオフにするには</span><span class="sxs-lookup"><span data-stu-id="96316-124">To turn off the Microsoft Office colors for one ToolStrip control</span></span>  
  
-   <span data-ttu-id="96316-125">次のコード例に似たコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="96316-125">Use code similar to the following code example.</span></span>  
  
    ```vb  
    Dim colorTable As ProfessionalColorTable()  
    colorTable.UseSystemColors = True  
    Dim toolStrip.Renderer As ToolStripProfessionalRenderer(colorTable)  
    ```  
  
    ```csharp  
    ProfessionalColorTable colorTable = new ProfessionalColorTable();  
    colorTable.UseSystemColors = true;  
    toolStrip.Renderer = new ToolStripProfessionalRenderer(colorTable);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="96316-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="96316-126">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripSystemRenderer>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
 <xref:System.Windows.Forms.ToolStripRenderer>  
 [<span data-ttu-id="96316-127">組み込みのオーナー描画サポートを備えたコントロール</span><span class="sxs-lookup"><span data-stu-id="96316-127">Controls with Built-In Owner-Drawing Support</span></span>](../../../../docs/framework/winforms/controls/controls-with-built-in-owner-drawing-support.md)  
 [<span data-ttu-id="96316-128">方法: Windows フォームに ToolStrip コントロールのカスタム レンダラーを作成して設定する</span><span class="sxs-lookup"><span data-stu-id="96316-128">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
 [<span data-ttu-id="96316-129">ToolStrip コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="96316-129">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
