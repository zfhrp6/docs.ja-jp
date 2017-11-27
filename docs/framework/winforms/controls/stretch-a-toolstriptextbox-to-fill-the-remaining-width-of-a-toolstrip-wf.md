---
title: "方法 : ToolStripTextBox を拡大して ToolStrip の残りの幅に合わせる (Windows フォーム)"
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
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 213929e52f08fff19eb7641092789501c31648e0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a><span data-ttu-id="2e681-102">方法 : ToolStripTextBox を拡大して ToolStrip の残りの幅に合わせる (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="2e681-102">How to: Stretch a ToolStripTextBox to Fill the Remaining Width of a ToolStrip (Windows Forms)</span></span>
<span data-ttu-id="2e681-103">設定すると、<xref:System.Windows.Forms.ToolStrip.Stretch%2A>のプロパティ、<xref:System.Windows.Forms.ToolStrip>に制御を`true`コントロールのコンテナーをエンド ツー エンドで塗りつぶし、コンテナーのサイズを変更すると、サイズ変更します。</span><span class="sxs-lookup"><span data-stu-id="2e681-103">When you set the <xref:System.Windows.Forms.ToolStrip.Stretch%2A> property of a <xref:System.Windows.Forms.ToolStrip> control to `true`, the control fills its container from end to end, and resizes when its container resizes.</span></span> <span data-ttu-id="2e681-104">この構成では有用なことなど、コントロールでは、項目をストレッチする、<xref:System.Windows.Forms.ToolStripTextBox>空き領域の塗りつぶし、およびコントロールのサイズを変更するとサイズ変更します。</span><span class="sxs-lookup"><span data-stu-id="2e681-104">In this configuration, you may find it useful to stretch an item in the control, such as a <xref:System.Windows.Forms.ToolStripTextBox>, to fill the available space and to resize when the control resizes.</span></span> <span data-ttu-id="2e681-105">この拡大役に立ちます、たとえば、外観と Microsoft® Internet Explorer のアドレス バーのような動作を実現したい場合。</span><span class="sxs-lookup"><span data-stu-id="2e681-105">This stretching is useful, for example, if you want to achieve appearance and behavior similar to the address bar in Microsoft® Internet Explorer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e681-106">例</span><span class="sxs-lookup"><span data-stu-id="2e681-106">Example</span></span>  
 <span data-ttu-id="2e681-107">次のコード例から派生したクラスを提供する<xref:System.Windows.Forms.ToolStripTextBox>と呼ばれる`ToolStripSpringTextBox`です。</span><span class="sxs-lookup"><span data-stu-id="2e681-107">The following code example provides a class derived from <xref:System.Windows.Forms.ToolStripTextBox> called `ToolStripSpringTextBox`.</span></span> <span data-ttu-id="2e681-108">このクラスは、オーバーライド、<xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A>親の使用可能な幅を計算するメソッド<xref:System.Windows.Forms.ToolStrip>他のすべての項目の幅の合計を削除した後に制御します。</span><span class="sxs-lookup"><span data-stu-id="2e681-108">This class overrides the <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> method to calculate the available width of the parent <xref:System.Windows.Forms.ToolStrip> control after the combined width of all other items has been subtracted.</span></span> <span data-ttu-id="2e681-109">このコード例も提供、<xref:System.Windows.Forms.Form>クラスおよび`Program`クラスに新しい動作を示します。</span><span class="sxs-lookup"><span data-stu-id="2e681-109">This code example also provides a <xref:System.Windows.Forms.Form> class and a `Program` class to demonstrate the new behavior.</span></span>  
  
 [!code-csharp[ToolStripSpringTextBox#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2e681-110">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="2e681-110">Compiling the Code</span></span>  
 <span data-ttu-id="2e681-111">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2e681-111">This example requires:</span></span>  
  
-   <span data-ttu-id="2e681-112">System、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="2e681-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e681-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="2e681-113">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripTextBox>  
 <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="2e681-114">ToolStrip コントロールのアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="2e681-114">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [<span data-ttu-id="2e681-115">方法: StatusStrip 内で Spring プロパティを対話的に使用する</span><span class="sxs-lookup"><span data-stu-id="2e681-115">How to: Use the Spring Property Interactively in a StatusStrip</span></span>](../../../../docs/framework/winforms/controls/how-to-use-the-spring-property-interactively-in-a-statusstrip.md)
