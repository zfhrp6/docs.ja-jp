---
title: "方法 : OpenFileDialog コンポーネントを使用してファイルを開く | Microsoft Docs"
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
  - "ファイル, 開く (OpenFileDialog コンポーネントを使用して)"
  - "OpenFile メソッド"
  - "OpenFile メソッド, OpenFileDialog コンポーネント"
  - "OpenFileDialog コンポーネント, 開く (ファイルを)"
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 方法 : OpenFileDialog コンポーネントを使用してファイルを開く
<xref:System.Windows.Forms.OpenFileDialog> コンポーネントを使用すると、ユーザーは、自分のコンピューターやネットワーク上の任意のコンピューターのフォルダーを参照し、1 つ以上のファイルを選択して開くことができます。  このダイアログ ボックスは、ユーザーがダイアログ ボックス内で選択したファイルのパスと名前を返します。  
  
 ユーザーが開くファイルを選択したら、そのファイルを開く方法として 2 とおりのアプローチがあります。  ファイル ストリームを使用する場合は、<xref:System.IO.StreamReader> クラスのインスタンスを作成します。  もう 1 つの方法は、<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> メソッドを使用して、選択されたファイルを開く方法です。  
  
 次に示す最初の例には、<xref:System.Security.Permissions.FileIOPermission> のアクセス許可チェック \(以降の「セキュリティに関するメモ」を参照\) が含まれますが、許可されるのはファイル名へのアクセスです。  この手法は、ローカル コンピューター、イントラネット、およびインターネットの各ゾーンから利用できます。  2 番目の方法でも <xref:System.Security.Permissions.FileIOPermission> のアクセス許可チェックが行われますが、この方法はイントラネット ゾーンまたはインターネット ゾーンのアプリケーションに適しています。  
  
### OpenFileDialog コンポーネントを使用してファイルをストリームとして開くには  
  
1.  **\[ファイルを開く\]** ダイアログ ボックスを表示し、ユーザーによって選択されたファイルを開くメソッドを呼び出します。  
  
     1 つのアプローチとしては、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> メソッドを使用して \[ファイルを開く\] ダイアログ ボックスを表示し、<xref:System.IO.StreamReader> クラスのインスタンスを使用してファイルを開きます。  
  
     次のコード例では、<xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーを使用して <xref:System.Windows.Forms.OpenFileDialog> コンポーネントのインスタンスを開いています。  ファイルが選択され、ユーザーが **\[OK\]** をクリックすると、ダイアログ ボックスで選択されたファイルが開きます。  この場合、ファイルの内容はメッセージ ボックスに表示され、ファイル ストリームが読み取られたことが単に示されます。  
  
    > [!IMPORTANT]
    >  <xref:System.Windows.Forms.FileDialog.FileName%2A> プロパティを取得または設定するには、アセンブリに対して、<xref:System.Security.Permissions.FileIOPermission?displayProperty=fullName> クラスから特権レベルが与えられている必要があります。  完全には信頼できないコンテキストでプロセスを実行している場合は、権限不足のため例外がスローされることがあります。  詳細については、「[コード アクセス セキュリティの基礎](../../../../docs/framework/misc/code-access-security-basics.md)」を参照してください。  
  
     この例のコードは、フォームに <xref:System.Windows.Forms.Button> コントロールと <xref:System.Windows.Forms.OpenFileDialog> コンポーネントがあることを想定して書かれています。  
  
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
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] および [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) フォームのコンストラクターに次のコードを挿入してイベント ハンドラーを登録します。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
    > [!NOTE]
    >  ファイル ストリームからの読み取りの詳細については、「[FileStream.BeginRead メソッド](frlrfSystemIOFileStreamClassBeginReadTopic)」および「[FileStream.Read メソッド](https://msdn.microsoft.com/en-us/library/system.io.filestream.read.aspx)」を参照してください。  
  
### OpenFileDialog コンポーネントを使用してファイルをファイルとして開くには  
  
1.  <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> メソッドを使用してダイアログ ボックスを表示し、<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> メソッドを使用してファイルを開きます。  
  
     <xref:System.Windows.Forms.OpenFileDialog> コンポーネントの <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> メソッドは、ファイルを構成するバイトを返します。  これらのバイトにより、読み取り元のストリームが提供されます。  次のコード例では、<xref:System.Windows.Forms.OpenFileDialog> コンポーネントが "カーソル" フィルターと共にインスタンス化され、ユーザーが拡張子 `.cur` のファイルだけを選択できるようになっています。  `.cur`  ファイルが選択されると、フォームのカーソルが選択されたカーソルに設定されます。  
  
    > [!IMPORTANT]
    >  <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> メソッドを呼び出すには、アセンブリに対して <xref:System.Security.Permissions.FileIOPermission?displayProperty=fullName> クラスで特権レベルが許可されている必要があります。  完全には信頼できないコンテキストでプロセスを実行している場合は、権限不足のため例外がスローされることがあります。  詳細については、「[コード アクセス セキュリティの基礎](../../../../docs/framework/misc/code-access-security-basics.md)」を参照してください。  
  
     この例のコードは、フォームに <xref:System.Windows.Forms.Button> コントロールがあることを想定して書かれています。  
  
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
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] および [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) フォームのコンストラクターに次のコードを挿入してイベント ハンドラーを登録します。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.OpenFileDialog>   
 [OpenFileDialog コンポーネント](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)