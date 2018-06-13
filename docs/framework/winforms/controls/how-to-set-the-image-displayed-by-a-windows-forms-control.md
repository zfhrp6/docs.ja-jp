---
title: '方法 : Windows フォーム コントロールによって表示されるイメージを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
ms.openlocfilehash: 4870f9e2acc48a90e1e2193d514926fedee05f61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533742"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a><span data-ttu-id="484b2-102">方法 : Windows フォーム コントロールによって表示されるイメージを設定する</span><span class="sxs-lookup"><span data-stu-id="484b2-102">How to: Set the Image Displayed by a Windows Forms Control</span></span>
<span data-ttu-id="484b2-103">いくつかの Windows フォーム コントロールは、イメージを表示できます。</span><span class="sxs-lookup"><span data-stu-id="484b2-103">Several Windows Forms controls can display images.</span></span> <span data-ttu-id="484b2-104">これらのイメージはボタン上のフロッピー ディスク アイコンなど、コントロールの目的を明確にするアイコンを指定できます、**保存**コマンド。</span><span class="sxs-lookup"><span data-stu-id="484b2-104">These images can be icons that clarify the purpose of the control, such as a diskette icon on a button denoting the **Save** command.</span></span> <span data-ttu-id="484b2-105">目的の動作と外観の制御できるように背景画像の代わりに、アイコンもあります。</span><span class="sxs-lookup"><span data-stu-id="484b2-105">Alternatively, the icons can be background images to give the control the appearance and behavior you want.</span></span>  
  
### <a name="to-set-the-image-displayed-by-a-control"></a><span data-ttu-id="484b2-106">コントロールによって表示されるイメージを設定するには</span><span class="sxs-lookup"><span data-stu-id="484b2-106">To set the image displayed by a control</span></span>  
  
1.  <span data-ttu-id="484b2-107">コントロールの設定`Image`または`BackgroundImage`プロパティ型のオブジェクトを<xref:System.Drawing.Image>です。</span><span class="sxs-lookup"><span data-stu-id="484b2-107">Set the control's `Image` or `BackgroundImage` property to an object of type <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="484b2-108">一般に、するはから読み込まれるイメージ ファイルを使用して、<xref:System.Drawing.Image.FromFile%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="484b2-108">Generally, you will be loading the image from a file by using the <xref:System.Drawing.Image.FromFile%2A> method.</span></span>  
  
     <span data-ttu-id="484b2-109">イメージの場所は次のコード例では、パスが設定、**マイ ピクチャ**フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="484b2-109">In the following code example, the path set for the location of the image is the **My Pictures** folder.</span></span> <span data-ttu-id="484b2-110">Windows オペレーティング システムを実行しているほとんどのコンピューターは、このディレクトリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="484b2-110">Most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="484b2-111">最小限のシステムのアクセス レベルを持つユーザー、アプリケーションを安全に実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="484b2-111">This also enables users with minimal system access levels to run the application safely.</span></span> <span data-ttu-id="484b2-112">次のコード例では、既にフォームにある必要があります、<xref:System.Windows.Forms.PictureBox>コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="484b2-112">The following code example requires that you already have a form with a <xref:System.Windows.Forms.PictureBox> control added.</span></span>  
  
    ```vb  
    ' Replace the image named below  
    ' with an icon of your own choosing.  
    PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.MyPictures) _  
       & "\Image.gif")  
    ```  
  
    ```csharp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.MyPictures)  
       + @"\Image.gif");  
    ```  
  
    ```cpp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    pictureBox1->Image = Image::FromFile(String::Concat  
       (System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::MyPictures),  
       "\\Image.gif"));  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="484b2-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="484b2-113">See Also</span></span>  
 <xref:System.Drawing.Image.FromFile%2A>  
 <xref:System.Drawing.Image>  
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>
