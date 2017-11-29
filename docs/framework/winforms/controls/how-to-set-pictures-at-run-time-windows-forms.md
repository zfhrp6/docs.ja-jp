---
title: "方法 : 実行時にピクチャを設定する (Windows フォーム)"
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
- pictures [Windows Forms], setting display
- examples [Windows Forms], PictureBox control
- bitmaps [Windows Forms], displaying in PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding images
- images [Windows Forms], adding with PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 18ca41d0-68a5-4660-985e-a6c1fbc01d76
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 429c0c928d8bff4f837186040288d9447fc18687
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a><span data-ttu-id="94e6e-102">方法 : 実行時にピクチャを設定する (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="94e6e-102">How to: Set Pictures at Run Time (Windows Forms)</span></span>
<span data-ttu-id="94e6e-103">Windows フォームが表示されるイメージをプログラムで設定できる<xref:System.Windows.Forms.PictureBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="94e6e-103">You can programmatically set the image displayed by a Windows Forms <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-set-a-picture-programmatically"></a><span data-ttu-id="94e6e-104">画像をコードから設定するには</span><span class="sxs-lookup"><span data-stu-id="94e6e-104">To set a picture programmatically</span></span>  
  
-   <span data-ttu-id="94e6e-105">設定、<xref:System.Windows.Forms.PictureBox.Image%2A>プロパティを使用して、<xref:System.Drawing.Image.FromFile%2A>のメソッド、<xref:System.Drawing.Image>クラスです。</span><span class="sxs-lookup"><span data-stu-id="94e6e-105">Set the <xref:System.Windows.Forms.PictureBox.Image%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image> class.</span></span>  
  
     <span data-ttu-id="94e6e-106">次の例では、イメージの場所の設定パスは、マイ ドキュメント フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="94e6e-106">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="94e6e-107">これは、Windows オペレーティング システムを実行しているほとんどのコンピューターがこのディレクトリを含めることを想定するためです。</span><span class="sxs-lookup"><span data-stu-id="94e6e-107">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="94e6e-108">また、このようにすることで、最小限のシステム アクセス レベルしか持たないユーザーもアプリケーションを安全に実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="94e6e-108">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="94e6e-109">次の例にフォームを前提としています、<xref:System.Windows.Forms.PictureBox>コントロールが既に追加されています。</span><span class="sxs-lookup"><span data-stu-id="94e6e-109">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
    ```vb  
    Private Sub LoadNewPict()  
       ' You should replace the bold image   
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void LoadNewPict(){  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    }  
    ```  
  
    ```cpp  
    private:  
       void LoadNewPict()  
       {  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
### <a name="to-clear-a-graphic"></a><span data-ttu-id="94e6e-110">画像を消去するには</span><span class="sxs-lookup"><span data-stu-id="94e6e-110">To clear a graphic</span></span>  
  
-   <span data-ttu-id="94e6e-111">最初に、イメージで使用されているメモリを解放し、グラフィックをクリアします。</span><span class="sxs-lookup"><span data-stu-id="94e6e-111">First, release the memory being used by the image, and then clear the graphic.</span></span> <span data-ttu-id="94e6e-112">ガベージ コレクションは、メモリ管理が問題になる場合後で、メモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="94e6e-112">Garbage collection will free up the memory later if memory management becomes a problem.</span></span>  
  
    ```vb  
    If Not (PictureBox1.Image Is Nothing) Then  
       PictureBox1.Image.Dispose()  
       PictureBox1.Image = Nothing  
    End If  
    ```  
  
    ```csharp  
    if (pictureBox1.Image != null)   
    {  
       pictureBox1.Image.Dispose();  
       pictureBox1.Image = null;  
    }  
    ```  
  
    ```cpp  
    if (pictureBox1->Image != nullptr)  
    {  
       pictureBox1->Image->Dispose();  
       pictureBox1->Image = nullptr;  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="94e6e-113">使用する必要があります理由の詳細については、<xref:System.Drawing.Image.Dispose%2A>この方法でメソッドを参照してください[アンマネージ リソースのクリーンアップ](../../../../docs/standard/garbage-collection/unmanaged.md)です。</span><span class="sxs-lookup"><span data-stu-id="94e6e-113">For more information on why you should use the <xref:System.Drawing.Image.Dispose%2A> method in this way, see [Cleaning Up Unmanaged Resources](../../../../docs/standard/garbage-collection/unmanaged.md).</span></span>  
  
     <span data-ttu-id="94e6e-114">このコードは、画像がデザイン時にコントロールに読み込まれた場合でも、イメージがクリアされます。</span><span class="sxs-lookup"><span data-stu-id="94e6e-114">This code will clear the image even if a graphic was loaded into the control at design time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94e6e-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="94e6e-115">See Also</span></span>  
 <xref:System.Windows.Forms.PictureBox>  
 <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="94e6e-116">PictureBox コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="94e6e-116">PictureBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [<span data-ttu-id="94e6e-117">方法: デザイナーを使用してピクチャを読み込む</span><span class="sxs-lookup"><span data-stu-id="94e6e-117">How to: Load a Picture Using the Designer</span></span>](../../../../docs/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms.md)  
 [<span data-ttu-id="94e6e-118">方法: 実行時にピクチャのサイズまたは配置を変更する</span><span class="sxs-lookup"><span data-stu-id="94e6e-118">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](../../../../docs/framework/winforms/controls/how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)  
 [<span data-ttu-id="94e6e-119">PictureBox コントロール</span><span class="sxs-lookup"><span data-stu-id="94e6e-119">PictureBox Control</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)
