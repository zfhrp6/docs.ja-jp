---
title: '方法 : テキストの文字体裁を変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- setting Typography attributes [WPF]
- Typography attribute [WPF], setting
ms.assetid: 19a3b49b-60a2-4c11-a786-e26b4c965588
ms.openlocfilehash: fcc9c894970934bb5a69debef2f4e38297f82198
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542930"
---
# <a name="how-to-alter-the-typography-of-text"></a>方法 : テキストの文字体裁を変更する
次の例は、設定する方法を示します、<xref:System.Windows.Documents.TextElement.Typography%2A>属性を使用して<xref:System.Windows.Documents.Paragraph>例要素として。  
  
## <a name="example"></a>例  
 [!code-xaml[TextElementSnippets#_TextElement_TypogXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]  
  
 この例の表示結果を次の図に示します。  
  
 ![スクリーンショット: 変更されたタイポグラフィを含むテキスト](../../../../docs/framework/wpf/advanced/media/textelement-typog.png "TextElement_Typog")  
  
 これに対し、既定の文字体裁プロパティを設定した同様の例がどのように表示されるかを次の図に示します。  
  
 ![スクリーンショット: 変更されたタイポグラフィを含むテキスト](../../../../docs/framework/wpf/advanced/media/textelement-typog-default.png "TextElement_Typog_Default")  
  
## <a name="example"></a>例  
 次の例は、設定する方法を示します、<xref:System.Windows.Controls.TextBox.Typography%2A>プロパティ プログラムでします。  
  
 [!code-csharp[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
 [!code-vb[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]  
  
## <a name="see-also"></a>関連項目  
 [フロー ドキュメントの概要](../../../../docs/framework/wpf/advanced/flow-document-overview.md)
