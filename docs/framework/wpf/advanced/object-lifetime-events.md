---
title: "オブジェクトの有効期間イベント | Microsoft Docs"
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
  - "Activated イベント"
  - "アプリケーション オブジェクト, 有効期間イベント"
  - "クラス, フレーム"
  - "クラス, NavigationWindow"
  - "Closed イベント"
  - "Closing イベント"
  - "ContentRendered イベント"
  - "Deactivated イベント"
  - "イベント, Activated"
  - "イベント, 終了"
  - "イベント, Closing"
  - "イベント, ContentRendered"
  - "イベント, Deactivated"
  - "イベント, 初期化済み"
  - "イベント, 読み込み"
  - "イベント, アンロードされました"
  - "終了イベント"
  - "Frame クラス"
  - "Initialized イベント"
  - "オブジェクトの有効期間イベント"
  - "Loaded イベント"
  - "NavigationWindow クラス"
  - "オブジェクトの有効期間イベント"
  - "起動イベント"
  - "Unloaded イベント"
ms.assetid: face6fc7-465b-4502-bfe5-e88d2e729a78
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# オブジェクトの有効期間イベント
ここでは、オブジェクトの作成、使用、および破棄の有効期間におけるステージを示す特定の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] イベントについて説明します。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="prerequisites"></a>   
## 必要条件  
 このトピックでは、ユーザーが [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] クラスの既存の[依存関係プロパティ](GTMT)の使用という観点から依存関係プロパティを理解し、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」トピックを通読していることを前提としています。  このトピックの例を理解するには、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] についての理解があり \(「[XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)」を参照\)、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションの記述方法を理解していることも必要です。  
  
<a name="intro"></a>   
## オブジェクトの有効期間イベント  
 [!INCLUDE[TLA#tla_netframewk](../../../../includes/tlasharptla-netframewk-md.md)] マネージ コードのオブジェクトはすべて、作成、使用、および破棄という一連の有効期間のステージを経由します。  また、多くのオブジェクトには、破棄フェーズの一環として発生する有効期間の終了ステージがあります。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] オブジェクト \(具体的には [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] が要素として識別するビジュアル オブジェクト\) にも、共通する一連のオブジェクト有効期間ステージがあります。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プログラミングおよびアプリケーション モデルでは、これらのステージが一連のイベントとして公開されます。  有効期間イベントに関しては、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に、全般的要素、ウィンドウ要素、ナビゲーション ホスト、およびアプリケーション オブジェクトの 4 種類の主要オブジェクトがあります。  ウィンドウ要素とナビゲーション ホストは、さらに大きなビジュアル オブジェクト \(要素\) のグループ内にも存在します。  このトピックでは、すべての要素に共通する有効期間イベントについて説明し、次にアプリケーション定義、ウィンドウ要素、またはナビゲーション ホストに適用される特定の有効期間イベントについて説明します。  
  
<a name="common_events"></a>   
## 要素に関する共通の有効期間イベント  
 任意の [WPF フレームワーク レベル](GTMT)要素 \(<xref:System.Windows.FrameworkElement> または <xref:System.Windows.FrameworkContentElement> から派生しているオブジェクト\) には、次の 3 つの共通する有効期間イベントがあります。それらは、<xref:System.Windows.FrameworkElement.Initialized>、<xref:System.Windows.FrameworkElement.Loaded>、および <xref:System.Windows.FrameworkElement.Unloaded> です。  
  
### 初期化  
 <xref:System.Windows.FrameworkElement.Initialized> が最初に発生し、コンストラクターの呼び出しによって、オブジェクトの初期化に大まかに対応します。  イベントは初期化に応答して発生するため、オブジェクトのすべてのプロパティが設定されることが保証されます   \(例外は、動的リソースまたはバインディングなどの評価されない式の使用です\)。すべてのプロパティが設定されるという要件の結果として、マークアップで定義される入れ子にした要素によって発生する一連の <xref:System.Windows.FrameworkElement.Initialized> は、要素ツリーの最下位の要素からルート方向の親要素への順序で発生するように見えます。  この順序は親子のリレーションシップおよびコンテインメントがプロパティであるためで、親のプロパティを設定する子要素も完全に初期化されるまで、親は初期化を報告できません。  
  
 <xref:System.Windows.FrameworkElement.Initialized> イベントへの応答としてハンドラーを記述する際は、ハンドラーが添付される周辺の要素ツリー \([論理ツリー](GTMT)または[ビジュアル ツリー](GTMT)\) 内に他のすべての要素、特に親要素が作成されているという保証がないことを考慮する必要があります。  メンバー変数が null であるか、データ ソースが基になるバインディングによってまだ設定されていない可能性があります \(式レベルでも\)。  
  
### 読み込み済み  
 <xref:System.Windows.FrameworkElement.Loaded> が次に発生します。  <xref:System.Windows.FrameworkElement.Loaded> イベントは、最終的な描画の前に発生しますが、それはレイアウト システムが描画に必要なすべての値を計算した後です。  <xref:System.Windows.FrameworkElement.Loaded> は、要素を含む論理ツリーが完全である場合にのみ発生し、HWND とレンダリング サーフェイスを提供するプレゼンテーション ソースに接続されています。  標準データ バインディング \(他のプロパティや直接定義したデータ ソースなどのローカル ソースへのバインディング\) は、<xref:System.Windows.FrameworkElement.Loaded> の前に発生しています。  非同期データ バインディング \(外部ソースまたは動的ソース\) が発生している可能性もありますが、非同期であるという性質の定義から、その保証はできません。  
  
 <xref:System.Windows.FrameworkElement.Loaded> イベントを発生させる機構は、<xref:System.Windows.FrameworkElement.Initialized> とは異なります。  <xref:System.Windows.FrameworkElement.Initialized> イベントは、要素単位で発生し、完全な要素ツリーによる直接の調整はありません。  これに対し、<xref:System.Windows.FrameworkElement.Loaded> イベントは、要素ツリー \(特に、[論理ツリー](GTMT)\) 全体にわたる調整動作として発生します。  ツリーのすべての要素が読み込まれたと見なされる状態にあると、<xref:System.Windows.FrameworkElement.Loaded> イベントは、最初にルート要素で発生します。  次に、<xref:System.Windows.FrameworkElement.Loaded> イベントは、各子要素で連続して発生します。  
  
> [!NOTE]
>  この動作は、表面上は、[ルーティング イベント](GTMT)のトンネリングに似ているとも言えます。  ただし、イベントからイベントへと伝達される情報はありません。  各要素は常に <xref:System.Windows.FrameworkElement.Loaded> イベントを処理することができ、イベント データを処理済みとしてマークしても、その要素以外への影響はありません。  
  
### アンロード  
 最後に <xref:System.Windows.FrameworkElement.Unloaded> が発生し、プレゼンテーション ソースまたは削除されているビジュアル親によって開始されます。  <xref:System.Windows.FrameworkElement.Unloaded> が発生して処理される際、\(<xref:System.Windows.FrameworkElement.Parent%2A> プロパティによって決定される\) イベント ソースの親または、論理ツリーまたはビジュアル ツリー内にある任意の要素が既に設定解除されている可能性があります。これは、データ バインディング、リソース参照、およびスタイルが、通常または前回のランタイム値に設定されていない可能性があることを意味します。  
  
<a name="application_model_elements"></a>   
## 有効期間イベント アプリケーション モデルの要素  
 要素の共通する有効期間イベントに基づいて構築されたアプリケーション モデル要素には、<xref:System.Windows.Application>、<xref:System.Windows.Window>、<xref:System.Windows.Controls.Page>、<xref:System.Windows.Navigation.NavigationWindow>、および <xref:System.Windows.Controls.Frame> があります。  これらの要素は、共通する有効期間イベントを、特定の目的に関する追加イベントで拡張します。  これらの詳細については、次のトピックで説明しています。  
  
-   <xref:System.Windows.Application>: [アプリケーション管理の概要](../../../../docs/framework/wpf/app-development/application-management-overview.md).  
  
-   <xref:System.Windows.Window>: [WPF ウィンドウの概要](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md).  
  
-   <xref:System.Windows.Controls.Page>、<xref:System.Windows.Navigation.NavigationWindow>、および <xref:System.Windows.Controls.Frame>: [ナビゲーションの概要](../../../../docs/framework/wpf/app-development/navigation-overview.md)  
  
## 参照  
 [依存関係プロパティ値の優先順位](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)   
 [ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)