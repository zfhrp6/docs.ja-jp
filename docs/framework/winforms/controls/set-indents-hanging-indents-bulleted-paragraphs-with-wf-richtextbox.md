---
title: "方法 : Windows フォームの RichTextBox コントロールを使用してインデント、ぶら下げインデント、および箇条書き段落を設定する | Microsoft Docs"
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
  - "例 [Windows フォーム], テキスト ボックス"
  - "RichTextBox コントロール [Windows フォーム], 設定 (インデントと箇条書きを)"
  - "RTF ファイル, 書式指定 (RichTextBox コントロールで)"
  - "テキスト ボックス, 箇条書き"
  - "テキスト ボックス, 設定 (インデントを)"
ms.assetid: abfb40e6-5642-4691-8ec1-9d9ae91688dc
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : Windows フォームの RichTextBox コントロールを使用してインデント、ぶら下げインデント、および箇条書き段落を設定する
Windows フォームの <xref:System.Windows.Forms.RichTextBox> コントロールには、表示するテキストの書式を設定する数多くのオプションがあります。  <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> プロパティを設定することにより、選択した段落を箇条書きとして設定できます。  また、<xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>、<xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>、および <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> の各プロパティを使用して、コントロールの左端または右端、およびテキストの他の行の左端を基準にして、段落のインデントを設定できます。  
  
### 段落を箇条書きに設定するには  
  
1.  <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> プロパティを `true` に設定します。  
  
    ```vb  
    RichTextBox1.SelectionBullet = True  
  
    ```  
  
    ```csharp  
    richTextBox1.SelectionBullet = true;  
  
    ```  
  
    ```cpp  
    richTextBox1->SelectionBullet = true;  
    ```  
  
### 段落にインデントを設定するには  
  
1.  <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> プロパティに、コントロールの左端とテキストの左端の間のピクセル数を示す整数を設定します。  
  
2.  <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> プロパティに、段落内のテキストの 1 行目の左端と同じ段落の 2 行目以降の左端の間のピクセル数を示す整数を設定します。  <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> プロパティの値は、1 行目の下で折り返されている段落の行にだけ適用されます。  
  
3.  <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> プロパティに、コントロールの右端とテキストの右端の間のピクセル数を示す整数を設定します。  
  
    ```vb  
    RichTextBox1.SelectionIndent = 8  
    RichTextBox1.SelectionHangingIndent = 3  
    RichTextBox1.SelectionRightIndent = 12  
  
    ```  
  
    ```csharp  
    richTextBox1.SelectionIndent = 8;  
    richTextBox1.SelectionHangingIndent = 3;  
    richTextBox1.SelectionRightIndent = 12;  
  
    ```  
  
    ```cpp  
    richTextBox1->SelectionIndent = 8;  
    richTextBox1->SelectionHangingIndent = 3;  
    richTextBox1->SelectionRightIndent = 12;  
    ```  
  
    > [!NOTE]
    >  これらのプロパティはすべて、選択したテキストを含む段落に適用されます。または、現在のカーソル位置から入力されるテキストに適用されます。  たとえば、ユーザーが段落内の 1 語を選択してインデントを調整すると、新しい設定はその語を含む段落全体に適用され、さらに、選択された段落の後に入力されるすべての段落にも適用されます。  テキストをプログラムで選択する方法については、「[TextBoxBase.Select メソッド](frlrfSystemWindowsFormsTextBoxBaseClassSelectTopic)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.RichTextBox>   
 [RichTextBox コントロール](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)   
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)