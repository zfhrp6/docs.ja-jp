---
title: "方法 : 文字の装飾を作成する | Microsoft Docs"
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
  - "ベースライン タイプ"
  - "フォント, ベースライン"
  - "フォント, 上線"
  - "フォント, 取り消し線"
  - "フォント, 下線"
  - "上線タイプ"
  - "取り消し線タイプ"
  - "テキスト, 装飾"
  - "タイポグラフィ, 文字の装飾"
  - "下線タイプ"
ms.assetid: cf3cb4e7-782a-4be7-b2d4-e0935e21e4e0
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : 文字の装飾を作成する
<xref:System.Windows.TextDecoration> オブジェクトは、テキストに追加できる視覚的な装飾です。  文字装飾には、下線、ベースライン、取り消し線、および上線の 4 種類あります。  テキストに対する文字装飾の位置を次の例に示します。  
  
 ![テキスト装飾位置のダイアグラム](../../../../docs/framework/wpf/advanced/media/textdecoration01.png "TextDecoration01")  
文字装飾の種類の例  
  
 テキストに文字装飾を追加するには、<xref:System.Windows.TextDecoration> オブジェクトを作成し、そのプロパティを変更します。  下線などの文字装飾を表示する位置を指定するには、<xref:System.Windows.TextDecoration.Location%2A> プロパティを使用します。  塗りつぶしの純色やグラデーション カラーなどの文字装飾の外観を指定するには、<xref:System.Windows.TextDecoration.Pen%2A> プロパティを使用します。  <xref:System.Windows.TextDecoration.Pen%2A> プロパティに値を指定しない場合、装飾は既定でテキストと同じ色になります。  <xref:System.Windows.TextDecoration> オブジェクトを定義したら、それを目的のテキスト オブジェクトの <xref:System.Windows.TextDecorations> コレクションに追加します。  
  
 線形グラデーション ブラシと破線のペンによってスタイルが設定されている文字装飾の例を次に示します。  
  
 ![線形グラデーション下線を使用したテキスト装飾](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")  
線形グラデーション ブラシと破線のペンによってスタイルが設定された下線の例  
  
 <xref:System.Windows.Documents.Hyperlink> オブジェクトはインラインレベルのフロー コンテンツ要素であり、これを使用すると、フロー コンテンツ内でハイパーリンクをホストできます。  既定では、<xref:System.Windows.Documents.Hyperlink> は、下線を表示するために、<xref:System.Windows.TextDecoration> オブジェクトを使用します。  <xref:System.Windows.TextDecoration> オブジェクトは、インスタンス化するために、パフォーマンスに大きな負荷をかけることがあります。特に、多数の <xref:System.Windows.Documents.Hyperlink> オブジェクトを使用する場合には、大きな負荷をかけます。  <xref:System.Windows.Documents.Hyperlink> 要素を広く使用する場合は、<xref:System.Windows.ContentElement.MouseEnter> イベントのようなイベントが発生したときにだけ下線を表示することを、検討する必要があります。  
  
 次の例では、"My MSN" リンクの下線は動的であり、<xref:System.Windows.ContentElement.MouseEnter> イベントが発生したときにのみ表示されます。  
  
 ![TextDecorations を表示するハイパーリンク](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")  
TextDecorations が定義されたハイパーリンク  
  
 詳細については、「[ハイパーリンクに下線を引くかどうかを指定する](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)」を参照してください。  
  
## 使用例  
 次のコード例では、下線の文字装飾で既定のフォント値が使用されています。  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xml[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 次のコード例では、純色のブラシをペンとして使用した下線の文字装飾が作成されます。  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xml[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 次のコード例では、破線のペン用の線形グラデーション ブラシによって下線の文字装飾が作成されます。  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xml[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## 参照  
 <xref:System.Windows.TextDecoration>   
 <xref:System.Windows.Documents.Hyperlink>   
 [ハイパーリンクに下線を引くかどうかを指定する](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)