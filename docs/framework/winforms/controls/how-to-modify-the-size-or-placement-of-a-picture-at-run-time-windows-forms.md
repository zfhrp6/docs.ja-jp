---
title: "方法 : 実行時にピクチャのサイズまたは配置を変更する (Windows フォーム)"
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
helpviewer_keywords:
- images [Windows Forms], controlling placement in PictureBox control [Windows Forms]
- examples [Windows Forms], PictureBox control
- PictureBox control [Windows Forms], picture size and alignment
- pictures [Windows Forms], controlling placement in PictureBox control [Windows Forms]
ms.assetid: d0b332a3-fae2-4891-957c-dc3e17743326
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: df67871b0b133297a6f53ff9e4a42c7630a5f56d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a><span data-ttu-id="6f20f-102">方法 : 実行時にピクチャのサイズまたは配置を変更する (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="6f20f-102">How to: Modify the Size or Placement of a Picture at Run Time (Windows Forms)</span></span>
<span data-ttu-id="6f20f-103">Windows フォームを使用する場合<xref:System.Windows.Forms.PictureBox>コントロール、フォームで設定することができます、<xref:System.Windows.Forms.PictureBox.SizeMode%2A>のプロパティ。</span><span class="sxs-lookup"><span data-stu-id="6f20f-103">If you use the Windows Forms <xref:System.Windows.Forms.PictureBox> control on a form, you can set the <xref:System.Windows.Forms.PictureBox.SizeMode%2A> property on it to:</span></span>  
  
-   <span data-ttu-id="6f20f-104">画像の左上隅にコントロールの左上隅を揃える</span><span class="sxs-lookup"><span data-stu-id="6f20f-104">Align the picture's upper left corner with the control's upper left corner</span></span>  
  
-   <span data-ttu-id="6f20f-105">コントロール内で画像を中央揃え</span><span class="sxs-lookup"><span data-stu-id="6f20f-105">Center the picture within the control</span></span>  
  
-   <span data-ttu-id="6f20f-106">表示される画像に合わせてコントロールのサイズを調整します。</span><span class="sxs-lookup"><span data-stu-id="6f20f-106">Adjust the size of the control to fit the picture it displays</span></span>  
  
-   <span data-ttu-id="6f20f-107">コントロールに合わせて、表示される任意の画像を拡大します。</span><span class="sxs-lookup"><span data-stu-id="6f20f-107">Stretch any picture it displays to fit the control</span></span>  
  
 <span data-ttu-id="6f20f-108">(特にビットマップ形式の 1 つ) 画像を拡大すると、イメージ品質の低下が生成できます。</span><span class="sxs-lookup"><span data-stu-id="6f20f-108">Stretching a picture (especially one in bitmap format) can produce a loss in image quality.</span></span> <span data-ttu-id="6f20f-109">実行時にイメージを描画するためのグラフィックス命令のリストのメタファイルはビットマップよりも伸縮適しています。</span><span class="sxs-lookup"><span data-stu-id="6f20f-109">Metafiles, which are lists of graphics instructions for drawing images at run time, are better suited for stretching than bitmaps are.</span></span>  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a><span data-ttu-id="6f20f-110">実行時に、このプロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="6f20f-110">To set the SizeMode property at run time</span></span>  
  
1.  <span data-ttu-id="6f20f-111">設定<xref:System.Windows.Forms.PictureBox.SizeMode%2A>に<xref:System.Windows.Forms.PictureBoxSizeMode.Normal>(既定)、 <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>、 <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>、または<xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>です。</span><span class="sxs-lookup"><span data-stu-id="6f20f-111">Set <xref:System.Windows.Forms.PictureBox.SizeMode%2A> to <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (the default), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, or <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span></span> <span data-ttu-id="6f20f-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal>コントロールの左上隅にある; に、イメージが配置されていることを意味します。イメージ コントロールよりも大きい場合は、その右下隅、クリッピングされます。</span><span class="sxs-lookup"><span data-stu-id="6f20f-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal> means that the image is placed in the control's upper-left corner; if the image is larger than the control, its lower and right edges are clipped.</span></span> <span data-ttu-id="6f20f-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>イメージが、コントロール内で中央揃えする方法イメージ コントロールよりも大きい場合は、画像の外側の端がクリッピングされます。</span><span class="sxs-lookup"><span data-stu-id="6f20f-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> means that the image is centered within the control; if the image is larger than the control, the picture's outside edges are clipped.</span></span> <span data-ttu-id="6f20f-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>コントロールのサイズは、イメージのサイズに調整されていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="6f20f-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> means that the size of the control is adjusted to the size of the image.</span></span> <span data-ttu-id="6f20f-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>逆の場合は、イメージのサイズは、コントロールのサイズに調整されていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="6f20f-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> is the reverse, and means that the size of the image is adjusted to the size of the control.</span></span>  
  
     <span data-ttu-id="6f20f-116">次の例では、イメージの場所の設定パスは、マイ ドキュメント フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="6f20f-116">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="6f20f-117">これは、Windows オペレーティング システムを実行しているほとんどのコンピューターがこのディレクトリを含めることを想定するためです。</span><span class="sxs-lookup"><span data-stu-id="6f20f-117">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="6f20f-118">また、このようにすることで、最小限のシステム アクセス レベルしか持たないユーザーもアプリケーションを安全に実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="6f20f-118">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="6f20f-119">次の例にフォームを前提としています、<xref:System.Windows.Forms.PictureBox>コントロールが既に追加されています。</span><span class="sxs-lookup"><span data-stu-id="6f20f-119">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
    ```vb  
    Private Sub StretchPic()  
       ' Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage  
       ' Load the picture into the control.  
       ' You should replace the bold image   
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void StretchPic(){  
       // Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage;  
       // Load the picture into the control.  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\Image.gif")  
    }  
    ```  
  
    ```cpp  
    private:  
       void StretchPic()  
       {  
          // Stretch the picture to fit the control.  
          pictureBox1->SizeMode = PictureBoxSizeMode::StretchImage;  
          // Load the picture into the control.  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6f20f-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="6f20f-120">See Also</span></span>  
 <xref:System.Windows.Forms.PictureBox>  
 [<span data-ttu-id="6f20f-121">方法: デザイナーを使用してピクチャを読み込む</span><span class="sxs-lookup"><span data-stu-id="6f20f-121">How to: Load a Picture Using the Designer</span></span>](../../../../docs/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms.md)  
 [<span data-ttu-id="6f20f-122">PictureBox コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="6f20f-122">PictureBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [<span data-ttu-id="6f20f-123">方法: 実行時にピクチャを設定する</span><span class="sxs-lookup"><span data-stu-id="6f20f-123">How to: Set Pictures at Run Time</span></span>](../../../../docs/framework/winforms/controls/how-to-set-pictures-at-run-time-windows-forms.md)  
 [<span data-ttu-id="6f20f-124">PictureBox コントロール</span><span class="sxs-lookup"><span data-stu-id="6f20f-124">PictureBox Control</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)
