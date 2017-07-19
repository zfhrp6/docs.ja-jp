---
title: "方法 : Windows フォームで ToolStrip コントロールの AutoComplete を有効にする | Microsoft Docs"
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
  - "AutoComplete, 有効化 (ツール バーで)"
  - "AutoComplete, 例"
  - "例 [Windows フォーム], ツール バー"
  - "ツール バー [Windows フォーム], AutoComplete"
  - "ToolStrip コントロール [Windows フォーム], AutoComplete"
  - "ToolStripComboBox クラス, 例"
ms.assetid: fd66d085-1af1-45d4-930a-cde944da2e16
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : Windows フォームで ToolStrip コントロールの AutoComplete を有効にする
最近アクセスした Web サイトなど、項目の一覧を表示するためにドロップダウンできる <xref:System.Windows.Forms.ToolStripComboBox> を、<xref:System.Windows.Forms.ToolStripLabel> と組み合わせる手順を次に示します。  ユーザーが入力した文字が一覧のいずれかの項目の最初の文字と一致した場合は、その項目が直ちに表示されます。  
  
> [!NOTE]
>  オートコンプリート機能は、<xref:System.Windows.Forms.ComboBox> や <xref:System.Windows.Forms.TextBox> などの従来のコントロールと同様に、`ToolStrip` コントロールでも使用できます。  
  
### ToolStrip コントロールで AutoComplete を有効にするには  
  
1.  <xref:System.Windows.Forms.ToolStrip> コントロールを作成して、項目を追加します。  
  
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
  
2.  フォームのサイズに関係なく一覧を常に使用できるように、ラベルとコンボ ボックスの <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> プロパティを <xref:System.Windows.Forms.ToolStripItemOverflow> に設定します。  
  
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
  
3.  <xref:System.Windows.Forms.ToolStripComboBox> コントロールの項目コレクションに単語を追加します。  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
  
    ```  
  
4.  コンボ ボックスの <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> プロパティを <xref:System.Windows.Forms.AutoCompleteMode> に設定します。  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
  
    ```  
  
5.  コンボ ボックスの <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> プロパティを <xref:System.Windows.Forms.AutoCompleteSource> に設定します。  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteSource = _  
        System.Windows.Forms.AutoCompleteSource.ListItems  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteSource = System.Windows.Forms.AutoCompleteSource.ListItems;  
  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.ToolStripLabel>   
 <xref:System.Windows.Forms.ToolStripComboBox>   
 <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteMode%2A>   
 <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteSource%2A>   
 [ToolStrip コントロールの概要](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)   
 [ToolStrip コントロールのアーキテクチャ](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)   
 [ToolStrip テクノロジの概要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)