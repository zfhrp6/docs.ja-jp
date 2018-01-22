---
title: "方法 : 既存のコントロールを別の親に再配置する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 26998c002591850c0af3c265ae88b10657343787
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="d9e12-102">方法 : 既存のコントロールを別の親に再配置する</span><span class="sxs-lookup"><span data-stu-id="d9e12-102">How to: Reassign Existing Controls to a Different Parent</span></span>
<span data-ttu-id="d9e12-103">フォームに存在するコントロールを新しいコンテナー コントロールに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="d9e12-103">You can assign controls that exist on your form to a new container control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d9e12-104">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d9e12-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d9e12-105">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9e12-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d9e12-106">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9e12-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="d9e12-107">既存のコントロールを別の親に再配置するには</span><span class="sxs-lookup"><span data-stu-id="d9e12-107">To reassign existing controls to a different parent</span></span>  
  
1.  <span data-ttu-id="d9e12-108"><xref:System.Windows.Forms.Button> [ツールボックス] **から 3 つの** コントロールをフォームにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="d9e12-108">Drag three <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto the form.</span></span>  
  
     <span data-ttu-id="d9e12-109">これらを互いに近づけて配置しますが、整列はさせません。</span><span class="sxs-lookup"><span data-stu-id="d9e12-109">Position them near to each other, but leave them unaligned.</span></span>  
  
2.  <span data-ttu-id="d9e12-110">**[ツールボックス]**で <xref:System.Windows.Forms.FlowLayoutPanel> コントロール アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9e12-110">In the **Toolbox**, click the <xref:System.Windows.Forms.FlowLayoutPanel> control icon.</span></span>  
  
     <span data-ttu-id="d9e12-111">アイコンはフォームにドラッグしないでください。</span><span class="sxs-lookup"><span data-stu-id="d9e12-111">Do not drag the icon onto the form.</span></span>  
  
3.  <span data-ttu-id="d9e12-112">マウス ポインターを 3 つの <xref:System.Windows.Forms.Button> コントロールに近づけます。</span><span class="sxs-lookup"><span data-stu-id="d9e12-112">Move the mouse pointer close to the three <xref:System.Windows.Forms.Button> controls.</span></span>  
  
     <span data-ttu-id="d9e12-113">ポインターが <xref:System.Windows.Forms.FlowLayoutPanel> コントロール アイコンが付いた十字カーソルに変わります。</span><span class="sxs-lookup"><span data-stu-id="d9e12-113">The pointer changes to a crosshair with the <xref:System.Windows.Forms.FlowLayoutPanel> control icon attached.</span></span>  
  
4.  <span data-ttu-id="d9e12-114">マウス ボタンを押したままにします。</span><span class="sxs-lookup"><span data-stu-id="d9e12-114">Click and hold the mouse button.</span></span>  
  
5.  <span data-ttu-id="d9e12-115">マウス ポインターをドラッグして、 <xref:System.Windows.Forms.FlowLayoutPanel> コントロールのアウトラインを描画します。</span><span class="sxs-lookup"><span data-stu-id="d9e12-115">Drag the mouse pointer to draw the outline of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
6.  <span data-ttu-id="d9e12-116">3 つの <xref:System.Windows.Forms.Button> コントロールを囲むようにアウトラインを描画します。</span><span class="sxs-lookup"><span data-stu-id="d9e12-116">Draw the outline around the three <xref:System.Windows.Forms.Button> controls.</span></span>  
  
7.  <span data-ttu-id="d9e12-117">マウスのボタンを離します。</span><span class="sxs-lookup"><span data-stu-id="d9e12-117">Release the mouse button.</span></span>  
  
     <span data-ttu-id="d9e12-118">これで、3 つの <xref:System.Windows.Forms.Button> コントロールが <xref:System.Windows.Forms.FlowLayoutPanel> コントロールに挿入されました。</span><span class="sxs-lookup"><span data-stu-id="d9e12-118">The three <xref:System.Windows.Forms.Button> controls are now inserted into the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9e12-119">参照</span><span class="sxs-lookup"><span data-stu-id="d9e12-119">See Also</span></span>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [<span data-ttu-id="d9e12-120">Windows フォームでのコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="d9e12-120">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="d9e12-121">チュートリアル: TableLayoutPanel を使用した Windows フォーム上のコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="d9e12-121">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="d9e12-122">チュートリアル: スナップ線を使用した Windows フォーム上のコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="d9e12-122">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
