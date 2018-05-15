---
title: '方法 : Windows フォーム GroupBox コントロールを使用してコントロールをグループ化する'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: 718367e9da9efda20c79fbff3bd2f14f11c96ee1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a><span data-ttu-id="506d0-102">方法 : Windows フォーム GroupBox コントロールを使用してコントロールをグループ化する</span><span class="sxs-lookup"><span data-stu-id="506d0-102">How to: Group Controls with the Windows Forms GroupBox Control</span></span>
<span data-ttu-id="506d0-103">Windows フォーム<xref:System.Windows.Forms.GroupBox>コントロールを使用すると、その他のコントロールをグループ化します。</span><span class="sxs-lookup"><span data-stu-id="506d0-103">Windows Forms <xref:System.Windows.Forms.GroupBox> controls are used to group other controls.</span></span> <span data-ttu-id="506d0-104">グループ コントロールに次の 3 つの理由があります。</span><span class="sxs-lookup"><span data-stu-id="506d0-104">There are three reasons to group controls:</span></span>  
  
-   <span data-ttu-id="506d0-105">わかりやすいユーザー インターフェイスの関連するフォーム要素のビジュアル グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="506d0-105">To create a visual grouping of related form elements for a clear user interface.</span></span>  
  
-   <span data-ttu-id="506d0-106">プログラムによるグループ化 (たとえばのラジオ ボタン) を作成します。</span><span class="sxs-lookup"><span data-stu-id="506d0-106">To create programmatic grouping (of radio buttons, for example).</span></span>  
  
-   <span data-ttu-id="506d0-107">単位として、コントロールをデザイン時に移動します。</span><span class="sxs-lookup"><span data-stu-id="506d0-107">For moving the controls as a unit at design time.</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="506d0-108">コントロールのグループを作成するには</span><span class="sxs-lookup"><span data-stu-id="506d0-108">To create a group of controls</span></span>  
  
1.  <span data-ttu-id="506d0-109">描画、<xref:System.Windows.Forms.GroupBox>フォーム上のコントロールです。</span><span class="sxs-lookup"><span data-stu-id="506d0-109">Draw a <xref:System.Windows.Forms.GroupBox> control on a form.</span></span>  
  
2.  <span data-ttu-id="506d0-110">グループ ボックスで各グループ ボックスの内部を描画するには、他のコントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="506d0-110">Add other controls to the group box, drawing each inside the group box.</span></span>  
  
     <span data-ttu-id="506d0-111">グループ ボックス内で囲む必要のある既存のコントロールを使っている場合は、すべてのコントロールを選択して、それらを選択、クリップボードに切り取れません、<xref:System.Windows.Forms.GroupBox>制御、およびグループ ボックスに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="506d0-111">If you have existing controls that you want to enclose in a group box, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.GroupBox> control, and then paste them into the group box.</span></span> <span data-ttu-id="506d0-112">グループ ボックスにドラッグすることもできます。</span><span class="sxs-lookup"><span data-stu-id="506d0-112">You can also drag them into the group box.</span></span>  
  
3.  <span data-ttu-id="506d0-113">設定、<xref:System.Windows.Forms.GroupBox.Text%2A>グループ ボックスに適切なキャプションのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="506d0-113">Set the <xref:System.Windows.Forms.GroupBox.Text%2A> property of the group box to an appropriate caption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="506d0-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="506d0-114">See Also</span></span>  
 <xref:System.Windows.Forms.GroupBox>  
 [<span data-ttu-id="506d0-115">GroupBox コントロール</span><span class="sxs-lookup"><span data-stu-id="506d0-115">GroupBox Control</span></span>](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)
