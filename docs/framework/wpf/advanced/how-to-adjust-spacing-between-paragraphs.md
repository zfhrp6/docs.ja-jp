---
title: '方法 : 段落間の間隔を調整する'
ms.date: 03/30/2017
helpviewer_keywords:
- spacing between paragraphs [WPF]
- paragraphs [WPF], spacing between
- documents [WPF], adjusting spacing between paragraphs
ms.assetid: 7cd2f2ac-0e19-4587-bfb6-7f5b18c9536e
ms.openlocfilehash: b232903054cf45b70ba99a9223352391498cf79b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542949"
---
# <a name="how-to-adjust-spacing-between-paragraphs"></a>方法 : 段落間の間隔を調整する
この例では、調整またはフロー コンテンツ内の段落の間隔を排除する方法を示します。  
  
 フロー コンテンツの段落の間に表示される余分なスペースは余白の段落に設定の結果したがって、段落の間隔は、それらの段落の余白を調整することによって制御できます。  2 つの段落の余分なスペースを完全になくすため、設定には、段落の余白**0**します。  段落全体を通じて等間隔に整列を実現するために<xref:System.Windows.Documents.FlowDocument>のすべての段落の統一された余白の値を設定するスタイルを使用して、<xref:System.Windows.Documents.FlowDocument>です。  
  
 ことが重要に、2 つの余白のうち大きい方ではなくを 2 倍になり、2 つの隣接する段落の余白は「折りたたま」に注意してください。 したがって、隣接する 2 つの段落では、それぞれ 20 ピクセルと 40 ピクセルの余白がある、段落の間の結果として得られる領域は 40 (ピクセル単位)、2 つの余白の値のうち、大きい方です。  
  
## <a name="example"></a>例  
 次の例は、すべての余白を設定するスタイルをで<xref:System.Windows.Documents.Paragraph>内の要素、<xref:System.Windows.Documents.FlowDocument>に**0**、内の段落の間で余分なスペースが実質的に、<xref:System.Windows.Documents.FlowDocument>です。  
  
 [!code-xaml[BlockSnippets#_ParagraphSpacingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BlockSnippets/CSharp/Window1.xaml#_paragraphspacingxaml)]
