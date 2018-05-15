---
title: '方法 : Windows フォームに ToolStrip コントロールのカスタム レンダラーを作成して設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], custom rendering
- toolbars [Windows Forms], rendering
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], rendering
ms.assetid: 88a804ba-679f-4ba3-938a-0dc396199c5b
ms.openlocfilehash: 0b7a77a4a923065cba8c7ea366826f7b04126f11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a><span data-ttu-id="57a60-102">方法 : Windows フォームに ToolStrip コントロールのカスタム レンダラーを作成して設定する</span><span class="sxs-lookup"><span data-stu-id="57a60-102">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>
<span data-ttu-id="57a60-103"><xref:System.Windows.Forms.ToolStrip> コントロールは、テーマとスタイルを簡単なサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="57a60-103"><xref:System.Windows.Forms.ToolStrip> controls give easy support to themes and styles.</span></span> <span data-ttu-id="57a60-104">いずれかを設定して完全なカスタムの外観と動作 (ルック アンド フィール) を実現できる、<xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType>プロパティまたは<xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType>プロパティ、カスタム レンダラーをします。</span><span class="sxs-lookup"><span data-stu-id="57a60-104">You can achieve completely custom appearance and behavior (look and feel) by setting either the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property or the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to a custom renderer.</span></span>  
  
 <span data-ttu-id="57a60-105">レンダラーを各ユーザーに割り当てることができます<xref:System.Windows.Forms.ToolStrip>、 <xref:System.Windows.Forms.MenuStrip>、 <xref:System.Windows.Forms.ContextMenuStrip>、または<xref:System.Windows.Forms.StatusStrip>を使用するか、コントロール、<xref:System.Windows.Forms.ToolStripManager.Renderer%2A>プロパティを設定してすべてのオブジェクトに影響を与える、<xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType>プロパティを<xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="57a60-105">You can assign renderers to each individual <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, or <xref:System.Windows.Forms.StatusStrip> control, or you can use the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> property to affect all objects by setting the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57a60-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> 返します<xref:System.Windows.Forms.ToolStripRenderMode.Custom>場合にのみ、値の<xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType>は`null`します。</span><span class="sxs-lookup"><span data-stu-id="57a60-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> returns <xref:System.Windows.Forms.ToolStripRenderMode.Custom> only if the value of <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> is not `null`.</span></span>  
  
### <a name="to-create-a-custom-renderer"></a><span data-ttu-id="57a60-107">カスタム レンダラーを作成するには</span><span class="sxs-lookup"><span data-stu-id="57a60-107">To create a custom renderer</span></span>  
  
1.  <span data-ttu-id="57a60-108">拡張、<xref:System.Windows.Forms.ToolStripRenderer>クラスです。</span><span class="sxs-lookup"><span data-stu-id="57a60-108">Extend the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span>  
  
2.  <span data-ttu-id="57a60-109">実装して目的のカスタム レンダリングをオーバーライドする適切な*にしています.*</span><span class="sxs-lookup"><span data-stu-id="57a60-109">Implement desired custom rendering by overriding appropriate *On…*</span></span> <span data-ttu-id="57a60-110">メンバー</span><span class="sxs-lookup"><span data-stu-id="57a60-110">members</span></span>  
  
    ```vb  
    Public Class RedTextRenderer  
        Inherits System.Windows.Forms.ToolStripRenderer  
        Protected Overrides Sub OnRenderItemText(ByVal e As _  
            ToolStripItemTextRenderEventArgs)   
            e.TextColor = Color.Red  
            e.TextFont = New Font("Helvetica", 7, FontStyle.Bold)  
            MyBase.OnRenderItemText(e)  
        End Sub  
    End Class  
    ```  
  
    ```csharp  
    public class RedTextRenderer : _  
        System.Windows.Forms.ToolStripRenderer  
    {  
        protected override void _  
            OnRenderItemText(ToolStripItemTextRenderEventArgs e)  
        {  
            e.TextColor = Color.Red;  
            e.TextFont = new Font("Helvetica", 7, FontStyle.Bold);  
           base.OnRenderItemText(e);  
        }  
    }  
    ```  
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a><span data-ttu-id="57a60-111">現在のレンダラーにカスタム レンダラーを設定するには</span><span class="sxs-lookup"><span data-stu-id="57a60-111">To set the custom renderer to be the current renderer</span></span>  
  
1.  <span data-ttu-id="57a60-112">1 つのカスタム レンダラーを設定する<xref:System.Windows.Forms.ToolStrip>、設定、<xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType>プロパティは、カスタム レンダラーをします。</span><span class="sxs-lookup"><span data-stu-id="57a60-112">To set the custom renderer for one <xref:System.Windows.Forms.ToolStrip>, set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to the custom renderer.</span></span>  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2.  <span data-ttu-id="57a60-113">または、すべてのカスタム レンダラーを設定する<xref:System.Windows.Forms.ToolStrip>アプリケーションに含まれるクラス: 設定、<xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType>プロパティを設定し、カスタム レンダラー、<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>プロパティを<xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>です。</span><span class="sxs-lookup"><span data-stu-id="57a60-113">Or to set the custom renderer for all <xref:System.Windows.Forms.ToolStrip> classes contained in your application: Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to the custom renderer and set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="57a60-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="57a60-114">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>  
 <xref:System.Windows.Forms.ToolStripRenderer>  
 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>  
 [<span data-ttu-id="57a60-115">ToolStrip コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="57a60-115">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="57a60-116">ToolStrip コントロールのアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="57a60-116">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [<span data-ttu-id="57a60-117">ToolStrip テクノロジの概要</span><span class="sxs-lookup"><span data-stu-id="57a60-117">ToolStrip Technology Summary</span></span>](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
