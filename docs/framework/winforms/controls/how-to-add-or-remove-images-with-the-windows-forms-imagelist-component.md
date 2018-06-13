---
title: '方法 : Windows フォームの ImageList コンポーネントにイメージを追加または削除する'
ms.date: 03/30/2017
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
ms.openlocfilehash: e5c563c4f46924a95936bc5a51862230f2cbdb99
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527639"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a>方法 : Windows フォームの ImageList コンポーネントにイメージを追加または削除する
Windows フォーム<xref:System.Windows.Forms.ImageList>コンポーネントには通常、イメージ コントロールに関連付けられている前にします。 ただし、追加し、イメージ リスト コントロールとの関連付けの後イメージを削除します。  
  
> [!NOTE]
>  イメージを削除するときにいることを確認、<xref:System.Windows.Forms.ButtonBase.ImageIndex%2A>の関連付けられたコントロールのプロパティは現在も有効です。  
  
### <a name="to-add-images-programmatically"></a>プログラムからイメージを追加するには  
  
-   使用して、<xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A>メソッドのイメージ リストの<xref:System.Windows.Forms.ImageList.Images%2A>プロパティです。  
  
     イメージの場所は次のコード例では、パスが設定、**マイ ドキュメント**フォルダーです。 この場所は、Windows オペレーティング システムを実行しているほとんどのコンピューターがこのフォルダーを含めることを想定するために使用されます。 この場所を選択すると、最小限のシステム アクセス レベル、アプリケーションを安全に実行を持つユーザーもできます。 次のコード例では、フォームがあることが必要です、<xref:System.Windows.Forms.ImageList>コントロールが既に追加されています。  
  
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
  
### <a name="to-add-images-with-a-key-value"></a>イメージを追加するキー値を持つ。  
  
-   いずれかを使用して、<xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A>のイメージ リストのメソッド<xref:System.Windows.Forms.ImageList.Images%2A>キー値を取得するプロパティです。  
  
     イメージの場所は次のコード例では、パスが設定、**マイ ドキュメント**フォルダーです。 この場所は、Windows オペレーティング システムを実行しているほとんどのコンピューターがこのフォルダーを含めることを想定するために使用されます。 この場所を選択すると、最小限のシステム アクセス レベル、アプリケーションを安全に実行を持つユーザーもできます。 次のコード例では、フォームがあることが必要です、<xref:System.Windows.Forms.ImageList>コントロールが既に追加されています。  
  
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
  
### <a name="to-remove-all-images-programmatically"></a>すべてのイメージをプログラムで削除するには  
  
-   使用して、 <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> 1 つのイメージを削除する方法  
  
     、- または -  
  
     使用して、<xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A>イメージ リスト内のすべてのイメージをクリアします。  
  
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
  
### <a name="to-remove-images-by-key"></a>キーにイメージを削除するには  
  
-   使用して、<xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A>キーを使用して 1 つのイメージを削除する方法です。  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a>関連項目  
 [ImageList コンポーネント](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)  
 [ImageList コンポーネントの概要](../../../../docs/framework/winforms/controls/imagelist-component-overview-windows-forms.md)  
 [イメージ、ビットマップ、メタファイル](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
