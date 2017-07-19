---
title: "方法 : プログラムによってコンテンツの FlowDirection を変更する | Microsoft Docs"
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
  - "ドキュメント, 変更 (FlowDirection プロパティをプログラムで)"
  - "FlowDirection プロパティ, 変更 (プログラムで)"
ms.assetid: 02f5a8ba-f8c0-4e5a-84b9-4c5bf12922a2
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : プログラムによってコンテンツの FlowDirection を変更する
この例では、<xref:System.Windows.Controls.FlowDocumentReader> の <xref:System.Windows.FrameworkElement.FlowDirection%2A> プロパティをプログラムで変更する方法を示します。  
  
## 使用例  
 2 つの <xref:System.Windows.Controls.Button> 要素が作成され、それぞれが <xref:System.Windows.FlowDirection> の有効値の 1 つを表しています。  ボタンをクリックすると、関連付けられたプロパティ値が、`tf1` という名前の <xref:System.Windows.Controls.FlowDocumentReader> のコンテンツに適用されます。  プロパティ値は、`txt1` という名前の <xref:System.Windows.Controls.TextBlock> にも書き込まれます。  
  
 [!code-xml[FlowDirectionSnippets#_FlowDirectionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml#_flowdirectionxaml)]  
  
## 使用例  
 上で定義されているボタン クリックに関連付けられたイベントは、[!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] の分離コード ファイルで処理されます。  
  
 [!code-csharp[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml.cs#_flowdirection)]
 [!code-vb[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDirectionSnippets/VisualBasic/Window1.xaml.vb#_flowdirection)]