---
title: "方法 : 実行時にピクチャのサイズまたは配置を変更する (Windows フォーム) | Microsoft Docs"
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
  - "例 [Windows フォーム], PictureBox コントロール"
  - "イメージ [Windows フォーム], 制御 (PictureBox コントロール内の配置を) [Windows フォーム]"
  - "PictureBox コントロール [Windows フォーム], ピクチャのサイズと配置"
  - "ピクチャ, 制御 (PictureBox コントロール内の配置を) [Windows フォーム]"
ms.assetid: d0b332a3-fae2-4891-957c-dc3e17743326
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : 実行時にピクチャのサイズまたは配置を変更する (Windows フォーム)
Windows フォーム <xref:System.Windows.Forms.PictureBox> コントロールをフォームで使用している場合は、フォームの <xref:System.Windows.Forms.PictureBox.SizeMode%2A> プロパティを次のように設定できます。  
  
-   ピクチャの左上隅をコントロールの左上隅と揃えます。  
  
-   ピクチャをコントロールの中央に配置します。  
  
-   コントロールに表示されるピクチャに合わせて、コントロールのサイズを調整します。  
  
-   コントロールに合わせて、表示されるピクチャを伸縮します。  
  
 特にビットマップ形式のピクチャの場合、伸縮するとイメージの画質が低下することがあります。  メタファイルは、イメージを実行時に描画するためのグラフィックス命令のリストであり、ビットマップよりも伸縮に適しています。  
  
### 実行時に SizeMode プロパティを設定するには  
  
1.  <xref:System.Windows.Forms.PictureBox.SizeMode%2A> を <xref:System.Windows.Forms.PictureBoxSizeMode> \(既定\)、<xref:System.Windows.Forms.PictureBoxSizeMode>、<xref:System.Windows.Forms.PictureBoxSizeMode>、または <xref:System.Windows.Forms.PictureBoxSizeMode> に設定します。  <xref:System.Windows.Forms.PictureBoxSizeMode> は、イメージがコントロールの左上隅に配置されることを示し、イメージがコントロールよりも大きい場合、ピクチャの下辺と右辺がクリップされます。  <xref:System.Windows.Forms.PictureBoxSizeMode> は、イメージがコントロール内の中央に配置されることを示し、イメージがコントロールよりも大きい場合、ピクチャの周囲の端がクリップされます。  <xref:System.Windows.Forms.PictureBoxSizeMode> は、コントロールのサイズがイメージのサイズに合わせて調整されることを示します。  <xref:System.Windows.Forms.PictureBoxSizeMode> はその逆で、イメージのサイズがコントロールのサイズに合わせて調整されることを示します。  
  
     次の例では、イメージの場所に対するパスとして **My Documents** フォルダーが設定されています。  これは、Windows オペレーティング システムを実行するコンピューターには、通常このディレクトリが存在すると考えられるためです。  また、ユーザーは最小限のシステム アクセス レベルでアプリケーションを安全に実行できます。  次の例は、既に <xref:System.Windows.Forms.PictureBox> コントロールが追加されたフォームを想定しています。  
  
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
  
## 参照  
 <xref:System.Windows.Forms.PictureBox>   
 [方法 : デザイナーを使用してピクチャを読み込む](../../../../docs/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms.md)   
 [PictureBox コントロールの概要](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)   
 [方法 : 実行時にピクチャを設定する](../../../../docs/framework/winforms/controls/how-to-set-pictures-at-run-time-windows-forms.md)   
 [PictureBox コントロール](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)