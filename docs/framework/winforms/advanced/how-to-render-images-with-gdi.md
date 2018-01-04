---
title: "方法 : GDI+ を使用してイメージをレンダリングする"
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
- images [Windows Forms], creating
- GDI+, rendering existing images
ms.assetid: c128b79a-3e31-47d8-9e66-3470f570a056
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a6edc48c93f83611bdc2be5b7398ab0abe843407
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-render-images-with-gdi"></a><span data-ttu-id="0aac4-102">方法 : GDI+ を使用してイメージをレンダリングする</span><span class="sxs-lookup"><span data-stu-id="0aac4-102">How to: Render Images with GDI+</span></span>
<span data-ttu-id="0aac4-103">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] を使用すると、アプリケーションにファイルとして存在するイメージをレンダリングできます。</span><span class="sxs-lookup"><span data-stu-id="0aac4-103">You can use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to render images that exist as files in your applications.</span></span> <span data-ttu-id="0aac4-104">新しいオブジェクトを作成することで、これを行う、<xref:System.Drawing.Image>クラス (など<xref:System.Drawing.Bitmap>)、作成、 <xref:System.Drawing.Graphics> 、使用する描画サーフェイスへの参照オブジェクトし、呼び出し、<xref:System.Drawing.Graphics.DrawImage%2A>のメソッド、<xref:System.Drawing.Graphics>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0aac4-104">You do this by creating a new object of an <xref:System.Drawing.Image> class (such as <xref:System.Drawing.Bitmap>), creating a <xref:System.Drawing.Graphics> object that refers to the drawing surface you want to use, and calling the <xref:System.Drawing.Graphics.DrawImage%2A> method of the <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="0aac4-105">イメージは、グラフィックス クラスで表される描画サーフェイス上に描画されます。</span><span class="sxs-lookup"><span data-stu-id="0aac4-105">The image will be painted onto the drawing surface represented by the graphics class.</span></span> <span data-ttu-id="0aac4-106">イメージ エディターを使用して、デザイン時にイメージ ファイルを作成および編集し、実行時に [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] を使用してレンダリングできます。</span><span class="sxs-lookup"><span data-stu-id="0aac4-106">You can use the Image Editor to create and edit image files at design time, and render them with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] at run time.</span></span> <span data-ttu-id="0aac4-107">詳細については、「[アイコン用イメージ エディター](/cpp/windows/image-editor-for-icons)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0aac4-107">For more information, see [Image Editor for Icons](/cpp/windows/image-editor-for-icons).</span></span>  
  
### <a name="to-render-an-image-with-gdi"></a><span data-ttu-id="0aac4-108">GDI + を使用してイメージをレンダリングするには</span><span class="sxs-lookup"><span data-stu-id="0aac4-108">To render an image with GDI+</span></span>  
  
1.  <span data-ttu-id="0aac4-109">表示するイメージを表すオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="0aac4-109">Create an object representing the image you want to display.</span></span> <span data-ttu-id="0aac4-110">このオブジェクトから継承するクラスのメンバーである必要があります<xref:System.Drawing.Image>など<xref:System.Drawing.Bitmap>または<xref:System.Drawing.Imaging.Metafile>です。</span><span class="sxs-lookup"><span data-stu-id="0aac4-110">This object must be a member of a class that inherits from <xref:System.Drawing.Image>, such as <xref:System.Drawing.Bitmap> or <xref:System.Drawing.Imaging.Metafile>.</span></span> <span data-ttu-id="0aac4-111">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="0aac4-111">An example is shown:</span></span>  
  
    ```vb  
    ' Uses the System.Environment.GetFolderPath to get the path to the   
    ' current user's MyPictures folder.  
    Dim myBitmap as New Bitmap _  
       (System.Environment.GetFolderPath _  
          (System.Environment.SpecialFolder.MyPictures))  
    ```  
  
    ```csharp  
    // Uses the System.Environment.GetFolderPath to get the path to the   
    // current user's MyPictures folder.  
    Bitmap myBitmap = new Bitmap  
       (System.Environment.GetFolderPath  
          (System.Environment.SpecialFolder.MyPictures));  
    ```  
  
    ```cpp  
    // Uses the System.Environment.GetFolderPath to get the path to the   
    // current user's MyPictures folder.  
    Bitmap^ myBitmap = gcnew Bitmap  
       (System::Environment::GetFolderPath  
          (System::Environment::SpecialFolder::MyPictures));  
    ```  
  
2.  <span data-ttu-id="0aac4-112">作成、<xref:System.Drawing.Graphics>を使用する描画サーフェイスを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0aac4-112">Create a <xref:System.Drawing.Graphics> object that represents the drawing surface you want to use.</span></span> <span data-ttu-id="0aac4-113">詳細については、「[方法 : 描画する Graphics オブジェクトを作成する](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0aac4-113">For more information, see [How to: Create Graphics Objects for Drawing](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
    ```vb  
    ' Creates a Graphics object that represents the drawing surface of   
    ' Button1.  
    Dim g as Graphics = Button1.CreateGraphics  
    ```  
  
    ```csharp  
    // Creates a Graphics object that represents the drawing surface of   
    // Button1.  
    Graphics g = Button1.CreateGraphics();  
    ```  
  
    ```cpp  
    // Creates a Graphics object that represents the drawing surface of   
    // Button1.  
    Graphics^ g = button1->CreateGraphics();  
    ```  
  
3.  <span data-ttu-id="0aac4-114">呼び出す、<xref:System.Drawing.Graphics.DrawImage%2A>のイメージを表示するために、グラフィックス オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0aac4-114">Call the <xref:System.Drawing.Graphics.DrawImage%2A> of your graphics object to render the image.</span></span> <span data-ttu-id="0aac4-115">描画対象のイメージとイメージを描画する場所の座標を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0aac4-115">You must specify both the image to be drawn, and the coordinates where it is to be drawn.</span></span>  
  
    ```vb  
    g.DrawImage(myBitmap, 1, 1)  
    ```  
  
    ```csharp  
    g.DrawImage(myBitmap, 1, 1);  
    ```  
  
    ```cpp  
    g->DrawImage(myBitmap, 1, 1);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0aac4-116">参照</span><span class="sxs-lookup"><span data-stu-id="0aac4-116">See Also</span></span>  
 [<span data-ttu-id="0aac4-117">グラフィックス プログラミングについて</span><span class="sxs-lookup"><span data-stu-id="0aac4-117">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="0aac4-118">方法: 描画する Graphics オブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="0aac4-118">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="0aac4-119">GDI+ でのペン、直線、および四角形</span><span class="sxs-lookup"><span data-stu-id="0aac4-119">Pens, Lines, and Rectangles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)  
 [<span data-ttu-id="0aac4-120">方法: Windows フォームにテキストを描画する</span><span class="sxs-lookup"><span data-stu-id="0aac4-120">How to: Draw Text on a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-on-a-windows-form.md)  
 [<span data-ttu-id="0aac4-121">Windows フォームにおけるグラフィックスと描画</span><span class="sxs-lookup"><span data-stu-id="0aac4-121">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="0aac4-122">描画線または閉じた図形</span><span class="sxs-lookup"><span data-stu-id="0aac4-122">Drawing Lines or Closed Figures</span></span>](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)  
 [<span data-ttu-id="0aac4-123">アイコン用イメージ エディター</span><span class="sxs-lookup"><span data-stu-id="0aac4-123">Image Editor for Icons</span></span>](/cpp/windows/image-editor-for-icons)
