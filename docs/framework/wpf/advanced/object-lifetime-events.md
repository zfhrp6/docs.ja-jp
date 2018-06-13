---
title: オブジェクトの有効期間イベント
ms.date: 03/30/2017
helpviewer_keywords:
- events [WPF], ContentRendered
- events [WPF], Deactivated
- events [WPF], Unloaded
- Activated events [WPF]
- events [WPF], Loaded
- Application objects [WPF], lifetime events
- events [WPF], Activated
- ContentRendered events [WPF]
- Deactivated events [WPF]
- events [WPF], Initialized
- events [WPF], Closing
- Unloaded events [WPF]
- exit events [WPF]
- objects' lifetime events [WPF]
- Loaded events [WPF]
- Closing events [WPF]
- events [WPF], Closed
- Initialized events [WPF]
- Closed events [WPF]
- startup events [WPF]
- lifetime events of objects [WPF]
ms.assetid: face6fc7-465b-4502-bfe5-e88d2e729a78
ms.openlocfilehash: 02a6736fe54be4683044f648e9d5ed5e8a3d95dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547535"
---
# <a name="object-lifetime-events"></a>オブジェクトの有効期間イベント
このトピックでは、オブジェクトの有効期間における作成、使用、破棄のステージを示す特定の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] イベントについて説明します。  
  

  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] クラスの既存の依存関係プロパティのコンシューマーの観点から依存関係プロパティを理解しており、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」というトピックを読んでいることを前提としています。 このトピックの例を理解するには、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] について理解し (「[XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)」を参照)、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションの記述方法を理解していることも必要です。  
  
<a name="intro"></a>   
## <a name="object-lifetime-events"></a>オブジェクトの有効期間イベント  
 Microsoft .NET Framework マネージ コード内のすべてのオブジェクトのような一連の有効期間、作成、使用、および破棄のステージを通過します。 また、多くのオブジェクトには、破棄フェーズの一環として発生する有効期間の終了ステージもあります。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] オブジェクト (具体的には [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] が要素として識別するビジュアル オブジェクト) にも、共通する一連のオブジェクト有効期間ステージがあります。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プログラミングおよびアプリケーション モデルでは、これらのステージが一連のイベントとして公開されます。 有効期間イベントに関しては、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に、全般的要素、ウィンドウ要素、ナビゲーション ホスト、アプリケーション オブジェクトの 4 種類の主要オブジェクトがあります。 ウィンドウ要素とナビゲーション ホストは、さらに大きなビジュアル オブジェクト (要素) のグループにも含まれます。 このトピックでは、すべての要素に共通する有効期間イベントについて説明し、次にアプリケーション定義、ウィンドウ要素、またはナビゲーション ホストに適用される特定の有効期間イベントについて説明します。  
  
<a name="common_events"></a>   
## <a name="common-lifetime-events-for-elements"></a>要素に関する共通の有効期間イベント  
 任意の WPF フレームワーク レベルの要素 (いずれかから派生するオブジェクト<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>) が 3 つの一般的な有効期間イベント: <xref:System.Windows.FrameworkElement.Initialized>、<xref:System.Windows.FrameworkElement.Loaded>と<xref:System.Windows.FrameworkElement.Unloaded>です。  
  
### <a name="initialized"></a>初期化済み  
 <xref:System.Windows.FrameworkElement.Initialized> 最初に発生し、コンス トラクターの呼び出しによって、オブジェクトの初期化にほぼ対応します。 このイベントは初期化に応答して発生するため、オブジェクトのすべてのプロパティが設定されることが保証されます。 (例外は、動的リソースまたはバインディングなどの式の使用です。これらは評価されない式となります。)すべてのプロパティが設定されている要件のシーケンスの結果として<xref:System.Windows.FrameworkElement.Initialized>最初に、要素ツリー内の最下位要素の順序で発生しますが、マークアップで定義されている入れ子になった要素で発生する次のルートに向かって要素に親。 この順序に従うのは、親子のリレーションシップおよびコンテインメントがプロパティであるためです。その結果、親のプロパティを設定する子要素も完全に初期化されるまで、親は初期化を報告できません。  
  
 応答ハンドラーを作成する場合、<xref:System.Windows.FrameworkElement.Initialized>イベント、考慮する必要が、要素ツリーで (論理ツリーまたはビジュアル ツリーのいずれか)、ハンドラーがアタッチされている場合の周囲の他のすべての要素が作成されている、特にという保証はありません親要素です。 メンバー変数が null である可能性や、基になるバインディングによってデータ ソースがまだ設定されていない可能性があります (式レベルでも)。  
  
### <a name="loaded"></a>読み込み  
 <xref:System.Windows.FrameworkElement.Loaded> 次に発生します。 <xref:System.Windows.FrameworkElement.Loaded>最終的なレンダリングの前に、レイアウト システムに表示するためのすべての必要な値が計算された後にイベントが発生します。 <xref:System.Windows.FrameworkElement.Loaded> 論理ツリー内に含まれる要素が完了して、HWND と表示画面を提供するプレゼンテーション ソースに接続することが必要です。 前のバージョンに標準的なデータ バインディング (他のプロパティまたは直接定義されたデータ ソースなどのローカル ソースにバインド) が発生している<xref:System.Windows.FrameworkElement.Loaded>です。 非同期データ バインディング (外部ソースまたは動的ソース) が発生する可能性もありますが、非同期であるという性質の定義から、その保証はできません。  
  
 ためのメカニズム、<xref:System.Windows.FrameworkElement.Loaded>イベントが発生したとは異なる<xref:System.Windows.FrameworkElement.Initialized>です。 <xref:System.Windows.FrameworkElement.Initialized>イベントが完了した要素のツリーで直接調整なしの要素で発生した要素。 これに対し、<xref:System.Windows.FrameworkElement.Loaded>全体の要素ツリー (具体的には、論理ツリー) 全体で組織的な手段としてイベントが発生します。 ツリー内のすべての要素が状態と見なされますが、読み込まれたときに、<xref:System.Windows.FrameworkElement.Loaded>イベントが最初にルート要素で発生しました。 <xref:System.Windows.FrameworkElement.Loaded>イベントが各子要素で連続して発生し、します。  
  
> [!NOTE]
>  この動作は、表面上は、ルーティング イベントのトンネリングに似ているとも言えます。 ただし、イベントからイベントへと伝達される情報はありません。 各要素が処理する機会を常にはその<xref:System.Windows.FrameworkElement.Loaded>イベント、およびイベント データを処理済みとしてマークすることも何も起こりませんその要素を超える。  
  
### <a name="unloaded"></a>アンロードされました  
 <xref:System.Windows.FrameworkElement.Unloaded> 最後が発生し、プレゼンテーション ソースまたは削除されるビジュアルの親によって開始されます。 ときに<xref:System.Windows.FrameworkElement.Unloaded>が発生し、イベント ソースの親である要素を処理 (によって決定される<xref:System.Windows.FrameworkElement.Parent%2A>プロパティ) または下方論理またはビジュアル ツリー内の要素で指定された可能性がありますが既に設定されていない、データ バインディングをリソースの参照の意味、スタイル可能性があります、標準または最後既知実行時の値に設定されていないとします。  
  
<a name="application_model_elements"></a>   
## <a name="lifetime-events-application-model-elements"></a>有効期間イベント アプリケーション モデルの要素  
 要素は、次のアプリケーション モデル要素の一般的な有効期間イベントでの構築: <xref:System.Windows.Application>、 <xref:System.Windows.Window>、 <xref:System.Windows.Controls.Page>、 <xref:System.Windows.Navigation.NavigationWindow>、および<xref:System.Windows.Controls.Frame>です。 これらの要素は、共通の有効期間イベントを拡張して、特定の目的に関連するイベントを追加します。 これらの詳細については、次のトピックで説明しています。  
  
-   <xref:System.Windows.Application>:[アプリケーション管理の概要](../../../../docs/framework/wpf/app-development/application-management-overview.md)です。  
  
-   <xref:System.Windows.Window>: [WPF Windows 概要](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md)です。  
  
-   <xref:System.Windows.Controls.Page>、 <xref:System.Windows.Navigation.NavigationWindow>、および<xref:System.Windows.Controls.Frame>:[ナビゲーション概要](../../../../docs/framework/wpf/app-development/navigation-overview.md)です。  
  
## <a name="see-also"></a>関連項目  
 [依存関係プロパティ値の優先順位](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)  
 [ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
