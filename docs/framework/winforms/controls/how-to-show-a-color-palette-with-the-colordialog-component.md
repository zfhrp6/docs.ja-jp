---
title: "方法 : ColorDialog コンポーネントを使用してカラー パレットを表示する | Microsoft Docs"
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
  - "色のダイアログ ボックス, 表示 (カラー パレットを)"
  - "カラー パレット, ダイアログ ボックス"
  - "カラー パレット, 表示 (ColorDialog コンポーネントで)"
  - "Color プロパティ"
  - "ColorDialog コンポーネント, 表示 (カラー パレットを)"
  - "色, 許可 (ユーザーに選択を)"
  - "色, 表示 (パレットを)"
  - "パレット, 表示 (カラーを)"
ms.assetid: ee050f61-dbc8-4436-ba22-51360981ab48
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : ColorDialog コンポーネントを使用してカラー パレットを表示する
[ColorDialog](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md) コンポーネントは、色のパレットを表示し、ユーザーが選択した色を含むプロパティを返します。  
  
### ColorDialog コンポーネントを使用して色を選択するには  
  
1.  <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> メソッドを使用してダイアログ ボックスを表示します。  
  
2.  <xref:System.Windows.Forms.DialogResult> プロパティを使用して、ダイアログ ボックスがどのように閉じられたかを確認します。  
  
3.  <xref:System.Windows.Forms.ColorDialog> コンポーネントの <xref:System.Windows.Forms.ColorDialog.Color%2A> プロパティを使用して、選択された色を設定します。  
  
     次のコード例では、<xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーで <xref:System.Windows.Forms.ColorDialog> コンポーネントを開いています。  ユーザーが色を選択して **\[OK\]** をクリックすると、<xref:System.Windows.Forms.Button> コントロールの背景色が選択された色に設定されます。  この例のコードは、フォームに <xref:System.Windows.Forms.Button> コントロールと <xref:System.Windows.Forms.ColorDialog> コンポーネントがあることを想定して書かれています。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button1.Click  
       If ColorDialog1.ShowDialog() = DialogResult.OK Then  
          Button1.BackColor = ColorDialog1.Color  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(colorDialog1.ShowDialog() == DialogResult.OK)  
       {  
          button1.BackColor = colorDialog1.Color;  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,   
          System::EventArgs ^ e)  
       {  
          if(colorDialog1->ShowDialog() == DialogResult::OK)  
          {  
             button1->BackColor = colorDialog1->Color;  
          }  
       }  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) フォームのコンストラクターに次のコードを挿入してイベント ハンドラーを登録します。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
  
    ```  
  
    ```cpp  
    this->button1->Click +=   
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.ColorDialog>   
 [ColorDialog コンポーネント](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)