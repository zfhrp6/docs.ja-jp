---
title: "方法 : TextBox コントロールのテキストの先頭または末尾にカーソルを配置する | Microsoft Docs"
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
  - "配置 (カーソルを)"
  - "テキスト ボックス コントロールをカーソルの位置"
  - "カーソル位置"
ms.assetid: c771a0b8-c6b4-4240-aecd-a21d0ba51a2e
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : TextBox コントロールのテキストの先頭または末尾にカーソルを配置する
この例では、先頭または末尾のテキスト コンテンツにカーソルを配置、 <xref:System.Windows.Controls.TextBox>コントロールです。  
  
## <a name="example"></a>例  
 次[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]コードについて説明します、 <xref:System.Windows.Controls.TextBox>を制御し、名前を割り当てます。  
  
 [!code-xml[TextBox_MiscCode#_MoveCursorXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_movecursorxaml)]  
  
## <a name="example"></a>例  
 内容の先頭にカーソルを配置する、 <xref:System.Windows.Controls.TextBox>コントロールを呼び出す、<xref:System.Windows.Controls.TextBox.Select%2A>メソッドし、選択範囲の開始位置に 0、および選択範囲の長さは 0 を指定します。  
  
 [!code-csharp[TextBox_MiscCode#_CursorToStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortostart)]
 [!code-vb[TextBox_MiscCode#_CursorToStart](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortostart)]  
  
## <a name="example"></a>例  
 内容の末尾にカーソルを配置する、 <xref:System.Windows.Controls.TextBox>コントロールを呼び出す、<xref:System.Windows.Controls.TextBox.Select%2A>メソッドし、コンテンツのテキストの長さと選択範囲の長さは 0 に等しく選択の開始位置を指定します。  
  
 [!code-csharp[TextBox_MiscCode#_CursorToEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortoend)]
 [!code-vb[TextBox_MiscCode#_CursorToEnd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortoend)]  
  
## <a name="see-also"></a>関連項目  
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)