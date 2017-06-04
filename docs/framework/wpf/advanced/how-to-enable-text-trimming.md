---
title: "方法 : テキストのトリミングを有効にする | Microsoft Docs"
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
  - "ドキュメント, トリミング (テキストを)"
  - "テキスト, トリム"
  - "トリミング (テキストを)"
ms.assetid: dd8c9191-d2be-45fd-9fb4-3c75b65578c5
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : テキストのトリミングを有効にする
この例では、<xref:System.Windows.TextTrimming> 列挙体で使用可能な値の使用方法と効果を示します。  
  
## 使用例  
 次の例では、<xref:System.Windows.Controls.TextBlock.TextTrimming%2A> 属性セットを使用して <xref:System.Windows.Controls.TextBlock> 要素を定義します。  
  
 [!code-xml[TextTrimmingSnippets#_TextTrimmingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml#_texttrimmingxaml)]  
  
## 使用例  
 次の例では、対応する <xref:System.Windows.TextTrimming> プロパティをコード内で設定します。  
  
 [!code-csharp[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml.cs#_texttrimmingsettexttrimming)]
 [!code-vb[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextTrimmingSnippets/VisualBasic/Window1.xaml.vb#_texttrimmingsettexttrimming)]  
  
 現在、テキストのトリミングでは、**CharacterEllipsis**、**WordEllipsis**、および **None** の 3 つのオプションを使用できます。  
  
 <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> を **CharacterEllipsis** に設定した場合、テキストが切り取られ、トリミング エッジに最も近い文字の位置に省略記号が挿入されます。  この設定では、トリミング境界により近い位置でテキストが切り取られます。ただし、単語の一部が切り取られる可能性があります。  次の図は、上記で定義したものと同様の <xref:System.Windows.Controls.TextBlock> にこの設定を適用した場合の効果を示しています。  
  
 ![例: TextTrimming.CharacterEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-character.png "TextTrimming\_Character")  
  
 <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> を **WordEllipsis** に設定した場合、テキストが切り取られ、トリミング エッジに最も近い位置にある最初の完全な単語の後に省略記号が挿入されます。  この設定では、部分的に切り取られた単語は表示されません。ただし、**CharacterEllipsis** 設定よりもトリミング エッジから離れた位置でテキストが切り取られます。  次の図は、上記で定義した <xref:System.Windows.Controls.TextBlock> にこの設定を適用した場合の効果を示しています。  
  
 ![例 : TextTrimming.WordEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-word.png "TextTrimming\_Word")  
  
 <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> を **None** に設定した場合、テキストのトリミングは実行されません。  この場合、テキストは親テキスト コンテナーの境界にトリミングされるだけです。  次の図は、上記で定義したものと同様の <xref:System.Windows.Controls.TextBlock> にこの設定を適用した場合の効果を示しています。  
  
 ![例 : TextTrimming.None](../../../../docs/framework/wpf/advanced/media/texttrimming-none.png "TextTrimming\_None")