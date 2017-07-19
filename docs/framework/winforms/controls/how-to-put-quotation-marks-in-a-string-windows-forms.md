---
title: "方法 : 文字列に引用符を挿入する (Windows フォーム) | Microsoft Docs"
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
  - "引用符"
  - "引用符, 追加 (テキスト ボックスの文字列に)"
  - "TextBox コントロール [Windows フォーム], 表示 (引用符を)"
ms.assetid: 68bdc3f3-4177-4eab-99cd-cac17a82b515
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : 文字列に引用符を挿入する (Windows フォーム)
テキストの文字列への引用符 \(" "\) の挿入が必要となることがあります。  次に例を示します。  
  
 She said, "You deserve a treat\!"  
  
 代わりに、<xref:Microsoft.VisualBasic.ControlChars.Quote> フィールドを定数として使用することもできます。  
  
### コードの文字列に引用符を挿入するには  
  
1.  [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] では、引用符が 2 つ並んでいる場合、埋め込み引用符として解釈されます。  [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] と [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)] では、エスケープ シーケンス \\" が埋め込み引用符として解釈されます。  たとえば、上記の文字列を作成するには、次のコードを使用します。  
  
    ```vb  
    Private Sub InsertQuote()  
       TextBox1.Text = "She said, ""You deserve a treat!"" "  
    End Sub  
  
    ```  
  
    ```csharp  
    private void InsertQuote(){  
       textBox1.Text = "She said, \"You deserve a treat!\" ";  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void InsertQuote()  
       {  
          textBox1->Text = "She said, \"You deserve a treat!\" ";  
       }  
    ```  
  
     または  
  
2.  引用符に相当する ASCII 文字または Unicode 文字を挿入します。  [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] では、ASCII 文字 \(34\) を使用します。  [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] では、Unicode 文字 \(\\u0022\) を使用します。  
  
    ```vb  
    Private Sub InsertAscii()  
       TextBox1.Text = "She said, " & Chr(34) & "You deserve a treat!" & Chr(34)  
    End Sub  
  
    ```  
  
    ```csharp  
    private void InsertAscii(){  
       textBox1.Text = "She said, " + '\u0022' + "You deserve a treat!" + '\u0022';  
    }  
    ```  
  
    > [!NOTE]
    >  この例で \\u0022 を使用することはできません。これは、基本文字セットの文字を指定するユニバーサル文字名を使用できないためです。  使用した場合は、C3851 が発生します。  詳細については、「[コンパイラ エラー C3851](../Topic/Compiler%20Error%20C3851.md)」を参照してください。  
  
     または  
  
3.  文字に定数を定義し、必要に応じて使用することもできます。  
  
    ```vb  
    Const quote As String = """"  
    TextBox1.Text = "She said, " & quote & "You deserve a treat!" & quote  
  
    ```  
  
    ```csharp  
    const string quote = "\"";  
    textBox1.Text = "She said, " + quote +  "You deserve a treat!"+ quote ;  
  
    ```  
  
    ```cpp  
    const String^ quote = "\"";  
    textBox1->Text = String::Concat("She said, ",  
       const_cast<String^>(quote), "You deserve a treat!",  
       const_cast<String^>(quote));  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.TextBox>   
 <xref:Microsoft.VisualBasic.ControlChars.Quote>   
 [TextBox コントロールの概要](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)   
 [方法 : Windows フォーム TextBox コントロールでのカーソル位置を制御する](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)   
 [方法 : Windows フォームの TextBox コントロールを使用してパスワード テキスト ボックスを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)   
 [方法 : 読み取り専用テキスト ボックスを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)   
 [方法 : Windows フォーム TextBox コントロールでテキストを選択する](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)   
 [方法 : Windows フォーム TextBox コントロールで複数行を表示する](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)   
 [TextBox コントロール](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)