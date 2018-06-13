---
title: '方法 : 実行時にピクチャを設定する (Windows フォーム)'
ms.date: 03/30/2017
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
ms.openlocfilehash: fedddf56966c3ab11a1dfb20c1d4cbd8a45fb1a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533475"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a>方法 : 実行時にピクチャを設定する (Windows フォーム)
Windows フォームが表示されるイメージをプログラムで設定できる<xref:System.Windows.Forms.PictureBox>コントロール。  
  
### <a name="to-set-a-picture-programmatically"></a>画像をコードから設定するには  
  
-   設定、<xref:System.Windows.Forms.PictureBox.Image%2A>プロパティを使用して、<xref:System.Drawing.Image.FromFile%2A>のメソッド、<xref:System.Drawing.Image>クラスです。  
  
     次の例では、イメージの場所の設定パスは、マイ ドキュメント フォルダーです。 これは、Windows オペレーティング システムを実行しているほとんどのコンピューターがこのディレクトリを含めることを想定するためです。 また、このようにすることで、最小限のシステム アクセス レベルしか持たないユーザーもアプリケーションを安全に実行できるようになります。 次の例にフォームを前提としています、<xref:System.Windows.Forms.PictureBox>コントロールが既に追加されています。  
  
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
  
### <a name="to-clear-a-graphic"></a>画像を消去するには  
  
-   最初に、イメージで使用されているメモリを解放し、グラフィックをクリアします。 ガベージ コレクションは、メモリ管理が問題になる場合後で、メモリを解放します。  
  
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
    >  使用する必要があります理由の詳細については、<xref:System.Drawing.Image.Dispose%2A>この方法でメソッドを参照してください[アンマネージ リソースのクリーンアップ](../../../../docs/standard/garbage-collection/unmanaged.md)です。  
  
     このコードは、画像がデザイン時にコントロールに読み込まれた場合でも、イメージがクリアされます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.PictureBox>  
 <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>  
 [PictureBox コントロールの概要](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [方法: デザイナーを使用してピクチャを読み込む](../../../../docs/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms.md)  
 [方法: 実行時にピクチャのサイズまたは配置を変更する](../../../../docs/framework/winforms/controls/how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)  
 [PictureBox コントロール](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)
