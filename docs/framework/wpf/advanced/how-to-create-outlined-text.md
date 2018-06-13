---
title: '方法 : 中抜きの文字列を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], linear gradient brush
- outlined text [WPF]
- gradient brush [WPF]
- linear gradient brush [WPF]
- typography [WPF], outline effects
ms.assetid: 4aa3cf6e-1953-4f26-8230-7c1409e5f28d
ms.openlocfilehash: c79f5c1c6812b1175119133664e39995af29bd4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544966"
---
# <a name="how-to-create-outlined-text"></a>方法 : 中抜きの文字列を作成する
ほとんどの場合、テキスト文字列内に装飾を追加するときに、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]アプリケーションでは、個別の文字、またはグリフのコレクションの観点からテキストを使用しています。 たとえば、線形グラデーション ブラシを作成し、適用、<xref:System.Windows.Controls.Control.Foreground%2A>のプロパティ、<xref:System.Windows.Controls.TextBox>オブジェクト。 表示またはテキスト ボックスを編集するときに、現在のテキスト文字列の文字のセットに線形グラデーション ブラシが自動的に適用します。  
  
 ![線形グラデーション ブラシで表示されるテキスト](../../../../docs/framework/wpf/advanced/media/outlinedtext01.jpg "OutlinedText01")  
テキスト ボックスに適用された線形グラデーション ブラシの例  
  
 ただし、変換することもにテキストを<xref:System.Windows.Media.Geometry>オブジェクト、その他の種類の視覚的に豊富なテキストを作成することができます。 たとえば、作成した、<xref:System.Windows.Media.Geometry>テキスト文字列のアウトラインに基づいてオブジェクト。  
  
 ![線形グラデーション ブラシを使用するテキスト アウトライン](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")  
テキストのアウトライン ジオメトリに適用される線形グラデーション ブラシの例  
  
 テキストに変換するときに、<xref:System.Windows.Media.Geometry>オブジェクト、文字のコレクションではなくなりました: テキスト文字列内の文字を変更することはできません。 ただし、変換されたテキストのストロークおよび塗りつぶしのプロパティを変更することで、テキストの外観を変えることができます。 ストロークは、変換したテキストのアウトラインを参照します。塗りつぶしは、変換したテキストのアウトラインの内側の領域を参照します。  
  
 次の例では、変換されたテキストの塗りつぶし、ストロークを変更して視覚効果を作成するいくつかの方法を示します。  
  
 ![塗りつぶしとストロークを別の色を含むテキスト](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")  
ストロークと塗りつぶしを別々の色に設定した例  
  
 ![ストロークに適用されるイメージ ブラシを含むテキスト](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")  
ストロークに適用したイメージ ブラシの例  
  
 境界ボックスの四角形、または変換されたテキストの強調表示を変更することもできます。 次の例は、ストロークおよび変換されたテキストの強調表示を変更することによって、視覚効果を作成する方法を示しています。  
  
 ![ストロークに適用されるイメージ ブラシを含むテキスト](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")  
ストロークと強調表示に適用したイメージ ブラシの例  
  
## <a name="example"></a>例  
 テキストを変換するキー、<xref:System.Windows.Media.Geometry>オブジェクトは、使用する、<xref:System.Windows.Media.FormattedText>オブジェクト。 使用することがこのオブジェクトを作成した後、<xref:System.Windows.Media.FormattedText.BuildGeometry%2A>と<xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A>をテキストに変換するメソッド<xref:System.Windows.Media.Geometry>オブジェクト。 最初のメソッドは、フォーマットされたテキストのジオメトリを返します2 番目のメソッドは、境界ボックスの書式設定されたテキストのジオメトリを返します。 次のコード例を作成する方法を示しています、<xref:System.Windows.Media.FormattedText>オブジェクトの書式設定されたテキストと、境界ボックスのジオメトリを取得するとします。  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 取得した表示するために、<xref:System.Windows.Media.Geometry>オブジェクトにアクセスする必要があります、<xref:System.Windows.Media.DrawingContext>変換されたテキストが表示されているオブジェクトの。 これらのコード例では、これはユーザー定義のレンダリングをサポートするクラスから派生したカスタム コントロール オブジェクトを作成することで行われます。  
  
 表示する<xref:System.Windows.Media.Geometry>、カスタム コントロール内のオブジェクトのオーバーライドを提供する、<xref:System.Windows.UIElement.OnRender%2A>メソッドです。 オーバーライドされたメソッドを使用する必要があります、<xref:System.Windows.Media.DrawingContext.DrawGeometry%2A>を描画するメソッド、<xref:System.Windows.Media.Geometry>オブジェクト。  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
## <a name="see-also"></a>関連項目  
 [書式設定されたテキストの描画](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
