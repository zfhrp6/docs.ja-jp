---
title: インクの収集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ink [WPF], collecting
- InkCanvas element [WPF]
- properties [WPF], DrawingAttributes
- collecting digital ink [WPF]
- digital ink [WPF], collecting
- properties [WPF], DefaultDrawingAttributes
- DefaultDrawingAttributes property [WPF]
ms.assetid: 66a3129d-9577-43eb-acbd-56c147282016
ms.openlocfilehash: d441f606a577a2c0506a0f9ae510b3ea1045bba9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541071"
---
# <a name="collecting-ink"></a>インクの収集
[Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) プラットフォームでは、その機能の中核としてデジタル インクが収集されます。 このトピックでは、インク Windows Presentation Foundation (WPF) のコレクションの方法を説明します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 以降に示す例を使用するには、まず、[!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] と [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)] をインストールする必要があります。 また、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に対応するアプリケーションの作成方法も理解しておく必要があります。 概要の詳細については[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を参照してください[チュートリアル: 最初の WPF デスクトップ アプリケーション](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)です。  
  
## <a name="using-the-inkcanvas-element"></a>InkCanvas 要素の使用  
 <xref:System.Windows.Controls.InkCanvas>要素でインクを収集する最も簡単な方法を提供する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。 <xref:System.Windows.Controls.InkCanvas>要素がに似ていますが、 [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/microsoft.ink.inkoverlay\(v=vs.90\).aspx)オブジェクトから、[!INCLUDE[TLA2#tla_tpclssdk](../../../../includes/tla2sharptla-tpclssdk-md.md)]と以前のバージョン。  
  
 使用して、<xref:System.Windows.Controls.InkCanvas>要素を受け取り、インク入力を表示します。 インクは一般的に、スタイラスを使用して入力します。スタイラスはデジタイザーとの対話により、インク ストロークを生成します。 また、スタイラスの代わりにマウスを使用することもできます。 作成したストロークとして表されます<xref:System.Windows.Ink.Stroke>プログラムとユーザーの両方の入力、オブジェクト、およびそれらを操作できます。 <xref:System.Windows.Controls.InkCanvas>により、ユーザーが選択、変更、削除、既存<xref:System.Windows.Ink.Stroke>です。  
  
 XAML を使用して、`InkCanvas` 要素をツリーに追加するだけで簡単にインク収集を設定できます。 次の例では追加、<xref:System.Windows.Controls.InkCanvas>既定[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]で作成されたプロジェクト[!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)]です。  
  
 [!code-xaml[DigitalInkTopics#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]  
  
 `InkCanvas` 要素には子要素を含めることもできます。これにより、ほとんどすべての XAML 要素にインク注釈機能を追加できます。 たとえば、機能を追加する場合は、インクをテキスト要素に、単に使用するの子、<xref:System.Windows.Controls.InkCanvas>です。  
  
 [!code-xaml[DigitalInkTopics#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]  
  
 インクを使用したイメージのマークアップのサポートも、簡単に追加できます。  
  
 [!code-xaml[DigitalInkTopics#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]  
  
### <a name="inkcollection-modes"></a>InkCollection モード  
 <xref:System.Windows.Controls.InkCanvas>さまざまな入力モードをサポートしています、<xref:System.Windows.Controls.InkCanvas.EditingMode%2A>プロパティです。  
  
### <a name="manipulating-ink"></a>インクの操作  
 <xref:System.Windows.Controls.InkCanvas>多くのインクの編集操作に対するサポートを提供します。 たとえば、<xref:System.Windows.Controls.InkCanvas>追加のコードを持たない要素への機能を追加するために必要なサポート ペンの背面を消去します。  
  
#### <a name="selection"></a>選択ツール  
 選択モードは設定などの単純な<xref:System.Windows.Controls.InkCanvasEditingMode>プロパティを**選択**です。 次のコードの値に基づいて編集モードの設定、 <xref:System.Windows.Forms.CheckBox>:  
  
 [!code-csharp[DigitalInkTopics#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
 [!code-vb[DigitalInkTopics#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]  
  
#### <a name="drawingattributes"></a>DrawingAttributes  
 使用して、<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>インク ストロークの外観を変更するプロパティです。 インスタンス、<xref:System.Windows.Ink.DrawingAttributes.Color%2A>のメンバー <xref:System.Windows.Ink.DrawingAttributes> 、表示の色を設定<xref:System.Windows.Ink.Stroke>です。 次の例では、選択されたストロークの色を赤に変更します。  
  
 [!code-csharp[DigitalInkTopics#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
 [!code-vb[DigitalInkTopics#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]  
  
### <a name="defaultdrawingattributes"></a>DefaultDrawingAttributes  
 <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>プロパティは高さ、幅、およびで作成される線の色などのプロパティへのアクセスを提供する<xref:System.Windows.Controls.InkCanvas>です。 変更すると、<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>に入力されたすべての将来のストローク、<xref:System.Windows.Controls.InkCanvas>は、新しいプロパティの値で表示します。  
  
 変更だけでなく、<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>を指定するため、XAML 構文を使用する分離コード ファイルで<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>プロパティです。 次の XAML コードを設定する方法を示しています、<xref:System.Windows.Ink.DrawingAttributes.Color%2A>プロパティです。 このコードを使用するには、Visual Studio 2005 で "HelloInkCanvas" という新しい [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロジェクトを作成します。 Window1.xaml ファイルのコードを次のコードに置き換えます。  
  
 [!code-xaml[HelloInkCanvas#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]  
  
 次に、以下のボタン イベント ハンドラーを、分離コード ファイルの Window1 クラス内に追加します。  
  
 [!code-csharp[HelloInkCanvas#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]  
  
 このコードのコピー後に、Microsoft Visual Studio 2005 で **F5** キーを押し、デバッガーでプログラムを実行します。  
  
 通知方法、<xref:System.Windows.Controls.StackPanel>ボタンの上に配置します。、<xref:System.Windows.Controls.InkCanvas>です。 ボタンの上にインクをしようとする場合、<xref:System.Windows.Controls.InkCanvas>を収集し、ボタンの背景にインクをレンダリングします。 これは、ボタンがあるため、<xref:System.Windows.Controls.InkCanvas>子とは対照的です。 また、ボタンは z オーダーの上位に位置するため、インクはその背後で描画されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Ink.DrawingAttributes>  
 <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>  
 <xref:System.Windows.Ink>
