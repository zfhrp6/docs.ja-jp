---
title: "方法 : テキストのトリミングを有効にする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], trimming
- documents [WPF], trimmng text
- trimmng text [WPF]
ms.assetid: dd8c9191-d2be-45fd-9fb4-3c75b65578c5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e8f0f24bb6271e63dc50bd063aedfd8185711e7a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-enable-text-trimming"></a>方法 : テキストのトリミングを有効にする
この例は、使用法とで使用できる値の効果を示しています、<xref:System.Windows.TextTrimming>列挙します。  
  
## <a name="example"></a>例  
 次の例では定義、<xref:System.Windows.Controls.TextBlock>を持つ要素、<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>属性に設定します。  
  
 [!code-xaml[TextTrimmingSnippets#_TextTrimmingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml#_texttrimmingxaml)]  
  
## <a name="example"></a>例  
 対応する設定<xref:System.Windows.TextTrimming>以下にコードでプロパティを示すです。  
  
 [!code-csharp[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml.cs#_texttrimmingsettexttrimming)]
 [!code-vb[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextTrimmingSnippets/VisualBasic/Window1.xaml.vb#_texttrimmingsettexttrimming)]  
  
 テキストのトリミングの現在の 3 つのオプションがある:**切り取ら**、 **WordEllipsis**、および**None**です。  
  
 ときに<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>に設定されている**切り取ら**テキストが切り捨てられるし、トリミング枠に最も近い文字の省略記号では継続します。  この設定では、トリミング境界により近い位置でテキストが切り取られます。ただし、単語の一部が切り取られる可能性があります。  次の図でこの設定の効果を示しています、<xref:System.Windows.Controls.TextBlock>上に定義されたものに似ています。  
  
 ![例: TextTrimming.CharacterEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-character.png "TextTrimming_Character")  
  
 ときに<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>に設定されている**WordEllipsis**テキストが切り捨てられるし、トリミング枠に最も近い最初の完全単語の末尾にある省略記号では継続します。  この設定は、部分的に単語は表示されませんが、傾向としてトリミング枠の類似した形にテキストのトリミングされませんが、**切り取ら**設定します。  次の図でこの設定の効果を示しています、<xref:System.Windows.Controls.TextBlock>上で定義します。  
  
 ![例: TextTrimming.WordEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-word.png "TextTrimming_Word")  
  
 ときに<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>に設定されている**None**テキストのトリミングは実行されません。  この場合、テキストは親テキスト コンテナーの境界にトリミングされるだけです。  次の図でこの設定の効果を示しています、<xref:System.Windows.Controls.TextBlock>上に定義されたものに似ています。  
  
 ![例: TextTrimming.None](../../../../docs/framework/wpf/advanced/media/texttrimming-none.png "TextTrimming_None")
