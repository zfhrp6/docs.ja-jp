---
title: "方法 : TextWrapping プロパティをプログラムにより変更する | Microsoft Docs"
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
  - "ドキュメント, 変更 (TextWrapping プロパティをプログラムで)"
  - "TextWrapping プロパティ, 変更 (プログラムで)"
ms.assetid: 30d25554-4c82-4df9-a8d6-35683a4a13bb
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : TextWrapping プロパティをプログラムにより変更する
## 使用例  
 <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> プロパティの値を、プログラムによって変更する方法を、次のコード例に示します。  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で、3 つの <xref:System.Windows.Controls.Button> 要素を 1 つの <xref:System.Windows.Controls.StackPanel> 要素内に配置しています。<xref:System.Windows.Controls.Button> の各 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントは、コード内のイベント ハンドラーに対応しています。  ボタンがクリックされると、イベント ハンドラーは `txt2` に適用する <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> 値と同じ名前を使用します。  また、`txt1` 内のテキスト \([!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] に表示されない <xref:System.Windows.Controls.TextBlock>\) は、プロパティの変更を反映するように更新されます。  
  
 [!code-xml[TextWrapProperty#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml#1)]  
  
 [!code-csharp[TextWrapProperty#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextWrapProperty/CSharp/Window1.xaml.cs#2)]
 [!code-vb[TextWrapProperty#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml.vb#2)]  
  
## 参照  
 <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>   
 <xref:System.Windows.TextWrapping>