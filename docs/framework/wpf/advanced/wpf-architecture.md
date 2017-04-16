---
title: "WPF アーキテクチャ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アフィニティ スレッド"
  - "アーキテクチャ"
  - "添付プロパティ"
  - "クラス, System.Object"
  - "クラス, System.Threading.DispatcherObject"
  - "クラス, System.Windows.Controls.Control"
  - "クラス, System.Windows.DependencyObject"
  - "クラス, System.Windows.FrameworkElement"
  - "クラス, System.Windows.Media.Visual"
  - "クラス, System.Windows.UIElement"
  - "CommandBindings"
  - "コンポーネント, unmanaged"
  - "Control クラス"
  - "データ テンプレート"
  - "DependencyObject クラス"
  - "DispatcherObject クラス"
  - "FrameworkElement クラス"
  - "INotifyPropertyChange インターフェイス"
  - "インターフェイス, INotifyPropertyChange"
  - "milcore"
  - "ペインタ アルゴリズム"
  - "プロパティ, 添付"
  - "ストーリーボード"
  - "System.Object クラス"
  - "System.Threading.DispatcherObject クラス"
  - "System.Windows.Controls.Control クラス"
  - "System.Windows.DependencyObject クラス"
  - "System.Windows.FrameworkElement クラス"
  - "System.Windows.Media.Visual クラス"
  - "System.Windows.UIElement クラス"
  - "スレッド, アフィニティ"
  - "UIElement クラス"
  - "アンマネージ コンポーネント"
  - "Visual クラス"
ms.assetid: 8579c10b-76ab-4c52-9691-195ce02333c8
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# WPF アーキテクチャ
ここでは、[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] のクラス階層について順を追って説明します。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の主要なサブシステムをほぼ網羅し、その相互作用を示すと共に、  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の設計者が下した選択事項についても説明します。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="System_Object"></a>   
## System.Object  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の主なプログラミング モデルは、マネージ コードを通じて公開されます。  システムのマネージ コンポーネントとアンマネージ コンポーネントの境界をどこに設定するかについて、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の設計初期段階に議論が重ねられました。  [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] には、開発の生産性と信頼性を高める多数の機能 \(メモリ管理、エラー処理、共通型システムなど\) が用意されていますが、これによって犠牲になったものもあります。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の主なコンポーネントを下の図に示します。  図の赤い部分 \(PresentationFramework、PresentationCore、および milcore\) は、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の主要コード部分です。  このうち、アンマネージ コンポーネントは milcore だけです。  milcore がアンマネージ コードで記述されているのは、[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] との緊密な統合を実現するためです。  ハードウェア レンダリングおよびソフトウェア レンダリングの効率性を考え、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] での表示はすべて [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] エンジンによって実行されるようになっています。  メモリと実行の細かい制御も、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] に対する要件の 1 つでした。  milcore の合成エンジンはきわめて高いパフォーマンスを必要としますが、パフォーマンスを確保するために [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] の多くの利点を放棄しなければなりませんでした。  
  
 ![.NET Framework 内の WPF の位置。](../../../../docs/framework/wpf/advanced/media/wpf-architect1.png "wpf\_architect1")  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] のマネージ部分とアンマネージ部分の間の通信については、後ほどこのトピックで説明します。  マネージ プログラミング モデルの残りの部分について、次に説明します。  
  
<a name="System_Threading_DispatcherObject"></a>   
## System.Threading.DispatcherObject  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] のオブジェクトのほとんどは、<xref:System.Windows.Threading.DispatcherObject> から派生しています。このオブジェクトを基本構造として、同時実行とスレッドの処理が行われます。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、このディスパッチャーによって実装されるメッセージング システムに基づいています。  このしくみは、[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] のメッセージ ポンプとよく似ており、実際に、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] のディスパッチャーはスレッド間呼び出しの実行に User32 のメッセージを使用します。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] での同時実行について論じる場合に理解しておく必要のある中心的概念として、ディスパッチャーとスレッド アフィニティの 2 つがあります。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の設計段階で目標としていたのは、シングル スレッド実行、ただしスレッドとの "アフィニティ \(密接な関係\)" を持たないモデルでした。  スレッド アフィニティが生じるのは、コンポーネントが状態情報を保存するために実行スレッドの ID を使用しているときです。  その最も一般的な形態は、スレッド ローカル ストア \(TLS\) を使用した状態保存です。  スレッド アフィニティが存在するということは、1 つの論理実行スレッドを所有する物理スレッドは 1 つだけでなければならないので、メモリ消費量が増加する可能性があります。  最終的に、WPF のスレッド モデルは、スレッド アフィニティのあるシングル スレッド実行方式をとる既存の User32 スレッド モデルとの同期を保った形になりました。  その主な理由は相互運用性で、[!INCLUDE[TLA2#tla_ole2.0](../../../../includes/tla2sharptla-ole2-0-md.md)] のようなシステム、クリップボード、および Internet Explorer はいずれもシングル スレッド アフィニティ \(STA\) 実行を必要とするためです。  
  
 オブジェクトで STA スレッドを使用する場合は、スレッド間通信の手段が必要になります。また、正しいスレッドで実行しているかどうかを検証する必要があります。  この役割を担うのがディスパッチャーです。  ディスパッチャーとは、基本的なメッセージ ディスパッチ システムで、優先順位の付けられた複数のキューを備えています。  メッセージの例としては、未加工の入力通知 \(マウスの移動\)、フレームワーク機能 \(レイアウト\)、ユーザー コマンド \(このメソッドの実行\) などが挙げられます。  <xref:System.Windows.Threading.DispatcherObject> から派生させて [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] オブジェクトを作成すると、このオブジェクトは STA 動作を持つことになり、作成時にディスパッチャーへのポインターが与えられます。  
  
<a name="System_Windows_DependencyObject"></a>   
## System.Windows.DependencyObject  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] を構築するにあたってのアーキテクチャ面での理念の 1 つに、"メソッドやイベントよりも、なるべくプロパティを使用する" があります。  プロパティは宣言的であり、開発者はアクションではなく意図を容易に指定することができます。  モデル ドリブン、つまりデータ ドリブンでユーザー インターフェイス コンテンツを表示するシステムも、この理念によって支えられています。  この理念の意図は、アプリケーションの動作を詳しく制御できるように、バインド先として指定可能なプロパティの数を増やすことでした。  
  
 プロパティで制御できるシステムの範囲を広げるために、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] が提供するプロパティ システムよりも多様なプロパティ システムが求められていました。  この多様性のわかりやすい例として、変更通知が挙げられます。  双方向バインディングを可能にするには、バインドの両側で変更通知がサポートされる必要があります。  動作をプロパティ値と連動させるには、プロパティ値の変更時に通知が送られるようにする必要があります。  [!INCLUDE[TLA#tla_netframewk](../../../../includes/tlasharptla-netframewk-md.md)] の **INotifyPropertyChange** というインターフェイスを使用すると、オブジェクトによる変更通知の発行が可能になります。ただし、これは必須ではありません。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] には、<xref:System.Windows.DependencyObject> 型から派生した、多機能のプロパティ システムが用意されています。  プロパティ式どうしの依存関係を把握し、依存関係が変化したときにプロパティ値を自動的に再検証するという点で、このプロパティ システムは真の "依存関係" プロパティ システムと言えます。  たとえば、プロパティが継承される場合 \(<xref:System.Windows.Controls.Control.FontSize%2A> など\) は、値を継承する要素の親でそのプロパティが変更されると、プロパティ システムが自動的に更新されます。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] プロパティ システムの基盤となるのは、プロパティ式の概念です。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の最初のリリースとなる今回のリリースでは、プロパティ式システムは非公開になっており、式はすべてフレームワークの一部として提供されます。  プロパティ システムが式を持つことで、データ バインディング、スタイル設定、継承はハード コーディングされるのではなく、フレームワーク内の後の層で提供されるようになっています。  
  
 このプロパティ システムは、プロパティ値のスパース ストレージ \(sparse storage\) にも対応しています。  オブジェクトのプロパティ数が数十個に及ぶこともありますが、その値の大多数は既定の状態 \(継承された状態、スタイルで設定された状態など\) です。定義済みのすべてのプロパティの値をオブジェクトのすべてのインスタンスに持たせることが必要であるとは限りません。  
  
 プロパティ システムの新機能として最後に挙げられるのは、[添付プロパティ](GTMT)の概念です。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の要素は、合成とコンポーネント再利用の原則に基づいて構築されています。  他の要素を格納する要素 \(<xref:System.Windows.Controls.Grid> レイアウト要素など\) は、多くの場合、子要素の動作を制御するために子要素に関する追加データ \(行や列の情報など\) を必要とします。  このようなプロパティをすべて個々の要素に関連付ける代わりに、どのオブジェクトも他のオブジェクトのプロパティを定義できるようになっています。  これは、JavaScript の "expando" 機能と似ています。  
  
<a name="System_Windows_Media_Visual"></a>   
## System.Windows.Media.Visual  
 システムの定義が完了したら、画面にピクセルを描画するための手順に移ります。  <xref:System.Windows.Media.Visual> は、ビジュアル オブジェクト ツリーを構築するためのクラスです。各オブジェクトは、描画命令と、その命令をレンダリングする方法 \(クリッピング、変換など\) に関するメタデータを任意で持つことができます。  <xref:System.Windows.Media.Visual> は、負荷を抑え、柔軟性を持たせるように設計されているので、ほとんどの機能はパブリック [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] を公開しておらず、保護されたコールバック関数に大きく依存します。  
  
 <xref:System.Windows.Media.Visual> はまさに、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 合成システムへのエントリ ポイントです。  <xref:System.Windows.Media.Visual> が接続ポイントとなって、マネージ [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] とアンマネージ milcore の 2 つのサブシステムが連結されます。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、milcore で管理されているアンマネージ データ構造をスキャンすることによってデータを表示します。  この構造 \(合成ノード\) は階層構造の表示ツリーを表し、各ノードにレンダリング命令があります。  このツリー \(次の図の右側に示すツリー\) には、メッセージ プロトコルを介してのみアクセスできます。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] のプログラミング時には、<xref:System.Windows.Media.Visual> 要素と派生型を作成します。これらの要素と型は、このメッセージ プロトコルを通して合成ツリーとの内部的な通信を行います。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 内の各 <xref:System.Windows.Media.Visual> によって作成される合成ノードは、1 つの場合もあれば、まったくない場合も複数の場合もあります。  
  
 ![Windows Presentation Foundation ビジュアル ツリー。](../../../../docs/framework/wpf/advanced/media/wpf-architecture2.png "wpf\_architecture2")  
  
 ここで、アーキテクチャの詳細に関して非常に重要な注目点があります。ビジュアルと描画命令のツリー全体がキャッシュされる点です。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、グラフィック用語で言う保持モードのレンダリング システムを使用します。  このため、再描画のリフレッシュ レートを高くしても、ユーザー コードへのコールバックが合成システムによってブロックされることはありません。  これは、アプリケーションが応答しなくなったように見えるという事態の防止に役立ちます。  
  
 図から読み取れることではありませんが、もう 1 つ重要なのは、システムが実際にどのような方法で合成を実行するかという点です。  
  
 User32 と [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] において、システムは即時モードのクリッピング システム上で動作します。  コンポーネントのレンダリングが必要になると、システムはクリッピングの境界を設定し、その外側のピクセルにはコンポーネントの影響が及ばないようにしたうえで、そのボックス内にピクセルを描画するようコンポーネントに要求します。  このシステムは、メモリが限られているシステムで非常に有効に機能します。なんらかの変更が発生した場合には、その影響を受けるコンポーネントだけを修正すればよいからです。2 つのコンポーネントが 1 ピクセルの色に寄与することはありません。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、"画家のアルゴリズム \(painter's algorithm\)" 描画モデルを使用します。  これは、各コンポーネントをクリッピングするのではなく、それぞれのコンポーネントに対して画面の奥から手前の順にレンダリングするよう要求するものです。  これにより、各コンポーネントは前のコンポーネントの表示に重ねて描画することができます。  このモデルの利点は、複雑で部分的に透明な図形を描けることです。  User32 や [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] が作成されたときとは異なり、今日の最新のグラフィックス ハードウェアでは、このモデルは比較的高速に処理されます。  
  
 前述のように、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、より宣言的な "プロパティ中心" のプログラミング モデルへの移行を中心的理念としていました。  ビジュアル システムには、このことが現れている興味深い部分が 2 つあります。  
  
 第 1 に、保持モードのグラフィック システムについて考えてみると、これがまさに命令型の DrawLine\/DrawLine 型モデルからデータ指向モデル new Line\(\)\/new Line\(\) への移行を意味します。  このデータ ドリブン レンダリングへの移行によって、描画命令に関する複雑な操作をプロパティで表現できるようになります。  <xref:System.Windows.Media.Drawing> から派生する型が、事実上、レンダリングのオブジェクト モデルになります。  
  
 第 2 に、アニメーション システムを評価してみると、ほぼ完全に宣言的であることがわかります。  開発者が次の位置や次の色を計算する必要はなく、アニメーション オブジェクトの一連のプロパティとしてアニメーションを表現することができます。  このようなアニメーションは、開発者またはデザイナーの意図 \(このボタンをここからそこへ 5 秒で移動する\) を表すものであり、その意図を実現する最も効率的な方法がシステムによって特定されます。  
  
<a name="System_Windows_UIElement"></a>   
## System.Windows.UIElement  
 <xref:System.Windows.UIElement> は、レイアウト、入力、イベントなどの中心的なサブシステムを定義します。  
  
 レイアウトは、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の中心的概念です。  システムの多くは、一連のレイアウト モデルが固定されているか \(HTML ではレイアウトのモデルとしてフロー、絶対、テーブルの 3 つがサポートされます\)、レイアウトのモデルが 1 つもありません \(User32 でサポートされるのは絶対位置指定のみです\)。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、開発者とデザイナーが命令型ロジックではなくプロパティ値で制御できる柔軟で拡張性の高いレイアウト モデルを求めているという前提から出発しています。  <xref:System.Windows.UIElement> のレベルでは、レイアウト用の基本的なコントラクトとして、<xref:System.Windows.UIElement.Measure%2A> パスと <xref:System.Windows.UIElement.Arrange%2A> パスから成る 2 フェーズ モデルが導入されています。  
  
 <xref:System.Windows.UIElement.Measure%2A> では、コンポーネントが自らの描画サイズを決定することができます。  このフェーズが <xref:System.Windows.UIElement.Arrange%2A> とは切り離されているのは、親要素が自身の最適な位置とサイズを特定するために、子要素に対してサイズ測定を何度も要求するケースが多々あるためです。  親要素が子要素にサイズ測定を要求するという事実は、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] のもう 1 つの重要な理念、つまり "コンテンツに合わせたサイズ変更" の現れです。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] のコントロールはいずれも、コンテンツの自然なサイズに合わせたサイズ変更機能をサポートしています。  これによってローカライズがはるかに簡単になり、項目のサイズ変更に応じた要素の動的レイアウトが可能になります。  <xref:System.Windows.UIElement.Arrange%2A> フェーズでは、親がそれぞれの子の位置と最終的なサイズを決定することができます。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の出力側である <xref:System.Windows.Media.Visual> と関連オブジェクトは取り上げられる頻度が高く、その話題には多くの時間が費やされています。  しかしながら、入力側における革新も同じようにもきわめて大きなものです。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の入力モデルに見られる最も根本的な変化は、システムを通して入力イベントの行き先を決定する一貫したモデルであると言えるでしょう。  
  
 入力は、カーネル モードのデバイス ドライバー上で信号として発生しますが、この信号が正しいプロセスおよびスレッドに届けられるまでには、Windows カーネルと User32 が関与する複雑な複雑なプロセスを通過します。  入力に対応する User32 メッセージが [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] にルーティングされると、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の未加工入力メッセージに変換され、ディスパッチャーに送信されます。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] では、未加工入力イベントを複数の実際のイベントに変換できるようになっており、"MouseEnter" のような機能をシステムの低レベルで実装しても確実に配信されます。  
  
 それぞれの入力イベントは、少なくとも "プレビュー" イベントと実際のイベントの 2 つのイベントに変換されます。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] のすべてのイベントに共通する概念として、"要素ツリーを通じたルーティング" があります。  イベントが、ターゲットからツリーのルートまで上位へ向かうものである場合は "バブリング" と言い、ルートからターゲットまで下位に向かうものである場合は "トンネリング" と言います。  入力プレビュー イベントはトンネリングするので、ツリー内の任意の要素でイベントをフィルタリングしたり、イベントに対してアクションを実行したりすることができます。  その後で、通常の \(プレビューでない\) イベントがターゲットからルートへと上向きにバブリングします。  
  
 このように、トンネリング フェーズとバブリング フェーズに分けることで、キーボード アクセラレータのような機能の実装を複合環境で一貫性を持って機能させることができます。  User32 でキーボード アクセラレータを実装すると仮定しましょう。それには、サポート対象のアクセラレータ \(Ctrl \+ N から "新規作成" へのマッピング\) をすべて 1 つのグローバル テーブルに格納します。  アプリケーションのディスパッチャーで **TranslateAccelerator** を呼び出して、User32 で入力メッセージをスニッフィングし、登録済みのアクセラレータと一致するものがあるかどうかを判断します。  これは、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] では機能しません。なぜなら、システムが完全に "合成可能" であり、任意の要素で任意のキーボード アクセラレータを処理および使用できるようになっているためです。  入力にこの 2 フェーズ モデルが採用されているので、コンポーネントは独自の "TranslateAccelerator" を実装することができます。  
  
 さらに踏み込んで言うと、<xref:System.Windows.UIElement> にはコマンド バインディングの概念も導入されています。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] のコマンド システムでは、開発者がコマンド エンド ポイント \(<xref:System.Windows.Input.ICommand> を実装するもの\) によって機能を定義できるようになっています。  コマンド バインディングとは、入力ジェスチャ \(Ctrl \+ N\) とコマンド \("新規作成"\) の間のマッピングを 1 つの要素で定義することです。  入力ジェスチャとコマンド定義はいずれも拡張可能であり、使用時に結び付けられるようになっています。  これにより、たとえば、特定のアプリケーション内で使用するキー バインディングをエンド ユーザーがカスタマイズできるようにすることも、特別難しい問題ではなくなります。  
  
 ここまでは、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の "中心的" 機能、つまり PresentationCore アセンブリに実装されている機能に焦点を当ててきました。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の構築にあたっては、基礎部分 \(**Measure** と **Arrange** を使用するレイアウト用のコントラクトなど\) とフレームワーク部分 \(<xref:System.Windows.Controls.Grid> のような特定のレイアウトの実装など\) の明確な区別を目指していました。  目標は、スタックの下層に機能拡張ポイントを設け、外部の開発者が必要に応じて独自のフレームワークを作成できるようにすることでした。  
  
<a name="System_Windows_FrameworkElement"></a>   
## System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement> については 2 つの見方があります。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の下位層に導入されているサブシステムに対する一連のポリシーとカスタマイズを導入するクラスであり、  一連の新しいサブシステムを導入するクラスでもあります。  
  
 <xref:System.Windows.FrameworkElement> によって導入される主なポリシーは、アプリケーション レイアウトに関するものです。  <xref:System.Windows.FrameworkElement> は、<xref:System.Windows.UIElement> によって導入される基本レイアウト コントラクトに基づいて構築され、レイアウト "スロット" の概念が付加されています。この概念によって、レイアウト作成時に、プロパティで制御されるレイアウトのセマンティクスの整合性を取ることが容易になりました。  <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>、<xref:System.Windows.FrameworkElement.MinWidth%2A>、<xref:System.Windows.FrameworkElement.Margin%2A> を始めとするプロパティによって、<xref:System.Windows.FrameworkElement> から派生したすべてのコンポーネントの、レイアウト コンテナー内での動作が統一されます。  
  
 <xref:System.Windows.FrameworkElement> には、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の中心層にある多くの機能に関する [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] の公開を容易にする効果もあります。  たとえば、<xref:System.Windows.FrameworkElement> は、<xref:System.Windows.FrameworkElement.BeginStoryboard%2A> メソッドを通じてアニメーションへの直接アクセスを可能にします。  <xref:System.Windows.Media.Animation.Storyboard> を使用すると、一連のプロパティに対して複数のアニメーションのスクリプトを記述できます。  
  
 <xref:System.Windows.FrameworkElement> によって導入される機能の中で最も重要なのは、データ バインディングとスタイルの 2 つです。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] のデータ バインディング サブシステムは、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]や [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)] を使用してアプリケーション [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] を作成したことがあれば比較的理解しやすいはずです。  これらのシステムにはそれぞれ、指定した要素の 1 つ以上のプロパティを特定のデータにバインドする意図を簡単に表現する方法があります。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、プロパティ バインディング、変換、およびリスト バインディングを完全にサポートしています。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] におけるデータ バインディングの最も興味深い機能の 1 つに、データ テンプレートの導入があります。  データ テンプレートを使用すると、データの視覚的表現を宣言的に指定することができます。  データにバインドできるカスタム ユーザー インターフェイスを作成する代わりに、問題を裏返して考え、作成される画面がデータによって決定されるようにすることができます。  
  
 スタイル設定とは、実際にはデータ バインディングを軽量化したものです。  スタイルを使用すると、共有定義の一連のプロパティを要素の 1 つ以上のインスタンスにバインドすることができます。  スタイルは、<xref:System.Windows.FrameworkElement.Style%2A> プロパティを設定することによって明示的に参照して要素に適用することも、要素の [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 型にスタイルを関連付けることによって暗黙的に適用することもできます。  
  
<a name="System_Windows_Controls_Control"></a>   
## System.Windows.Controls.Control  
 Control の最も重要な機能はテンプレートです。  WPF の合成システムを保持モードのレンダリング システムと考えた場合、テンプレートは、コントロールのレンダリング方法をパラメーターとして宣言的な方法で記述できるようにする役割を担います。  <xref:System.Windows.Controls.ControlTemplate> は実のところ、一連の子要素を作成して、コントロールの持つプロパティにバインドさせるスクリプトに過ぎません。  
  
 <xref:System.Windows.Controls.Control> には、<xref:System.Windows.Controls.Control.Foreground%2A>、<xref:System.Windows.Controls.Control.Background%2A>、<xref:System.Windows.Controls.Control.Padding%2A> を始めとする一連のストック プロパティがあり、テンプレート作成者はこれを使用してコントロールの表示をカスタマイズすることができます。  コントロールの実装によって、データ モデルと操作モデルが利用可能になります。  操作モデルは、一連のコマンド \(ウィンドウを閉じるコマンドなど\) と入力ジェスチャへのバインディング \(ウィンドウの上隅にある赤い X をクリックするなど\) を定義するものです。  データ モデルは、操作モデルをカスタマイズしたり、テンプレートによって決定される表示をカスタマイズしたりするための一連のプロパティを持ちます。  
  
 このようにデータ モデル \(プロパティ\)、操作モデル \(コマンドおよびイベント\)、および表示モデル \(テンプレート\) を分離することで、コントロールの外観と動作全体がカスタマイズ可能になります。  
  
 コントロールのデータ モデルの代表的な形態がコンテンツ モデルです。  <xref:System.Windows.Controls.Button> などのコントロールを見てみると、"Content" という名前の <xref:System.Object> 型のプロパティが存在することがわかります。  [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]と [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)] では、一般にこのプロパティは文字列ですが、その結果、ボタンに配置できるコンテンツの型が制限されることになります。  ボタンのコンテンツは、単純な文字列の場合もあれば、複雑なデータ オブジェクトやツリー全体の場合もあります。  データ オブジェクトの場合は、表示の構築にデータ テンプレートが使用されます。  
  
<a name="Summary"></a>   
## 概要  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、動的なデータ ドリブン プレゼンテーション システムを作成できるように設計されています。  システムのどの部分も、動作を制御するプロパティ セットを通じてオブジェクトを作成するように設計されています。  データ バインディングはシステムの基礎となる部分であり、どの層にも統合されています。  
  
 従来のアプリケーションは、表示方法を作成してからデータにバインドしています。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] では、コントロールに関するすべての事項、表示のあらゆる側面が、なんらかのデータ バインディングによって生成されます。  たとえば、ボタンの内側にテキストを表示するには、コントロールを組み立ててボタンの内側に配置し、表示方法をボタンのコンテンツ プロパティにバインドします。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ベースのアプリケーションの開発を始めてみると、なじみ深さを感じるはずです。  プロパティの設定、オブジェクトの使用、およびデータ バインディングの方法は、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]や [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)] を使用する場合とほぼ同じです。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] のアーキテクチャを詳しく知るにつれて、基本的にデータをアプリケーションの中心的原動力として扱う多機能なアプリケーションを作成できる可能性があることがわかるでしょう。  
  
## 参照  
 <xref:System.Windows.Media.Visual>   
 <xref:System.Windows.UIElement>   
 <xref:System.Windows.Input.ICommand>   
 <xref:System.Windows.FrameworkElement>   
 <xref:System.Windows.Threading.DispatcherObject>   
 <xref:System.Windows.Input.CommandBinding>   
 <xref:System.Windows.Controls.Control>   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [レイアウト](../../../../docs/framework/wpf/advanced/layout.md)   
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)