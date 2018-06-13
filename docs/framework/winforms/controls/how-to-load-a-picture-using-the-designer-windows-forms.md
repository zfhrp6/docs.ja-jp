---
title: '方法 : デザイナーを使用してピクチャを読み込む (Windows フォーム)'
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: 5eb85c6f3ca232f8b53ac01d57ee71f73415cf83
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533544"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a><span data-ttu-id="94dca-102">方法 : デザイナーを使用してピクチャを読み込む (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="94dca-102">How to: Load a Picture Using the Designer (Windows Forms)</span></span>
<span data-ttu-id="94dca-103">Windows フォームで<xref:System.Windows.Forms.PictureBox>コントロール、読み込みし、設定して、デザイン時にフォームに画像を表示できます、<xref:System.Windows.Forms.PictureBox.Image%2A>に有効な画像のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="94dca-103">With the Windows Forms <xref:System.Windows.Forms.PictureBox> control, you can load and display a picture on a form at design time by setting the <xref:System.Windows.Forms.PictureBox.Image%2A> property to a valid picture.</span></span> <span data-ttu-id="94dca-104">次の表は、使用可能なファイルの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="94dca-104">The following table shows the acceptable file types.</span></span>  
  
|<span data-ttu-id="94dca-105">型</span><span class="sxs-lookup"><span data-stu-id="94dca-105">Type</span></span>|<span data-ttu-id="94dca-106">ファイル名拡張子</span><span class="sxs-lookup"><span data-stu-id="94dca-106">File name extension</span></span>|  
|----------|-------------------------|  
|<span data-ttu-id="94dca-107">ビットマップ</span><span class="sxs-lookup"><span data-stu-id="94dca-107">Bitmap</span></span>|<span data-ttu-id="94dca-108">.bmp</span><span class="sxs-lookup"><span data-stu-id="94dca-108">.bmp</span></span>|  
|<span data-ttu-id="94dca-109">アイコン</span><span class="sxs-lookup"><span data-stu-id="94dca-109">Icon</span></span>|<span data-ttu-id="94dca-110">.ico</span><span class="sxs-lookup"><span data-stu-id="94dca-110">.ico</span></span>|  
|<span data-ttu-id="94dca-111">GIF</span><span class="sxs-lookup"><span data-stu-id="94dca-111">GIF</span></span>|<span data-ttu-id="94dca-112">.gif</span><span class="sxs-lookup"><span data-stu-id="94dca-112">.gif</span></span>|  
|<span data-ttu-id="94dca-113">メタファイル</span><span class="sxs-lookup"><span data-stu-id="94dca-113">Metafile</span></span>|<span data-ttu-id="94dca-114">.wmf</span><span class="sxs-lookup"><span data-stu-id="94dca-114">.wmf</span></span>|  
|<span data-ttu-id="94dca-115">JPEG</span><span class="sxs-lookup"><span data-stu-id="94dca-115">JPEG</span></span>|<span data-ttu-id="94dca-116">.jpg</span><span class="sxs-lookup"><span data-stu-id="94dca-116">.jpg</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="94dca-117">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="94dca-117">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="94dca-118">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="94dca-118">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="94dca-119">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94dca-119">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-display-a-picture-at-design-time"></a><span data-ttu-id="94dca-120">デザイン時に画像を表示するには</span><span class="sxs-lookup"><span data-stu-id="94dca-120">To display a picture at design time</span></span>  
  
1.  <span data-ttu-id="94dca-121">描画、<xref:System.Windows.Forms.PictureBox>フォーム上のコントロールです。</span><span class="sxs-lookup"><span data-stu-id="94dca-121">Draw a <xref:System.Windows.Forms.PictureBox> control on a form.</span></span>  
  
2.  <span data-ttu-id="94dca-122">プロパティ ウィンドウで、次のように選択します。、<xref:System.Windows.Forms.PictureBox.Image%2A>プロパティ、し、省略記号ボタンを表示をクリックして、**開く** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="94dca-122">On the Properties window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property, then click the ellipsis button to display the **Open** dialog box.</span></span>  
  
3.  <span data-ttu-id="94dca-123">特定のファイル タイプ (たとえば、.gif ファイルを探している場合にこれを選択、**ファイルの種類**ボックス。</span><span class="sxs-lookup"><span data-stu-id="94dca-123">If you are looking for a specific file type (for example, .gif files), select it in the **Files of type** box.</span></span>  
  
4.  <span data-ttu-id="94dca-124">表示するファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="94dca-124">Select the file you want to display.</span></span>  
  
### <a name="to-clear-the-picture-at-design-time"></a><span data-ttu-id="94dca-125">デザイン時に、画像を消去するには</span><span class="sxs-lookup"><span data-stu-id="94dca-125">To clear the picture at design time</span></span>  
  
1.  <span data-ttu-id="94dca-126">**プロパティ**ウィンドウで、<xref:System.Windows.Forms.PictureBox.Image%2A>プロパティと、イメージ オブジェクトの名前の左側に表示される小さなのサムネイル画像を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="94dca-126">On the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property and right-click the small thumbnail image that appears to the left of the name of the image object.</span></span> <span data-ttu-id="94dca-127">選択**リセット**です。</span><span class="sxs-lookup"><span data-stu-id="94dca-127">Choose **Reset**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94dca-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="94dca-128">See Also</span></span>  
 <xref:System.Windows.Forms.PictureBox>  
 [<span data-ttu-id="94dca-129">PictureBox コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="94dca-129">PictureBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [<span data-ttu-id="94dca-130">方法: 実行時にピクチャのサイズまたは配置を変更する</span><span class="sxs-lookup"><span data-stu-id="94dca-130">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](../../../../docs/framework/winforms/controls/how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)  
 [<span data-ttu-id="94dca-131">方法: 実行時にピクチャを設定する</span><span class="sxs-lookup"><span data-stu-id="94dca-131">How to: Set Pictures at Run Time</span></span>](../../../../docs/framework/winforms/controls/how-to-set-pictures-at-run-time-windows-forms.md)  
 [<span data-ttu-id="94dca-132">PictureBox コントロール</span><span class="sxs-lookup"><span data-stu-id="94dca-132">PictureBox Control</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)
