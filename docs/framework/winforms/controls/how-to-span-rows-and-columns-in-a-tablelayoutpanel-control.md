---
title: "方法 : TableLayoutPanel コントロールの行と列を拡大する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns
helpviewer_keywords:
- columns [Windows Forms], spanning
- merging cells
- TableLayoutPanel control [Windows Forms], spanning rows and columns
- rows [Windows Forms], spanning
- cells [Windows Forms], merging
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e29db51401edccf57aa89307a159efc28eb1d4da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a><span data-ttu-id="df275-102">方法 : TableLayoutPanel コントロールの行と列を拡大する</span><span class="sxs-lookup"><span data-stu-id="df275-102">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>
<span data-ttu-id="df275-103">コントロールで、<xref:System.Windows.Forms.TableLayoutPanel>コントロールが隣接する行と列にまたがることができます。</span><span class="sxs-lookup"><span data-stu-id="df275-103">Controls in a <xref:System.Windows.Forms.TableLayoutPanel> control can span adjacent rows and columns.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df275-104">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="df275-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="df275-105">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="df275-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="df275-106">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="df275-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-span-columns-and-rows"></a><span data-ttu-id="df275-107">列と行にまたがること</span><span class="sxs-lookup"><span data-stu-id="df275-107">To span columns and rows</span></span>  
  
1.  <span data-ttu-id="df275-108">ドラッグ、<xref:System.Windows.Forms.TableLayoutPanel>から制御、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="df275-108">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="df275-109">ドラッグ、<xref:System.Windows.Forms.Button>から制御、**ツールボックス**の左上隅のセルに、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="df275-109">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the upper-left cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
3.  <span data-ttu-id="df275-110">設定、<xref:System.Windows.Forms.Button>コントロールの**ColumnSpan**プロパティを**2**です。</span><span class="sxs-lookup"><span data-stu-id="df275-110">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **2**.</span></span> <span data-ttu-id="df275-111">なお、<xref:System.Windows.Forms.Button>コントロールが最初と 2 番目の列にまたがってです。</span><span class="sxs-lookup"><span data-stu-id="df275-111">Note that the <xref:System.Windows.Forms.Button> control spans the first and second columns.</span></span>  
  
4.  <span data-ttu-id="df275-112">設定、<xref:System.Windows.Forms.Button>コントロールの**RowSpan**プロパティを**2**です。</span><span class="sxs-lookup"><span data-stu-id="df275-112">Set the <xref:System.Windows.Forms.Button> control's **RowSpan** property to **2**.</span></span> <span data-ttu-id="df275-113">なお、<xref:System.Windows.Forms.Button>コントロールの最初と 2 番目の行にまたがって表示します。</span><span class="sxs-lookup"><span data-stu-id="df275-113">Note that the <xref:System.Windows.Forms.Button> control spans the first and second rows.</span></span>  
  
5.  <span data-ttu-id="df275-114">設定、<xref:System.Windows.Forms.Button>コントロールの**ColumnSpan**プロパティを**1**です。</span><span class="sxs-lookup"><span data-stu-id="df275-114">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **1**.</span></span> <span data-ttu-id="df275-115">なお、<xref:System.Windows.Forms.Button>コントロールは、最初の列に移動し、最初と 2 番目の行にまたがるです。</span><span class="sxs-lookup"><span data-stu-id="df275-115">Note that the <xref:System.Windows.Forms.Button> control moves into the first column and spans the first and second rows.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df275-116">参照</span><span class="sxs-lookup"><span data-stu-id="df275-116">See Also</span></span>  
 [<span data-ttu-id="df275-117">TableLayoutPanel コントロール</span><span class="sxs-lookup"><span data-stu-id="df275-117">TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
