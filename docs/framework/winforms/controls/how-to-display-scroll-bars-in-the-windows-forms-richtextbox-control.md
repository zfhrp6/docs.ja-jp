---
title: "方法 : Windows フォームの RichTextBox コントロールにスクロール バーを表示する | Microsoft Docs"
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
  - "RichTextBox コントロール [Windows フォーム], 表示 (スクロール バーを)"
  - "スクロール バー, 表示 (コントロールに)"
  - "テキスト ボックス, 表示 (スクロール バーを)"
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : Windows フォームの RichTextBox コントロールにスクロール バーを表示する
既定では、Windows フォームの <xref:System.Windows.Forms.RichTextBox> コントロールには必要に応じて水平スクロール バーと垂直スクロール バーが表示されます。  <xref:System.Windows.Forms.RichTextBox> コントロールの <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> プロパティには、下の表に示す 7 つの値を使用できます。  
  
### RichTextBox コントロールにスクロール バーを表示するには  
  
1.  <xref:System.Windows.Forms.RichTextBox.Multiline%2A> プロパティを `true` に設定します。  <xref:System.Windows.Forms.RichTextBox.Multiline%2A> プロパティが `false` に設定されている場合、水平スクロール バーも含めてスクロール バーはまったく表示されません。  
  
2.  <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> プロパティを <xref:System.Windows.Forms.RichTextBoxScrollBars> 列挙体の適切な値に設定します。  
  
    |値|Description|  
    |-------|-----------------|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars> \(既定値\)|テキストがコントロールの幅または長さを超えた場合にだけ、水平スクロール バーまたは垂直スクロール バー、またはその両方を表示します。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars>|どちらのスクロール バーも表示しません。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars>|テキストがコントロールの幅を超えた場合にだけ、水平スクロール バーを表示します。  <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> プロパティを `false` に設定する必要があります。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars>|テキストがコントロールの高さを超えた場合にだけ、垂直スクロール バーを表示します。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars>|<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> プロパティが `false` に設定されている場合に、水平スクロール バーを表示します。  テキストがコントロールの幅を超えていない場合、スクロール バーは淡色表示になります。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars>|垂直スクロール バーを常に表示します。  テキストがコントロールの高さを超えていない場合、スクロール バーは淡色表示になります。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars>|垂直スクロール バーを常に表示します。  <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> プロパティが `false` に設定されている場合に、水平スクロール バーを表示します。  テキストがコントロールの幅または高さを超えていない場合、スクロール バーは淡色表示になります。|  
  
3.  <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> プロパティに適切な値を設定します。  
  
    |値|Description|  
    |-------|-----------------|  
    |`false`|コントロールのテキストは、コントロールの幅に収まるように自動的に調整されないため、改行に達するまで右方向にスクロールされます。  この値は、ScrollBars プロパティの設定で、水平スクロール バーまたは両方のスクロール バーを表示するように選択した場合に使用します。|  
    |`true` \(既定値\)|コントロール内のテキストは、コントロールの幅に収まるように自動的に調整されます。  水平スクロール バーは表示されません。  この値は、ScrollBars プロパティの設定で垂直スクロール バーを表示するか、どのスクロール バーも表示しないように選択した場合に使用して、1 つ以上の段落を表示します。|  
  
## 参照  
 <xref:System.Windows.Forms.RichTextBoxScrollBars>   
 <xref:System.Windows.Forms.RichTextBox>   
 [RichTextBox コントロール](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)   
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)