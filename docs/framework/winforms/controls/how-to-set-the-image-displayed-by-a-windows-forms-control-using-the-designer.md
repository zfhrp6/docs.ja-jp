---
title: "方法 : デザイナーを使用して Windows フォーム コントロールによって表示されるイメージを設定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
- setting images [Windows Forms], Windows Forms controls
ms.assetid: ae80d07a-e469-4251-90ca-df71f5852454
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2eff8d302b6e65f386835f744965f3754c3e3ffb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control-using-the-designer"></a><span data-ttu-id="bff3e-102">方法 : デザイナーを使用して Windows フォーム コントロールによって表示されるイメージを設定する</span><span class="sxs-lookup"><span data-stu-id="bff3e-102">How to: Set the Image Displayed by a Windows Forms Control Using the Designer</span></span>
<span data-ttu-id="bff3e-103">いくつかの Windows フォーム コントロールは、イメージを表示できます。</span><span class="sxs-lookup"><span data-stu-id="bff3e-103">Several Windows Forms controls can display images.</span></span> <span data-ttu-id="bff3e-104">イメージをボタン上のフロッピー ディスク アイコンなど、コントロールの目的を明確にするアイコンがあります、**保存**コマンド。</span><span class="sxs-lookup"><span data-stu-id="bff3e-104">The image can be an icon that clarifies the purpose of the control, such as a disk icon on a button denoting the **Save** command.</span></span> <span data-ttu-id="bff3e-105">コントロールの外観を与えるように背景画像の代わりに、アイコンもあります。</span><span class="sxs-lookup"><span data-stu-id="bff3e-105">Alternatively, the icon can be a background image to give the control the appearance you want.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bff3e-106">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="bff3e-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="bff3e-107">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bff3e-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="bff3e-108">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bff3e-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-the-image-displayed-by-a-control"></a><span data-ttu-id="bff3e-109">コントロールによって表示されるイメージを設定するには</span><span class="sxs-lookup"><span data-stu-id="bff3e-109">To set the image displayed by a control</span></span>  
  
1.  <span data-ttu-id="bff3e-110">**プロパティ**ウィンドウで、**イメージ**または**BackgroundImage**コントロールのプロパティには、省略記号ボタン (をクリックして</span><span class="sxs-lookup"><span data-stu-id="bff3e-110">In the **Properties** window, select the **Image** or **BackgroundImage** property of the control, then click the ellipsis button (</span></span>  
  
     <span data-ttu-id="bff3e-111">![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")</span><span class="sxs-lookup"><span data-stu-id="bff3e-111">![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")</span></span>  
  
     <span data-ttu-id="bff3e-112">) を表示する、 **[リソースの**] ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="bff3e-112">) to display the **Select Resource** dialog box.</span></span>  
  
2.  <span data-ttu-id="bff3e-113">表示するイメージを選択します。</span><span class="sxs-lookup"><span data-stu-id="bff3e-113">Select the image you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bff3e-114">参照</span><span class="sxs-lookup"><span data-stu-id="bff3e-114">See Also</span></span>  
 <xref:System.Drawing.Image.FromFile%2A>  
 <xref:System.Drawing.Image>  
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>  
 [<span data-ttu-id="bff3e-115">各 Windows フォーム コントロールのラベル設定とショートカットの作成</span><span class="sxs-lookup"><span data-stu-id="bff3e-115">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
