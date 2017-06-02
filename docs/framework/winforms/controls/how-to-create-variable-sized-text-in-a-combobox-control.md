---
title: "方法 : ComboBox コントロールにサイズ変更可能なテキストを作成する | Microsoft Docs"
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
  - "コンボ ボックス, 描画 (テキストを)"
  - "ComboBox コントロール [Windows フォーム], 描画 (カスタム テキストを)"
  - "ComboBox コントロール [Windows フォーム], 例 [C#]"
  - "例 [Windows フォーム], ComboBox コントロール"
  - "テキスト, 描画 (コンボ ボックスに)"
ms.assetid: ce39b9ea-e626-49fe-bd5a-f567f6d157df
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : ComboBox コントロールにサイズ変更可能なテキストを作成する
この例では、<xref:System.Windows.Forms.ComboBox> コントロールでのテキストのカスタム描画の方法を示します。  項目が特定の基準を満たす場合、より大きなフォントで描画され赤色になります。  
  
## 使用例  
  
```vb  
Private Sub ComboBox1_MeasureItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.MeasureItemEventArgs) Handles ComboBox1.MeasureItem  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
    Dim siText As SizeF  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), _  
lFont)  
    Else  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), bFont)  
    End If  
  
    e.ItemHeight = siText.Height  
    e.ItemWidth = siText.Width  
End Sub  
  
Private Sub ComboBox1_DrawItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.DrawItemEventArgs) Handles ComboBox1.DrawItem  
    Dim g As Graphics = e.Graphics  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        g.DrawString(ComboBox1.Items.Item(e.Index), lfont, Brushes.Red, _  
e.Bounds.X, e.Bounds.Y)  
    Else  
        g.DrawString(ComboBox1.Items.Item(e.Index), bFont, Brushes.Black, e.Bounds.X, e.Bounds.Y)  
    End If  
End Sub  
```  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   Windows フォーム。  
  
-   <xref:System.Windows.Forms.ComboBox.Items%2A> プロパティに 3 つの項目を持つ、 `ListBox1`  という名前の <xref:System.Windows.Forms.ComboBox> コントロール。  この例では、3 つの項目に  `"One", Two", and Three"` という名前が付けられています。   `ComboBox1`  の <xref:System.Windows.Forms.ComboBox.DrawMode%2A> プロパティを <xref:System.Windows.Forms.DrawMode> に設定する必要があります。  
  
    > [!NOTE]
    >  この手法は <xref:System.Windows.Forms.ListBox> コントロールにも適用できます。その場合は、<xref:System.Windows.Forms.ComboBox> の代わりに <xref:System.Windows.Forms.ListBox> を使用します。  
  
-   <xref:System.Windows.Forms?displayProperty=fullName> 名前空間および <xref:System.Drawing?displayProperty=fullName> 名前空間への参照。  
  
## 参照  
 <xref:System.Windows.Forms.ComboBox.DrawItem>   
 <xref:System.Windows.Forms.DrawItemEventArgs>   
 <xref:System.Windows.Forms.ComboBox.MeasureItem>   
 [組み込みのオーナー描画サポートを備えたコントロール](../../../../docs/framework/winforms/controls/controls-with-built-in-owner-drawing-support.md)   
 [ListBox コントロール](../../../../docs/framework/winforms/controls/listbox-control-windows-forms.md)   
 [ComboBox コントロール](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)