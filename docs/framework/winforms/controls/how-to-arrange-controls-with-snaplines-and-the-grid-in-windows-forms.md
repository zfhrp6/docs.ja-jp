---
title: "方法 : コントロールを Windows フォームのスナップ線とグリッドを使用して配置する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: GridSize
helpviewer_keywords:
- snap to grid [Windows Forms], Windows Forms Designer
- Windows Forms, grid options in designer
- controls [Windows Forms], aligning
ms.assetid: bb54bce5-880f-4a36-af68-8cf92058dc1c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ab199f390fa6a704ad3b3d2a17387d034cf2e57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-arrange-controls-with-snaplines-and-the-grid-in-windows-forms"></a><span data-ttu-id="d1612-102">方法 : コントロールを Windows フォームのスナップ線とグリッドを使用して配置する</span><span class="sxs-lookup"><span data-stu-id="d1612-102">How to: Arrange Controls with Snaplines and the Grid in Windows Forms</span></span>
<span data-ttu-id="d1612-103">レイアウト機能を使用して[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]フォーム上のコントロールの配置場所を正確に指定できます。</span><span class="sxs-lookup"><span data-stu-id="d1612-103">Using the layout features of [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], you can precisely direct where controls are placed on a form.</span></span> <span data-ttu-id="d1612-104">行と、Windows フォーム デザイナーのグリッドの列に、コントロールをフォームに追加し、フォームを移動したかを自動的にアラインできます。 またはスナップ線機能を使用してコントロールを揃えることができます。</span><span class="sxs-lookup"><span data-stu-id="d1612-104">Controls added to a form or moved on a form can be automatically aligned to the rows and columns of the Windows Forms Designer's grid, or you can align controls by using the snaplines feature.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1612-105">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d1612-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d1612-106">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1612-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d1612-107">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1612-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-snap-all-controls-to-the-grid"></a><span data-ttu-id="d1612-108">すべてのコントロールをグリッドにスナップするには</span><span class="sxs-lookup"><span data-stu-id="d1612-108">To snap all controls to the grid</span></span>  
  
-   <span data-ttu-id="d1612-109">選択、 **SnapToGrid** Windows フォーム デザイナーでレイアウト モード**オプション** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="d1612-109">Select the **SnapToGrid** layout mode in the Windows Forms Designer **Options** dialog box.</span></span>  
  
     <span data-ttu-id="d1612-110">詳細については、次を参照してください。 [[全般]、[Windows フォーム デザイナー、オプション] ダイアログ ボックス](http://msdn.microsoft.com/en-us/8dd170af-72f0-4212-b04b-034ceee92834)です。</span><span class="sxs-lookup"><span data-stu-id="d1612-110">For more information, see [General, Windows Forms Designer, Options Dialog Box](http://msdn.microsoft.com/en-us/8dd170af-72f0-4212-b04b-034ceee92834).</span></span> <span data-ttu-id="d1612-111">すべてのコントロールでは、グリッド上の点に沿った自体今すぐ揃えます。</span><span class="sxs-lookup"><span data-stu-id="d1612-111">All controls now align themselves along the points on the grid.</span></span>  
  
     <span data-ttu-id="d1612-112">個々 のコントロールをグリッドをスナップするには、それらの場所でロックできます。</span><span class="sxs-lookup"><span data-stu-id="d1612-112">You can snap individual controls to the grid by locking them in place.</span></span> <span data-ttu-id="d1612-113">ただし、ロックされているときに移動したりできないのサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="d1612-113">However, while they are locked, they cannot be moved or resized.</span></span> <span data-ttu-id="d1612-114">コントロールのロックの詳細については、次を参照してください。[する方法: Windows フォーム コントロールのロック](../../../../docs/framework/winforms/controls/how-to-lock-controls-to-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="d1612-114">For more information about locking controls, see [How to: Lock Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-lock-controls-to-windows-forms.md).</span></span>  
  
### <a name="to-align-controls-using-snaplines"></a><span data-ttu-id="d1612-115">スナップ線を使用してコントロールを配置するには</span><span class="sxs-lookup"><span data-stu-id="d1612-115">To align controls using snaplines</span></span>  
  
-   <span data-ttu-id="d1612-116">選択、**スナップ**Windows フォーム デザイナーでレイアウト モード**オプション** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="d1612-116">Select the **SnapLines** layout mode in the Windows Forms Designer **Options** dialog box.</span></span>  
  
     <span data-ttu-id="d1612-117">詳細については、次を参照してください。[チュートリアル: Windows フォームを使用するスナップ線上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)です。</span><span class="sxs-lookup"><span data-stu-id="d1612-117">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span> <span data-ttu-id="d1612-118">スナップ線を使用して、フォーム上のコントロールを配置したりするようになりましたことができます。</span><span class="sxs-lookup"><span data-stu-id="d1612-118">You can now use snaplines to align and arrange controls on your form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1612-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="d1612-119">See Also</span></span>  
 [<span data-ttu-id="d1612-120">一般に、Windows フォーム デザイナー、オプション ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="d1612-120">General, Windows Forms Designer, Options Dialog Box</span></span>](http://msdn.microsoft.com/en-us/8dd170af-72f0-4212-b04b-034ceee92834)  
 [<span data-ttu-id="d1612-121">チュートリアル: スナップ線を使用した Windows フォーム上のコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="d1612-121">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="d1612-122">Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="d1612-122">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="d1612-123">方法: Windows フォームにコントロールを追加する</span><span class="sxs-lookup"><span data-stu-id="d1612-123">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [<span data-ttu-id="d1612-124">Windows フォームでのコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="d1612-124">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="d1612-125">各 Windows フォーム コントロールのラベル設定とショートカットの作成</span><span class="sxs-lookup"><span data-stu-id="d1612-125">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="d1612-126">Windows フォームで使用するコントロール</span><span class="sxs-lookup"><span data-stu-id="d1612-126">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="d1612-127">Windows フォーム コントロールの機能別一覧</span><span class="sxs-lookup"><span data-stu-id="d1612-127">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
