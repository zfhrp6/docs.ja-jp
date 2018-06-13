---
title: '方法 : 文字の装飾を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [WPF], baseline
- text [WPF], decorations
- fonts [WPF], underline
- fonts [WPF], overline
- strikethrough type [WPF]
- fonts [WPF], strikethrough
- overline type [WPF]
- underline type [WPF]
- typography [WPF], text decorations
- baseline type [WPF]
ms.assetid: cf3cb4e7-782a-4be7-b2d4-e0935e21e4e0
ms.openlocfilehash: c16073dd2413c1258f4875ac4118e0656d29b171
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545410"
---
# <a name="how-to-create-a-text-decoration"></a>方法 : 文字の装飾を作成する
A<xref:System.Windows.TextDecoration>オブジェクトがテキストに追加できるビジュアルの装飾します。 文字の装飾の 4 つの種類があります: 下線、基準、取り消し線、および上線。 次の例は、文字の装飾のテキストに対する相対位置を示します。  
  
 ![テキスト装飾位置のダイアグラム](../../../../docs/framework/wpf/advanced/media/textdecoration01.gif "TextDecoration01")  
テキスト装飾の種類の例  
  
 テキストに文字の装飾を追加するには、作成、<xref:System.Windows.TextDecoration>オブジェクトし、そのプロパティを変更します。 使用して、<xref:System.Windows.TextDecoration.Location%2A>文字飾りが表示される場所、下線などの文字を指定するプロパティです。 使用して、<xref:System.Windows.TextDecoration.Pen%2A>文字飾りを純色の塗りつぶしのグラデーションの色などの外観を指定するプロパティです。 値を指定しない場合、<xref:System.Windows.TextDecoration.Pen%2A>プロパティ、テキストと同じ色に装飾の既定値です。 定義した後、<xref:System.Windows.TextDecoration>オブジェクトに追加して、<xref:System.Windows.TextDecorations>目的のテキスト オブジェクトのコレクション。  
  
 次の例では、線形グラデーション ブラシとペンの破線スタイルが設定されているテキスト装飾を示します。  
  
 ![線形グラデーション下線付き文字飾り](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")  
線形グラデーションのスタイルの下線の例ブラシ、ペンの破線  
  
 <xref:System.Windows.Documents.Hyperlink>オブジェクトはインライン レベル フロー コンテンツ要素フロー コンテンツ内のハイパーリンクをホストすることができます。 既定では、<xref:System.Windows.Documents.Hyperlink>を使用して、<xref:System.Windows.TextDecoration>下線を表示するオブジェクト。 <xref:System.Windows.TextDecoration> オブジェクトができる処理を要するインスタンスを作成すると、パフォーマンスが多数ある場合に特に<xref:System.Windows.Documents.Hyperlink>オブジェクト。 広範な利用を加えた場合<xref:System.Windows.Documents.Hyperlink>要素、するをお勧めしますように、イベントをトリガーする場合にのみ下線を表示、<xref:System.Windows.ContentElement.MouseEnter>イベント。  
  
 次の例では、"My MSN"リンクの下線は動的 — これ場合のみ表示されます、<xref:System.Windows.ContentElement.MouseEnter>イベントが発生します。  
  
 ![Textdecorations を表示するハイパーリンク](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")  
Textdecorations をで定義されているハイパーリンク  
  
 詳細については、「[方法: ハイパーリンクに下線を引くかどうかを指定する](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)」を参照してください。  
  
## <a name="example"></a>例  
 次のコード例では、下線の文字装飾は、フォントの既定値を使用します。  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 次のコード例では、下線の文字装飾を純色のブラシ、ペンを使用した作成されます。  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 次のコード例では、下線の文字装飾を破線のペンの線形グラデーション ブラシを使用して作成されます。  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.TextDecoration>  
 <xref:System.Windows.Documents.Hyperlink>  
 [ハイパーリンクに下線を引くかどうかを指定する](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)
