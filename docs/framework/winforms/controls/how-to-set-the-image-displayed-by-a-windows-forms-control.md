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
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a>方法 : Windows フォーム コントロールによって表示されるイメージを設定する
いくつかの Windows フォーム コントロールは、イメージを表示できます。 これらのイメージはボタン上のフロッピー ディスク アイコンなど、コントロールの目的を明確にするアイコンを指定できます、**保存**コマンド。 目的の動作と外観の制御できるように背景画像の代わりに、アイコンもあります。  
  
### <a name="to-set-the-image-displayed-by-a-control"></a>コントロールによって表示されるイメージを設定するには  
  
1.  コントロールの設定`Image`または`BackgroundImage`プロパティ型のオブジェクトを<xref:System.Drawing.Image>です。 一般に、するはから読み込まれるイメージ ファイルを使用して、<xref:System.Drawing.Image.FromFile%2A>メソッドです。  
  
     イメージの場所は次のコード例では、パスが設定、**マイ ピクチャ**フォルダーです。 Windows オペレーティング システムを実行しているほとんどのコンピューターは、このディレクトリが含まれます。 最小限のシステムのアクセス レベルを持つユーザー、アプリケーションを安全に実行することもできます。 次のコード例では、既にフォームにある必要があります、<xref:System.Windows.Forms.PictureBox>コントロールを追加します。  
  
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
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.Image.FromFile%2A>  
 <xref:System.Drawing.Image>  
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>
