---
title: "オブジェクト ツリーに存在しないオブジェクト要素の初期化 | Microsoft Docs"
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
  - "要素, 初期化"
  - "初期化 (要素を)"
  - "論理ツリー"
  - "ビジュアル ツリー"
ms.assetid: 7b8dfc9b-46ac-4ce8-b7bb-035734d688b7
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# オブジェクト ツリーに存在しないオブジェクト要素の初期化
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] における初期化処理を委託されるプロセスの中には、その要素が[論理ツリー](GTMT)または[ビジュアル ツリー](GTMT)のいずれかに接続されていることを前提とするものがあります。  ここでは、どちらのツリーにも接続されていない要素を初期化するために必要となる可能性のある手順について説明します。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
## 要素と論理ツリー  
 コード内で [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] クラスのインスタンスを作成するときは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] クラスのオブジェクト初期化処理の一部が、クラス コンストラクターの呼び出し時に実行されるコードから意図的に除外されていることに注意してください。  特に、コントロール クラスの場合は、コントロールの視覚的表現の大部分が、コンストラクターではなく  コントロールのテンプレートによって定義されます。  このテンプレートのソースにはさまざまなものがありますが、ほとんどの場合はテーマ スタイルから取得されます。  テンプレートは、実質的には遅延バインディングです。必要なテンプレートがコントロールに結び付けられるのは、そのコントロールがレイアウト可能になったときです。  コントロールがレイアウト可能になるのは、ルートでレンダリング サーフェイスに接続される論理ツリーに結び付けられたときです。  このルート レベル要素によって、論理ツリーで定義されているすべての子要素のレンダリングが行われます。  
  
 このプロセスには、ビジュアル ツリーも関与します。  テンプレートによってビジュアル ツリーに組み込まれる要素も、接続されなければ完全にはインスタンス化されません。  
  
 この動作の影響で、要素の視覚的特性がすべて揃っていることを前提とする操作には追加の手順が必要になります。  既に構築されているがまだツリーに関連付けられていないクラスの視覚的特性を取得する場合などがそうです。  たとえば、<xref:System.Windows.Media.Imaging.RenderTargetBitmap> に対して <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> を呼び出すときに、渡そうとしているビジュアルがツリーに接続されていない要素である場合は、追加の初期化手順が実行されるまでその要素の視覚的特性は揃いません。  
  
### BeginInit と EndInit を使用して要素を初期化する  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のさまざまなクラスに、<xref:System.ComponentModel.ISupportInitialize> インターフェイスが実装されています。  このインターフェイスの <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> メソッドと <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> メソッドを使用して、コード内の初期化手順 \(たとえばレンダリングに影響を与えるプロパティ値の設定\) の部分を示します。  シーケンス内で <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> が呼び出された後に、レイアウト システムは要素を処理し、暗黙的なスタイルの検索を開始します。  
  
 プロパティ設定対象の要素が <xref:System.Windows.FrameworkElement> または <xref:System.Windows.FrameworkContentElement> 派生クラスである場合は、<xref:System.ComponentModel.ISupportInitialize> にキャストする代わりに、クラス バージョンの <xref:System.Windows.FrameworkElement.BeginInit%2A> と <xref:System.Windows.FrameworkElement.EndInit%2A> を呼び出します。  
  
### サンプル コード  
 次のコンソール アプリケーションのサンプル コードでは、Loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルのレンダリング [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] および <xref:System.Windows.Markup.XamlReader.Load%28System.IO.Stream%29?displayProperty=fullName> を使用して、<xref:System.Windows.FrameworkElement.BeginInit%2A> と <xref:System.Windows.FrameworkElement.EndInit%2A> の正しい配置方法を示します。これらのメソッドは、レンダリングに影響を与えるプロパティを調整する他の [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 呼び出しを囲むように配置します。  
  
 この例では、Main 関数のみを示します。  関数 `Rasterize` および `Save` \(この例には示していません\) は、イメージ処理および入出力を扱うユーティリティ関数です。  
  
 [!code-csharp[InitializeElements#Main](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InitializeElements/CSharp/initializeelements.cs#main)]
 [!code-vb[InitializeElements#Main](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InitializeElements/VisualBasic/initializeelements.vb#main)]  
  
## 参照  
 [WPF のツリー](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)   
 [WPF グラフィックス レンダリングの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)   
 [XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)