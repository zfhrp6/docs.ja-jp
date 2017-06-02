---
title: "方法 : 中抜きの文字列を作成する | Microsoft Docs"
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
  - "グラデーション ブラシ"
  - "線形グラデーション ブラシ"
  - "中抜きの文字列"
  - "タイポグラフィ, 線形グラデーション ブラシ"
  - "タイポグラフィ, 中抜き効果"
ms.assetid: 4aa3cf6e-1953-4f26-8230-7c1409e5f28d
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : 中抜きの文字列を作成する
通常、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションでテキスト文字列に装飾を追加する場合は、別個の文字、つまりグリフのコレクションとしてのテキストを使用します。  たとえば、線形グラデーション ブラシを作成し、それを <xref:System.Windows.Controls.TextBox> オブジェクトの <xref:System.Windows.Controls.Control.Foreground%2A> プロパティに適用できます。  テキスト ボックスを表示または編集すると、テキスト文字列の現在の文字セットに、線形グラデーション ブラシが自動的に適用されます。  
  
 ![線形グラデーション ブラシで表示されるテキスト](../../../../docs/framework/wpf/advanced/media/outlinedtext01.png "OutlinedText01")  
テキスト ボックスに適用された線形グラデーション ブラシの例  
  
 テキストを <xref:System.Windows.Media.Geometry> オブジェクトに変換し、人の目をひきつける他の種類のテキストを作成することもできます。  たとえば、テキスト文字列のアウトラインに基づいて <xref:System.Windows.Media.Geometry> オブジェクトを作成できます。  
  
 ![線形グラデーション ブラシを使用するテキスト アウトライン](../../../../docs/framework/wpf/advanced/media/outlinedtext02.png "OutlinedText02")  
アウトライン ジオメトリのテキストに適用された線形グラデーション ブラシの例  
  
 テキストを <xref:System.Windows.Media.Geometry> オブジェクトに変換すると、テキストは文字の集まりではなくなります。つまり、文字列内の文字を変更することはできません。  ただし、変換されたテキストのストロークおよび塗りつぶしのプロパティを変更することで、テキストの外観を変えることができます。  ストロークは、変換したテキストのアウトラインを参照します。塗りつぶしは、変換したテキストのアウトラインの内側の領域を参照します。  
  
 変換されたテキストのストロークおよび塗りつぶしを変更して、視覚効果を作成するいくつかの方法を次の例に示します。  
  
 ![塗りつぶしとストロークに別の色を使用するテキスト](../../../../docs/framework/wpf/advanced/media/outlinedtext03.png "OutlinedText03")  
ストロークおよび塗りつぶしを別々の色に設定した例  
  
 ![ストロークに適用されるイメージ ブラシを含むテキスト](../../../../docs/framework/wpf/advanced/media/outlinedtext04.png "OutlinedText04")  
ストロークに適用したイメージ ブラシの例  
  
 変換されたテキストの境界ボックスの四角形または強調表示を変更することもできます。  変換されたテキストのストロークおよび強調表示を変更して、視覚効果を作成する方法の一例を次に示します。  
  
 ![ストロークに適用されるイメージ ブラシを含むテキスト](../../../../docs/framework/wpf/advanced/media/outlinedtext05.png "OutlinedText05")  
ストロークおよび強調表示に適用したイメージ ブラシの例  
  
## 使用例  
 テキストを <xref:System.Windows.Media.Geometry> オブジェクトに変換する場合の要点は、<xref:System.Windows.Media.FormattedText> オブジェクトを使用することです。  このオブジェクトを作成したら、<xref:System.Windows.Media.FormattedText.BuildGeometry%2A> メソッドと <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> メソッドを使用して、テキストを <xref:System.Windows.Media.Geometry> オブジェクトに変換できます。  最初のメソッドは、書式設定されたテキストのジオメトリを返します。2 番目のメソッドは、書式設定されたテキストの境界ボックスのジオメトリを返します。  <xref:System.Windows.Media.FormattedText> オブジェクトを作成し、書式設定されたテキストとその境界ボックスのジオメトリを取得する方法を次のコード例に示します。  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 取得された <xref:System.Windows.Media.Geometry> オブジェクトを表示するには、変換されたテキストを表示しているオブジェクトの <xref:System.Windows.Media.DrawingContext> にアクセスする必要があります。  これらのコード例では、ユーザー定義のレンダリングをサポートするクラスの派生カスタム コントロール オブジェクトを作成することで、これを行います。  
  
 カスタム コントロールで <xref:System.Windows.Media.Geometry> オブジェクトを表示するには、<xref:System.Windows.UIElement.OnRender%2A> メソッドのオーバーライドを提供します。  オーバーライドしたメソッドでは、<xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> メソッドを使用して <xref:System.Windows.Media.Geometry> オブジェクトを描画する必要があります。  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
## 参照  
 [書式設定されたテキストの描画](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)