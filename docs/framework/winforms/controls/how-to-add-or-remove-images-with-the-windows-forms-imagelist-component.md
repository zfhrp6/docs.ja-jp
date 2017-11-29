---
title: "方法 : Windows フォームの ImageList コンポーネントにイメージを追加または削除する"
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
- images [Windows Forms], removing from ImageList component
- images [Windows Forms], storing for controls
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
- images [Windows Forms], displaying with controls
ms.assetid: c5eacc56-f769-4e2e-bfb7-f756620913db
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ce13ba3413c13ced7ff9a967e23d87622309feb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a><span data-ttu-id="09ee0-102">方法 : Windows フォームの ImageList コンポーネントにイメージを追加または削除する</span><span class="sxs-lookup"><span data-stu-id="09ee0-102">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>
<span data-ttu-id="09ee0-103">Windows フォーム<xref:System.Windows.Forms.ImageList>コンポーネントには通常、イメージ コントロールに関連付けられている前にします。</span><span class="sxs-lookup"><span data-stu-id="09ee0-103">The Windows Forms <xref:System.Windows.Forms.ImageList> component is typically populated with images before it is associated with a control.</span></span> <span data-ttu-id="09ee0-104">ただし、追加し、イメージ リスト コントロールとの関連付けの後イメージを削除します。</span><span class="sxs-lookup"><span data-stu-id="09ee0-104">However, you can add and remove images after associating the image list with a control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09ee0-105">イメージを削除するときにいることを確認、<xref:System.Windows.Forms.ButtonBase.ImageIndex%2A>の関連付けられたコントロールのプロパティは現在も有効です。</span><span class="sxs-lookup"><span data-stu-id="09ee0-105">When you remove images, verify that the <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> property of any associated controls is still valid.</span></span>  
  
### <a name="to-add-images-programmatically"></a><span data-ttu-id="09ee0-106">プログラムからイメージを追加するには</span><span class="sxs-lookup"><span data-stu-id="09ee0-106">To add images programmatically</span></span>  
  
-   <span data-ttu-id="09ee0-107">使用して、<xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A>メソッドのイメージ リストの<xref:System.Windows.Forms.ImageList.Images%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="09ee0-107">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> method of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>  
  
     <span data-ttu-id="09ee0-108">イメージの場所は次のコード例では、パスが設定、**マイ ドキュメント**フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="09ee0-108">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="09ee0-109">この場所は、Windows オペレーティング システムを実行しているほとんどのコンピューターがこのフォルダーを含めることを想定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="09ee0-109">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="09ee0-110">この場所を選択すると、最小限のシステム アクセス レベル、アプリケーションを安全に実行を持つユーザーもできます。</span><span class="sxs-lookup"><span data-stu-id="09ee0-110">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="09ee0-111">次のコード例では、フォームがあることが必要です、<xref:System.Windows.Forms.ImageList>コントロールが既に追加されています。</span><span class="sxs-lookup"><span data-stu-id="09ee0-111">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
    ```vb  
    Public Sub LoadImage()  
       Dim myImage As System.Drawing.Image = _  
         Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
       ImageList1.Images.Add(myImage)  
    End Sub  
    ```  
  
    ```csharp  
    public void addImage()  
    {  
    // Be sure that you use an appropriate escape sequence (such as the   
    // @) when specifying the location of the file.  
       System.Drawing.Image myImage =   
         Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
       imageList1.Images.Add(myImage);  
    }  
    ```  
  
    ```cpp  
    public:  
       void addImage()  
       {  
       // Replace the bold image in the following sample   
       // with your own icon.  
       // Be sure that you use an appropriate escape sequence (such as   
       // \\) when specifying the location of the file.  
          System::Drawing::Image ^ myImage =   
             Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
          imageList1->Images->Add(myImage);  
       }  
    ```  
  
### <a name="to-add-images-with-a-key-value"></a><span data-ttu-id="09ee0-112">イメージを追加するキー値を持つ。</span><span class="sxs-lookup"><span data-stu-id="09ee0-112">To add images with a key value.</span></span>  
  
-   <span data-ttu-id="09ee0-113">いずれかを使用して、<xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A>のイメージ リストのメソッド<xref:System.Windows.Forms.ImageList.Images%2A>キー値を取得するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="09ee0-113">Use one of the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> methods of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property that takes a key value.</span></span>  
  
     <span data-ttu-id="09ee0-114">イメージの場所は次のコード例では、パスが設定、**マイ ドキュメント**フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="09ee0-114">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="09ee0-115">この場所は、Windows オペレーティング システムを実行しているほとんどのコンピューターがこのフォルダーを含めることを想定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="09ee0-115">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="09ee0-116">この場所を選択すると、最小限のシステム アクセス レベル、アプリケーションを安全に実行を持つユーザーもできます。</span><span class="sxs-lookup"><span data-stu-id="09ee0-116">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="09ee0-117">次のコード例では、フォームがあることが必要です、<xref:System.Windows.Forms.ImageList>コントロールが既に追加されています。</span><span class="sxs-lookup"><span data-stu-id="09ee0-117">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
    ```vb  
    Public Sub LoadImage()  
       Dim myImage As System.Drawing.Image = _  
         Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
       ImageList1.Images.Add("myPhoto", myImage)  
    End Sub  
    ```  
  
```csharp  
public void addImage()  
{  
// Be sure that you use an appropriate escape sequence (such as the   
// @) when specifying the location of the file.  
   System.Drawing.Image myImage =   
     Image.FromFile  
   (System.Environment.GetFolderPath  
   (System.Environment.SpecialFolder.Personal)  
   + @"\Image.gif");  
   imageList1.Images.Add("myPhoto", myImage);  
}  
```  
  
1.  
  
### <a name="to-remove-all-images-programmatically"></a><span data-ttu-id="09ee0-118">すべてのイメージをプログラムで削除するには</span><span class="sxs-lookup"><span data-stu-id="09ee0-118">To remove all images programmatically</span></span>  
  
-   <span data-ttu-id="09ee0-119">使用して、 <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> 1 つのイメージを削除する方法</span><span class="sxs-lookup"><span data-stu-id="09ee0-119">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> method to remove a single image</span></span>  
  
     <span data-ttu-id="09ee0-120">、- または -</span><span class="sxs-lookup"><span data-stu-id="09ee0-120">,-or-</span></span>  
  
     <span data-ttu-id="09ee0-121">使用して、<xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A>イメージ リスト内のすべてのイメージをクリアします。</span><span class="sxs-lookup"><span data-stu-id="09ee0-121">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> method to clear all images in the image list.</span></span>  
  
    ```vb  
    ' Removes the first image in the image list  
    ImageList1.Images.Remove(myImage)  
    ' Clears all images in the image list  
    ImageList1.Images.Clear()  
    ```  
  
```csharp  
// Removes the first image in the image list.  
imageList1.Images.Remove(myImage);  
// Clears all images in the image list.  
imageList1.Images.Clear();  
```  
  
### <a name="to-remove-images-by-key"></a><span data-ttu-id="09ee0-122">キーにイメージを削除するには</span><span class="sxs-lookup"><span data-stu-id="09ee0-122">To remove images by key</span></span>  
  
-   <span data-ttu-id="09ee0-123">使用して、<xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A>キーを使用して 1 つのイメージを削除する方法です。</span><span class="sxs-lookup"><span data-stu-id="09ee0-123">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> method to remove a single image by its key.</span></span>  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a><span data-ttu-id="09ee0-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="09ee0-124">See Also</span></span>  
 [<span data-ttu-id="09ee0-125">ImageList コンポーネント</span><span class="sxs-lookup"><span data-stu-id="09ee0-125">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)  
 [<span data-ttu-id="09ee0-126">ImageList コンポーネントの概要</span><span class="sxs-lookup"><span data-stu-id="09ee0-126">ImageList Component Overview</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-overview-windows-forms.md)  
 [<span data-ttu-id="09ee0-127">イメージ、ビットマップ、メタファイル</span><span class="sxs-lookup"><span data-stu-id="09ee0-127">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
