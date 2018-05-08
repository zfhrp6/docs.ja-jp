---
title: '方法: Windows フォームの RichTextBox コントロールのフォント属性を設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- .rtf files [Windows Forms], formatting in RichTextBox control
- fonts [Windows Forms], changing attributes in RichTextBox control
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting font attributes
- text [Windows Forms]
- text boxes [Windows Forms], formatting text
- formatting [Windows Forms]
ms.assetid: 2bc23ddb-0529-4489-a1a2-ad253cb43f9a
ms.openlocfilehash: 7c4c9362bb5a32bd8d5afc2b1edeb935d505fd19
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a>方法: Windows フォームの RichTextBox コントロールのフォント属性を設定する
Windows フォーム<xref:System.Windows.Forms.RichTextBox>コントロールが、表示されるテキストを書式設定するためのさまざまなオプションです。 ことができます、選択した文字太字、下線、または斜体などを使用して、<xref:System.Windows.Forms.RichTextBox.SelectionFont%2A>プロパティです。 また、このプロパティを使用して、選択した文字のサイズと書体を変更することもできます。 <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A>プロパティでは、選択した文字の色を変更することができます。  
  
### <a name="to-change-the-appearance-of-characters"></a>文字の外観を変更するには  
  
1.  設定、<xref:System.Windows.Forms.RichTextBox.SelectionFont%2A>プロパティを適切なフォントです。  
  
     ユーザーにアプリケーションでのフォント ファミリ、サイズ、およびフォントの設定を有効にするのには通常使用する、<xref:System.Windows.Forms.FontDialog>コンポーネントです。 概要については、「[FontDialog Component Overview](../../../../docs/framework/winforms/controls/fontdialog-component-overview-windows-forms.md)」 (FontDialog コンポーネントの概要) を参照してください。  
  
2.  設定、<xref:System.Windows.Forms.RichTextBox.SelectionColor%2A>プロパティを適切な色にします。  
  
     アプリケーションで色を設定するユーザーを有効にするのには通常使用する、<xref:System.Windows.Forms.ColorDialog>コンポーネントです。 概要については、「[ColorDialog Component Overview](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md)」 (ColorDialog コンポーネントの概要) を参照してください。  
  
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
    >  これらのプロパティは選択したテキストにのみ影響します。テキストが選択されていない場合は、現在の挿入ポイントの場所に入力されるテキストに影響します。 プログラムによってテキストを選択する方法の詳細については、次を参照してください。<xref:System.Windows.Forms.TextBoxBase.Select%2A>です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox コントロール](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
