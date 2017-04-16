---
title: "方法 : Windows フォームの ImageList コンポーネントにイメージを追加または削除する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ImageList コンポーネント [Windows フォーム], 追加 (イメージを)"
  - "ImageList コンポーネント [Windows フォーム], 削除 (イメージを)"
  - "イメージ [Windows フォーム], 追加 (ImageList コンポーネントに)"
  - "イメージ [Windows フォーム], 表示 (コントロールと共に)"
  - "イメージ [Windows フォーム], 削除 (ImageList コンポーネントから)"
  - "イメージ [Windows フォーム], 格納 (コントロールの)"
ms.assetid: c5eacc56-f769-4e2e-bfb7-f756620913db
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : Windows フォームの ImageList コンポーネントにイメージを追加または削除する
Windows フォームの <xref:System.Windows.Forms.ImageList> コンポーネントは、コントロールに関連付ける前にイメージを設定するのが普通です。  ただし、イメージ リストをコントロールに関連付けた後で、イメージを追加または削除することもできます。  
  
> [!NOTE]
>  イメージを削除するときには、関連付けられているコントロールの <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> プロパティがイメージの削除後も有効であることを確認してください。  
  
### プログラムによってイメージを追加するには  
  
-   イメージ リストの <xref:System.Windows.Forms.ImageList.Images%2A> プロパティの <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> メソッドを使用します。  
  
     次のコード例では、イメージの場所に対するパスとして **My Documents** フォルダーが設定されています。  この場所を使用するのは、Windows オペレーティング システムを実行するコンピューターには、通常このディレクトリが存在すると考えられるためです。  また、この場所を選択すると、最小限のシステム アクセス レベルのユーザーがアプリケーションをより安全に実行できます。  次のコード例には、<xref:System.Windows.Forms.ImageList> コントロールを追加済みのフォームが必要です。  
  
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
  
### キー値を指定してイメージを追加するには  
  
-   キー値を引数に受け取る、イメージ リストの <xref:System.Windows.Forms.ImageList.Images%2A> プロパティのいずれかの <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> メソッドを使用します。  
  
     次のコード例では、イメージの場所に対するパスとして **My Documents** フォルダーが設定されています。  この場所を使用するのは、Windows オペレーティング システムを実行するコンピューターには、通常このディレクトリが存在すると考えられるためです。  また、この場所を選択すると、最小限のシステム アクセス レベルのユーザーがアプリケーションをより安全に実行できます。  次のコード例には、<xref:System.Windows.Forms.ImageList> コントロールを追加済みのフォームが必要です。  
  
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
  
### プログラムによってすべてのイメージを削除するには  
  
-   <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> メソッドを使用して単一のイメージを削除します。  
  
     または  
  
     <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> メソッドを使用して、イメージ リストのすべてのイメージを削除します。  
  
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
  
### キーを指定してイメージを削除するには  
  
-   <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> メソッドを使用して、キーに対応する単一のイメージを削除します。  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
  
```  
  
## 参照  
 [ImageList コンポーネント](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)   
 [ImageList コンポーネントの概要](../../../../docs/framework/winforms/controls/imagelist-component-overview-windows-forms.md)   
 [イメージ、ビットマップ、およびメタファイル](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)