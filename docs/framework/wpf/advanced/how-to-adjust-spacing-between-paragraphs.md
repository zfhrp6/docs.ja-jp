---
title: "方法 : 段落間の間隔を調整する | Microsoft Docs"
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
  - "ドキュメント, 調整 (段落間の間隔を)"
  - "段落, 間隔"
  - "間隔 (段落間の)"
ms.assetid: 7cd2f2ac-0e19-4587-bfb6-7f5b18c9536e
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 方法 : 段落間の間隔を調整する
フロー コンテンツ内の段落間の間隔を調整する、または間隔をなくす方法を次の例に示します。  
  
 フロー コンテンツの段落間に余分な間隔が空くのは、段落にマージンが設定されているからです。したがって、段落間の間隔を制御するには、段落のマージンを調整します。  2 つの段落間の余分な間隔を完全になくすには、段落のマージンを **0** に設定します。  <xref:System.Windows.Documents.FlowDocument> の全体にわたって段落間の間隔を均一にするには、スタイルを使用して、<xref:System.Windows.Documents.FlowDocument> のすべての段落に対して均一のマージン値を設定します。  
  
 2 つの隣接する段落のマージンは、縮小されて、大きい方だけが残ることに注意してください。2 つのマージンが足されるのではありません。  したがって、2 つの隣接する段落のマージンがそれぞれ 20 ピクセルと 40 ピクセルならば、段落間の間隔は、2 つのマージン値のうち大きい方である 40 ピクセルになります。  
  
## 使用例  
 <xref:System.Windows.Documents.FlowDocument> のすべての <xref:System.Windows.Documents.Paragraph> 要素のマージンを **0** に設定するスタイルを使用して <xref:System.Windows.Documents.FlowDocument> の段落間の余分な間隔を実質的に除去する例を次に示します。  
  
 [!code-xml[BlockSnippets#_ParagraphSpacingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BlockSnippets/CSharp/Window1.xaml#_paragraphspacingxaml)]