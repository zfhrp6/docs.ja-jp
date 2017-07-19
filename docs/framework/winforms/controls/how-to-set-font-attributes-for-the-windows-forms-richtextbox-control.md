---
title: "方法 : Windows フォームの RichTextBox コントロールのフォント属性を設定する | Microsoft Docs"
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
  - ".rtf ファイル, 書式指定 (RichTextBox コントロールで)"
  - "フォント, 変更 (RichTextBox コントロールの属性を)"
  - "書式設定 [Windows フォーム]"
  - "RichTextBox コントロール [Windows フォーム], 設定 (フォント属性を)"
  - "RTF ファイル, 書式指定 (RichTextBox コントロールで)"
  - "テキスト [Windows フォーム]"
  - "テキスト ボックス, 書式設定 (テキストの)"
ms.assetid: 2bc23ddb-0529-4489-a1a2-ad253cb43f9a
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : Windows フォームの RichTextBox コントロールのフォント属性を設定する
Windows フォームの <xref:System.Windows.Forms.RichTextBox> コントロールには、表示するテキストの書式を設定する数多くのオプションがあります。  <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> プロパティを使用して、選択した文字を太字や斜体にしたり、下線を付けたりできます。  また、このプロパティを使用して、選択した文字のサイズやタイプフェイスも変更できます。  <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> プロパティを使用すると、選択した文字の色を変更できます。  
  
### 文字の外観を変更するには  
  
1.  <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> プロパティに適切なフォントを設定します。  
  
     アプリケーションでユーザーがフォント ファミリ、サイズ、およびタイプフェイスを設定できるようにするには、通常、<xref:System.Windows.Forms.FontDialog> コンポーネントを使用します。  概要については、「[FontDialog コンポーネントの概要](../../../../docs/framework/winforms/controls/fontdialog-component-overview-windows-forms.md)」を参照してください。  
  
2.  <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> プロパティに適切な色を設定します。  
  
     アプリケーションでユーザーが色を設定できるようにするには、通常、<xref:System.Windows.Forms.ColorDialog> コンポーネントを使用します。  概要については、「[ColorDialog コンポーネントの概要](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md)」を参照してください。  
  
    ```vb  
    RichTextBox1.SelectionFont = New Font("Tahoma", 12, FontStyle.Bold)  
    RichTextBox1.SelectionColor = System.Drawing.Color.Red  
  
    ```  
  
    ```csharp  
    richTextBox1.SelectionFont = new Font("Tahoma", 12, FontStyle.Bold);  
    richTextBox1.SelectionColor = System.Drawing.Color.Red;  
  
    ```  
  
    ```cpp  
    richTextBox1->SelectionFont =  
       gcnew System::Drawing::Font("Tahoma", 12, FontStyle::Bold);  
    richTextBox1->SelectionColor = System::Drawing::Color::Red;  
    ```  
  
    > [!NOTE]
    >  これらのプロパティは、選択したテキストだけに適用されます。テキストが選択されていない場合は、現在のカーソル位置に入力されるテキストに適用されます。  テキストをプログラムで選択する方法については、「[Select メソッド](frlrfSystemWindowsFormsTextBoxBaseClassSelectTopic)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.RichTextBox>   
 [RichTextBox コントロール](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)   
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)