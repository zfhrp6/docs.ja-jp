---
title: "方法 : FocusVisualStyle をコントロールに適用する | Microsoft Docs"
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
  - "FocusVisualStyle プロパティ"
  - "プロパティ, FocusVisualStyle"
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : FocusVisualStyle をコントロールに適用する
この例では、<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> プロパティを使用して、フォーカス表示スタイルをリソース内で作成し、このスタイルをコントロールに適用する方法を示しています。  
  
## 使用例  
 次の例では、コントロールが [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 内でキーボードのフォーカスを受け取ったときにのみ適用される追加のコントロール複合を作成するスタイルを定義しています。  これを行うには、<xref:System.Windows.Controls.ControlTemplate> を使用してスタイルを定義し、<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> プロパティを設定する際に、そのスタイルをリソースとして参照します。  
  
 境界線に似た外部四角形を四角形領域の外側に配置します。  他の部分を変更しない限り、スタイルのサイズ指定には、フォーカス表示スタイルが適用される四角形コントロールの <xref:System.Windows.FrameworkElement.ActualHeight%2A> および <xref:System.Windows.FrameworkElement.ActualWidth%2A> が使用されます。  次の例では、<xref:System.Windows.FrameworkElement.Margin%2A>\> に負の値を設定して、フォーカスされたコントロールの少し外側に境界線を表示しています。  
  
 [!code-xml[FEFocusVisualStyle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> は、明示的なスタイルまたはテーマ スタイルに由来するコントロール テンプレート スタイルに付け加えるスタイルです。コントロールの主なスタイルは、<xref:System.Windows.Controls.ControlTemplate> を使用し、このスタイルを <xref:System.Windows.FrameworkElement.Style%2A> プロパティに設定することにより作成できます。  
  
 フォーカス表示スタイルは、フォーカス可能な要素ごとに別のスタイルを使用するのではなく、テーマまたは UI 全体で一貫して同じスタイルを使用する必要があります。  詳細については、「[コントロールのフォーカスのスタイルと FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>   
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [コントロールのフォーカスのスタイルと FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md)