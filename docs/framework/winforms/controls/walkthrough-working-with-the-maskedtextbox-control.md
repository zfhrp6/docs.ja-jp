---
title: 'チュートリアル : MaskedTextBox コントロールの使用'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- input [Windows Forms], controlling to ensure validity
- MaskedTextBox control [Windows Forms], walkthroughs
- MaskedTextBox control [Windows Forms], validation
- user input [Windows Forms], controlling
- text [Windows Forms], controls for input
ms.assetid: df60565e-5447-4110-92a6-be1f6ff5faa3
ms.openlocfilehash: bcca6c5f5481d351a39a4e71532cc0f006075128
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538442"
---
# <a name="walkthrough-working-with-the-maskedtextbox-control"></a>チュートリアル : MaskedTextBox コントロールの使用
このチュートリアルでは、以下のタスクを行います。  
  
-   初期化中、<xref:System.Windows.Forms.MaskedTextBox>コントロール  
  
-   使用して、<xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected>文字がマスクに準拠していないときにユーザーに警告するイベント ハンドラー  
  
-   型を割り当てる、<xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A>プロパティを使用して、<xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted>をコミットしようとしている値の型の有効な場合、ユーザーのアラートを生成するイベント ハンドラー  
  
## <a name="creating-the-project-and-adding-a-control"></a>プロジェクトを作成して、コントロールの追加  
  
#### <a name="to-add-a-maskedtextbox-control-to-your-form"></a>MaskedTextBox コントロールをフォームに追加するには  
  
1.  配置するフォームを開いて、<xref:System.Windows.Forms.MaskedTextBox>コントロール。  
  
2.  ドラッグ、<xref:System.Windows.Forms.MaskedTextBox>から制御、**ツールボックス**をフォームにします。  
  
3.  コントロールを右クリックして選択**プロパティ**です。 **プロパティ**ウィンドウで、**マスク**プロパティをクリックして、**しています.** プロパティ名の横にある (省略記号) ボタンをクリックします。  
  
4.  **定型入力**ダイアログ ボックスで、**短い日付**マスクし、をクリックして**OK**です。  
  
5.  **プロパティ**ウィンドウのセット、<xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A>プロパティを`true`です。 このプロパティはにより、ビープ音を鳴らすたびに、ユーザーが、マスク定義に違反する文字を入力しようとしています。 です。  
  
 概要については、マスクのプロパティをサポートする文字のの「解説」セクションを参照してください、<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>プロパティです。  
  
## <a name="alert-the-user-to-input-errors"></a>入力エラーをユーザーに警告します。  
  
#### <a name="add-a-balloon-tip-for-rejected-mask-input"></a>拒否されたマスクの入力のバルーン ヒントを追加します。  
  
1.  戻り、**ツールボックス**を追加し、<xref:System.Windows.Forms.ToolTip>をフォームにします。  
  
2.  イベント ハンドラーを作成、<xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected>イベントを発生させる、<xref:System.Windows.Forms.ToolTip>入力エラーが発生します。 バルーン ヒントは引き続き、5 秒間のまたは、ユーザーがクリックするまで表示します。  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)   
    {  
        ... // Other initialization code  
        maskedTextBox1.Mask = "00/00/0000";  
        maskedTextBox1.MaskInputRejected += new MaskInputRejectedEventHandler(maskedTextBox1_MaskInputRejected)  
    }  
  
    void maskedTextBox1_MaskInputRejected(object sender, MaskInputRejectedEventArgs e)  
    {  
        toolTip1.ToolTipTitle = "Invalid Input";  
        toolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", maskedTextBox1, maskedTextBox1.Location, 5000);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load  
        Me.ToolTip1.IsBalloon = True  
        Me.MaskedTextBox1.Mask = "00/00/0000"  
    End Sub  
  
    Private Sub MaskedTextBox1_MaskInputRejected(sender as Object, e as MaskInputRejectedEventArgs) Handles MaskedTextBox1.MaskInputRejected  
        ToolTip1.ToolTipTitle = "Invalid Input"  
        ToolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", MaskedTextBox1, 5000)  
    End Sub  
    ```  
  
## <a name="alert-the-user-to-a-type-that-is-not-valid"></a>無効な型をユーザーに警告します。  
  
#### <a name="add-a-balloon-tip-for-invalid-data-types"></a>無効なデータ型のバルーン ヒントを追加します。  
  
1.  フォームの<xref:System.Windows.Forms.Form.Load>、イベント ハンドラーを割り当てます、<xref:System.Type>オブジェクトを表す、<xref:System.DateTime>型を<xref:System.Windows.Forms.MaskedTextBox>コントロールの<xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A>プロパティ。  
  
    ```csharp  
    private void Form1_Load(Object sender, EventArgs e)  
    {  
        // Other code  
        maskedTextBox1.ValidatingType = typeof(System.DateTime);  
        maskedTextBox1.TypeValidationCompleted += new TypeValidationEventHandler(maskedTextBox1_TypeValidationCompleted);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(sender as Object, e as EventArgs)  
        // Other code  
        MaskedTextBox1.ValidatingType = GetType(System.DateTime)  
    End Sub  
    ```  
  
2.  <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> イベントのイベント ハンドラーを追加します。  
  
    ```csharp  
    public void maskedTextBox1_TypeValidationCompleted(object sender, TypeValidationEventArgs e)  
    {  
        if (!e.IsValidInput)  
        {  
           toolTip1.ToolTipTitle = "Invalid Date Value";  
           toolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000);  
           e.Cancel = true;  
        }  
    }  
    ```  
  
    ```vb  
    Public Sub MaskedTextBox1_TypeValidationCompleted(sender as Object, e as TypeValidationEventArgs)  
        If Not e.IsValidInput Then  
           ToolTip1.ToolTipTitle = "Invalid Date Value"  
           ToolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000)  
           e.Cancel = True  
        End If  
    End Sub  
    ```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.MaskedTextBox>  
 [MaskedTextBox コントロール](../../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md)
