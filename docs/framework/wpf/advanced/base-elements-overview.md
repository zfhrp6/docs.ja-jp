---
title: 基本要素の概要
ms.date: 03/30/2017
helpviewer_keywords:
- base elements [WPF]
ms.assetid: 2c997092-72c6-4767-bc84-74267f4eee72
ms.openlocfilehash: bcfcb87d0ddf5181a47d459e821bacd9b9f6b61c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541834"
---
# <a name="base-elements-overview"></a>基本要素の概要
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のクラスの大部分は、[!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] のドキュメントで一般に基本要素クラスと呼ばれている 4 つのクラスから派生しています。 これらのクラスは<xref:System.Windows.UIElement>、 <xref:System.Windows.FrameworkElement>、 <xref:System.Windows.ContentElement>、および<xref:System.Windows.FrameworkContentElement>です。 <xref:System.Windows.DependencyObject>両方の共通の基本クラスになっているため、クラスが関係も<xref:System.Windows.UIElement>と <xref:System.Windows.ContentElement>  
 
  
<a name="base_apis"></a>   
## <a name="base-element-apis-in-wpf-classes"></a>WPF クラスの基本要素 API  
 両方<xref:System.Windows.UIElement>と<xref:System.Windows.ContentElement>から派生した<xref:System.Windows.DependencyObject>、若干異なる経路を通じてします。 このレベルでの分割が扱う方法、<xref:System.Windows.UIElement>または<xref:System.Windows.ContentElement>ユーザー インターフェイスと、アプリケーションで使用され、どのような目的で使用されます。 <xref:System.Windows.UIElement> <xref:System.Windows.Media.Visual>を基になる下位レベルのグラフィックスのサポートを公開するクラス、クラスの階層構造では、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]です。 <xref:System.Windows.Media.Visual> 独立した四角形の画面領域を定義することによってレンダリングのフレームワークを提供します。 実際には、<xref:System.Windows.UIElement>大規模オブジェクト モデルをサポートする要素は、表示するために意図したものとレイアウト領域の四角形の画面領域としてを記述することができ、コンテンツ モデルが意図的に複数開いている、異なる許可するには要素の組み合わせ。 <xref:System.Windows.ContentElement> 派生していません<xref:System.Windows.Media.Visual>; は、そのモデルを<xref:System.Windows.ContentElement>リーダーや、要素を解釈し、完全な生成されるビューアーなどの他のものによって消費するか<xref:System.Windows.Media.Visual>の[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]を使用します。 特定<xref:System.Windows.UIElement>クラスが意図されてコンテンツ ホスト: 1 つまたは複数のホストおよびレンダリングを提供する<xref:System.Windows.ContentElement>クラス (<xref:System.Windows.Controls.DocumentViewer>ようなクラスの例に示します)。 <xref:System.Windows.ContentElement> やや小さいオブジェクト モデルと要素の基本クラスとことについては、テキストを対処の詳細またはドキュメントの内容を内でホストする可能性がありますとして使用され、<xref:System.Windows.UIElement>です。  
  
### <a name="framework-level-and-core-level"></a>フレームワークレベルとコアレベル  
 <xref:System.Windows.UIElement> 基本クラスとして機能<xref:System.Windows.FrameworkElement>、および<xref:System.Windows.ContentElement>の基本クラスとして機能<xref:System.Windows.FrameworkContentElement>します。 この次のレベルのクラスが存在する理由は、WPF フレームワーク レベルとは異なる WPF コア レベルをサポートすることです。この区分は、PresentationCore と PresentationFramework アセンブリ間での [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] の区分にも存在します。 WPF フレームワーク レベルは、表示のためのレイアウト マネージャーの実装など、アプリケーションの基本的ニーズに対して、より完全なソリューションを提供します。 WPF コア レベルは、アセンブリの追加によるオーバーヘッドを引き起こすことなく [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の大部分を使用する方法を提供します。 これらのレベルの区別は、ほとんどの通常のアプリケーション開発シナリオでほとんど問題になりません。一般には、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] を 1 つのものと見なして、WPF フレームワーク レベルと WPF コア レベルの違いについて意識する必要はありません。 アプリケーション設計で WPF フレームワーク レベルの機能の大部分を置き換えることにした場合、たとえば開発中のソリューション全体に、独自の[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] の構成およびレイアウトが既に実装されている場合には、これらのレベルの区分に関する理解が必要となる可能性があります。  
  
<a name="subclassing_elements"></a>   
## <a name="choosing-which-element-to-derive-from"></a>派生元の要素を選択する  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] を拡張したカスタム クラスを作成するための最も実際的な方法は、既存のクラス階層から必要な機能を可能な限り得ることのできる、いずれかの [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] クラスから派生させることです。 このセクションでは、継承元とするクラスの選択に役立つように、最も重要な要素クラスのうちの 3 つのクラスが提供する機能を示します。  
  
 コントロールを実装する場合はから派生するより一般的な理由の 1 つは実際に、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]クラス、多くの場合をまたはには、実用的なコントロール、コントロールのファミリ基本クラス、クラスから派生させるためから最低限、<xref:System.Windows.Controls.Control>基底クラス。 いくつかのガイドラインと実際の例については、「[コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)」を参照してください。  
  
 コントロールを作成しているのではなく、階層の上位にあるクラスから派生する必要がある場合は、各基本要素クラスに定義された特性に関するガイドを意図した、以下のセクションを参照してください。  
  
 派生するクラスを作成する場合<xref:System.Windows.DependencyObject>、次の機能を継承します。  
  
-   <xref:System.Windows.DependencyObject.GetValue%2A> および<xref:System.Windows.DependencyObject.SetValue%2A>サポート、およびシステムのサポートの [全般] プロパティ。  
  
-   依存関係プロパティと、依存関係プロパティとして実装されている添付プロパティを使用する機能。  
  
 派生するクラスを作成する場合<xref:System.Windows.UIElement>、それに加えてによって提供される次の機能を継承する<xref:System.Windows.DependencyObject>:  
  
-   アニメーション化されたプロパティ値の基本的なサポート。 詳しくは、「 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」をご覧ください。  
  
-   基本的な入力イベントのサポートと、コマンド実行のサポート。 詳細については、「[入力の概要](../../../../docs/framework/wpf/advanced/input-overview.md)」および「[コマンド実行の概要](../../../../docs/framework/wpf/advanced/commanding-overview.md)」を参照してください。  
  
-   レイアウト システムに情報を提供するためにオーバーライドできる仮想メソッド。  
  
 派生するクラスを作成する場合<xref:System.Windows.FrameworkElement>、それに加えてによって提供される次の機能を継承する<xref:System.Windows.UIElement>:  
  
-   スタイル設定とストーリーボードのサポート。 詳細については、次を参照してください。<xref:System.Windows.Style>と[ストーリー ボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)です。  
  
-   データ バインディングのサポート。 詳しくは、「 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」をご覧ください。  
  
-   動的リソース参照のサポート。 詳細については、「[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)」を参照してください。  
  
-   プロパティ値継承のサポート、および、データ バインディング、スタイル、またはレイアウトのフレームワークの実装などのフレームワーク サービスのプロパティに関する条件をレポートする場合に役立つ、メタデータ内の他のフラグ。 詳細については、「[フレームワーク プロパティ メタデータ](../../../../docs/framework/wpf/advanced/framework-property-metadata.md)」を参照してください。  
  
-   論理ツリーの概念。 詳細については、「[WPF のツリー](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)」を参照してください。  
  
-   レイアウト システムの実際の WPF フレームワーク レベルの実装のサポートを含む、<xref:System.Windows.FrameworkElement.OnPropertyChanged%2A>を検出する上書きのプロパティにその影響を与えるレイアウトが変更されます。  
  
 派生するクラスを作成する場合<xref:System.Windows.ContentElement>、それに加えてによって提供される次の機能を継承する<xref:System.Windows.DependencyObject>:  
  
-   アニメーションのサポート。 詳しくは、「 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」をご覧ください。  
  
-   基本的な入力イベントのサポートと、コマンド実行のサポート。 詳細については、「[入力の概要](../../../../docs/framework/wpf/advanced/input-overview.md)」および「[コマンド実行の概要](../../../../docs/framework/wpf/advanced/commanding-overview.md)」を参照してください。  
  
 派生するクラスを作成する場合<xref:System.Windows.FrameworkContentElement>、それに加えてによって提供される次の機能を取得する<xref:System.Windows.ContentElement>:  
  
-   スタイル設定とストーリーボードのサポート。 詳細については、次を参照してください。<xref:System.Windows.Style>と[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)です。  
  
-   データ バインディングのサポート。 詳しくは、「 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」をご覧ください。  
  
-   動的リソース参照のサポート。 詳しくは、「[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)」を参照してください。  
  
-   プロパティ値継承のサポート、および、データ バインディング、スタイル、またはレイアウトのフレームワークの実装などのフレームワーク サービスのプロパティに関する条件をレポートする場合に役立つ、メタデータ内の他のフラグ。 詳細については、「[フレームワーク プロパティ メタデータ](../../../../docs/framework/wpf/advanced/framework-property-metadata.md)」を参照してください。  
  
-   レイアウト システムの変更へのアクセスを継承しない場合 (など<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>)。 レイアウト システムの実装はのみに使用できます<xref:System.Windows.FrameworkElement>です。 ただし、継承、<xref:System.Windows.FrameworkElement.OnPropertyChanged%2A>レイアウトに影響を与えるし、レポート、コンテンツ ホストにこれらをプロパティへの変更を検出するオーバーライドします。  
  
 さまざまなクラスに関してコンテンツ モデルがドキュメント化されています。 派生元として適切なクラスを見つける必要がある場合、クラスのコンテンツ モデルは、考慮する必要がある項目の候補の 1 つです。 詳細については、「[WPF のコンテンツ モデル](../../../../docs/framework/wpf/controls/wpf-content-model.md)」を参照してください。  
  
<a name="other_base_classes"></a>   
## <a name="other-base-classes"></a>他の基本クラス  
  
### <a name="dispatcherobject"></a>DispatcherObject  
 <xref:System.Windows.Threading.DispatcherObject> サポートを提供、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]スレッド モデルとのすべてのオブジェクトが作成できるように[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションに関連付けられる、<xref:System.Windows.Threading.Dispatcher>です。 派生していない場合でも<xref:System.Windows.UIElement>、 <xref:System.Windows.DependencyObject>、または<xref:System.Windows.Media.Visual>から派生することを検討する必要があります<xref:System.Windows.Threading.DispatcherObject>このスレッド処理モデルのサポートを取得するためにします。 詳細については、「[スレッド モデル](../../../../docs/framework/wpf/advanced/threading-model.md)」を参照してください。  
  
### <a name="visual"></a>ビジュアル  
 <xref:System.Windows.Media.Visual> 一般に約四角形の領域に視覚的な表示を必要とする 2D オブジェクトという概念を実装します。 実際のレンダリング、 <xref:System.Windows.Media.Visual> (自己完結型はありません) 他のクラスで行われますが、<xref:System.Windows.Media.Visual>クラスは、さまざまなレベルでのレンダリング プロセスによって使用される既知の型を提供します。 <xref:System.Windows.Media.Visual> ヒット テストの実装が、陽性のヒット テストを報告するイベントを公開しません (は<xref:System.Windows.UIElement>)。 詳細については、「[ビジュアル層のプログラミング](../../../../docs/framework/wpf/graphics-multimedia/visual-layer-programming.md)」を参照してください。  
  
### <a name="freezable"></a>Freezable  
 <xref:System.Windows.Freezable> 変更できないオブジェクトが必要なまたはパフォーマンス向上のために必要なときに、オブジェクトのコピーを生成するための手段を提供することで、変更可能なオブジェクトの不変性をシミュレートします。 <xref:System.Windows.Freezable>型は、共通の基本特定のジオメトリとブラシ、さらにアニメーションなどのグラフィックス要素。 特に、<xref:System.Windows.Freezable>はありません、 <xref:System.Windows.Media.Visual>; サブプロパティになるプロパティを保持できるときに、<xref:System.Windows.Freezable>が別のオブジェクトのプロパティの値を入力に適用し、それらのサブプロパティがレンダリングに影響する可能性です。 詳細については、「[Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)」を参照してください。  
  
 <xref:System.Windows.Media.Animation.Animatable>  
  
 <xref:System.Windows.Media.Animation.Animatable> <xref:System.Windows.Freezable>派生クラスでは、具体的には、アニメーション コントロール レイヤーとユーティリティの一部のメンバー現在アニメーションのプロパティを識別できるようにから追加アニメート プロパティです。  
  
### <a name="control"></a>コントロール  
 <xref:System.Windows.Controls.Control> 目的の基底クラス型のオブジェクトは、コントロールまたはテクノロジによって、コンポーネントと呼ばれるさまざまです。 一般に [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロール クラスは、UI コントロールを直接表すクラスか、コントロールの複合に密接に参加するクラスです。 主要な機能を<xref:System.Windows.Controls.Control>コントロール テンプレートは、有効にします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.Control>  
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [WPF アーキテクチャ](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
