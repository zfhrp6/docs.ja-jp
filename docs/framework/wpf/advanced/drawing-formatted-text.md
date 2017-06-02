---
title: "書式設定されたテキストの描画 | Microsoft Docs"
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
  - "描画, 書式設定テキスト"
  - "書式設定テキスト [WPF]"
  - "テキスト [WPF]"
  - "タイポグラフィ, 描画 (書式設定されたテキストを)"
ms.assetid: b1d851c1-331c-4814-9964-6fe769db6f1f
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 書式設定されたテキストの描画
ここでは、<xref:System.Windows.Media.FormattedText> オブジェクトの機能の概要について説明します。  このオブジェクトは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションでのテキストの描画に対する低レベルの制御を提供します。  
  
   
  
<a name="technology_overview"></a>   
## テクノロジの概要  
 <xref:System.Windows.Media.FormattedText> オブジェクトを使用すると、複数行のテキストを描画できます。このテキストでは、テキスト内の各文字を個々に書式設定できます。  複数の書式が適用されたテキストを次の例に示します。  
  
 ![FormattedText オブジェクトを使用して表示されるテキスト](../../../../docs/framework/wpf/advanced/media/formattedtext01.png "FormattedText01")  
FormattedText メソッドを使用して表示されたテキスト  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] API から移行する開発者のために、「[Win32 の移行](#win32_migration)」の表に [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText フラグと [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] におけるほぼ同等のものを示します。  
  
### 書式設定されたテキストを使用する理由  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、画面にテキストを描画するための複数のコントロールが含まれています。  各コントロールは、異なるシナリオを対象にしており、それぞれに一連の機能と制限があります。  一般的に、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] で短い文を使用するなど、限定的なテキストのサポートが必要な場合は、<xref:System.Windows.Controls.TextBlock> 要素を使用する必要があります。  最小限のテキスト サポートが必要な場合には、<xref:System.Windows.Controls.Label> を使用できます。  詳細については、「[WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)」を参照してください。  
  
 <xref:System.Windows.Media.FormattedText> オブジェクトは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] テキスト コントロールよりも強力なテキスト書式設定機能を提供し、テキストを装飾的要素として使用する場合に役立ちます。詳細については、後の「[書式設定されたテキストのジオメトリへの変換](#converting_formatted_text)」を参照してください。  
  
 また、<xref:System.Windows.Media.FormattedText> オブジェクトは、テキスト指向の <xref:System.Windows.Media.DrawingVisual> 派生オブジェクトを作成する場合に役立ちます。  <xref:System.Windows.Media.DrawingVisual> は、図形、イメージ、またはテキストのレンダリングに使用する軽量の描画クラスです。  詳細については、[DrawingVisuals を使用したヒット テストのサンプル](http://go.microsoft.com/fwlink/?LinkID=159994)を参照してください。  
  
<a name="using_the_formattedtext_object"></a>   
## FormattedText オブジェクトの使用  
 書式設定されたテキストを作成するには、<xref:System.Windows.Media.FormattedText.%23ctor%2A> コンストラクターを呼び出して <xref:System.Windows.Media.FormattedText> オブジェクトを作成します。  最初の書式設定済みテキスト文字列を作成したら、書式スタイルの範囲を適用できます。  
  
 テキストを特定の幅に制限するには、<xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> プロパティを使用します。  テキストは、指定された幅を超えないように自動的に折り返されます。  テキストを特定の高さに制限するには、<xref:System.Windows.Media.FormattedText.MaxTextHeight%2A> プロパティを使用します。  テキストは、指定された高さを超えた部分に省略記号 "…" を表示します。  
  
 ![FormattedText オブジェクトを使用して表示されるテキスト](../../../../docs/framework/wpf/advanced/media/formattedtext02.png "FormattedText02")  
折り返しと省略記号を示す表示テキスト  
  
 複数の書式スタイルを 1 つ以上の文字に適用できます。  たとえば、<xref:System.Windows.Media.FormattedText.SetFontSize%2A> メソッドと <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> メソッドの両方を呼び出して、テキストの最初の 5 文字の書式設定を変更できます。  
  
 <xref:System.Windows.Media.FormattedText> オブジェクトを作成し、複数の書式設定スタイルをテキストに適用するコード例を次に示します。  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### フォント サイズの測定単位  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションの他のテキスト オブジェクトと同様に、<xref:System.Windows.Media.FormattedText> オブジェクトでは、測定単位としてデバイス非依存ピクセルが使用されます。  ただし、ほとんどの [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] アプリケーションでは、測定単位としてポイントが使用されます。  [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションでポイント単位の表示テキストを使用する場合は、[!INCLUDE[TLA#tla_dipixel#plural](../../../../includes/tlasharptla-dipixelsharpplural-md.md)] をポイントに変換する必要があります。  この変換を実行する方法を次のコード例に示します。  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>   
### 書式設定されたテキストのジオメトリへの変換  
 書式設定したテキストを <xref:System.Windows.Media.Geometry> オブジェクトに変換し、人の目をひきつける他の種類のテキストを作成することができます。  たとえば、テキスト文字列のアウトラインに基づいて <xref:System.Windows.Media.Geometry> オブジェクトを作成できます。  
  
 ![線形グラデーション ブラシを使用するテキスト アウトライン](../../../../docs/framework/wpf/advanced/media/outlinedtext02.png "OutlinedText02")  
線形グラデーション ブラシを使用したテキスト アウトライン  
  
 変換されたテキストのストローク、塗りつぶし、および強調表示を変更して、人の目をひく視覚効果を作成するいくつかの方法を次の例に示します。  
  
 ![塗りつぶしとストロークに別の色を使用するテキスト](../../../../docs/framework/wpf/advanced/media/outlinedtext03.png "OutlinedText03")  
ストロークおよび塗りつぶしを別々の色に設定した例  
  
 ![ストロークに適用されるイメージ ブラシを含むテキスト](../../../../docs/framework/wpf/advanced/media/outlinedtext04.png "OutlinedText04")  
ストロークに適用したイメージ ブラシの例  
  
 ![ストロークに適用されるイメージ ブラシを含むテキスト](../../../../docs/framework/wpf/advanced/media/outlinedtext05.png "OutlinedText05")  
ストロークおよび強調表示に適用したイメージ ブラシの例  
  
 テキストを <xref:System.Windows.Media.Geometry> オブジェクトに変換すると、テキストは文字の集まりではなくなります。つまり、文字列内の文字を変更することはできません。  ただし、変換されたテキストのストロークおよび塗りつぶしのプロパティを変更することで、テキストの外観を変えることができます。  ストロークは、変換したテキストのアウトラインを参照します。塗りつぶしは、変換したテキストのアウトラインの内側の領域を参照します。  詳細については、「[中抜きの文字列を作成する](../../../../docs/framework/wpf/advanced/how-to-create-outlined-text.md)」を参照してください。  
  
 書式設定されたテキストを <xref:System.Windows.Media.PathGeometry> オブジェクトに変換し、そのオブジェクトをテキストの強調表示に使用することもできます。  たとえば、<xref:System.Windows.Media.PathGeometry> オブジェクトに 1 つのアニメーションを適用することができ、これによりアニメーションは書式設定されたテキストのアウトラインに従うようになります。  
  
 次の例は、<xref:System.Windows.Media.PathGeometry> オブジェクトに変換された書式付きテキストを示しています。  アニメーション化された楕円は、レンダリングされたテキストのストロークのパスに従います。  
  
 ![テキストのパス ジオメトリに続く球](../../../../docs/framework/wpf/advanced/media/textpathgeometry01.png "TextPathGeometry01")  
テキストのパス図形座標に従う球体  
  
 詳細については、「[How to: Create a PathGeometry Animation for Text](http://msdn.microsoft.com/ja-jp/29f8051e-798a-463f-a926-a099a99e9c67)」を参照してください。  
  
 書式設定したテキストを <xref:System.Windows.Media.PathGeometry> オブジェクトに変換したら、他の有意義な効果を作成することができます。  たとえば、ビデオをクリップしてテキスト内に表示することができます。  
  
 ![テキストのパス ジオメトリに表示されるビデオ](../../../../docs/framework/wpf/advanced/media/videotextdemo01.png "VideoTextDemo01")  
テキストのパス図形座標に表示されるビデオ  
  
<a name="win32_migration"></a>   
## Win32 の移行  
 テキストを描画するための <xref:System.Windows.Media.FormattedText> の機能は、[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText 関数の機能に似ています。  [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] API から移行する開発者のために、次の表に [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText フラグと [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] におけるほぼ同等のものを示します。  
  
|DrawText フラグ|同等の WPF 操作|説明|  
|------------------|----------------|--------|  
|DT\_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|適切な [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText の 'y' 位置を計算するには、<xref:System.Windows.Media.FormattedText.Height%2A> プロパティを使用します。|  
|DT\_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|出力四角形を計算するには、<xref:System.Windows.Media.FormattedText.Height%2A> プロパティおよび <xref:System.Windows.Media.FormattedText.Width%2A> プロパティを使用します。|  
|DT\_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|<xref:System.Windows.Media.FormattedText.TextAlignment%2A> プロパティを使用して値を <xref:System.Windows.TextAlignment> に設定します。|  
|DT\_EDITCONTROL|なし|必要ありません。  スペースの幅および最後の行のレンダリングは、フレームワークのエディット コントロールと同じです。|  
|DT\_END\_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|<xref:System.Windows.Media.FormattedText.Trimming%2A> プロパティを使用して値を <xref:System.Windows.TextTrimming> に設定します。<br /><br /> <xref:System.Windows.TextTrimming> を使用して、DT\_WORD\_ELIPSIS の末尾の省略記号が設定された [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DT\_END\_ELLIPSIS を取得します。この場合、省略記号は 1 行に収まらない単語にのみ表示されます。|  
|DT\_EXPAND\_TABS|なし|必要ありません。  タブは自動的に全角 4 文字分ごとに展開されます。これは、言語非依存文字の約 8 文字分の幅です。|  
|DT\_EXTERNALLEADING|なし|必要ありません。  外部レディングは、常に行間隔に含まれます。  <xref:System.Windows.Media.FormattedText.LineHeight%2A> プロパティを使用して、ユーザー定義の行間隔を作成します。|  
|DT\_HIDEPREFIX|なし|サポートされていません。  <xref:System.Windows.Media.FormattedText> オブジェクトを構築する前に、文字列から '&' を削除します。|  
|DT\_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|これは、テキストの配置の既定値です。  <xref:System.Windows.Media.FormattedText.TextAlignment%2A> プロパティを使用して値を <xref:System.Windows.TextAlignment> に設定します   \(WPF のみ\)。|  
|DT\_MODIFYSTRING|なし|サポートされていません。|  
|DT\_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|クリッピングは自動的には行われません。  テキストをクリップする場合は、<xref:System.Windows.Media.Visual.VisualClip%2A> プロパティを使用します。|  
|DT\_NOFULLWIDTHCHARBREAK|なし|サポートされていません。|  
|DT\_NOPREFIX|なし|必要ありません。  文字列内の '&' 文字は、常に通常の文字として扱われます。|  
|DT\_PATHELLIPSIS|なし|<xref:System.Windows.Media.FormattedText.Trimming%2A> プロパティを使用して値を <xref:System.Windows.TextTrimming> に設定します。|  
|DT\_PREFIX|なし|サポートされていません。  アクセラレータ キーやリンクなどのテキストにアンダースコアを使用する場合は、<xref:System.Windows.Media.FormattedText.SetTextDecorations%2A> メソッドを使用します。|  
|DT\_PREFIXONLY|なし|サポートされていません。|  
|DT\_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|<xref:System.Windows.Media.FormattedText.TextAlignment%2A> プロパティを使用して値を <xref:System.Windows.TextAlignment> に設定します   \(WPF のみ\)。|  
|DT\_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|<xref:System.Windows.Media.FormattedText.FlowDirection%2A> プロパティを <xref:System.Windows.FlowDirection> に設定します。|  
|DT\_SINGLELINE|なし|必要ありません。  <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> プロパティが設定されていない場合、またはテキストに改行コード \(CR\/LF\) が含まれていない場合、<xref:System.Windows.Media.FormattedText> オブジェクトは単一行コントロールとして動作します。|  
|DT\_TABSTOP|なし|ユーザー定義のタブ位置はサポートされていません。|  
|DT\_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|必要ありません。  上端揃えが既定値です。  その他の垂直方向の配置の値を定義するには、<xref:System.Windows.Media.FormattedText.Height%2A> プロパティを使用して、適切な [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText の 'y' 位置を計算します。|  
|DT\_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|適切な [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText の 'y' 位置を計算するには、<xref:System.Windows.Media.FormattedText.Height%2A> プロパティを使用します。|  
|DT\_WORDBREAK|なし|必要ありません。  単語の区切りは、<xref:System.Windows.Media.FormattedText> オブジェクトで自動的に行われます。  無効にすることはできません。|  
|DT\_WORD\_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|<xref:System.Windows.Media.FormattedText.Trimming%2A> プロパティを使用して値を <xref:System.Windows.TextTrimming> に設定します。|  
  
## 参照  
 <xref:System.Windows.Media.FormattedText>   
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [WPF のタイポグラフィ](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)   
 [中抜きの文字列を作成する](../../../../docs/framework/wpf/advanced/how-to-create-outlined-text.md)   
 [How to: Create a PathGeometry Animation for Text](http://msdn.microsoft.com/ja-jp/29f8051e-798a-463f-a926-a099a99e9c67)