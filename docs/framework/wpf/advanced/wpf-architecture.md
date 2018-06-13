---
title: WPF アーキテクチャ
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], attached
- attached properties [WPF]
- architecture [WPF]
- unmanaged components [WPF]
- affinity thread [WPF]
- Storyboards [WPF]
- milcore [WPF]
- components [WPF], unmanaged
- painter's algorithm
- interfaces [WPF], INotifyPropertyChange
- CommandBindings [WPF]
- data templates [WPF]
- thread [WPF], affinity
ms.assetid: 8579c10b-76ab-4c52-9691-195ce02333c8
ms.openlocfilehash: 70afa7e193832837650d72837b25e26e3b64c180
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549647"
---
# <a name="wpf-architecture"></a>WPF アーキテクチャ
このトピックでは、Windows Presentation Foundation (WPF) のクラス階層のガイド付きツアーを提供します。 主要なサブシステムのほとんどをカバー [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、それらの相互作用について説明します。 いくつかの設計担当者が行った選択の表示[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]です。  
  
  
<a name="System_Object"></a>   
## <a name="systemobject"></a>System.Object  
 プライマリ[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]プログラミング モデルがマネージ コードによって公開されます。 設計フェーズの早い段階で[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]システムのマネージ コンポーネントとアンマネージ コンポーネントとの間の線を描画する場所に関する議論の数が発生しました。 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]より生産的かつ (メモリ管理、エラー処理、共通型システムなど) を含む堅牢な開発を構成する機能のいくつか提供コストで送られてきたが、します。  
  
 主要コンポーネント[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]下の図に示します。 ダイアグラム (PresentationFramework、PresentationCore、および milcore) の赤のセクションでは、主要なコードの特定の部分は、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]です。 これらは、1 つだけです。 アンマネージ コンポーネント – milcore です。 Milcore が緊密に統合を有効にするためにアンマネージ コードで記述された[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]です。 すべて表示[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]はを通じて行われます、[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]エンジン、効率的なハードウェアとソフトウェア レンダリングを許可します。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] メモリと実行を細かく制御を必要もあります。 Milcore 合成エンジンが機密性の高い、必要と多くの利点のパフォーマンスでは非常に高く、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]パフォーマンスを確保します。  
  
 ![.NET Framework 内での WPF の位置。] (../../../../docs/framework/wpf/advanced/media/wpf-architect1.PNG "wpf_architect1")  
  
 マネージ コードとアンマネージの部分の間の通信[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]はこのトピックの後半で説明します。 マネージ プログラミング モデルの残りの部分は次のとおりです。  
  
<a name="System_Threading_DispatcherObject"></a>   
## <a name="systemthreadingdispatcherobject"></a>System.Threading.DispatcherObject  
 多くのオブジェクトに[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]から派生<xref:System.Windows.Threading.DispatcherObject>、同時実行を処理して、スレッド処理の基本的な構造を提供します。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ディスパッチャーによって実装されたメッセージング システムに基づいています。 これは同様に機能、使い慣れた[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]メッセージ ポンプ以外の場合は実際には、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ディスパッチャーが User32 メッセージをクロス スレッド呼び出しを実行するために使用します。  
  
 本当に 2 つのコアで同時実行を検討する場合を理解しておくべき概念がある[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]– ディスパッチャーとスレッド関係。  
  
 デザイン フェーズ中に[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]目標、実行の 1 つのスレッドに移動することでしたが、非スレッド「関連付け」モデル。 スレッドの関係は、コンポーネントの状態を保存するために実行中のスレッドの id を使用するときに発生します。 最も一般的な形式では、状態を格納する、スレッド ローカル ストア (TLS) を使用します。 スレッドの関係は、実行の各論理スレッドの所有大量のメモリになることがオペレーティング システムの物理スレッドの 1 つだけである必要があります。 最後に、WPF のスレッド モデルはスレッド アフィニティを使用して 1 つのスレッド実行の既存の User32 スレッド モデルとの同期が保持されます。 これの主な理由が相互運用性 – などのシステム[!INCLUDE[TLA2#tla_ole2.0](../../../../includes/tla2sharptla-ole2-0-md.md)]クリップボード、および Internet Explorer のすべて 1 つのスレッド (STA) のアフィニティの実行を必要とします。  
  
 STA スレッドを持つオブジェクトがある場合は、ある必要があります、スレッド間で通信を検証する方法は、正しいスレッド上にあります。 ディスパッチャーの役割が生じます。 ディスパッチャーは、複数の優先順位の高いキューでのシステムをディスパッチする基本的なメッセージです。 メッセージの例には、生の入力通知 (マウスの移動)、framework 機能 (レイアウト)、またはユーザー コマンドが含まれます (このメソッドを実行) します。 派生することによって<xref:System.Windows.Threading.DispatcherObject>、作成する、 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] STA 動作を持つオブジェクトおよびに割り当てられる、ポインター、ディスパッチャーの作成時にします。  
  
<a name="System_Windows_DependencyObject"></a>   
## <a name="systemwindowsdependencyobject"></a>System.Windows.DependencyObject  
 ビルドで使用されるプライマリ アーキテクチャ理念のいずれかの[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]プロパティの設定をしたメソッドまたはイベント上にあります。 プロパティは宣言型であり、アクションではなくの目的を簡単を指定すると、詳細が許可されます。 これは、モデル ドリブン、またはデータ ドリブン、ユーザー インターフェイスのコンテンツを表示するためのシステムにもサポートされます。 この方針には、意図された効果をする可能性があります、バインドするアプリケーションの動作をより細かく制御するために他のプロパティを作成する必要があります。  
  
 高度なプロパティ システムのプロパティによって、システムの詳細を確保するため、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]提供が必要でした。 この機能の簡単な例は、変更通知です。 双方向バインディングを有効にするために、変更通知をサポートするバインドの両方の側を作成する必要があります。 プロパティの値に関連付けられている動作するために、プロパティ値が変更されたときに通知する必要があります。 Microsoft .NET Framework には、インターフェイス**INotifyPropertyChange**、ただし、これは省略可能な変更通知を発行するオブジェクトを許可します。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 派生したより豊富なプロパティ システムを提供、<xref:System.Windows.DependencyObject>型です。 プロパティ システムは、プロパティ式間の依存関係の追跡、依存関係を変更するときに、プロパティの値を自動的に再評価という点で、「依存関係」プロパティのシステムでは真です。 継承したプロパティがある場合など (と同様に<xref:System.Windows.Controls.Control.FontSize%2A>)、値を継承する要素の親のプロパティが変更された場合、システムが自動的に更新します。  
  
 基盤となる、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]プロパティ システムは、プロパティ式の概念です。 この最初のリリースの[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]プロパティ式システムは閉じられ、式はすべて、framework の一部として提供します。 式は、プロパティのシステムは、データ バインディング、スタイル設定がないか、継承ハード コード化されたがフレームワーク内のそれ以降のレイヤーによって提供されるではなく理由です。  
  
 プロパティのシステムでは、プロパティ値のスパース ストレージも提供します。 オブジェクトは、数十個 (ない場合数百台) のプロパティを持つことができますの値が既定の状態であるため (スタイルで設定を継承など)、オブジェクトのすべてのインスタンスを完全に定義されているすべてのプロパティの重みをおく必要があります。  
  
 プロパティ システムの最終的な新しい機能は、添付プロパティの概念です。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 要素は、構成とコンポーネントの再利用の原則に基づいて構築されます。 多くの場合、大文字と小文字の一部の要素を含む (と同様に、<xref:System.Windows.Controls.Grid>レイアウト要素) (行/列の情報) のような動作を制御する子要素の追加のデータが必要です。 これらすべてのプロパティを関連付けると、すべての要素を代わりに任意のオブジェクトが許可されたその他のオブジェクトのプロパティ定義を提供します。 これは、JavaScript の"expando"機能に似ています。  
  
<a name="System_Windows_Media_Visual"></a>   
## <a name="systemwindowsmediavisual"></a>System.Windows.Media.Visual  
 システムでは定義されている、次の手順を画面に描画されるピクセルを取得します。 <xref:System.Windows.Media.Visual>クラスがそれぞれ必要に応じて描画命令とこれらの手順 (クリッピング、変換など) を表示する方法についてのメタデータを含む、ビジュアル オブジェクトのツリーを構築するために提供します。 <xref:System.Windows.Media.Visual> 設計されています非常に軽量で柔軟性の高いため、機能のほとんどないパブリック[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]公開し、保護されているコールバック関数に大きく依存します。  
  
 <xref:System.Windows.Media.Visual> エントリ ポイントを実際には、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]コンポジション システムです。 <xref:System.Windows.Media.Visual> これら 2 つのサブシステム、マネージ間の接続ポイントは、[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]まさに、します。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] milcore によって管理されているアンマネージ データ構造を走査してデータを表示します。 コンポジション ノードと呼ばれるこれらの構造は、各ノードでレンダリング指示を含む階層表示にはツリーを表します。 このツリーで、次の図の右側の図では、メッセージング プロトコル経由でアクセスできるのみです。  
  
 プログラミング時に[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、作成する<xref:System.Windows.Media.Visual>要素、および派生型は、内部的にこのメッセージング プロトコルを使って構成ツリーと通信します。 各<xref:System.Windows.Media.Visual>で[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]1 つのフィルターまたはコンポジションの複数のノードを作成する場合があります。  
  
 ![Windows Presentation Foundation ビジュアル ツリー。] (../../../../docs/framework/wpf/advanced/media/wpf-architecture2.PNG "wpf_architecture2")  
  
 描画命令はキャッシュし、が非常に重要なアーキテクチャの詳細にビジュアルのツリー全体をここで注目してください。 グラフィックスに言えば、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]保持レンダリング システムを使用します。 これにより、再コンポジション システムがユーザー コードへのコールバックをブロックしていない高いリフレッシュ レートを描画するシステムです。 これは、応答しないアプリケーションの外観を防止に役立ちます。  
  
 本当に顕著ダイアグラムにはない別の重要な詳細は、合成が実際には、システムを実行する方法です。  
  
 User32 内および[!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]システムは、イミディ エイト モードのクリッピング システムで動作します。 コンポーネントは、描画する必要がある、システムの外部でコンポーネントがタッチ (ピクセル単位) 許可されていないし、そのボックスのピクセルを描画するコンポーネントに要求し、クリッピングの境界を確立します。 このシステムで問題なく動作メモリの制約システムで変更が生じた場合だけで済むため、影響を受けるコンポーネントをタッチする – これまでの単一のピクセルの色に影響する 2 つのコンポーネントではありません。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アルゴリズムを使用して、"画家の"モデルを描画します。 これは、各コンポーネント、クリッピングの代わりに各コンポーネントは表示の前に、バックアップから表示するために要求ことを意味します。 これにより、前のコンポーネントの表示を描画するには、各コンポーネントです。 このモデルの場合は、複雑な半透明な図形をとります。 このモデルは比較的高速、今日の最新のグラフィックス ハードウェアに (ケースではないときに User32/[!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]作成された)。  
  
 前述の主要理念[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]プログラミングの複数宣言"property 中心"モデルに移動します。 ビジュアルのシステムでは、これに表示、いくつかの興味深い場所。  
  
 最初に、保持モード グラフィック システムの場合は、これが実際に不可欠な DrawLine/DrawLine 型モデルから離れた場所に移動データ指向モデル – 新しい行 ()/新しい Line() です。 データ ドリブン レンダリングするには、この移動は、プロパティを使用して表現を描画命令で複雑な操作を使用できます。 派生する型<xref:System.Windows.Media.Drawing>表示オブジェクト モデルでは実質的にします。  
  
 次に、アニメーション システムを評価する場合に、ほとんどの完全な宣言型であるが表示されます。 開発者が次の場所、または次の色を計算する必要はありません、アニメーションをアニメーション オブジェクトのプロパティのセットとして表現できます。 これらのアニメーションは、デザイナー、開発者の意図を表すことができますし、(このボタンをここからに移動が 5 秒以内に)、および、システムがこれを実現する最も効率的な方法を判断することができます。  
  
<a name="System_Windows_UIElement"></a>   
## <a name="systemwindowsuielement"></a>System.Windows.UIElement  
 <xref:System.Windows.UIElement> レイアウト、入力、およびイベントを含むコア サブシステムを定義します。  
  
 レイアウトでの主要な概念は、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]です。 多くのシステムでは、レイアウトのモデルのセットが固定 (HTML は、レイアウトの 3 つのモデルをサポートしています。 フロー、絶対、およびテーブル) またはレイアウトのモデルが存在しない (User32 だけでは絶対配置) します。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 開発者とデザイナーが、命令型のロジックではなく、プロパティ値で制御できる、柔軟で拡張性のレイアウトのモデルを求めているという前提で起動されます。 <xref:System.Windows.UIElement>レベル、レイアウトの基本的なコントラクトが導入されました-モデルを 2 フェーズ<xref:System.Windows.UIElement.Measure%2A>と<xref:System.Windows.UIElement.Arrange%2A>を渡します。  
  
 <xref:System.Windows.UIElement.Measure%2A> 対処が必要な量のサイズを決定するコンポーネントを使用します。 これから独立したフェーズ<xref:System.Windows.UIElement.Arrange%2A>が多くの場合は親要素が子の最適な位置とサイズを決定するいくつかの時間を測定するように求められます。 測定する子要素を親要素が要求されたことを示しますのもう 1 つの主要理念[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]– コンテンツをサイズ。 すべてのコントロール[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]サイズをコンテンツの自然なサイズにする機能をサポートします。 これによってローカライズを簡単に、し要素の動的レイアウトのように項目のサイズ変更できます。 <xref:System.Windows.UIElement.Arrange%2A>フェーズでは、親を配置し、それぞれの子の最終的なサイズを決定します。  
  
 多くの時間が、出力側の話にかかった多くの場合、 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] –<xref:System.Windows.Media.Visual>と関連オブジェクト。 ただしこれには入力側の同様の膨大な技術革新があります。 入力モデルで最も基本的な変更可能性[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]システムを経由する入力イベントのルーティング一貫したモデルです。  
  
 入力は、カーネル モード デバイス ドライバーのシグナルとして開始され、正しいプロセスと Windows カーネルおよび User32 に関連する複雑なプロセスのスレッドにルーティングされます。 入力に対応する User32 メッセージがルーティングされると[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]に変換、 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] raw メッセージを入力し、ディスパッチャーに送信します。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 配信の保証を使用してシステムの低レベルで実装するには、"MouseEnter"などの機能を有効にすると、実際の複数のイベントに変換される生の入力イベント、できます。  
  
 それぞれの入力イベントは、「プレビュー」イベントと実際のイベントには、少なくとも 2 つのイベントに変換されます。 すべてのイベント[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]要素ツリーを通じてルーティングの概念があります。 イベントと見なされます「バブル」および場合は、ルートの場合に、ツリーをターゲットから走査するルートを起点し、ターゲットまで走査する場合は「トンネル」と呼ばれます。 ツリーをフィルター処理またはイベントでアクションを実行することで任意の要素を有効にすると、プレビュー イベント トンネルを入力します。 通常の (非プレビュー) のイベントは、ルート ターゲットから、バブルします。  
  
 この分割トンネルおよびバブル チャートのフェーズの間では、キーボード アクセラレータは、複合世界で一貫した方法で動作などの機能の実装です。 User32 では、グローバル含む単一のテーブルをサポートするすべてのアクセラレータ (Ctrl キーを押しながら N キーの「新規」へのマッピング) を持つキーボード アクセラレータを実装とします。 呼び出しは、アプリケーションのディスパッチャーで**TranslateAccelerator**は User32 で入力メッセージをスニッフィングできないし、登録済みのアクセラレータが一致するかどうかはいずれかを判断します。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]システムは完全に「コンポーザブル」– をいずれかの要素を処理し、キーボード アクセラレータを使用できますのでこの組み合わせは機能します。 この 2 つのフェーズ モデルの入力を持つことにより、自分"TranslateAccelerator"を実装するコンポーネントです。  
  
 さらに、この 1 つの手順を実行する<xref:System.Windows.UIElement>も踏み込んで言うと導入されています。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]コマンド システムにより、何かのコマンドの終了点 – という観点から機能を定義する開発者を実装する<xref:System.Windows.Input.ICommand>です。 コマンドのバインドには、入力ジェスチャ (Ctrl + N) および (新規) コマンドの間のマッピングを定義する要素が有効にします。 入力ジェスチャとコマンドの定義の両方、拡張性、および使用時にまとめることができます。 これにより、単純ななど、エンドユーザーにアプリケーション内で使用するキーのバインディングをカスタマイズできるようにします。  
  
 このトピックのポイントに「コア」機能の[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]– PresentationCore アセンブリ内に実装された機能は、フォーカスされています。 構築するときに[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、基本的なコンポーネント間の分離をクリーンアップする (などのレイアウトとの契約**メジャー**と**配置**) と (特定の実装などのフレームワーク要素ようなレイアウト<xref:System.Windows.Controls.Grid>) が目的の結果。 目標は、ために必要な場合は、独自のフレームワークを作成する外部の開発者は、スタックの下層に機能拡張ポイントを提供することでした。  
  
<a name="System_Windows_FrameworkElement"></a>   
## <a name="systemwindowsframeworkelement"></a>System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement> 2 つの異なる方法で参照できます。 一連のポリシーとの下位層で導入されたサブシステムでのカスタマイズを加える[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]です。 一連の新しいサブシステムも導入されています。  
  
 導入されたプライマリ ポリシー<xref:System.Windows.FrameworkElement>アプリケーション レイアウトです。 <xref:System.Windows.FrameworkElement> 導入された基本的なレイアウト コントラクトに基づいて<xref:System.Windows.UIElement>レイアウトやすくレイアウト セマンティクスを駆動型のプロパティの一貫性を確保するレイアウト作成者「スロット」の概念を追加します。 などのプロパティ<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>、<xref:System.Windows.FrameworkElement.MinWidth%2A>と<xref:System.Windows.FrameworkElement.Margin%2A>(を埋める) から派生したすべてのコンポーネントを与える<xref:System.Windows.FrameworkElement>レイアウト コンテナー内で一貫性のある動作します。  
  
 <xref:System.Windows.FrameworkElement> 簡単に提供[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]の基本レイヤーについては、多くの機能への露出[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]です。 たとえば、<xref:System.Windows.FrameworkElement>を通じてアニメーションに直接アクセスできる、<xref:System.Windows.FrameworkElement.BeginStoryboard%2A>メソッドです。 A<xref:System.Windows.Media.Animation.Storyboard>プロパティのセットに対し複数のアニメーションのスクリプトを作成する方法を提供します。  
  
 2 つの最も重要なことを<xref:System.Windows.FrameworkElement>が導入されていますが、データ バインドとスタイル。  
  
 データ バインディング サブシステム[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]が使用するユーザーにとって比較的について理解する必要があります[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]または[!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)]アプリケーションを作成する[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]です。 これらのシステムの各では、express の一部のデータにバインドされている指定された要素から 1 つ以上のプロパティを表示する簡単な方法です。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] プロパティのバインド、変換、およびリストのバインディングを完全にサポートがあります。  
  
 データ バインディングの最も一般的な機能の 1 つ[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]データ テンプレートを導入します。 データ テンプレートを使用すると、一部のデータを視覚化する方法を宣言によって指定できます。 データにバインドできるカスタム ユーザー インターフェイスを作成するには、代わりに代わりの周囲の問題を有効にし、データが作成される表示を決定できるようにできます。  
  
 スタイルは、実際に、データ バインディングの軽量な形式です。 スタイルを使用するのにバインドできます一連のプロパティ共有定義から要素の 1 つまたは複数のインスタンス。 要素に適用されるスタイル明示的な参照でいずれか (設定して、<xref:System.Windows.FrameworkElement.Style%2A>プロパティ) のスタイルを関連付けることによって暗黙的にまたは、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]要素の型。  
  
<a name="System_Windows_Controls_Control"></a>   
## <a name="systemwindowscontrolscontrol"></a>System.Windows.Controls.Control  
 コントロールの最上位機能とは、テンプレートです。 WPF のコンポジション システム保持モード レンダリング システムとしてを検討する場合は、パラメーター化された宣言型の方法で、レンダリングを記述するためのコントロールが、テンプレートできます。 A<xref:System.Windows.Controls.ControlTemplate>は実際にコントロールによって提供されるプロパティへのバインドと一連の子要素を作成するスクリプトをより詳細に何も行われません。  
  
 <xref:System.Windows.Controls.Control> ストック プロパティのセットを提供<xref:System.Windows.Controls.Control.Foreground%2A>、 <xref:System.Windows.Controls.Control.Background%2A>、<xref:System.Windows.Controls.Control.Padding%2A>テンプレートの作成者がコントロールの表示のカスタマイズに使用できるし、いくつかの名前を付ける。 コントロールの実装では、データ モデルとの相互作用モデルを提供します。 相互作用モデルでは、(ウィンドウの隅に赤い X 印をクリックする) などのジェスチャを入力するには、(ウィンドウを閉じる) のようなコマンドとバインドのセットを定義します。 データ モデルでは、一連の相互作用モデルをカスタマイズするか、(テンプレートによって異なります) の表示をカスタマイズするプロパティを提供します。  
  
 データ モデル (プロパティ)、相互作用モデル (コマンドとイベント)、および表示モデル (テンプレート) の間には、この分割は、コントロールの外観と動作のカスタマイズを完了できます。  
  
 コントロールのデータ モデルの一般的な側面は、コンテンツ モデルです。 コントロールを確認する場合と同様に<xref:System.Windows.Controls.Button>、型の「コンテンツ」という名前のプロパティを使用しているが表示されます<xref:System.Object>です。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]と[!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)]、このプロパティは文字列である通常 –、ボタンに配置することができますが、コンテンツの種類を制限します。 ボタンのコンテンツできます、単純な文字列、複雑なデータ オブジェクト、またはツリー全体。 データ オブジェクトの場合は、データ テンプレートは、ディスプレイを構築するために使用されます。  
  
<a name="Summary"></a>   
## <a name="summary"></a>まとめ  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] データ ドリブン プレゼンテーション システムを動的に作成できるように設計されています。 動作を制御するプロパティ セットを通じてオブジェクトを作成するのには、システムのすべての部分は設計されています。 データ バインディングは、システムの基本的な部分は、され、すべてのレイヤーで統合されます。  
  
 従来のアプリケーションは、表示を作成し、後、一部のデータをバインドします。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、いくつかの種類のデータ バインディングによって生成される、コントロール、ディスプレイ画面のあらゆる側面に関するすべてのものです。 ボタンの内側にあるテキストは、ボタンの内部で構成されるコントロールを作成し、ボタンのコンテンツ プロパティの表示をバインドして表示されます。  
  
 開発を開始すると、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ベースのアプリケーション、非常になじみと考える必要があります。 プロパティ、オブジェクトを使用してを設定することができ、データ バインドほぼ同じ方法を使用できる[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]または[!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)]です。 アーキテクチャに深く調査と[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、基本的に、アプリケーションのコア ドライバーとしてデータを処理するはるかに充実したアプリケーションを作成するためにできる可能性があることがわかります。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.Visual>  
 <xref:System.Windows.UIElement>  
 <xref:System.Windows.Input.ICommand>  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.Threading.DispatcherObject>  
 <xref:System.Windows.Input.CommandBinding>  
 <xref:System.Windows.Controls.Control>  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [レイアウト](../../../../docs/framework/wpf/advanced/layout.md)  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
