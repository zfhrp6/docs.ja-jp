---
title: '方法 : Windows フォームで ToolStrip コントロールの AutoComplete を有効にする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutoComplete [Windows Forms], examples
- toolbars [Windows Forms], AutoComplete
- examples [Windows Forms], toolbars
- AutoComplete [Windows Forms], enabling in toolbars
- ToolStripComboBox class [Windows Forms], examples
- ToolStrip control [Windows Forms], AutoComplete
ms.assetid: fd66d085-1af1-45d4-930a-cde944da2e16
ms.openlocfilehash: c5836b03ad185d4a31a24dfea46db54214ac54b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enable-autocomplete-in-toolstrip-controls-in-windows-forms"></a>方法 : Windows フォームで ToolStrip コントロールの AutoComplete を有効にする
次の手順を組み合わせて、<xref:System.Windows.Forms.ToolStripLabel>で、<xref:System.Windows.Forms.ToolStripComboBox>を削除できる最近など、アイテムの一覧を表示する Web サイトにアクセスします。 リスト内の項目のいずれかの最初の文字に一致する文字を入力すると、アイテムがすぐに表示されます。  
  
> [!NOTE]
>  オート コンプリートと協力`ToolStrip`と連携して従来のコントロールなどのと同じ方法でコントロール<xref:System.Windows.Forms.ComboBox>と<xref:System.Windows.Forms.TextBox>です。  
  
### <a name="to-enable-autocomplete-in-a-toolstrip-control"></a>ToolStrip コントロールの AutoComplete を有効にするには  
  
1.  作成、<xref:System.Windows.Forms.ToolStrip>を制御し、項目を追加します。  
  
    ```vb  
    ToolStrip1 = New System.Windows.Forms.ToolStrip  
    ToolStrip1.Items.AddRange(New System.Windows.Forms.ToolStripItem()_  
        {ToolStripLabel1, ToolStripComboBox1})  
    ```  
  
    ```csharp  
    toolStrip1 = new System.Windows.Forms.ToolStrip();  
    toolStrip1.Items.AddRange(new System.Windows.Forms.ToolStripItem[]   
        {toolStripLabel1, toolStripComboBox1});  
    ```  
  
2.  設定、<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>ラベルにコンボ ボックスのプロパティに<xref:System.Windows.Forms.ToolStripItemOverflow.Never>リストが常に、フォームのサイズに関係なく使用できるようにします。  
  
    ```vb  
    ToolStripLabel1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    ToolStripComboBox1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
    ```csharp  
    toolStripLabel1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    toolStripComboBox1.Overflow = System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
3.  単語、項目のコレクションに追加、<xref:System.Windows.Forms.ToolStripComboBox>コントロール。  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
    ```  
  
4.  設定、<xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A>コンボ ボックスのプロパティ<xref:System.Windows.Forms.AutoCompleteMode.Append>です。  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
    ```  
  
5.  設定、<xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A>コンボ ボックスのプロパティ<xref:System.Windows.Forms.AutoCompleteSource.ListItems>です。  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteSource = _  
        System.Windows.Forms.AutoCompleteSource.ListItems  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteSource = System.Windows.Forms.AutoCompleteSource.ListItems;  
    ```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripLabel>  
 <xref:System.Windows.Forms.ToolStripComboBox>  
 <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteMode%2A>  
 <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteSource%2A>  
 [ToolStrip コントロールの概要](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [ToolStrip コントロールのアーキテクチャ](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [ToolStrip テクノロジの概要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
