---
title: '方法 : ToolStrip を ToolStripContainer からフォームに移動する'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], parenting to forms
- Windows Forms, parenting ToolStrip controls
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
ms.openlocfilehash: 6cc54264033eca541ce845b75d608087fee8a542
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532331"
---
# <a name="how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a><span data-ttu-id="22b88-102">方法 : ToolStrip を ToolStripContainer からフォームに移動する</span><span class="sxs-lookup"><span data-stu-id="22b88-102">How to: Move a ToolStrip Out of a ToolStripContainer onto a Form</span></span>
<span data-ttu-id="22b88-103">移動する、次の手順を使用して、<xref:System.Windows.Forms.ToolStrip>のうち、<xref:System.Windows.Forms.ToolStripContainer>からフォームにします。</span><span class="sxs-lookup"><span data-stu-id="22b88-103">Use the following procedure to move a <xref:System.Windows.Forms.ToolStrip> out of a <xref:System.Windows.Forms.ToolStripContainer> onto a form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="22b88-104">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="22b88-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="22b88-105">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="22b88-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="22b88-106">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22b88-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a><span data-ttu-id="22b88-107">ToolStrip を ToolStripContainer からフォームに不足を移動するには</span><span class="sxs-lookup"><span data-stu-id="22b88-107">To move a ToolStrip out of a ToolStripContainer onto a form</span></span>  
  
1.  <span data-ttu-id="22b88-108"><xref:System.Windows.Forms.ToolStrip> を選択します。</span><span class="sxs-lookup"><span data-stu-id="22b88-108">Select the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
2.  <span data-ttu-id="22b88-109">切り取り、<xref:System.Windows.Forms.ToolStrip>で ctrl キーを押しながら X キーを押すかを右クリックし、<xref:System.Windows.Forms.ToolStrip>選択**切り取り**コンテキスト メニューからです。</span><span class="sxs-lookup"><span data-stu-id="22b88-109">Cut the <xref:System.Windows.Forms.ToolStrip> by pressing CTRL+X, or right-click the <xref:System.Windows.Forms.ToolStrip> and choose **Cut** from the context menu.</span></span>  
  
3.  <span data-ttu-id="22b88-110">フォームを選択します。</span><span class="sxs-lookup"><span data-stu-id="22b88-110">Select the form.</span></span>  
  
4.  <span data-ttu-id="22b88-111">貼り付け、<xref:System.Windows.Forms.ToolStrip>で ctrl キーを押しながら V キーを押すかを選択して**貼り付け**から、**編集**メニュー。</span><span class="sxs-lookup"><span data-stu-id="22b88-111">Paste the <xref:System.Windows.Forms.ToolStrip> by pressing CTRL+V, or choose **Paste** from the **Edit** menu.</span></span>  
  
5.  <span data-ttu-id="22b88-112">設定、<xref:System.Windows.Forms.ToolStrip.Dock%2A>のプロパティ、<xref:System.Windows.Forms.ToolStrip>に**上部**です。</span><span class="sxs-lookup"><span data-stu-id="22b88-112">Set the <xref:System.Windows.Forms.ToolStrip.Dock%2A> property of the <xref:System.Windows.Forms.ToolStrip> to **Top**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22b88-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="22b88-113">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 [<span data-ttu-id="22b88-114">ToolStrip コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="22b88-114">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
