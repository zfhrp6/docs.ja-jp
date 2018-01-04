---
title: "方法 : Windows フォーム ErrorProvider コンポーネントを使用してフォーム検証でエラー アイコンを表示する"
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
- errors [Windows Forms], displaying to users
- error icons
- ErrorProvider component [Windows Forms], displaying error icons
- error messages [Windows Forms], displaying icons
ms.assetid: 3b681a32-9db4-497b-a34b-34980eabee46
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 738ca9670635f78e8cb04318b192127184766c3c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a>方法 : Windows フォーム ErrorProvider コンポーネントを使用してフォーム検証でエラー アイコンを表示する
Windows フォームを使用することができます<xref:System.Windows.Forms.ErrorProvider>コンポーネントを無効なデータが入力されたときにエラー アイコンが表示されます。 それらの間 タブし、検証コードを呼び出すために、フォーム上には、少なくとも 2 つのコントロールが必要です。  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a>コントロールの値が無効である場合は、エラー アイコンを表示するには  
  
1.  2 つのコントロールを追加 — たとえば、テキスト ボックス: Windows フォームにします。  
  
2.  追加、<xref:System.Windows.Forms.ErrorProvider>コンポーネントをフォームにします。  
  
3.  最初のコントロールを選択し、コードを追加してその<xref:System.Windows.Forms.Control.Validating>イベント ハンドラー。 このコードを正しく実行するためには、プロシージャは、イベントに接続する必要があります。 詳細については、次を参照してください。[する方法: Windows フォームの時間の実行時のイベント ハンドラーの作成](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md)です。  
  
     次のコードは、ユーザーが入力したデータの妥当性をテストします。データが有効でない場合、<xref:System.Windows.Forms.ErrorProvider.SetError%2A>メソッドが呼び出されます。 最初の引数、<xref:System.Windows.Forms.ErrorProvider.SetError%2A>メソッドでは、横にアイコンを表示するコントロールを指定します。 2 番目の引数は、表示するエラー テキストです。  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) フォームのコンストラクターに次のコードを挿入してイベント ハンドラーを登録します。  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4.  プロジェクトを実行します。 (この例では、数値以外) では無効なデータを最初のコントロールとし、2 番目のタブに入力します。 エラー アイコンが表示されたら、ポイントにマウス ポインターがエラーのテキストを参照してください。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.ErrorProvider.SetError%2A>  
 [ErrorProvider コンポーネントの概要](../../../../docs/framework/winforms/controls/errorprovider-component-overview-windows-forms.md)  
 [方法: Windows フォーム ErrorProvider コンポーネントで DataSet 内にエラーを表示する](../../../../docs/framework/winforms/controls/view-errors-within-a-dataset-with-wf-errorprovider-component.md)
