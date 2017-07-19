---
title: "方法 : Windows フォームの RichTextBox コントロールを使用して Web スタイルのリンクを表示する | Microsoft Docs"
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
  - "例 [Windows フォーム], テキスト ボックス"
  - "RichTextBox コントロール [Windows フォーム], リンク (Web ページに)"
  - "テキスト ボックス, 表示 (Web リンクを)"
ms.assetid: 95089a37-a202-4f7a-94ee-6ee312908851
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : Windows フォームの RichTextBox コントロールを使用して Web スタイルのリンクを表示する
Windows フォームの <xref:System.Windows.Forms.RichTextBox> コントロールでは、Web リンクに色と下線を付けて表示できます。  リンクがクリックされたときにブラウザー ウィンドウを開いて、リンク テキストで指定されている Web サイトを表示するように、コードを記述できます。  
  
### RichTextBox コントロールで Web ページにリンクするには  
  
1.  <xref:System.Windows.Forms.RichTextBox.Text%2A> プロパティに、有効な URL \("http:\/\/www.microsoft.com\/japan" など\) を含む文字列を設定します。  
  
2.  <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> プロパティが `true` \(既定値\) に設定されていることを確認します。  
  
3.  <xref:System.Diagnostics.Process> オブジェクトの新しいグローバル インスタンスを作成します。  
  
4.  ブラウザーに目的のテキストを送信する <xref:System.Windows.Forms.RichTextBox.LinkClicked> イベントのイベント ハンドラーを記述します。  
  
     次の例では、<xref:System.Windows.Forms.RichTextBox.LinkClicked> イベントで Internet Explorer のインスタンスが開き、<xref:System.Windows.Forms.RichTextBox> コントロールの <xref:System.Windows.Forms.RichTextBox.Text%2A> プロパティに指定された URL にアクセスします。  この例では、フォームに <xref:System.Windows.Forms.RichTextBox> コントロールがあると仮定しています。  
  
    > [!IMPORTANT]
    >  <xref:System.Diagnostics.Process.Start%2A?displayProperty=fullName> メソッドを呼び出すと権限の不足により <xref:System.Security.SecurityException> 例外が発生します。  詳細については、「[コード アクセス セキュリティの基礎](../../../../docs/framework/misc/code-access-security-basics.md)」を参照してください。  
  
    ```vb  
    Public p As New System.Diagnostics.Process  
    Private Sub RichTextBox1_LinkClicked _  
       (ByVal sender As Object, ByVal e As _  
       System.Windows.Forms.LinkClickedEventArgs) _  
       Handles RichTextBox1.LinkClicked  
          ' Call Process.Start method to open a browser  
          ' with link text as URL.  
          p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText)  
    End Sub  
  
    ```  
  
    ```csharp  
    public System.Diagnostics.Process p = new System.Diagnostics.Process();  
  
    private void richTextBox1_LinkClicked(object sender,   
    System.Windows.Forms.LinkClickedEventArgs e)  
    {  
       // Call Process.Start method to open a browser  
       // with link text as URL.  
       p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText);  
    }  
  
    ```  
  
    ```cpp  
    public:  
       System::Diagnostics::Process ^ p;  
  
    private:  
       void richTextBox1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkClickedEventArgs ^  e)  
       {  
          // Call Process.Start method to open a browser  
          // with link text as URL.  
          p = System::Diagnostics::Process::Start("IExplore.exe",  
             e->LinkText);  
       }  
    ```  
  
     \([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) プロセス `p` を初期化する必要があります。そのためには、フォームのコンストラクターに次のステートメントを挿入します。  
  
    ```cpp  
    p = gcnew System::Diagnostics::Process();  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) フォームのコンストラクターに次のコードを挿入してイベント ハンドラーを登録します。  
  
    ```csharp  
    this.richTextBox1.LinkClicked += new   
       System.Windows.Forms.LinkClickedEventHandler  
       (this.richTextBox1_LinkClicked);  
  
    ```  
  
    ```cpp  
    this->richTextBox1->LinkClicked += gcnew  
       System::Windows::Forms::LinkClickedEventHandler  
       (this, &Form1::richTextBox1_LinkClicked);  
    ```  
  
     作成したプロセスを実行したら、すぐにそれを停止することが重要です。  上に示したコードを参考にして、プロセスを停止するコードを次のように記述できます。  
  
    ```vb  
    Public Sub StopWebProcess()  
       p.Kill()  
    End Sub  
  
    ```  
  
    ```csharp  
    public void StopWebProcess()  
    {  
       p.Kill();  
    }  
  
    ```  
  
    ```cpp  
    public: void StopWebProcess()  
    {  
       p->Kill();  
    }  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>   
 <xref:System.Windows.Forms.RichTextBox.LinkClicked>   
 <xref:System.Windows.Forms.RichTextBox>   
 [RichTextBox コントロール](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)   
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)