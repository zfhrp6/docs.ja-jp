---
title: '方法 : ToolStrip コントロールにトグル ボタンを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
ms.openlocfilehash: a04d531433273328c2d8eb0c5ef614f08c33952a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530382"
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a><span data-ttu-id="2d618-102">方法 : ToolStrip コントロールにトグル ボタンを作成する</span><span class="sxs-lookup"><span data-stu-id="2d618-102">How to: Create Toggle Buttons in ToolStrip Controls</span></span>
<span data-ttu-id="2d618-103">トグル ボタンをクリックすると、くぼみ表示され、ユーザーがボタンをもう一度クリックするまで、くぼみの外観を保持します。</span><span class="sxs-lookup"><span data-stu-id="2d618-103">When a user clicks a toggle button, it appears sunken and retains the sunken appearance until the user clicks the button again.</span></span>  
  
### <a name="to-create-a-toggling-toolstripbutton"></a><span data-ttu-id="2d618-104">切り替え ToolStripButton を作成するには</span><span class="sxs-lookup"><span data-stu-id="2d618-104">To create a toggling ToolStripButton</span></span>  
  
-   <span data-ttu-id="2d618-105">次のコード例のようなコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="2d618-105">Use code such as the following code example.</span></span> <span data-ttu-id="2d618-106">このコードは、フォームが含まれている前提としています。、<xref:System.Windows.Forms.ToolStrip>コントロール、およびその<xref:System.Windows.Forms.ToolStrip.Items%2A>コレクションが含まれています、<xref:System.Windows.Forms.ToolStripButton>と呼ばれる`toolStripButton1`です。</span><span class="sxs-lookup"><span data-stu-id="2d618-106">This code assumes that your form contains a <xref:System.Windows.Forms.ToolStrip> control, and that its <xref:System.Windows.Forms.ToolStrip.Items%2A> collection contains a <xref:System.Windows.Forms.ToolStripButton> called `toolStripButton1`.</span></span> <span data-ttu-id="2d618-107">呼ばれるイベント ハンドラーを設定することも想定`toolStripButton1_CheckedChanged`です。</span><span class="sxs-lookup"><span data-stu-id="2d618-107">It also assumes that you have an event handler called `toolStripButton1_CheckedChanged`.</span></span>  
  
    ```vb  
    toolStripButton1.CheckOnClick = True  
    toolStripButton1.CheckedChanged AddressOf _  
    EventHandler(toolStripButton1_CheckedChanged);  
    ```  
  
    ```csharp  
    toolStripButton1.CheckOnClick = true;  
    toolStripButton1.CheckedChanged += new _  
    EventHandler(toolStripButton1_CheckedChanged);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2d618-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d618-108">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripButton>  
 [<span data-ttu-id="2d618-109">ToolStrip コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="2d618-109">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
