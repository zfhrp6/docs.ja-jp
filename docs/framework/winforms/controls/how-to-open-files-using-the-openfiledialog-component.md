---
title: '方法 : OpenFileDialog コンポーネントを使用してファイルを開く'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: d7e1ebb319576aa7a38d55d8cb9f3652626966b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542276"
---
# <a name="how-to-open-files-using-the-openfiledialog-component"></a>方法 : OpenFileDialog コンポーネントを使用してファイルを開く
<xref:System.Windows.Forms.OpenFileDialog>コンポーネントにより、ユーザーが自分のコンピューターまたはネットワーク上のコンピューターのフォルダーを参照し、1 つまたは複数のファイルを選択します。 このダイアログ ボックスは、ユーザーがダイアログ ボックス内で選択したファイルのパスと名前を返します。  
  
 ユーザーが開くファイルを選択したら、そのファイルを開く方法として 2 とおりのアプローチがあります。 ファイル ストリームを使用する場合は、インスタンスを作成することができます、<xref:System.IO.StreamReader>クラスです。 また、使用することができます、<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>を選択したファイルを開くメソッドです。  
  
 次の最初の例では、<xref:System.Security.Permissions.FileIOPermission>が、アクセス許可のチェック (下の「セキュリティに関する注意」で説明) と、ファイル名にアクセスすることです。 この手法は、ローカル コンピューター、イントラネット、およびインターネットの各ゾーンから利用できます。 また、2 番目のメソッドも実行、<xref:System.Security.Permissions.FileIOPermission>権限チェックがより、イントラネットまたはインターネット ゾーンでのアプリケーションに適しています。  
  
### <a name="to-open-a-file-as-a-stream-using-the-openfiledialog-component"></a>OpenFileDialog コンポーネントを使用してファイルをストリームとして開くには  
  
1.  **[ファイルを開く]** ダイアログ ボックスを表示し、ユーザーによって選択されたファイルを開くメソッドを呼び出します。  
  
     1 つの方法は、使用する、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>メソッドのインスタンスを使用してファイルを開く ダイアログ ボックスを表示、<xref:System.IO.StreamReader>クラス ファイルを開きます。  
  
     使用して次の例、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Click>イベント ハンドラーのインスタンスを開く、<xref:System.Windows.Forms.OpenFileDialog>コンポーネントです。 ファイルが選択され、ユーザーが **[OK]** をクリックすると、ダイアログ ボックスで選択されたファイルが開きます。 この場合、ファイルの内容はメッセージ ボックスに表示され、ファイル ストリームが読み取られたことが単に示されます。  
  
    > [!IMPORTANT]
    >  取得または設定する、<xref:System.Windows.Forms.FileDialog.FileName%2A>プロパティをアセンブリが必要です、特権レベル許可によって、<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>クラスです。 部分的に信頼されたコンテキストで実行している場合、プロセスは、特権がないために例外をスローする可能性があります。 詳しくは、「[コード アクセス セキュリティの基礎](../../../../docs/framework/misc/code-access-security-basics.md)」をご覧ください。  
  
     この例では、フォームには、<xref:System.Windows.Forms.Button>コントロールと<xref:System.Windows.Forms.OpenFileDialog>コンポーネントです。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       If OpenFileDialog1.ShowDialog() = System.Windows.Forms.DialogResult.OK Then  
         Dim sr As New System.IO.StreamReader(OpenFileDialog1.FileName)  
         MessageBox.Show(sr.ReadToEnd)  
         sr.Close()  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(openFileDialog1.ShowDialog() == System.Windows.Forms.DialogResult.OK)  
       {  
          System.IO.StreamReader sr = new   
             System.IO.StreamReader(openFileDialog1.FileName);  
          MessageBox.Show(sr.ReadToEnd());  
          sr.Close();  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if(openFileDialog1->ShowDialog() == System::Windows::Forms::DialogResult::OK)  
          {  
             System::IO::StreamReader ^ sr = gcnew  
                System::IO::StreamReader(openFileDialog1->FileName);  
             MessageBox::Show(sr->ReadToEnd());  
             sr->Close();  
          }  
       }  
    ```  
  
     (Visual c# と[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)])、イベント ハンドラーを登録するフォームのコンス トラクターに次のコードを追加します。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
    > [!NOTE]
    >  ファイル ストリームからの読み取りの詳細については、次を参照してください。<xref:System.IO.FileStream.BeginRead%2A>と<xref:System.IO.FileStream.Read%2A>です。  
  
### <a name="to-open-a-file-as-a-file-using-the-openfiledialog-component"></a>OpenFileDialog コンポーネントを使用してファイルをファイルとして開くには  
  
1.  使用して、 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>  ダイアログ ボックスを表示する方法、および<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>ファイルを開くメソッドです。  
  
     <xref:System.Windows.Forms.OpenFileDialog>コンポーネントの<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>メソッドは、ファイルを構成するバイトを返します。 これらのバイトにより、読み取り元のストリームが提供されます。 次の例で、<xref:System.Windows.Forms.OpenFileDialog>コンポーネントが"cursor"にフィルターを適用し、ユーザーがファイル名拡張子を持つファイルだけを選択できるようにインスタンス化される`.cur`です。 `.cur` ファイルが選択されると、フォームのカーソルが選択されたカーソルに設定されます。  
  
    > [!IMPORTANT]
    >  呼び出す、<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>メソッド、アセンブリが必要です、特権レベル許可によって、<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>クラスです。 部分的に信頼されたコンテキストで実行している場合、プロセスは、特権がないために例外をスローする可能性があります。 詳しくは、「[コード アクセス セキュリティの基礎](../../../../docs/framework/misc/code-access-security-basics.md)」をご覧ください。  
  
     この例では、フォームには、<xref:System.Windows.Forms.Button>コントロール。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       ' Displays an OpenFileDialog so the user can select a Cursor.  
       Dim openFileDialog1 As New OpenFileDialog()  
       openFileDialog1.Filter = "Cursor Files|*.cur"  
       openFileDialog1.Title = "Select a Cursor File"  
  
       ' Show the Dialog.  
       ' If the user clicked OK in the dialog and   
       ' a .CUR file was selected, open it.  
       If openFileDialog1.ShowDialog() = System.Windows.Forms.DialogResult.OK Then  
         ' Assign the cursor in the Stream to the Form's Cursor property.  
         Me.Cursor = New Cursor(openFileDialog1.OpenFile())  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // Displays an OpenFileDialog so the user can select a Cursor.  
       OpenFileDialog openFileDialog1 = new OpenFileDialog();  
       openFileDialog1.Filter = "Cursor Files|*.cur";  
       openFileDialog1.Title = "Select a Cursor File";  
  
       // Show the Dialog.  
       // If the user clicked OK in the dialog and  
       // a .CUR file was selected, open it.  
        if (openFileDialog1.ShowDialog() == System.Windows.Forms.DialogResult.OK)  
       {  
          // Assign the cursor in the Stream to the Form's Cursor property.  
          this.Cursor = new Cursor(openFileDialog1.OpenFile());  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Displays an OpenFileDialog so the user can select a Cursor.  
          OpenFileDialog ^ openFileDialog1 = new OpenFileDialog();  
          openFileDialog1->Filter = "Cursor Files|*.cur";  
          openFileDialog1->Title = "Select a Cursor File";  
  
          // Show the Dialog.  
          // If the user clicked OK in the dialog and  
          // a .CUR file was selected, open it.  
          if (openFileDialog1->ShowDialog() == System::Windows::Forms::DialogResult::OK)  
          {  
             // Assign the cursor in the Stream to  
             // the Form's Cursor property.  
             this->Cursor = gcnew  
                System::Windows::Forms::Cursor(  
                openFileDialog1->OpenFile());  
          }  
       }  
    ```  
  
     (Visual c# と[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)])、イベント ハンドラーを登録するフォームのコンス トラクターに次のコードを追加します。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.OpenFileDialog>  
 [OpenFileDialog コンポーネント](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
