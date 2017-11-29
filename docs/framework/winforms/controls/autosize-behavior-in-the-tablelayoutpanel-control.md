---
title: "TableLayoutPanel コントロールにおける AutoSize 動作"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- localizing forms
- layout [Windows Forms], AutoSize
- sizing [Windows Forms], automatic
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- automatic sizing
- AutoSizeMode property
ms.assetid: 9233e0c3-2fa6-405e-8701-959479b1250e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3d4813b7bd37c0c5bd9b04b37cb825067b35ce3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="autosize-behavior-in-the-tablelayoutpanel-control"></a><span data-ttu-id="35f2b-102">TableLayoutPanel コントロールにおける AutoSize 動作</span><span class="sxs-lookup"><span data-stu-id="35f2b-102">AutoSize Behavior in the TableLayoutPanel Control</span></span>
## <a name="distinct-autosize-behaviors"></a><span data-ttu-id="35f2b-103">個別の AutoSize 動作</span><span class="sxs-lookup"><span data-stu-id="35f2b-103">Distinct AutoSize Behaviors</span></span>  
 <span data-ttu-id="35f2b-104"><xref:System.Windows.Forms.TableLayoutPanel>コントロールは、次のように自動サイズ変更動作をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="35f2b-104">The <xref:System.Windows.Forms.TableLayoutPanel> control supports automatic sizing behavior in the following ways:</span></span>  
  
-   <span data-ttu-id="35f2b-105">を介して、<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="35f2b-105">Through the <xref:System.Windows.Forms.Control.AutoSize%2A> property;</span></span>  
  
-   <span data-ttu-id="35f2b-106">を介して、<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>プロパティを<xref:System.Windows.Forms.TableLayoutPanel>コントロールの列と行のスタイル。</span><span class="sxs-lookup"><span data-stu-id="35f2b-106">Through the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property on the <xref:System.Windows.Forms.TableLayoutPanel> control’s column and row styles.</span></span>  
  
### <a name="the-autosize-property-with-row-and-column-styles"></a><span data-ttu-id="35f2b-107">行と列のスタイル AutoSize プロパティ</span><span class="sxs-lookup"><span data-stu-id="35f2b-107">The AutoSize Property with Row and Column Styles</span></span>  
 <span data-ttu-id="35f2b-108">次の表に、間の相互作用、<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティおよび<xref:System.Windows.Forms.TableLayoutPanel>コントロールの列と行のスタイル。</span><span class="sxs-lookup"><span data-stu-id="35f2b-108">The following table describes the interaction between the <xref:System.Windows.Forms.Control.AutoSize%2A> property and the <xref:System.Windows.Forms.TableLayoutPanel> control’s column and row styles.</span></span>  
  
|<span data-ttu-id="35f2b-109">Autosize プロパティの設定</span><span class="sxs-lookup"><span data-stu-id="35f2b-109">AutoSize setting</span></span>|<span data-ttu-id="35f2b-110">スタイルの相互作用</span><span class="sxs-lookup"><span data-stu-id="35f2b-110">Style interaction</span></span>|  
|----------------------|-----------------------|  
|`false`|<span data-ttu-id="35f2b-111"><xref:System.Windows.Forms.TableLayoutPanel>コントロールが右に左からプロセスが実行され、または次の順序で行または列の領域が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="35f2b-111">The <xref:System.Windows.Forms.TableLayoutPanel> control proceeds from left to right, and allocates space for the column or row or in the following order.</span></span><br /><br /> <span data-ttu-id="35f2b-112">1.場合、<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>プロパティに設定されている<xref:System.Windows.Forms.SizeType.Absolute>、ピクセル数で指定された<xref:System.Windows.Forms.ColumnStyle.Width%2A>または<xref:System.Windows.Forms.RowStyle.Height%2A>が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="35f2b-112">1.  If the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property is set to <xref:System.Windows.Forms.SizeType.Absolute>, the number of pixels specified by <xref:System.Windows.Forms.ColumnStyle.Width%2A> or <xref:System.Windows.Forms.RowStyle.Height%2A> is allocated.</span></span><br /><span data-ttu-id="35f2b-113">2.場合、<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>プロパティに設定されている<xref:System.Windows.Forms.SizeType.AutoSize>、子コントロールのによって返されるピクセル数<xref:System.Windows.Forms.Control.GetPreferredSize%2A>メソッドが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="35f2b-113">2.  If the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property is set to <xref:System.Windows.Forms.SizeType.AutoSize>, the number of pixels returned by the child control’s <xref:System.Windows.Forms.Control.GetPreferredSize%2A> method is allocated.</span></span><br /><span data-ttu-id="35f2b-114">3.すべてのスペース後<xref:System.Windows.Forms.SizeType.Absolute>と<xref:System.Windows.Forms.SizeType.AutoSize>列または行が割り当てられる列や行の<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>'éý'<xref:System.Windows.Forms.SizeType.Percent>比例して残りの空き領域を割り当てるために使用されます</span><span class="sxs-lookup"><span data-stu-id="35f2b-114">3.  After space for all <xref:System.Windows.Forms.SizeType.Absolute> and <xref:System.Windows.Forms.SizeType.AutoSize> columns or rows is allocated, any columns or rows with <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> set to <xref:System.Windows.Forms.SizeType.Percent> are used to proportionally allocate the remaining free space</span></span>|  
|`true`|<span data-ttu-id="35f2b-115">例外と、以前の相互作用のようなを<xref:System.Windows.Forms.SizeType.Percent>列または行は、上の自動サイズ変更を取得します。</span><span class="sxs-lookup"><span data-stu-id="35f2b-115">Similar to the previous interaction, with the exception that <xref:System.Windows.Forms.SizeType.Percent> columns or rows acquire an automatic sizing aspect.</span></span><br /><br /> <span data-ttu-id="35f2b-116"><xref:System.Windows.Forms.TableLayoutPanel>コントロールは、十分な空き領域を作成する行、列を拡張できるようになしの列または行を<xref:System.Windows.Forms.SizeType.Percent>スタイルがそのコンテンツをクリップします。</span><span class="sxs-lookup"><span data-stu-id="35f2b-116">The <xref:System.Windows.Forms.TableLayoutPanel> control expands the column or row to create adequate free space, so that no column or row with <xref:System.Windows.Forms.SizeType.Percent> styling clips its contents.</span></span> <span data-ttu-id="35f2b-117"><xref:System.Windows.Forms.TableLayoutPanel>コントロールが比例的によると、新しい領域を割り当て、<xref:System.Windows.Forms.ColumnStyle.Width%2A>または<xref:System.Windows.Forms.RowStyle.Height%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="35f2b-117">The <xref:System.Windows.Forms.TableLayoutPanel> control allocates the new space proportionally according to the <xref:System.Windows.Forms.ColumnStyle.Width%2A> or <xref:System.Windows.Forms.RowStyle.Height%2A> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="35f2b-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="35f2b-118">See Also</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [<span data-ttu-id="35f2b-119">TableLayoutPanel コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="35f2b-119">TableLayoutPanel Control Overview</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-overview.md)
