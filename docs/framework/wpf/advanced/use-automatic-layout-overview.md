---
title: "自動レイアウトの使用の概要 | Microsoft Docs"
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
  - "自動レイアウト"
  - "レイアウト, 自動"
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 自動レイアウトの使用の概要
ここでは、開発者がローカライズ可能な[!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)] を持つ [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションを作成する方法に関するガイドラインについて説明します。  これまで、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] のローカライズには時間がかかっていました。  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] が翻訳された言語をピクセル単位で調整する必要がありました。  現在では、適切な設計およびコーディング標準を使用して [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] を構築し、ローカライザーが行う必要があるサイズ変更や位置変更を減らすことができます。  サイズ変更や位置変更がより簡単になるアプリケーション作成方法は、自動レイアウトと呼ばれます。これは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーション設計を使用して実現できます。  
  
 このトピックは、次のセクションで構成されています。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
-   [自動レイアウトを使用する利点](#advantages_of_autolayout)  
  
-   [自動レイアウトとコントロール](#autolayout_controls)  
  
-   [自動レイアウトとコーディング標準](#autolayout_coding)  
  
-   [自動レイアウトとグリッド](#autolay_grids)  
  
-   [IsSharedSizeScope プロパティを使用した自動レイアウトとグリッド](#autolay_grids_issharedsizescope)  
  
-   [関連トピック](#seeAlsoToggle)  
  
<a name="advantages_of_autolayout"></a>   
## 自動レイアウトを使用する利点  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のプレゼンテーション システムは強力で柔軟なため、さまざまな言語の要件を満たすように調整できる、アプリケーション要素のレイアウト機能を提供します。  自動レイアウトの利点の一部を次に示します。  
  
-   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] がどの言語でも適切に表示されます。  
  
-   テキストの翻訳後にコントロールの位置およびサイズを再調整する必要性が軽減されます。  
  
-   ウィンドウ サイズを再調整する必要性が軽減されます。  
  
-   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] レイアウトがどの言語でも適切にレンダリングされます。  
  
-   ローカリゼーション作業を文字列の翻訳と同じ程度まで削減できます。  
  
<a name="autolayout_controls"></a>   
## 自動レイアウトとコントロール  
 自動レイアウトを使用すると、アプリケーションでコントロールのサイズを自動的に調整できます。  たとえば、文字列が収まる長さにコントロールを変更できます。  この機能により、ローカライザーは文字列を翻訳した後、翻訳したテキストに合わせてコントロールのサイズを変更する必要がなくなりました。  次の例では、英語のコンテンツを含むボタンが作成されます。  
  
 [!code-xml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 この例でスペイン語のボタンを作成するには、テキストを変更するだけで済みます。  次に例を示します。  
  
 [!code-xml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 コード サンプルによる出力を次の図に示します。  
  
 ![テキストの言語が異なる同じボタン](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")  
自動サイズ変更可能なボタン  
  
<a name="autolayout_coding"></a>   
## 自動レイアウトとコーディング標準  
 自動レイアウト方法を使用するには、完全にローカライズ可能な [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を生成するためのコーディングと設計の標準および規則のセットが必要です。  次のガイドラインは、自動レイアウト コーディングに役立ちます。  
  
|コーディング標準|Description|  
|--------------|-----------------|  
|絶対位置を使用しない。|-   <xref:System.Windows.Controls.Canvas> は要素を絶対位置に配置するため、使用しないでください。<br />-   コントロールを配置するには、<xref:System.Windows.Controls.DockPanel>、<xref:System.Windows.Controls.StackPanel>、および <xref:System.Windows.Controls.Grid> を使用します。<br />-   さまざまな種類のパネルの詳細については、「[パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)」を参照してください。|  
|ウィンドウに固定サイズを設定しない。|-   <xref:System.Windows.Window.SizeToContent%2A> を使用します。<br />-   次に例を示します。<br /><br /> [!code-xml[LocalizationGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A> を追加する。|<ul><li>アプリケーションのルート要素に <xref:System.Windows.FrameworkElement.FlowDirection%2A> を追加します。</li><li>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、横型、縦型、および双方向のレイアウトをサポートするための便利な方法が用意されています。  プレゼンテーション フレームワークで、<xref:System.Windows.FrameworkElement.FlowDirection%2A> プロパティを使用してレイアウトを定義できます。  フロー方向のパターンは次のとおりです。<br /><br /> <ul><li><xref:System.Windows.FlowDirection> \(LrTb\): ラテン言語や東アジア言語などの横型レイアウト。</li><li><xref:System.Windows.FlowDirection> \(RlTb\): アラビア語やヘブライ語などの双方向レイアウト。</li></ul></li></ul>|  
|物理フォントではなく複合フォントを使用する。|<ul><li>複合フォントでは、<xref:System.Windows.Controls.Control.FontFamily%2A> プロパティをローカライズする必要がありません。</li><li>開発者は、次のいずれかのフォントを使用するか、独自のフォントを作成することができます。<br /><br /> <ul><li>Global User Interface</li><li>Global San Serif</li><li>Global Serif</li></ul></li></ul>|  
|xml:lang を追加する。|-   `xml:lang` 属性を [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] のルート要素に追加します \(英語のアプリケーションの場合は `xml:lang="en-US"` など\)。<br />-   複合フォントでは `xml:lang` を使用して使用するフォントが決定されるため、このプロパティを設定して多言語シナリオをサポートします。|  
  
<a name="autolay_grids"></a>   
## 自動レイアウトとグリッド  
 <xref:System.Windows.Controls.Grid> 要素を使用すると、開発者は要素を配置できるため、自動レイアウトに役立ちます。  <xref:System.Windows.Controls.Grid> コントロールは、列と行の配置を使用して、使用可能なスペースを子要素間で配分できます。  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素は複数のセルにまたがることができ、グリッド内にグリッドを配置することもできます。  グリッドを使用すると、複雑な [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を作成および配置できるため便利です。  グリッドを使用してボタンとテキストを配置する方法を次の例に示します。  セルの高さと幅は <xref:System.Windows.GridUnitType> に設定されているため、イメージを持つボタンを含むセルがイメージに合わせて調整されます。  
  
 [!code-xml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 前のコードによって生成されるグリッドを次の図に示します。  
  
 ![グリッドの例](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob\_grid")  
\[グリッド\]  
  
<a name="autolay_grids_issharedsizescope"></a>   
## IsSharedSizeScope プロパティを使用した自動レイアウトとグリッド  
 <xref:System.Windows.Controls.Grid> 要素は、ローカライズ可能なアプリケーションでコンテンツに合わせて調整されるコントロールを作成する場合に便利です。  ただし、コンテンツに関係なくコントロールが特定のサイズを維持する必要がある場合もあります。  たとえば、多くの場合、\[OK\]、\[キャンセル\]、および \[参照\] ボタンをコンテンツに合わせてサイズ変更することはありません。  この場合、<xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=fullName> 添付プロパティを使用して、複数のグリッド要素間で同じサイズ設定を共有すると便利です。  複数の <xref:System.Windows.Controls.Grid> 要素間で列と行のサイズ設定データを共有する方法を次の例に示します。  
  
 [!code-xml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 **メモ** 完全なコード例については、「[グリッド間でサイズ設定プロパティを共有する](../../../../docs/framework/wpf/controls/how-to-share-sizing-properties-between-grids.md)」を参照してください。  
  
## 参照  
 [WPF のグローバリゼーション](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)   
 [自動レイアウトを使用してボタンを作成する](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)   
 [自動レイアウト用のグリッドを使用する](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)