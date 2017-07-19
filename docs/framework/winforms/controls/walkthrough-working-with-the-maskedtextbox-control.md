---
title: "チュートリアル : MaskedTextBox コントロールの使用 | Microsoft Docs"
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
  - "入力, 制御 (検証するために)"
  - "MaskedTextBox コントロール [Windows フォーム], 検証"
  - "MaskedTextBox コントロール [Windows フォーム], チュートリアル"
  - "テキスト, コントロール (入力の)"
  - "ユーザー入力, 制御"
ms.assetid: df60565e-5447-4110-92a6-be1f6ff5faa3
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# チュートリアル : MaskedTextBox コントロールの使用
このチュートリアルでは、以下のタスクを行います。  
  
-   <xref:System.Windows.Forms.MaskedTextBox> コントロールを初期化します。  
  
-   <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> イベント ハンドラーを使用して、文字がマスクに従っていない場合にユーザーに警告します。  
  
-   <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> プロパティに型を割り当て、<xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> イベント ハンドラーを使用して、ユーザーがコミットしようとした値がその型に対して有効でない場合にユーザーに警告します。  
  
## プロジェクトの作成とコントロールの追加  
  
#### MaskedTextBox コントロールをフォームに追加するには  
  
1.  <xref:System.Windows.Forms.MaskedTextBox> コントロールを配置するフォームを開きます。  
  
2.  **ツールボックス**からフォームに <xref:System.Windows.Forms.MaskedTextBox> コントロールをドラッグします。  
  
3.  コントロールを右クリックし、**\[プロパティ\]** をクリックします。  **\[プロパティ\]** ウィンドウの **\[マスク\]** プロパティを選択し、プロパティ名の横の **\[...\]** \(省略記号\) ボタンをクリックします。  
  
4.  **\[定型入力\]** ダイアログ ボックスで、**\[日付 \(和暦\)\]** マスクを選択し、**\[OK\]** をクリックします。  
  
5.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> プロパティを `true` に設定します。  このプロパティを設定すると、マスク定義に違反する文字をユーザーが入力するたびに、短いビープ音が鳴ります。  
  
 \[マスク\] プロパティがサポートする文字の概要については、<xref:System.Windows.Forms.MaskedTextBox.Mask%2A> プロパティの「解説」を参照してください。  
  
## 入力エラーについてのユーザーへの警告  
  
#### マスク入力の拒否に対するバルーン ヒントの追加  
  
1.  **ツールボックス**に戻り、<xref:System.Windows.Forms.ToolTip> をフォームに追加します。  
  
2.  <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> イベントに対するイベント ハンドラーを作成します。この中では、入力エラーが発生したときに <xref:System.Windows.Forms.ToolTip> を表示させます。  バルーン ヒントは、5 秒が経過するか、またはユーザーがクリックするまでは表示されたままとなります。  
  
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
  
## 有効でない型についてのユーザーへの警告  
  
#### 無効なデータ型に対するバルーン ヒントの追加  
  
1.  フォームの <xref:System.Windows.Forms.Form.Load> イベント ハンドラーで、<xref:System.DateTime> 型を表す <xref:System.Type> オブジェクトを、<xref:System.Windows.Forms.MaskedTextBox> コントロールの <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> プロパティに対して割り当てます。  
  
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
  
## 参照  
 <xref:System.Windows.Forms.MaskedTextBox>   
 [MaskedTextBox コントロール](../../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md)