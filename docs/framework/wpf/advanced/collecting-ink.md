---
title: "インクの収集 | Microsoft Docs"
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
  - "収集 (デジタル インクを)"
  - "DefaultDrawingAttributes プロパティ"
  - "デジタル インク, 収集"
  - "DrawingAttributes プロパティ"
  - "インク, 収集"
  - "InkCanvas 要素"
  - "プロパティ, DefaultDrawingAttributes"
  - "プロパティ, DrawingAttributes"
ms.assetid: 66a3129d-9577-43eb-acbd-56c147282016
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# インクの収集
[Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) プラットフォームでは、その機能の中核としてデジタル インクが収集されます。  ここでは、[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] でのインクの収集方法について説明します。  
  
## 必要条件  
 以降に示す例を使用するには、まず [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] と [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)] をインストールする必要があります。  また、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に対応するアプリケーションの作成方法も理解しておく必要があります。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の概要については、「[チュートリアル: WPF の概要](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)」を参照してください。  
  
## InkCanvas 要素の使用  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で最も簡単にインクを収集する方法は、<xref:System.Windows.Controls.InkCanvas> 要素を使用することです。  <xref:System.Windows.Controls.InkCanvas> 要素は、[!INCLUDE[TLA2#tla_tpclssdk](../../../../includes/tla2sharptla-tpclssdk-md.md)] 以前のバージョンの <xref:Microsoft.Ink.InkOverlay> オブジェクトに似ています。  
  
 <xref:System.Windows.Controls.InkCanvas> 要素は、インク入力を受け取って表示するために使用します。  インクは一般的に、スタイラスを使用して入力します。スタイラスはデジタイザーとの対話により、インク ストロークを生成します。  また、スタイラスの代わりにマウスを使用することもできます。  生成されたストロークは <xref:System.Windows.Ink.Stroke> オブジェクトとして表され、プログラムとユーザー入力の両方によって操作できます。  <xref:System.Windows.Controls.InkCanvas> を使用すると、ユーザーは既存の <xref:System.Windows.Ink.Stroke> を選択、変更、または削除することができます。  
  
 XAML を使用して、`InkCanvas` 要素をツリーに追加するだけで簡単にインク収集を設定できます。  次の例では、[!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] で作成された既定の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロジェクトに <xref:System.Windows.Controls.InkCanvas> を追加します。  
  
 [!code-xml[DigitalInkTopics#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]  
  
 `InkCanvas` 要素には子要素を含めることもできます。これにより、ほとんどすべての XAML 要素にインク注釈機能を追加できます。  たとえば、インク処理機能をテキスト要素に追加するには、単にその要素を <xref:System.Windows.Controls.InkCanvas> の子にします。  
  
 [!code-xml[DigitalInkTopics#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]  
  
 インクを使用したイメージのマークアップのサポートも、簡単に追加できます。  
  
 [!code-xml[DigitalInkTopics#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]  
  
### InkCollection モード  
 <xref:System.Windows.Controls.InkCanvas> は、<xref:System.Windows.Controls.InkCanvas.EditingMode%2A> プロパティを使用してさまざまな入力モードをサポートします。  
  
### インクの操作  
 <xref:System.Windows.Controls.InkCanvas> は、さまざまなインク編集操作をサポートしています。  たとえば、<xref:System.Windows.Controls.InkCanvas> は、ペンの消しゴム ツールによる消去をサポートします。この機能を要素に追加するために、追加コードは必要ありません。  
  
#### Selection  
 選択モードは、<xref:System.Windows.Controls.InkCanvasEditingMode> プロパティを **Select** に設定するだけで、簡単に設定できます。  次のコードは、<xref:System.Windows.Forms.CheckBox> の値に基づいて編集モードを設定します。  
  
 [!code-csharp[DigitalInkTopics#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
 [!code-vb[DigitalInkTopics#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]  
  
#### DrawingAttributes  
 <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> プロパティは、インク ストロークの外観を変更するために使用します。  たとえば、<xref:System.Windows.Ink.DrawingAttributes> の <xref:System.Windows.Ink.DrawingAttributes.Color%2A> メンバーは、描画される <xref:System.Windows.Ink.Stroke> の色を設定します。  選択されたストロークの色を赤に変更する方法を次の例に示します。  
  
 [!code-csharp[DigitalInkTopics#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
 [!code-vb[DigitalInkTopics#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]  
  
### DefaultDrawingAttributes  
 <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> プロパティを使用すると、<xref:System.Windows.Controls.InkCanvas> で作成されるストロークの高さ、幅、色などのプロパティにアクセスできます。  <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> を変更すると、それ以降に <xref:System.Windows.Controls.InkCanvas> に入力されるストロークはすべて新しいプロパティ値を使用して描画されます。  
  
 分離コード ファイルでの <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> の変更に加えて、XAML 構文を使用した <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> プロパティの指定もできます。  <xref:System.Windows.Ink.DrawingAttributes.Color%2A> プロパティを設定する方法を次の XAML コードに示します。  このコードを使用するには、Visual Studio 2005 で "HelloInkCanvas" という新しい [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロジェクトを作成します。  Window1.xaml ファイルのコードを次のコードに置き換えます。  
  
 [!code-xml[HelloInkCanvas#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]  
  
 次に、以下のボタン イベント ハンドラーを、分離コード ファイルの Window1 クラス内に追加します。  
  
 [!code-csharp[HelloInkCanvas#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]  
  
 このコードのコピー後に、Microsoft Visual Studio 2005 で F5 キーを押し、デバッガーでプログラムを実行します。  
  
 <xref:System.Windows.Controls.StackPanel> によってボタンが <xref:System.Windows.Controls.InkCanvas> の上に配置されることに注目してください。  ボタンの上でインク処理を実行しようとすると、<xref:System.Windows.Controls.InkCanvas> によってインクがボタンの背後で収集および描画されます。  これは、ボタンが <xref:System.Windows.Controls.InkCanvas> の子ではなく兄弟であるためです。  また、ボタンは z オーダーの上位に位置するため、インクはその背後で描画されます。  
  
## 参照  
 <xref:System.Windows.Ink.DrawingAttributes>   
 <xref:System.Windows.InkCanvas.DefaultDrawingAttributes%2A>   
 <xref:System.Windows.Ink>