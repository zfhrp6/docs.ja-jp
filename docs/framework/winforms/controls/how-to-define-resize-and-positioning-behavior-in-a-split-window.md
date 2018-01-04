---
title: "方法 : 分割ウィンドウでのサイズ変更および位置指定動作を定義する"
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
helpviewer_keywords:
- split windows [Windows Forms], resizing
- splitter windows [Windows Forms], resizing
- SplitContainer control [Windows Forms], resizing
ms.assetid: 9bf73f36-ed2d-4a02-b15a-0770eff4fdfa
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed78a49119c87c52a07cc2ade030e66087d3f420
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-resize-and-positioning-behavior-in-a-split-window"></a><span data-ttu-id="dbd0d-102">方法 : 分割ウィンドウでのサイズ変更および位置指定動作を定義する</span><span class="sxs-lookup"><span data-stu-id="dbd0d-102">How to: Define Resize and Positioning Behavior in a Split Window</span></span>
<span data-ttu-id="dbd0d-103">パネル、<xref:System.Windows.Forms.SplitContainer>コントロール役立つ中に適切にサイズ変更され、ユーザーが操作されます。</span><span class="sxs-lookup"><span data-stu-id="dbd0d-103">The panels of the <xref:System.Windows.Forms.SplitContainer> control lend themselves well to being resized and manipulated by users.</span></span> <span data-ttu-id="dbd0d-104">ただしがあるプログラムから分割線を制御する場合は、場所が配置されているしにどの程度まで移動できます。</span><span class="sxs-lookup"><span data-stu-id="dbd0d-104">However, there will be times when you will want to programmatically control the splitter—where it is positioned and to what degree it can be moved.</span></span>  
  
 <span data-ttu-id="dbd0d-105"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>プロパティおよびその他のプロパティを<xref:System.Windows.Forms.SplitContainer>コントロールは、ニーズに合わせて、ユーザー インターフェイスの動作を正確に制御を提供します。</span><span class="sxs-lookup"><span data-stu-id="dbd0d-105">The <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property and the other properties on the <xref:System.Windows.Forms.SplitContainer> control give you precise control over the behavior of your user interface to suit your needs.</span></span> <span data-ttu-id="dbd0d-106">これらのプロパティは、次の表に一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="dbd0d-106">These properties are listed in the following table.</span></span>  
  
|<span data-ttu-id="dbd0d-107">name</span><span class="sxs-lookup"><span data-stu-id="dbd0d-107">Name</span></span>|<span data-ttu-id="dbd0d-108">説明</span><span class="sxs-lookup"><span data-stu-id="dbd0d-108">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="dbd0d-109"><xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> プロパティ</span><span class="sxs-lookup"><span data-stu-id="dbd0d-109"><xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> property</span></span>|<span data-ttu-id="dbd0d-110">分割線は、キーボードまたはマウスを使用して移動可能なかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="dbd0d-110">Determines if the splitter is movable by means of the keyboard or mouse.</span></span>|  
|<span data-ttu-id="dbd0d-111"><xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> プロパティ</span><span class="sxs-lookup"><span data-stu-id="dbd0d-111"><xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> property</span></span>|<span data-ttu-id="dbd0d-112">移動可能な分割バーを左端または上端からのピクセル単位で距離を決定します。</span><span class="sxs-lookup"><span data-stu-id="dbd0d-112">Determines the distance in pixels from the left or upper edge to the movable splitter bar.</span></span>|  
|<span data-ttu-id="dbd0d-113"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> プロパティ</span><span class="sxs-lookup"><span data-stu-id="dbd0d-113"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property</span></span>|<span data-ttu-id="dbd0d-114">最小の距離 (ピクセル単位)、スプリッターをユーザーが移動できることを決定します。</span><span class="sxs-lookup"><span data-stu-id="dbd0d-114">Determines the minimum distance, in pixels, that the splitter can be moved by the user.</span></span>|  
  
 <span data-ttu-id="dbd0d-115">次の例を変更、 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> 「スナップ分割」効果; を作成するプロパティの既定値 1 ではなく、10 のピクセル単位で増加、ユーザーが分割線をドラッグしたとき。</span><span class="sxs-lookup"><span data-stu-id="dbd0d-115">The example below modifies the <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property to create a "snapping splitter" effect; when the user drags the splitter, it increments in units of 10 pixels rather than the default 1.</span></span>  
  
### <a name="to-define-splitcontainer-resize-behavior"></a><span data-ttu-id="dbd0d-116">SplitContainer のサイズ変更動作を定義するには</span><span class="sxs-lookup"><span data-stu-id="dbd0d-116">To define SplitContainer resize behavior</span></span>  
  
1.  <span data-ttu-id="dbd0d-117">プロシージャでは、設定、<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>プロパティ、希望するサイズを 'スナップ' スプリッターの動作を実現できるようにします。</span><span class="sxs-lookup"><span data-stu-id="dbd0d-117">In a procedure, set the <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property to the desired size, so that the 'snapping' behavior of the splitter is achieved.</span></span>  
  
     <span data-ttu-id="dbd0d-118">フォームの内で、次のコード例で<xref:System.Windows.Forms.Form.Load>イベント、内のスプリッター、<xref:System.Windows.Forms.SplitContainer>コントロールにドラッグすると、10 のピクセルのジャンプに設定します。</span><span class="sxs-lookup"><span data-stu-id="dbd0d-118">In the following code example, within the form's <xref:System.Windows.Forms.Form.Load> event, the splitter within the <xref:System.Windows.Forms.SplitContainer> control is set to jump 10 pixels when dragged.</span></span>  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, _  
        ByVal e As System.EventArgs) Handles MyBase.Load  
        Dim splitSnapper as new SplitContainer()  
        splitSnapper.SplitterIncrement = 10  
        splitSnapper.Dock = DockStyle.Fill  
        splitSnapper.Parent = me  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Load(System.Object sender, System.EventArgs e)  
    {  
        SplitContainer splitSnapper = new SplitContainer();  
        splitSnapper.SplitterIncrement = 10;  
        splitSnapper.Dock = DockStyle.Fill;  
        splitSnapper.Parent = this;  
    }  
    ```  
  
     <span data-ttu-id="dbd0d-119">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)])、イベント ハンドラーを登録するフォームのコンス トラクターに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="dbd0d-119">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
     <span data-ttu-id="dbd0d-120">左または右にスプリッターを若干移動効果はありません難しくします。ただし、マウス ポインターが両方向に 10 ピクセルに出ると、分割が新しい位置にスナップされます。</span><span class="sxs-lookup"><span data-stu-id="dbd0d-120">Moving the splitter slightly to the left or right will have no discernible effect; however, when the mouse pointer goes 10 pixels in either direction, the splitter will snap to the new position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbd0d-121">参照</span><span class="sxs-lookup"><span data-stu-id="dbd0d-121">See Also</span></span>  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>
