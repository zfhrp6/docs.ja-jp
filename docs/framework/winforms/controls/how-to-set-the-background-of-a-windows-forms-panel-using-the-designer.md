---
title: "方法 : デザイナーを使って Windows フォーム パネルの背景を設定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 56cb6f7ee9a7c52ff4763c0c310d679e4889dbd2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a><span data-ttu-id="eb6fd-102">方法 : デザイナーを使って Windows フォーム パネルの背景を設定する</span><span class="sxs-lookup"><span data-stu-id="eb6fd-102">How to: Set the Background of a Windows Forms Panel Using the Designer</span></span>
<span data-ttu-id="eb6fd-103">Windows フォーム<xref:System.Windows.Forms.Panel>コントロールは、背景色と背景イメージの両方を表示できます。</span><span class="sxs-lookup"><span data-stu-id="eb6fd-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="eb6fd-104"><xref:System.Windows.Forms.Control.BackColor%2A>プロパティ パネルで、ラベルなどに含まれ、ラジオ ボタン コントロールの背景色を設定します。</span><span class="sxs-lookup"><span data-stu-id="eb6fd-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for controls that are contained in the panel, such as labels and radio buttons.</span></span> <span data-ttu-id="eb6fd-105">場合、<xref:System.Windows.Forms.Control.BackgroundImage%2A>プロパティが設定されていない、<xref:System.Windows.Forms.Control.BackColor%2A>選択範囲がパネルのすべてを入力します。</span><span class="sxs-lookup"><span data-stu-id="eb6fd-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill all of the panel.</span></span> <span data-ttu-id="eb6fd-106">場合、<xref:System.Windows.Forms.Control.BackgroundImage%2A>プロパティが設定されて、イメージがパネルに含まれているコントロールの内側に表示されます。</span><span class="sxs-lookup"><span data-stu-id="eb6fd-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the controls that are contained in the panel.</span></span>  
  
 <span data-ttu-id="eb6fd-107">次の手順が必要です、 **Windows アプリケーション**を含むフォームを使用してプロジェクト、<xref:System.Windows.Forms.Panel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="eb6fd-107">The following procedure requires a **Windows Application** project with a form that contains a <xref:System.Windows.Forms.Panel> control.</span></span> <span data-ttu-id="eb6fd-108">このようなプロジェクトを設定する方法については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="eb6fd-108">For information about how to set up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb6fd-109">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="eb6fd-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="eb6fd-110">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb6fd-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="eb6fd-111">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb6fd-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-the-background-in-the-windows-forms-designer"></a><span data-ttu-id="eb6fd-112">Windows フォーム デザイナーの背景を設定するには</span><span class="sxs-lookup"><span data-stu-id="eb6fd-112">To set the background in the Windows Forms Designer</span></span>  
  
1.  <span data-ttu-id="eb6fd-113"><xref:System.Windows.Forms.Panel> コントロールを選択します。</span><span class="sxs-lookup"><span data-stu-id="eb6fd-113">Select the <xref:System.Windows.Forms.Panel> control.</span></span>  
  
2.  <span data-ttu-id="eb6fd-114">**プロパティ** ウィンドウで、矢印ボタンをクリックして、 <xref:System.Windows.Forms.Control.BackColor%2A> 3 つのタブとウィンドウを表示するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="eb6fd-114">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackColor%2A> property to display a window with three tabs.</span></span>  
  
3.  <span data-ttu-id="eb6fd-115">選択、**カスタム** タブの色のパレットを表示します。</span><span class="sxs-lookup"><span data-stu-id="eb6fd-115">Select the **Custom** tab to display a palette of colors.</span></span>  
  
4.  <span data-ttu-id="eb6fd-116">選択、 **Web**または**システム** タブの色の定義済みの名前の一覧を表示して、色を選択します。</span><span class="sxs-lookup"><span data-stu-id="eb6fd-116">Select the **Web** or **System** tab to display a list of predefined names for colors, and then select a color.</span></span>  
  
5.  <span data-ttu-id="eb6fd-117">**プロパティ** ウィンドウで、矢印ボタンをクリックして、<xref:System.Windows.Forms.Control.BackgroundImage%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="eb6fd-117">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span>  
  
6.  <span data-ttu-id="eb6fd-118">**開く** ダイアログ ボックスで、表示するファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="eb6fd-118">In the **Open** dialog box, select the file that you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb6fd-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb6fd-119">See Also</span></span>  
 <xref:System.Windows.Forms.Control.BackColor%2A>  
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>  
 [<span data-ttu-id="eb6fd-120">Panel コントロール</span><span class="sxs-lookup"><span data-stu-id="eb6fd-120">Panel Control</span></span>](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)  
 [<span data-ttu-id="eb6fd-121">Panel コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="eb6fd-121">Panel Control Overview</span></span>](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [<span data-ttu-id="eb6fd-122">方法: デザイナーを使用して Windows フォーム Panel コントロールでコントロールをグループ化する</span><span class="sxs-lookup"><span data-stu-id="eb6fd-122">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)
