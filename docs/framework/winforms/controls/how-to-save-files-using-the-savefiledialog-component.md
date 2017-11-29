---
title: "方法 : SaveFileDialog コンポーネントを使用してファイルを保存する"
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
- saving files
- SaveFileDialog component [Windows Forms], saving files
- files [Windows Forms], saving
- OpenFile method [Windows Forms], saving files with SaveFileDialog component
ms.assetid: 02e8f409-b83f-4707-babb-e71f6b223d90
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 01bac8fc020955e78e7648db72492014acc19944
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-save-files-using-the-savefiledialog-component"></a>方法 : SaveFileDialog コンポーネントを使用してファイルを保存する
<xref:System.Windows.Forms.SaveFileDialog>コンポーネントにより、ユーザーがファイル システムを参照し、保存するファイルを選択します。 このダイアログ ボックスは、ユーザーがダイアログ ボックス内で選択したファイルのパスと名前を返します。 ただし、ファイルを実際にディスクに書き込むためのコードを記述する必要があります。  
  
### <a name="to-save-a-file-using-the-savefiledialog-component"></a>SaveFileDialog コンポーネントを使用してファイルを保存するには  
  
-   **[ファイルの保存]** ダイアログ ボックスを表示し、ユーザーによって選択されたファイルを保存するメソッドを呼び出します。  
  
     使用して、<xref:System.Windows.Forms.SaveFileDialog>コンポーネントの<xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A>メソッド、ファイルを保存します。 このメソッドの結果、<xref:System.IO.Stream>オブジェクトに書き込むことができます。  
  
     使用して次の例、 <xref:System.Windows.Forms.DialogResult> 、ファイルの名前を取得するプロパティと<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>ファイルを保存する方法です。 <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A>メソッドの結果をファイルに書き込むストリーム。  
  
     次の例では、<xref:System.Windows.Forms.Button>コントロールにイメージが割り当てられます。 ボタンをクリックすると、<xref:System.Windows.Forms.SaveFileDialog>型 .gif、.jpeg、.bmp ファイルを許可するフィルターを使用してコンポーネントをインスタンス化します。 [ファイルの保存] ダイアログ ボックスでこれらの種類のファイルが選択されると、ボタンのイメージが保存されます。  
  
    > [!IMPORTANT]
    >  取得または設定する、<xref:System.Windows.Forms.FileDialog.FileName%2A>プロパティをアセンブリが必要です、特権レベル許可によって、<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>クラスです。 部分的に信頼されたコンテキストで実行している場合、プロセスは、特権がないために例外をスローする可能性があります。 詳しくは、「[コード アクセス セキュリティの基礎](../../../../docs/framework/misc/code-access-security-basics.md)」をご覧ください。  
  
     この例では、フォームに、<xref:System.Windows.Forms.Button>コントロールをその<xref:System.Windows.Forms.ButtonBase.Image%2A>プロパティ型 .gif、.jpeg、.bmp のファイルに設定します。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.FileDialog>クラスの<xref:System.Windows.Forms.FileDialog.FilterIndex%2A>プロパティ (、継承、原因の一部では、<xref:System.Windows.Forms.SaveFileDialog>クラス) は 1 から始まるインデックスを使用します。 これは、ファイルをバイナリ形式ではなくプレーン テキストで保存する場合など、データを特定の形式で保存するコードを記述する場合に重要です。 このプロパティは、次のコード例に示されています。  
  
    ```vb  
    Private Sub Button2_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button2.Click  
       ' Displays a SaveFileDialog so the user can save the Image  
       ' assigned to Button2.  
       Dim saveFileDialog1 As New SaveFileDialog()  
       saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif"  
       saveFileDialog1.Title = "Save an Image File"  
       saveFileDialog1.ShowDialog()  
  
       ' If the file name is not an empty string open it for saving.  
       If saveFileDialog1.FileName <> "" Then  
          ' Saves the Image via a FileStream created by the OpenFile method.  
          Dim fs As System.IO.FileStream = Ctype _  
             (saveFileDialog1.OpenFile(), System.IO.FileStream)  
          ' Saves the Image in the appropriate ImageFormat based upon the  
          ' file type selected in the dialog box.  
          ' NOTE that the FilterIndex property is one-based.  
          Select Case saveFileDialog1.FilterIndex  
             Case 1  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Jpeg)  
  
             Case 2  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Bmp)  
  
             Case 3  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Gif)  
           End Select  
  
           fs.Close()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button2_Click(object sender, System.EventArgs e)  
    {  
       // Displays a SaveFileDialog so the user can save the Image  
       // assigned to Button2.  
       SaveFileDialog saveFileDialog1 = new SaveFileDialog();  
       saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";  
       saveFileDialog1.Title = "Save an Image File";  
       saveFileDialog1.ShowDialog();  
  
       // If the file name is not an empty string open it for saving.  
       if(saveFileDialog1.FileName != "")  
       {  
          // Saves the Image via a FileStream created by the OpenFile method.  
          System.IO.FileStream fs =   
             (System.IO.FileStream)saveFileDialog1.OpenFile();  
          // Saves the Image in the appropriate ImageFormat based upon the  
          // File type selected in the dialog box.  
          // NOTE that the FilterIndex property is one-based.  
          switch(saveFileDialog1.FilterIndex)  
          {  
             case 1 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Jpeg);  
             break;  
  
             case 2 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Bmp);  
             break;  
  
             case 3 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Gif);  
             break;  
          }  
  
       fs.Close();  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void button2_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Displays a SaveFileDialog so the user can save the Image  
          // assigned to Button2.  
          SaveFileDialog ^ saveFileDialog1 = new SaveFileDialog();  
          saveFileDialog1->Filter =   
             "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";  
          saveFileDialog1->Title = "Save an Image File";  
          saveFileDialog1->ShowDialog();  
          // If the file name is not an empty string, open it for saving.  
          if(saveFileDialog1->FileName != "")  
          {  
             // Saves the Image through a FileStream created by  
             // the OpenFile method.  
             System::IO::FileStream ^ fs =   
                safe_cast\<System::IO::FileStream*>(  
                saveFileDialog1->OpenFile());  
             // Saves the Image in the appropriate ImageFormat based on  
             // the file type selected in the dialog box.  
             // Note that the FilterIndex property is one based.  
             switch(saveFileDialog1->FilterIndex)  
             {  
                case 1 :  
                   this->button2->Image->Save(fs,  
                      System::Drawing::Imaging::ImageFormat::Jpeg);  
                   break;  
                case 2 :  
                   this->button2->Image->Save(fs,   
                      System::Drawing::Imaging::ImageFormat::Bmp);  
                   break;  
                case 3 :  
                   this->button2->Image->Save(fs,   
                      System::Drawing::Imaging::ImageFormat::Gif);  
                   break;  
             }  
          fs->Close();  
          }  
       }  
    ```  
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] および [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) フォームのコンストラクターに次のコードを追加して、イベント ハンドラーを登録します。  
  
    ```csharp  
    this.button2.Click += new System.EventHandler(this.button2_Click);  
    ```  
  
    ```cpp  
    this->button2->Click += gcnew  
       System::EventHandler(this, &Form1::button2_Click);  
    ```  
  
     ファイル ストリームの書き込みの詳細については、次を参照してください。<xref:System.IO.FileStream.BeginWrite%2A>と<xref:System.IO.FileStream.Write%2A>です。  
  
    > [!NOTE]
    >  などの特定のコントロール、<xref:System.Windows.Forms.RichTextBox>制御、ファイルを保存する機能があります。 詳細については、MSDN オンライン ライブラリの技術文書「[Windows フォーム ダイアログ ボックスの重要コード](http://go.microsoft.com/fwlink/?LinkID=102575)」の「SaveFileDialog コンポーネント」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.SaveFileDialog>  
 [SaveFileDialog コンポーネント](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)
