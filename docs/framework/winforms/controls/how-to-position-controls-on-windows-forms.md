---
title: "方法 : Windows フォーム上のコントロールを位置設定する"
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
- cpp
f1_keywords:
- Location
- Location.Y
- Location.X
helpviewer_keywords:
- controls [Windows Forms]
- controls [Windows Forms], moving
- snaplines
- controls [Windows Forms], positioning
ms.assetid: 4693977e-34a4-4f19-8221-68c3120c2b2b
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4519be86d83fce5afc7410c9f76591158ed71cb6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="e0eb6-102">方法 : Windows フォーム上のコントロールを位置設定する</span><span class="sxs-lookup"><span data-stu-id="e0eb6-102">How to: Position Controls on Windows Forms</span></span>
<span data-ttu-id="e0eb6-103">コントロールの位置、Windows フォーム デザイナーを使用するかを指定する、<xref:System.Windows.Forms.Control.Location%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="e0eb6-103">To position controls, use the Windows Forms Designer, or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e0eb6-104">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e0eb6-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e0eb6-105">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e0eb6-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e0eb6-106">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0eb6-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="e0eb6-107">Windows フォーム デザイナーのデザイン画面上のコントロールを配置するには</span><span class="sxs-lookup"><span data-stu-id="e0eb6-107">To position a control on the design surface of the Windows Forms Designer</span></span>  
  
-   <span data-ttu-id="e0eb6-108">マウスを使用して適切な位置にコントロールをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e0eb6-108">Drag the control to the appropriate location with the mouse.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e0eb6-109">コントロールを選択しより正確に配置する矢印の付いたがキーに移動します。</span><span class="sxs-lookup"><span data-stu-id="e0eb6-109">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="e0eb6-110">また、*スナップ線*をフォームに正確にコントロールを配置するために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e0eb6-110">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="e0eb6-111">詳細については、次を参照してください。[チュートリアル: Windows フォームを使用するスナップ線上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)です。</span><span class="sxs-lookup"><span data-stu-id="e0eb6-111">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>  
  
### <a name="to-position-a-control-using-the-properties-window"></a><span data-ttu-id="e0eb6-112">[プロパティ] ウィンドウを使用してコントロールを配置するには</span><span class="sxs-lookup"><span data-stu-id="e0eb6-112">To position a control using the Properties window</span></span>  
  
1.  <span data-ttu-id="e0eb6-113">移動するコントロールをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e0eb6-113">Click the control you want to position.</span></span>  
  
2.  <span data-ttu-id="e0eb6-114">**プロパティ**ウィンドウで、値を入力、<xref:System.Windows.Forms.Control.Location%2A>プロパティ、コントロール コンテナー内の位置をコンマで区切って指定します。</span><span class="sxs-lookup"><span data-stu-id="e0eb6-114">In the **Properties** window, type values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>  
  
     <span data-ttu-id="e0eb6-115">最初の数値 (X) は、コンテナーの左端からの距離2 番目の数字 (Y) は、ピクセル単位で、コンテナー領域の上端からの距離です。</span><span class="sxs-lookup"><span data-stu-id="e0eb6-115">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e0eb6-116">展開することができます、<xref:System.Windows.Forms.Control.Location%2A>プロパティ型を**X**と**Y**個別の値します。</span><span class="sxs-lookup"><span data-stu-id="e0eb6-116">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>  
  
### <a name="to-position-a-control-programmatically"></a><span data-ttu-id="e0eb6-117">コントロールをプログラムで配置するには</span><span class="sxs-lookup"><span data-stu-id="e0eb6-117">To position a control programmatically</span></span>  
  
1.  <span data-ttu-id="e0eb6-118">設定、<xref:System.Windows.Forms.Control.Location%2A>するコントロールのプロパティ、<xref:System.Drawing.Point>です。</span><span class="sxs-lookup"><span data-stu-id="e0eb6-118">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>  
  
    ```vb  
    Button1.Location = New Point(100, 100)  
    ```  
  
    ```csharp  
    button1.Location = new Point(100, 100);  
    ```  
  
    ```cpp  
    button1->Location = Point(100, 100);  
    ```  
  
2.  <span data-ttu-id="e0eb6-119">コントロールの位置の X 座標の変更を使用して、<xref:System.Windows.Forms.Control.Left%2A>サブプロパティです。</span><span class="sxs-lookup"><span data-stu-id="e0eb6-119">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>  
  
    ```vb  
    Button1.Left = 300  
    ```  
  
    ```csharp  
    button1.Left = 300;  
    ```  
  
    ```cpp  
    button1->Left = 300;  
    ```  
  
### <a name="to-increment-a-controls-location-programmatically"></a><span data-ttu-id="e0eb6-120">コントロールの位置をプログラムでインクリメントするには</span><span class="sxs-lookup"><span data-stu-id="e0eb6-120">To increment a control's location programmatically</span></span>  
  
1.  <span data-ttu-id="e0eb6-121">設定、<xref:System.Windows.Forms.Control.Left%2A>サブプロパティをコントロールの X 座標をインクリメントします。</span><span class="sxs-lookup"><span data-stu-id="e0eb6-121">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>  
  
    ```vb  
    Button1.Left += 200  
    ```  
  
    ```csharp  
    button1.Left += 200;  
    ```  
  
    ```cpp  
    button1->Left += 200;  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="e0eb6-122">使用して、<xref:System.Windows.Forms.Control.Location%2A>コントロールの X と Y を設定するプロパティを同時に配置します。</span><span class="sxs-lookup"><span data-stu-id="e0eb6-122">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="e0eb6-123">位置を個別に設定するには、使用、コントロールの<xref:System.Windows.Forms.Control.Left%2A>(**X**) または<xref:System.Windows.Forms.Control.Top%2A>(**Y**) サブプロパティです。</span><span class="sxs-lookup"><span data-stu-id="e0eb6-123">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="e0eb6-124">X および Y 座標を暗黙的に設定してはいけません、<xref:System.Drawing.Point>この構造体には、ボタンの座標のコピーが含まれているため、ボタンの場所を表す構造です。</span><span class="sxs-lookup"><span data-stu-id="e0eb6-124">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0eb6-125">参照</span><span class="sxs-lookup"><span data-stu-id="e0eb6-125">See Also</span></span>  
 [<span data-ttu-id="e0eb6-126">Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="e0eb6-126">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="e0eb6-127">チュートリアル: スナップ線を使用した Windows フォーム上のコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="e0eb6-127">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="e0eb6-128">チュートリアル: TableLayoutPanel を使用した Windows フォーム上のコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="e0eb6-128">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="e0eb6-129">チュートリアル: FlowLayoutPanel を使用した Windows フォーム上のコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="e0eb6-129">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [<span data-ttu-id="e0eb6-130">Windows フォームでのコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="e0eb6-130">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="e0eb6-131">各 Windows フォーム コントロールのラベル設定とショートカットの作成</span><span class="sxs-lookup"><span data-stu-id="e0eb6-131">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="e0eb6-132">Windows フォームで使用するコントロール</span><span class="sxs-lookup"><span data-stu-id="e0eb6-132">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="e0eb6-133">Windows フォーム コントロールの機能別一覧</span><span class="sxs-lookup"><span data-stu-id="e0eb6-133">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)  
 [<span data-ttu-id="e0eb6-134">方法: Windows フォームの画面位置を設定</span><span class="sxs-lookup"><span data-stu-id="e0eb6-134">How to: Set the Screen Location of Windows Forms</span></span>](http://msdn.microsoft.com/library/cb023ab7-dea7-4284-9aa6-8c03c59b60c6)
