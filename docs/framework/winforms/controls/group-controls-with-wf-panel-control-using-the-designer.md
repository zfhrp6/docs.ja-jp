---
title: "方法 : デザイナーを使用して Windows フォーム Panel コントロールでコントロールをグループ化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b1d4a49f36ac294199871075a04b7e682bd5613b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a><span data-ttu-id="bb38f-102">方法 : デザイナーを使用して Windows フォーム Panel コントロールでコントロールをグループ化する</span><span class="sxs-lookup"><span data-stu-id="bb38f-102">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>
<span data-ttu-id="bb38f-103">Windows フォーム<xref:System.Windows.Forms.Panel>コントロールを使用すると、その他のコントロールをグループ化します。</span><span class="sxs-lookup"><span data-stu-id="bb38f-103">Windows Forms <xref:System.Windows.Forms.Panel> controls are used to group other controls.</span></span> <span data-ttu-id="bb38f-104">コントロールをグループ化の 3 つの理由があります。</span><span class="sxs-lookup"><span data-stu-id="bb38f-104">There are three reasons to group controls.</span></span> <span data-ttu-id="bb38f-105">視覚的にわかりやすいユーザー インターフェイスです。 関連するフォーム要素のグループ化もう 1 つは、プログラムによるグループ化、ラジオ ボタンの例を示します。最後は、デザイン時に単位として、コントロールを移動です。</span><span class="sxs-lookup"><span data-stu-id="bb38f-105">One is visual grouping of related form elements for a clear user interface; another is programmatic grouping, of radio buttons for example; the last is for moving the controls as a unit at design time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb38f-106">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="bb38f-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="bb38f-107">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb38f-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="bb38f-108">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb38f-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="bb38f-109">コントロールのグループを作成するには</span><span class="sxs-lookup"><span data-stu-id="bb38f-109">To create a group of controls</span></span>  
  
1.  <span data-ttu-id="bb38f-110">ドラッグ、<xref:System.Windows.Forms.Panel>から制御、 **Windows フォーム**からフォームにツールボックス タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb38f-110">Drag a <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab of the Toolbox onto a form.</span></span>  
  
2.  <span data-ttu-id="bb38f-111">パネル内の各描画、パネルには、その他のコントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="bb38f-111">Add other controls to the panel, drawing each inside the panel.</span></span>  
  
     <span data-ttu-id="bb38f-112">パネルにする既存のコントロールがあれば、すべてのコントロールを選択して、それらを選択、クリップボードに切り取れません、<xref:System.Windows.Forms.Panel>を制御して、パネルに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="bb38f-112">If you have existing controls that you want to enclose in a panel, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.Panel> control, and then paste them into the panel.</span></span> <span data-ttu-id="bb38f-113">パネルにドラッグすることもできます。</span><span class="sxs-lookup"><span data-stu-id="bb38f-113">You can also drag them into the panel.</span></span>  
  
3.  <span data-ttu-id="bb38f-114">(省略可能)パネルに罫線を追加する場合は、設定、<xref:System.Windows.Forms.BorderStyle>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="bb38f-114">(Optional) If you want to add a border to a panel, set its <xref:System.Windows.Forms.BorderStyle> property.</span></span> <span data-ttu-id="bb38f-115">次の 3 つの選択肢があります: <xref:System.Windows.Forms.BorderStyle.Fixed3D>、 <xref:System.Windows.Forms.BorderStyle.FixedSingle>、および<xref:System.Windows.Forms.BorderStyle.None>です。</span><span class="sxs-lookup"><span data-stu-id="bb38f-115">There are three choices: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, and <xref:System.Windows.Forms.BorderStyle.None>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb38f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb38f-116">See Also</span></span>  
 [<span data-ttu-id="bb38f-117">Panel コントロール</span><span class="sxs-lookup"><span data-stu-id="bb38f-117">Panel Control</span></span>](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)  
 [<span data-ttu-id="bb38f-118">Panel コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="bb38f-118">Panel Control Overview</span></span>](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [<span data-ttu-id="bb38f-119">方法: パネルの背景を設定する</span><span class="sxs-lookup"><span data-stu-id="bb38f-119">How to: Set the Background of a Panel</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md)
