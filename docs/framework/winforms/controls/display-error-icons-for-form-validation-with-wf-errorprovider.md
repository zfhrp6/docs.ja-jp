---
title: "方法 : Windows フォーム ErrorProvider コンポーネントを使用してフォーム妥当性検査でエラー アイコンを表示する | Microsoft Docs"
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
  - "エラー アイコン"
  - "エラー メッセージ, 表示 (アイコンを)"
  - "ErrorProvider コンポーネント [Windows フォーム], 表示 (エラー アイコンを)"
  - "エラー [Windows フォーム], 表示 (ユーザーに)"
ms.assetid: 3b681a32-9db4-497b-a34b-34980eabee46
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : Windows フォーム ErrorProvider コンポーネントを使用してフォーム妥当性検査でエラー アイコンを表示する
Windows フォームの <xref:System.Windows.Forms.ErrorProvider> コンポーネントを使用すると、ユーザーが無効なデータを入力したときに、エラー アイコンを表示できます。  タブでフォーカスを移動して妥当性検査のコードを呼び出すには、フォーム上に少なくとも 2 つのコントロールが必要です。  
  
### コントロールの値が無効の場合にエラー アイコンを表示するには  
  
1.  Windows フォームにテキスト ボックスなどのコントロールを 2 つ追加します。  
  
2.  フォームに <xref:System.Windows.Forms.ErrorProvider> コンポーネントを追加します。  
  
3.  1 番目のコントロールを選択し、そのコントロールの <xref:System.Windows.Forms.Control.Validating> イベント ハンドラーにコードを追加します。  このコードを正しく実行するには、イベントにプロシージャを関連付ける必要があります。  詳細については、「[方法 : Windows フォームで実行時にイベント ハンドラーを作成する](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md)」を参照してください。  
  
     ユーザーが入力したデータの妥当性を検査するコードの例を次に示します。データが無効の場合は、<xref:System.Windows.Forms.ErrorProvider.SetError%2A> メソッドが呼び出されます。  <xref:System.Windows.Forms.ErrorProvider.SetError%2A> メソッドの 1 番目の引数は、隣にアイコンを表示するコントロールを指定します。  2 番目の引数は、表示するエラー テキストです。  
  
    ```vb  
    Private Sub TextBox1_Validating(ByVal Sender As Object, _  
       ByVal e As System.ComponentModel.CancelEventArgs) Handles _  
       TextBox1.Validating  
          If Not IsNumeric(TextBox1.Text) Then  
             ErrorProvider1.SetError(TextBox1, "Not a numeric value.")  
          Else  
             ' Clear the error.  
             ErrorProvider1.SetError(TextBox1, "")  
          End If  
    End Sub  
  
    ```  
  
    ```csharp  
    protected void textBox1_Validating (object sender,  
       System.ComponentModel.CancelEventArgs e)  
    {  
       try  
       {  
          int x = Int32.Parse(textBox1.Text);  
          errorProvider1.SetError(textBox1, "");  
       }  
       catch (Exception ex)  
       {  
          errorProvider1.SetError(textBox1, "Not an integer value.");  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       System::Void textBox1_Validating(System::Object ^  sender,  
          System::ComponentModel::CancelEventArgs ^  e)  
       {  
          try  
          {  
             int x = Int32::Parse(textBox1->Text);  
             errorProvider1->SetError(textBox1, "");  
          }  
          catch (System::Exception ^ ex)  
          {  
             errorProvider1->SetError(textBox1, "Not an integer value.");  
          }  
       }  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) フォームのコンストラクターに次のコードを挿入してイベント ハンドラーを登録します。  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4.  プロジェクトを実行します。  無効なデータ \(上の例では、数値以外のデータ\) を 1 番目のコントロールに入力し、タブで 2 番目のコントロールに移動します。  エラー アイコンが表示されたら、マウス ポインターでアイコンをポイントし、エラー テキストを表示します。  
  
## 参照  
 <xref:System.Windows.Forms.ErrorProvider.SetError%2A>   
 [ErrorProvider コンポーネントの概要](../../../../docs/framework/winforms/controls/errorprovider-component-overview-windows-forms.md)   
 [方法 : Windows フォーム ErrorProvider コンポーネントで DataSet 内にエラーを表示する](../../../../docs/framework/winforms/controls/view-errors-within-a-dataset-with-wf-errorprovider-component.md)