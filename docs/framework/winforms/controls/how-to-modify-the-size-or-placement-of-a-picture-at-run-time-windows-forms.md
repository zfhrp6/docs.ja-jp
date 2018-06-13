---
title: '方法 : 実行時にピクチャのサイズまたは配置を変更する (Windows フォーム)'
ms.date: 03/30/2017
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
ms.openlocfilehash: 9e6e114e0a9d7e5e9c17ba21ef941703cd108784
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534775"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a>方法 : 実行時にピクチャのサイズまたは配置を変更する (Windows フォーム)
Windows フォームを使用する場合<xref:System.Windows.Forms.PictureBox>コントロール、フォームで設定することができます、<xref:System.Windows.Forms.PictureBox.SizeMode%2A>のプロパティ。  
  
-   画像の左上隅にコントロールの左上隅を揃える  
  
-   コントロール内で画像を中央揃え  
  
-   表示される画像に合わせてコントロールのサイズを調整します。  
  
-   コントロールに合わせて、表示される任意の画像を拡大します。  
  
 (特にビットマップ形式の 1 つ) 画像を拡大すると、イメージ品質の低下が生成できます。 実行時にイメージを描画するためのグラフィックス命令のリストのメタファイルはビットマップよりも伸縮適しています。  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a>実行時に、このプロパティを設定するには  
  
1.  設定<xref:System.Windows.Forms.PictureBox.SizeMode%2A>に<xref:System.Windows.Forms.PictureBoxSizeMode.Normal>(既定)、 <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>、 <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>、または<xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>です。 <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> コントロールの左上隅にある; に、イメージが配置されていることを意味します。イメージ コントロールよりも大きい場合は、その右下隅、クリッピングされます。 <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> イメージが、コントロール内で中央揃えする方法イメージ コントロールよりも大きい場合は、画像の外側の端がクリッピングされます。 <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> コントロールのサイズは、イメージのサイズに調整されていることを意味します。 <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> 逆の場合は、イメージのサイズは、コントロールのサイズに調整されていることを意味します。  
  
     次の例では、イメージの場所の設定パスは、マイ ドキュメント フォルダーです。 これは、Windows オペレーティング システムを実行しているほとんどのコンピューターがこのディレクトリを含めることを想定するためです。 また、このようにすることで、最小限のシステム アクセス レベルしか持たないユーザーもアプリケーションを安全に実行できるようになります。 次の例にフォームを前提としています、<xref:System.Windows.Forms.PictureBox>コントロールが既に追加されています。  
  
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
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.PictureBox>  
 [方法: デザイナーを使用してピクチャを読み込む](../../../../docs/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms.md)  
 [PictureBox コントロールの概要](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [方法: 実行時にピクチャを設定する](../../../../docs/framework/winforms/controls/how-to-set-pictures-at-run-time-windows-forms.md)  
 [PictureBox コントロール](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)
