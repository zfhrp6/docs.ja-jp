---
title: "方法 : Windows フォーム LinkLabel コントロールでオブジェクトまたは Web ページにリンクする | Microsoft Docs"
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
  - "例 [Windows フォーム], LinkLabel コントロール"
  - "リンク, ほかのフォームへの"
  - "LinkLabel コントロール [Windows フォーム], 例"
  - "LinkLabel コントロール [Windows フォーム], リンク (オブジェクトまたは Web ページに)"
  - "リンク, ほかのフォームへの"
  - "Web ページ リンク コントロール"
  - "Windows フォーム, リンク (オブジェクトに)"
  - "Windows フォーム, リンク (Web ページに)"
ms.assetid: 6c91c975-3cb7-4504-82f0-fc6255f8fb85
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : Windows フォーム LinkLabel コントロールでオブジェクトまたは Web ページにリンクする
Windows フォーム <xref:System.Windows.Forms.LinkLabel> コントロールを使用すると、フォーム上に Web スタイルのリンクを作成できます。  リンクをクリックしたときに、そのリンクにアクセスしたことがわかるように色を変更できます。  色の変更の詳細については、「[方法 : Windows フォーム LinkLabel コントロールの表示形式を変更する](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)」を参照してください。  
  
## 別のフォームへのリンク  
  
#### LinkLabel コントロールによって、別のフォームにリンクするには  
  
1.  <xref:System.Windows.Forms.LinkLabel.Text%2A> プロパティに適切なキャプションを設定します。  
  
2.  <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> プロパティを設定して、キャプションのどの部分をリンクとして表示するかを指定します。  どのように表示するかは、リンク ラベルの表示形式に関連するプロパティによって異なります。  <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> の値は、<xref:System.Windows.Forms.LinkLabel.LinkArea%2A> オブジェクトで表されます。このオブジェクトには、文字の開始位置と文字数を示す 2 つの数字が含まれています。  <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> プロパティは、\[プロパティ\] ウィンドウで、または次のような方法でコード内で設定できます。  
  
    ```vb  
    ' In this code example, the link area has been set to begin  
    ' at the first character and extend for eight characters.  
    ' You may need to modify this based on the text entered in Step 1.  
    LinkLabel1.LinkArea = New LinkArea(0, 8)  
  
    ```  
  
    ```csharp  
    // In this code example, the link area has been set to begin  
    // at the first character and extend for eight characters.  
    // You may need to modify this based on the text entered in Step 1.  
    linkLabel1.LinkArea = new LinkArea(0,8);  
  
    ```  
  
    ```cpp  
    // In this code example, the link area has been set to begin  
    // at the first character and extend for eight characters.  
    // You may need to modify this based on the text entered in Step 1.  
    linkLabel1->LinkArea = LinkArea(0,8);  
    ```  
  
3.  <xref:System.Windows.Forms.LinkLabel.LinkClicked> イベント ハンドラーで、<xref:System.Windows.Forms.Form.Show%2A> メソッドを呼び出してプロジェクトで別のフォームを開き、<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> プロパティを `true` に設定します。  
  
    > [!NOTE]
    >  クリックされた <xref:System.Windows.Forms.LinkLabel> コントロールへの参照が <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> クラスのインスタンスに含まれているため、`sender` オブジェクトをキャストする必要はありません。  
  
    ```vb  
    Protected Sub LinkLabel1_LinkClicked(ByVal Sender As System.Object, _  
       ByVal e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) _  
       Handles LinkLabel1.LinkClicked  
       ' Show another form.  
       Dim f2 As New Form()  
       f2.Show  
       LinkLabel1.LinkVisited = True  
    End Sub  
  
    ```  
  
    ```csharp  
    protected void linkLabel1_LinkClicked(object sender, System. Windows.Forms.LinkLabelLinkClickedEventArgs e)  
    {  
       // Show another form.  
       Form f2 = new Form();  
       f2.Show();  
       linkLabel1.LinkVisited = true;  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void linkLabel1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)  
       {  
          // Show another form.  
          Form ^ f2 = new Form();  
          f2->Show();  
          linkLabel1->LinkVisited = true;  
       }  
    ```  
  
## Web ページへのリンク  
 <xref:System.Windows.Forms.LinkLabel> コントロールを使用すると、既定のブラウザーで Web ページを表示することもできます。  
  
#### Internet Explorer を起動し、LinkLabel コントロールによって Web ページにリンクするには  
  
1.  <xref:System.Windows.Forms.LinkLabel.Text%2A> プロパティに適切なキャプションを設定します。  
  
2.  <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> プロパティを設定して、キャプションのどの部分をリンクとして表示するかを指定します。  
  
3.  <xref:System.Windows.Forms.LinkLabel.LinkClicked> イベント ハンドラーの例外処理ブロック内で第 2 のプロシージャを呼び出します。このプロシージャでは、<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> プロパティを `true` に設定し、<xref:System.Diagnostics.Process.Start%2A> メソッドを使用して既定のブラウザーを該当の URL で起動します。  <xref:System.Diagnostics.Process.Start%2A> メソッドを使用するには、<xref:System.Diagnostics?displayProperty=fullName> 名前空間への参照を追加する必要があります。  
  
    > [!IMPORTANT]
    >  部分的に信頼できる環境 \(共有ドライブなど\) で次のコードを実行した場合、`VisitLink` メソッドの呼び出し時に JIT コンパイラでエラーが発生します。  `System.Diagnostics.Process.Start` のステートメントが発生するリンク確認要求が発生します。  `VisitLink` メソッドの呼び出し時に例外をキャッチすると、次のコードで JIT コンパイラのエラーが発生しても正常に処理されるようになります。  
  
    ```vb  
    Private Sub LinkLabel1_LinkClicked(ByVal sender As System.Object, _  
       ByVal e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) _  
       Handles LinkLabel1.LinkClicked  
       Try  
          VisitLink()  
       Catch ex As Exception  
          ' The error message  
          MessageBox.Show("Unable to open link that was clicked.")  
       End Try  
    End Sub  
  
    Sub VisitLink()  
       ' Change the color of the link text by setting LinkVisited   
       ' to True.  
       LinkLabel1.LinkVisited = True  
       ' Call the Process.Start method to open the default browser   
       ' with a URL:  
       System.Diagnostics.Process.Start("http://www.microsoft.com")  
    End Sub  
  
    ```  
  
    ```csharp  
    private void linkLabel1_LinkClicked(object sender, System.Windows.Forms.LinkLabelLinkClickedEventArgs e)  
    {  
       try  
       {  
          VisitLink();  
       }  
       catch (Exception ex )  
       {  
          MessageBox.Show("Unable to open link that was clicked.");  
       }  
    }  
  
    private void VisitLink()  
    {  
       // Change the color of the link text by setting LinkVisited   
       // to true.  
       linkLabel1.LinkVisited = true;  
       //Call the Process.Start method to open the default browser   
       //with a URL:  
       System.Diagnostics.Process.Start("http://www.microsoft.com");  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void linkLabel1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)  
       {  
          try  
          {  
             VisitLink();  
          }  
          catch (Exception ^ ex)  
          {  
             MessageBox::Show("Unable to open link that was clicked.");  
          }  
       }  
    private:  
       void VisitLink()  
       {  
          // Change the color of the link text by setting LinkVisited   
          // to true.  
          linkLabel1->LinkVisited = true;  
          // Call the Process.Start method to open the default browser   
          // with a URL:  
          System::Diagnostics::Process::Start("http://www.microsoft.com");  
       }  
    ```  
  
## 参照  
 <xref:System.Diagnostics.Process.Start%2A?displayProperty=fullName>   
 [LinkLabel コントロールの概要](../../../../docs/framework/winforms/controls/linklabel-control-overview-windows-forms.md)   
 [方法 : Windows フォーム LinkLabel コントロールの表示形式を変更する](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)   
 [LinkLabel コントロール](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)