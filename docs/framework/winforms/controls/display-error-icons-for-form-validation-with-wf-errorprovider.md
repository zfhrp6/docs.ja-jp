---
title: '方法 : Windows フォーム ErrorProvider コンポーネントを使用してフォーム検証でエラー アイコンを表示する'
ms.date: 03/30/2017
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
ms.openlocfilehash: 237a61cc21a18805fa502c9870d8ea472ac54d71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527301"
---
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a><span data-ttu-id="ee2de-102">方法 : Windows フォーム ErrorProvider コンポーネントを使用してフォーム検証でエラー アイコンを表示する</span><span class="sxs-lookup"><span data-stu-id="ee2de-102">How to: Display Error Icons for Form Validation with the Windows Forms ErrorProvider Component</span></span>
<span data-ttu-id="ee2de-103">Windows フォームを使用することができます<xref:System.Windows.Forms.ErrorProvider>コンポーネントを無効なデータが入力されたときにエラー アイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee2de-103">You can use a Windows Forms <xref:System.Windows.Forms.ErrorProvider> component to display an error icon when the user enters invalid data.</span></span> <span data-ttu-id="ee2de-104">それらの間 タブし、検証コードを呼び出すために、フォーム上には、少なくとも 2 つのコントロールが必要です。</span><span class="sxs-lookup"><span data-stu-id="ee2de-104">You must have at least two controls on the form in order to tab between them and thereby invoke the validation code.</span></span>  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a><span data-ttu-id="ee2de-105">コントロールの値が無効である場合は、エラー アイコンを表示するには</span><span class="sxs-lookup"><span data-stu-id="ee2de-105">To display an error icon when a control's value is invalid</span></span>  
  
1.  <span data-ttu-id="ee2de-106">2 つのコントロールを追加 — たとえば、テキスト ボックス: Windows フォームにします。</span><span class="sxs-lookup"><span data-stu-id="ee2de-106">Add two controls — for example, text boxes — to a Windows Form.</span></span>  
  
2.  <span data-ttu-id="ee2de-107">追加、<xref:System.Windows.Forms.ErrorProvider>コンポーネントをフォームにします。</span><span class="sxs-lookup"><span data-stu-id="ee2de-107">Add an <xref:System.Windows.Forms.ErrorProvider> component to the form.</span></span>  
  
3.  <span data-ttu-id="ee2de-108">最初のコントロールを選択し、コードを追加してその<xref:System.Windows.Forms.Control.Validating>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="ee2de-108">Select the first control and add code to its <xref:System.Windows.Forms.Control.Validating> event handler.</span></span> <span data-ttu-id="ee2de-109">このコードを正しく実行するためには、プロシージャは、イベントに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee2de-109">In order for this code to run properly, the procedure must be connected to the event.</span></span> <span data-ttu-id="ee2de-110">詳細については、次を参照してください。[する方法: Windows フォームの時間の実行時のイベント ハンドラーの作成](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="ee2de-110">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
     <span data-ttu-id="ee2de-111">次のコードは、ユーザーが入力したデータの妥当性をテストします。データが有効でない場合、<xref:System.Windows.Forms.ErrorProvider.SetError%2A>メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ee2de-111">The following code tests the validity of the data the user has entered; if the data is invalid, the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method is called.</span></span> <span data-ttu-id="ee2de-112">最初の引数、<xref:System.Windows.Forms.ErrorProvider.SetError%2A>メソッドでは、横にアイコンを表示するコントロールを指定します。</span><span class="sxs-lookup"><span data-stu-id="ee2de-112">The first argument of the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method specifies which control to display the icon next to.</span></span> <span data-ttu-id="ee2de-113">2 番目の引数は、表示するエラー テキストです。</span><span class="sxs-lookup"><span data-stu-id="ee2de-113">The second argument is the error text to display.</span></span>  
  
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
  
     <span data-ttu-id="ee2de-114">(Visual C# の場合、 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)])、イベント ハンドラーを登録するフォームのコンス トラクターに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="ee2de-114">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4.  <span data-ttu-id="ee2de-115">プロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="ee2de-115">Run the project.</span></span> <span data-ttu-id="ee2de-116">(この例では、数値以外) では無効なデータを最初のコントロールとし、2 番目のタブに入力します。</span><span class="sxs-lookup"><span data-stu-id="ee2de-116">Type invalid (in this example, non-numeric) data into the first control, and then tab to the second.</span></span> <span data-ttu-id="ee2de-117">エラー アイコンが表示されたら、ポイントにマウス ポインターがエラーのテキストを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee2de-117">When the error icon is displayed, point at it with the mouse pointer to see the error text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee2de-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="ee2de-118">See Also</span></span>  
 <xref:System.Windows.Forms.ErrorProvider.SetError%2A>  
 [<span data-ttu-id="ee2de-119">ErrorProvider コンポーネントの概要</span><span class="sxs-lookup"><span data-stu-id="ee2de-119">ErrorProvider Component Overview</span></span>](../../../../docs/framework/winforms/controls/errorprovider-component-overview-windows-forms.md)  
 [<span data-ttu-id="ee2de-120">方法: Windows フォーム ErrorProvider コンポーネントで DataSet 内にエラーを表示する</span><span class="sxs-lookup"><span data-stu-id="ee2de-120">How to: View Errors Within a DataSet with the Windows Forms ErrorProvider Component</span></span>](../../../../docs/framework/winforms/controls/view-errors-within-a-dataset-with-wf-errorprovider-component.md)
