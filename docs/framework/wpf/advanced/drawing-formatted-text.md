---
title: 書式設定されたテキストの描画
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF]
- typography [WPF], drawing formatted text
- formatted text [WPF]
- drawing [WPF], formatted text
ms.assetid: b1d851c1-331c-4814-9964-6fe769db6f1f
ms.openlocfilehash: 978c97b8cae24bff4ebdea8f4e56a940e5907fa6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="drawing-formatted-text"></a>書式設定されたテキストの描画
このトピックの機能の概要を示します、<xref:System.Windows.Media.FormattedText>オブジェクト。 このオブジェクトは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションでのテキストの描画に対する低レベルの制御を提供します。  
  
  
## <a name="technology-overview"></a>テクノロジの概要  
 <xref:System.Windows.Media.FormattedText>オブジェクトでは、これで、テキスト内の各文字形式指定できる個別に、複数行のテキストを描画することができます。 複数の書式が適用されたテキストを次の例に示します。  
  
 ![FormattedText オブジェクトを使用して表示されるテキスト](../../../../docs/framework/wpf/advanced/media/formattedtext01.jpg "FormattedText01")  
FormattedText オブジェクトを使用して表示されるテキスト  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] API から移行する開発者のために、「[Win32 の移行](#win32_migration)」の表に [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText フラグと [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] におけるほぼ同等のものを示します。  
  
### <a name="reasons-for-using-formatted-text"></a>書式設定されたテキストを使用する理由  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には画面にテキストを描画するための複数のコントロールが含まれています。 各コントロールは異なるシナリオを対象にしており、それぞれに一連の機能と制限があります。 一般に、<xref:System.Windows.Controls.TextBlock>制限付きのテキストのサポートが必要な場合、簡単な文など、要素を使用する必要があります、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]です。 <xref:System.Windows.Controls.Label> 最小限のテキストのサポートが必要な場合に使用できます。 詳細については、「[WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)」を参照してください。  
  
 <xref:System.Windows.Media.FormattedText>オブジェクトが書式設定機能よりも大きい値のテキストを提供[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]テキスト コントロールとテキスト装飾的な要素として使用する場合に役に立ちます。 詳細については、後の「[書式設定されたテキストのジオメトリへの変換](#converting_formatted_text)」を参照してください。  
  
 さらに、<xref:System.Windows.Media.FormattedText>オブジェクトはテキスト指向の作成に役立つ<xref:System.Windows.Media.DrawingVisual>-派生オブジェクト。 <xref:System.Windows.Media.DrawingVisual> 図形、画像、またはテキストを表示するために使用される軽量の描画クラスです。 詳細については、「[DrawingVisuals を使用したヒット テストのサンプル](http://go.microsoft.com/fwlink/?LinkID=159994)」を参照してください。  
  
## <a name="using-the-formattedtext-object"></a>FormattedText オブジェクトの使用  
 書式設定されたテキストを作成するには、<xref:System.Windows.Media.FormattedText.%23ctor%2A>コンス トラクターを作成する、<xref:System.Windows.Media.FormattedText>オブジェクト。 最初の書式設定済みテキスト文字列を作成したら、書式スタイルの範囲を適用できます。  
  
 使用して、<xref:System.Windows.Media.FormattedText.MaxTextWidth%2A>幅を指定するテキストを制約するプロパティです。 テキストは、指定された幅を超えないように自動的に折り返されます。 使用して、<xref:System.Windows.Media.FormattedText.MaxTextHeight%2A>高さを指定するテキストを制約するプロパティです。 テキストは、指定された高さを超えた部分に省略記号 "…" を表示します。  
  
 ![FormattedText オブジェクトを使用して表示されるテキスト](../../../../docs/framework/wpf/advanced/media/formattedtext02.png "FormattedText02")  
折り返しと省略記号を示す表示テキスト  
  
 複数の書式スタイルを 1 つ以上の文字に適用できます。 たとえば、両方を呼び出す可能性があります、<xref:System.Windows.Media.FormattedText.SetFontSize%2A>と<xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A>テキスト内の最初の 5 文字の書式を変更する方法です。  
  
 次のコード例を作成、<xref:System.Windows.Media.FormattedText>オブジェクトをテキストにいくつかの書式スタイルを適用します。  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>フォント サイズの単位  
 場合は、他の文字列オブジェクトと同様に[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]、アプリケーション、<xref:System.Windows.Media.FormattedText>オブジェクトがメジャーの単位としてデバイスに依存しないピクセルを使用します。 ただし、ほとんどの [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] アプリケーションでは、単位としてポイントが使用されます。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションでポイント単位の表示テキストを使用する場合は、[!INCLUDE[TLA#tla_dipixel#plural](../../../../includes/tlasharptla-dipixelsharpplural-md.md)] をポイントに変換する必要があります。 この変換を実行する方法を次のコード例に示します。  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>   
### <a name="converting-formatted-text-to-a-geometry"></a>書式設定されたテキストのジオメトリへの変換  
 書式設定されたテキストに変換することができます<xref:System.Windows.Media.Geometry>オブジェクト、他の種類の視覚的に関心のテキストを作成することができます。 たとえば、作成した、<xref:System.Windows.Media.Geometry>テキスト文字列のアウトラインに基づいてオブジェクト。  
  
 ![線形グラデーション ブラシを使用するテキスト アウトライン](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")  
線形グラデーション ブラシを使用するテキスト アウトライン  
  
 変換されたテキストのストローク、塗りつぶし、強調表示を変更して、人の目をひく視覚効果を作成するいくつかの方法を次の例に示します。  
  
 ![塗りつぶしとストロークを別の色を含むテキスト](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")  
ストロークと塗りつぶしを別々の色に設定した例  
  
 ![ストロークに適用されるイメージ ブラシを含むテキスト](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")  
ストロークに適用したイメージ ブラシの例  
  
 ![ストロークに適用されるイメージ ブラシを含むテキスト](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")  
ストロークと強調表示に適用したイメージ ブラシの例  
  
 テキストに変換するときに、<xref:System.Windows.Media.Geometry>オブジェクト、文字のコレクションではなくなりました: テキスト文字列内の文字を変更することはできません。 ただし、変換されたテキストのストロークおよび塗りつぶしのプロパティを変更することで、テキストの外観を変えることができます。 ストロークは、変換したテキストのアウトラインを参照します。塗りつぶしは、変換したテキストのアウトラインの内側の領域を参照します。 詳細については、「[方法: 中抜きの文字列を作成する](../../../../docs/framework/wpf/advanced/how-to-create-outlined-text.md)」を参照してください。  
  
 書式設定されたテキストを変換することも、<xref:System.Windows.Media.PathGeometry>オブジェクト、およびテキストを強調表示のオブジェクトを使用します。 アニメーションを適用するなど、<xref:System.Windows.Media.PathGeometry>オブジェクトのアニメーションの書式設定テキスト アウトラインに依存できるようにします。  
  
 次の例では、書式設定されたテキストに変換されている、<xref:System.Windows.Media.PathGeometry>オブジェクト。 アニメーション化された楕円は、レンダリングされたテキストのストロークのパスに従います。  
  
 ![テキストのパス ジオメトリに続く球](../../../../docs/framework/wpf/advanced/media/textpathgeometry01.gif "TextPathGeometry01")  
テキストのパス ジオメトリに続く球  
  
 詳細については、「[How to: Create a PathGeometry Animation for Text](http://msdn.microsoft.com/library/29f8051e-798a-463f-a926-a099a99e9c67)」(方法: テキストの PathGeometry アニメーションを作成する) を参照してください。  
  
 その他の興味深い使用の書式設定されたテキストを作成するに変換された後、<xref:System.Windows.Media.PathGeometry>オブジェクト。 たとえば、ビデオをクリップしてテキスト内に表示することができます。  
  
 ![テキストのパス ジオメトリに表示されるビデオ](../../../../docs/framework/wpf/advanced/media/videotextdemo01.png "VideoTextDemo01")  
テキストのパス ジオメトリに表示されるビデオ  
  
<a name="win32_migration"></a>   
## <a name="win32-migration"></a>Win32 の移行  
 機能<xref:System.Windows.Media.FormattedText>テキストを描画するための機能に似ていますが、 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText 関数。 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] API から移行する開発者のために、[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText フラグと [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] におけるほぼ同等のものを次の表に示します。  
  
|DrawText フラグ|同等の WPF 操作|メモ|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|使用して、<xref:System.Windows.Media.FormattedText.Height%2A>プロパティを適切なコンピューティング[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]方向の位置。|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|使用して、<xref:System.Windows.Media.FormattedText.Height%2A>と<xref:System.Windows.Media.FormattedText.Width%2A>プロパティを出力四角形を計算します。|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|使用して、<xref:System.Windows.Media.FormattedText.TextAlignment%2A>プロパティ値を設定して<xref:System.Windows.TextAlignment.Center>です。|  
|DT_EDITCONTROL|なし|不要。 スペースの幅および最後の行のレンダリングは、フレームワークのエディット コントロールと同じです。|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|使用して、 <xref:System.Windows.Media.FormattedText.Trimming%2A> 、値を持つプロパティ<xref:System.Windows.TextTrimming.CharacterEllipsis>です。<br /><br /> 使用して<xref:System.Windows.TextTrimming.WordEllipsis>を取得する[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]DT_END_ELLIPSIS DT_WORD_ELIPSIS で省略記号を終了する — この場合、文字の省略記号のみが発生した 1 行に収まらないいる単語のです。|  
|DT_EXPAND_TABS|なし|不要。 タブは自動的に全角 4 文字分ごとに展開されます。これは、言語非依存文字の約 8 文字分の幅です。|  
|DT_EXTERNALLEADING|なし|不要。 外部レディングは、常に行間隔に含まれます。 使用して、<xref:System.Windows.Media.FormattedText.LineHeight%2A>ユーザー定義の行間を作成するプロパティです。|  
|DT_HIDEPREFIX|なし|サポートされていません。 作成する前に、文字列から '&' を削除、<xref:System.Windows.Media.FormattedText>オブジェクト。|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|これは、テキストの配置の既定値です。 使用して、<xref:System.Windows.Media.FormattedText.TextAlignment%2A>プロパティ値を設定して<xref:System.Windows.TextAlignment.Left>です。 (WPF のみ)。|  
|DT_MODIFYSTRING|なし|サポートされていません。|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|クリッピングは自動的には行われません。 クリップのテキストにする場合は、使用、<xref:System.Windows.Media.Visual.VisualClip%2A>プロパティです。|  
|DT_NOFULLWIDTHCHARBREAK|なし|サポートされていません。|  
|DT_NOPREFIX|なし|不要。 文字列内の '&' 文字は、常に通常の文字として扱われます。|  
|DT_PATHELLIPSIS|なし|使用して、 <xref:System.Windows.Media.FormattedText.Trimming%2A> 、値を持つプロパティ<xref:System.Windows.TextTrimming.WordEllipsis>です。|  
|DT_PREFIX|なし|サポートされていません。 アクセラレータ キーまたはリンクなどのテキストのアンダー スコアを使用する場合を使用して、<xref:System.Windows.Media.FormattedText.SetTextDecorations%2A>メソッドです。|  
|DT_PREFIXONLY|なし|サポートされていません。|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|使用して、<xref:System.Windows.Media.FormattedText.TextAlignment%2A>プロパティ値を設定して<xref:System.Windows.TextAlignment.Right>です。 (WPF のみ)。|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|<xref:System.Windows.Media.FormattedText.FlowDirection%2A> プロパティを <xref:System.Windows.FlowDirection.RightToLeft> に設定します。|  
|DT_SINGLELINE|なし|不要。 <xref:System.Windows.Media.FormattedText> オブジェクトは、1 行のコントロールとして動作しますが場合を除き、いずれか、<xref:System.Windows.Media.FormattedText.MaxTextWidth%2A>プロパティを設定またはテキストには、キャリッジ リターン/ライン フィード (CR/LF) が含まれています。|  
|DT_TABSTOP|なし|ユーザー定義のタブ位置はサポートされていません。|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|不要。 上端揃えが既定値です。 その他の垂直方向の位置指定値を使用して定義することができます、<xref:System.Windows.Media.FormattedText.Height%2A>プロパティを適切なコンピューティング[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]方向の位置。|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|使用して、<xref:System.Windows.Media.FormattedText.Height%2A>プロパティを適切なコンピューティング[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]方向の位置。|  
|DT_WORDBREAK|なし|不要。 単語区切り処理が自動的に行われます<xref:System.Windows.Media.FormattedText>オブジェクト。 無効にすることはできません。|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|使用して、 <xref:System.Windows.Media.FormattedText.Trimming%2A> 、値を持つプロパティ<xref:System.Windows.TextTrimming.WordEllipsis>です。|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.FormattedText>  
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [WPF のタイポグラフィ](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [中抜きの文字列を作成する](../../../../docs/framework/wpf/advanced/how-to-create-outlined-text.md)  
 [方法: テキストの PathGeometry アニメーションを作成する](http://msdn.microsoft.com/library/29f8051e-798a-463f-a926-a099a99e9c67)
