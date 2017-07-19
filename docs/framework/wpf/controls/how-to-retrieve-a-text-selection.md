---
title: "方法 : テキスト選択を取得する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "取得 (テキストを)"
  - "テキスト, 取得"
  - "TextBox コントロール, 取得 (テキストを)"
ms.assetid: d5793172-1e11-4a39-9be0-73f336ed858d
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : テキスト選択を取得する
この例では、<xref:System.Windows.Controls.TextBox.SelectedText%2A> プロパティを使用して、ユーザーが <xref:System.Windows.Controls.TextBox> コントロールで選択したテキストを取得する方法を 1 つ示します。  
  
## 使用例  
 次の [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] の例では、選択対象のテキストを格納した <xref:System.Windows.Controls.TextBox> コントロールと、<xref:System.Windows.Controls.Button.OnClick%2A> メソッドを指定した <xref:System.Windows.Controls.Button> コントロールの定義を示します。  
  
 この例では、<xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベント ハンドラーが関連付けられたボタンを使用して、テキスト選択を取得しています。  ユーザーがボタンをクリックすると、<xref:System.Windows.Controls.Button.OnClick%2A> メソッドにより、テキストボックス内で選択されたすべてのテキストが文字列にコピーされます。  テキスト選択の取得 \(ボタンのクリック\)、およびその選択に関連し実行されるアクション \(文字列へのテキスト選択のコピー\) に対応する特定環境を簡単に変更して、さまざまなシナリオに対応できます。  
  
 [!code-xml[TextBox_MiscCode#_TextBoxSelectTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxselecttextxaml)]  
  
## 使用例  
 次に示す [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] の例では、この例の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で定義したボタンで使用する <xref:System.Windows.Controls.Button.OnClick%2A> イベント ハンドラーを示します。  
  
 [!code-csharp[TextBox_MiscCode#_SelectText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_selecttext)]
 [!code-vb[TextBox_MiscCode#_SelectText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_selecttext)]  
  
## 参照  
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)