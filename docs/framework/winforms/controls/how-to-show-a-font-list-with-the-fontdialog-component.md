---
title: "方法 : FontDialog コンポーネントを使用してフォントの一覧を表示する | Microsoft Docs"
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
  - "フォント ダイアログ ボックス, 表示"
  - "Font プロパティ, 設定 (FontDialog コンポーネントで)"
  - "FontDialog コンポーネント [Windows フォーム]"
  - "フォント, 属性"
  - "フォント, 選択"
  - "フォント, 表示 (一覧を)"
ms.assetid: 35692c1b-0937-4b7a-9207-1ae6bdc244a0
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : FontDialog コンポーネントを使用してフォントの一覧を表示する
[FontDialog](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md) コンポーネントを使用すると、ユーザーはフォントを選択したり、フォントの幅やサイズなどの表示属性を変更したりできます。  
  
 ダイアログ ボックスで選択されたフォントは、<xref:System.Windows.Forms.FontDialog.Font%2A> プロパティに返されます。  そのため、ユーザーによって選択されたフォントは、プロパティを読み取るのと同じように簡単に利用できます。  
  
### FontDialog コンポーネントを使用してフォントのプロパティを選択するには  
  
1.  <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> メソッドを使用してダイアログ ボックスを表示します。  
  
2.  <xref:System.Windows.Forms.DialogResult> プロパティを使用して、ダイアログ ボックスがどのように閉じられたかを確認します。  
  
3.  <xref:System.Windows.Forms.FontDialog.Font%2A> プロパティを使用して、目的のフォントを設定します。  
  
     次のコード例では、<xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーで <xref:System.Windows.Forms.FontDialog> コンポーネントを開いています。  ユーザーがフォントを選択して **\[OK\]** をクリックすると、フォーム上の <xref:System.Windows.Forms.TextBox> コントロールの <xref:System.Windows.Forms.FontDialog.Font%2A> プロパティが、選択されたフォントに設定されます。  この例のコードは、フォームに <xref:System.Windows.Forms.Button> コントロールと <xref:System.Windows.Forms.TextBox> コントロール、および <xref:System.Windows.Forms.FontDialog> コンポーネントがあることを想定して書かれています。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       If FontDialog1.ShowDialog() = DialogResult.OK Then  
          TextBox1.Font = FontDialog1.Font  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(fontDialog1.ShowDialog() == DialogResult.OK)  
       {  
          textBox1.Font = fontDialog1.Font;  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if(fontDialog1->ShowDialog() == DialogResult::OK)  
          {  
             textBox1->Font = fontDialog1->Font;  
          }  
       }  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] および [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) フォームのコンストラクターに次のコードを挿入してイベント ハンドラーを登録します。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.FontDialog>   
 [FontDialog コンポーネント](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md)