---
title: "方法 : 実行時にピクチャを設定する (Windows フォーム) | Microsoft Docs"
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
  - "ビットマップ [Windows フォーム], 表示 (PictureBox コントロール内に) [Windows フォーム]"
  - "例 [Windows フォーム], PictureBox コントロール"
  - "イメージ [Windows フォーム], PictureBox コントロールの追加 [Windows フォーム]"
  - "PictureBox コントロール [Windows フォーム], 追加 (イメージを)"
  - "PictureBox コントロール [Windows フォーム], 追加 (ピクチャを)"
  - "ピクチャ, 設定 (表示を)"
ms.assetid: 18ca41d0-68a5-4660-985e-a6c1fbc01d76
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : 実行時にピクチャを設定する (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.PictureBox> コントロールで表示されるイメージをプログラムで設定できます。  
  
### プログラムによってピクチャを設定するには  
  
-   <xref:System.Drawing.Image> クラスの <xref:System.Drawing.Image.FromFile%2A> メソッドを使用して <xref:System.Windows.Forms.PictureBox.Image%2A> プロパティを設定します。  
  
     次の例では、イメージの場所に対するパスとして **My Documents** フォルダーが設定されています。  これは、Windows オペレーティング システムを実行するコンピューターには、通常このディレクトリが存在すると考えられるためです。  また、ユーザーは最小限のシステム アクセス レベルでアプリケーションを安全に実行できます。  次の例は、既に <xref:System.Windows.Forms.PictureBox> コントロールが追加されたフォームを想定しています。  
  
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
  
### グラフィックを消去するには  
  
-   最初にイメージによって使用されているメモリを解放してから、グラフィックを消去します。  メモリ管理で問題が発生した場合は、後でガベージ コレクションがメモリを解放します。  
  
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
    >  <xref:System.Drawing.Image.Dispose%2A> メソッドをこのように使用する理由の詳細については、「[Cleaning Up Unmanaged Resources](../../../../docs/standard/garbage-collection/unmanaged.md)」を参照してください。  
  
     このコードによって、デザイン時にコントロールにグラフィックが読み込まれた場合もイメージが消去されます。  
  
## 参照  
 <xref:System.Windows.Forms.PictureBox>   
 <xref:System.Drawing.Image.FromFile%2A?displayProperty=fullName>   
 [PictureBox コントロールの概要](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)   
 [方法 : デザイナーを使用してピクチャを読み込む](../../../../docs/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms.md)   
 [方法 : 実行時にピクチャのサイズまたは配置を変更する](../../../../docs/framework/winforms/controls/how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)   
 [PictureBox コントロール](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)