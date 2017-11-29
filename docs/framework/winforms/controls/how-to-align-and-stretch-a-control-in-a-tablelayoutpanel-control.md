---
title: "方法 : TableLayoutPanel コントロール内でコントロールを配置して伸縮する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: net.ComponentModel.StyleCollectionEditor.TLP.AlignStretchCtrl
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms], stretching controls
- controls [Windows Forms], stretching
- controls [Windows Forms], aligning
ms.assetid: 7dc1a157-6fee-4995-8ebc-b65bdc0909a8
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 043adb68b88ab031cea3de1206d1f2c4252b75d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control"></a><span data-ttu-id="b9d00-102">方法 : TableLayoutPanel コントロール内でコントロールを配置して伸縮する</span><span class="sxs-lookup"><span data-stu-id="b9d00-102">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>
<span data-ttu-id="b9d00-103">内のコントロールを拡大して整列することができます、<xref:System.Windows.Forms.TableLayoutPanel>で、<xref:System.Windows.Forms.Control.Anchor%2A>と<xref:System.Windows.Forms.Control.Dock%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="b9d00-103">You can align and stretch controls in a <xref:System.Windows.Forms.TableLayoutPanel> with the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9d00-104">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b9d00-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b9d00-105">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9d00-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b9d00-106">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9d00-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-align-and-stretch-a-control"></a><span data-ttu-id="b9d00-107">配置して伸縮コントロール</span><span class="sxs-lookup"><span data-stu-id="b9d00-107">To align and stretch a control</span></span>  
  
1.  <span data-ttu-id="b9d00-108">ドラッグ、<xref:System.Windows.Forms.TableLayoutPanel>から制御、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="b9d00-108">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="b9d00-109">ドラッグ、<xref:System.Windows.Forms.Button>から制御、**ツールボックス**の左上隅のセルに、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="b9d00-109">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the upper-left cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="b9d00-110"><xref:System.Windows.Forms.Button>コントロールがセルの中央に配置します。</span><span class="sxs-lookup"><span data-stu-id="b9d00-110">The <xref:System.Windows.Forms.Button> control is centered in the cell.</span></span>  
  
3.  <span data-ttu-id="b9d00-111">値を設定、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Anchor%2A>プロパティを`Left,Right`です。</span><span class="sxs-lookup"><span data-stu-id="b9d00-111">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left,Right`.</span></span> <span data-ttu-id="b9d00-112"><xref:System.Windows.Forms.Button>端まで拡大に合わせてセルの幅を制御します。</span><span class="sxs-lookup"><span data-stu-id="b9d00-112">The <xref:System.Windows.Forms.Button> control stretches to match the width of the cell.</span></span>  
  
4.  <span data-ttu-id="b9d00-113">値を設定、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Anchor%2A>プロパティを`Top,Bottom`です。</span><span class="sxs-lookup"><span data-stu-id="b9d00-113">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top,Bottom`.</span></span> <span data-ttu-id="b9d00-114"><xref:System.Windows.Forms.Button>セルの高さが揃うように端まで拡大を制御します。</span><span class="sxs-lookup"><span data-stu-id="b9d00-114">The <xref:System.Windows.Forms.Button> control stretches to match the height of the cell.</span></span>  
  
5.  <span data-ttu-id="b9d00-115">値を設定、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.Fill>です。</span><span class="sxs-lookup"><span data-stu-id="b9d00-115">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="b9d00-116"><xref:System.Windows.Forms.Button>コントロールがセルを満たす展開します。</span><span class="sxs-lookup"><span data-stu-id="b9d00-116">The <xref:System.Windows.Forms.Button> control expands to fill the cell.</span></span>  
  
6.  <span data-ttu-id="b9d00-117">値を設定、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.None>です。</span><span class="sxs-lookup"><span data-stu-id="b9d00-117">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.None>.</span></span> <span data-ttu-id="b9d00-118"><xref:System.Windows.Forms.Button>コントロールは、元のサイズを返し、セルの左上隅に移動します。</span><span class="sxs-lookup"><span data-stu-id="b9d00-118">The <xref:System.Windows.Forms.Button> control returns to its original size and moves to the upper-left corner of the cell.</span></span> <span data-ttu-id="b9d00-119">**Windows フォーム デザイナー**設定が、<xref:System.Windows.Forms.Control.Anchor%2A>プロパティを`Top, Left`です。</span><span class="sxs-lookup"><span data-stu-id="b9d00-119">The **Windows Forms Designer** has set the <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Left`.</span></span>  
  
7.  <span data-ttu-id="b9d00-120">値を設定、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Anchor%2A>プロパティを`Bottom,Right`です。</span><span class="sxs-lookup"><span data-stu-id="b9d00-120">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Bottom,Right`.</span></span> <span data-ttu-id="b9d00-121"><xref:System.Windows.Forms.Button>コントロールがセルの右下隅に移動します。</span><span class="sxs-lookup"><span data-stu-id="b9d00-121">The <xref:System.Windows.Forms.Button> control moves to the lower-right corner of the cell.</span></span>  
  
8.  <span data-ttu-id="b9d00-122">値を設定、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Anchor%2A>プロパティを<xref:System.Windows.Forms.AnchorStyles.None>です。</span><span class="sxs-lookup"><span data-stu-id="b9d00-122">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to <xref:System.Windows.Forms.AnchorStyles.None>.</span></span> <span data-ttu-id="b9d00-123"><xref:System.Windows.Forms.Button>コントロールがセルの中央に移動します。</span><span class="sxs-lookup"><span data-stu-id="b9d00-123">The <xref:System.Windows.Forms.Button> control moves to the center of the cell.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9d00-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9d00-124">See Also</span></span>  
 [<span data-ttu-id="b9d00-125">TableLayoutPanel コントロール</span><span class="sxs-lookup"><span data-stu-id="b9d00-125">TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
