---
title: "方法 : SaveFileDialog コンポーネントを使用してファイルを保存する | Microsoft Docs"
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
  - "ファイル, 保存"
  - "OpenFile メソッド, 保存 (ファイルを SaveFileDialog コンポーネントで)"
  - "SaveFileDialog コンポーネント, 保存 (ファイルを)"
  - "保存 (ファイルを)"
ms.assetid: 02e8f409-b83f-4707-babb-e71f6b223d90
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 方法 : SaveFileDialog コンポーネントを使用してファイルを保存する
<xref:System.Windows.Forms.SaveFileDialog> コンポーネントを使用すると、ユーザーはファイル システムを参照し、保存するファイルを選択できます。  このダイアログ ボックスは、ユーザーがダイアログ ボックス内で選択したファイルのパスと名前を返します。  ただし、ファイルを実際にディスクに書き込むためのコードを記述する必要があります。  
  
### SaveFileDialog コンポーネントを使用してファイルを保存するには  
  
-   **\[ファイルの保存\]** ダイアログ ボックスを表示し、ユーザーによって選択されたファイルを保存するメソッドを呼び出します。  
  
     <xref:System.Windows.Forms.SaveFileDialog> コンポーネントの <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> メソッドを使用して、ファイルを保存します。  このメソッドにより、書き込み先となる <xref:System.IO.Stream> オブジェクトが提供されます。  
  
     次のコード例では、<xref:System.Windows.Forms.DialogResult> プロパティを使用してファイルの名前を取得し、<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> メソッドを使用してファイルを保存しています。  <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> メソッドにより、ファイルの書き込み先となるストリームが提供されます。  
  
     次のコード例では、<xref:System.Windows.Forms.Button> コントロールにイメージが割り当てられています。  このボタンをクリックすると、ファイルの種類として .gif、.jpeg、および .bmp を許可するフィルターと共に、<xref:System.Windows.Forms.SaveFileDialog> コンポーネントがインスタンス化されます。  \[ファイルの保存\] ダイアログ ボックスでこれらの種類のファイルが選択されると、ボタンのイメージが保存されます。  
  
    > [!IMPORTANT]
    >  <xref:System.Windows.Forms.FileDialog.FileName%2A> プロパティを取得または設定するには、アセンブリに対して、<xref:System.Security.Permissions.FileIOPermission?displayProperty=fullName> クラスから特権レベルが与えられている必要があります。  完全には信頼できないコンテキストでプロセスを実行している場合は、権限不足のため例外がスローされることがあります。  詳細については、「[コード アクセス セキュリティの基礎](../../../../docs/framework/misc/code-access-security-basics.md)」を参照してください。  
  
     この例のコードは、フォームに <xref:System.Windows.Forms.Button> コントロールがあり、その <xref:System.Windows.Forms.ButtonBase.Image%2A> プロパティが .gif、.jpeg、または .bmp のファイルに設定されていることを想定して書かれています。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.FileDialog> クラスの <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> プロパティ \(継承により <xref:System.Windows.Forms.SaveFileDialog> クラスの一部\) では、1 から始まるインデックスが使用されます。  これは、ファイルをバイナリ形式ではなくプレーン テキストで保存する場合など、データを特定の形式で保存するコードを記述する場合に重要です。  このプロパティは、次のコード例に示されています。  
  
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
                safe_cast<System::IO::FileStream*>(  
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
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] および [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) フォームのコンストラクターに次のコードを挿入してイベント ハンドラーを登録します。  
  
    ```csharp  
    this.button2.Click += new System.EventHandler(this.button2_Click);  
  
    ```  
  
    ```cpp  
    this->button2->Click += gcnew  
       System::EventHandler(this, &Form1::button2_Click);  
    ```  
  
     ファイル ストリームの書き込みの詳細については、「[FileStream.BeginWrite メソッド](frlrfSystemIOFileStreamClassBeginWriteTopic)」および「[FileStream.Write メソッド](https://msdn.microsoft.com/en-us/library/system.io.filestream.write.aspx)」を参照してください。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.RichTextBox> コントロールなど、一部のコントロールには、ファイルを保存する機能があります。  詳細については、MSDN オンライン ライブラリの技術文書「[Essential Code for Windows Forms Dialog Boxes](http://go.microsoft.com/fwlink/?LinkID=102575)」の「SaveFileDialog Component」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.SaveFileDialog>   
 [SaveFileDialog コンポーネント](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)