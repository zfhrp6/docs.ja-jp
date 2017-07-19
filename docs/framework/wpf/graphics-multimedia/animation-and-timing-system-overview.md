---
title: "アニメーションとタイミング システムの概要 | Microsoft Docs"
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
  - "アニメーション [WPF]"
  - "タイミング システム [WPF]"
ms.assetid: 172cd5a8-a333-4c81-9456-fafccc19f382
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# アニメーションとタイミング システムの概要
ここでは、タイミング システムで、アニメーションの <xref:System.Windows.Media.Animation.Timeline> および <xref:System.Windows.Media.Animation.Clock> の各クラスを使用してプロパティをアニメーション化する方法について説明します。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="prerequisites"></a>   
## 必要条件  
 このトピックを理解するには、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」の説明に従って、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アニメーションを使用し、プロパティをアニメーション化できる必要があります。  また、[依存関係プロパティ](GTMT)についても知っておくと役に立ちます。詳細については、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」を参照してください。  
  
<a name="timelinesandclocks"></a>   
## タイムラインとクロック  
 「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」では、<xref:System.Windows.Media.Animation.Timeline> で時間のセグメントを表す方法、およびアニメーションが出力値を生成する <xref:System.Windows.Media.Animation.Timeline> の 1 つの型であることを説明しました。  <xref:System.Windows.Media.Animation.Timeline> 自体は、時間のセグメントを記述する以外、何も実行しません。  実際の処理を実行するのは、タイムラインの <xref:System.Windows.Media.Animation.Clock> オブジェクトです。  同様に、アニメーションは実際にはプロパティをアニメーション化しません。アニメーション クラスは出力値の計算方法を記述しますが、アニメーション出力を実行し、その出力をプロパティに適用するのは、そのアニメーション用に作成された <xref:System.Windows.Media.Animation.Clock> です。  
  
 <xref:System.Windows.Media.Animation.Clock> は、<xref:System.Windows.Media.Animation.Timeline> のタイミングに関連する実行時の状態を維持する特殊な型のオブジェクトです。  このオブジェクトは、アニメーションおよびタイミング システムには不可欠な 3 つの情報、<xref:System.Windows.Media.Animation.Clock.CurrentTime%2A>、<xref:System.Windows.Media.Animation.Clock.CurrentProgress%2A>、および <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> を提供します。  <xref:System.Windows.Media.Animation.Clock> は、その現在の時刻、進行状況、および状態を、その <xref:System.Windows.Media.Animation.Timeline> で記述された、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>、<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> などのタイミング動作を使用して判断します。  
  
 ほとんどの場合、タイムラインに自動的に <xref:System.Windows.Media.Animation.Clock> が作成されます。  <xref:System.Windows.Media.Animation.Storyboard> メソッドや <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> メソッドを使用してアニメーション化すると、タイムラインとアニメーションに自動的にクロックが作成されて対象のプロパティに適用されます。  <xref:System.Windows.Media.Animation.Timeline> の <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> メソッドを使用して、<xref:System.Windows.Media.Animation.Clock> を明示的に作成することもできます。  <xref:System.Windows.Media.MediaTimeline.CreateClock%2A?displayProperty=fullName> メソッドは、それが呼び出された <xref:System.Windows.Media.Animation.Timeline> に対応する型のクロックを作成します。  <xref:System.Windows.Media.Animation.Timeline> に子タイムラインが含まれる場合、それらの子タイムラインの <xref:System.Windows.Media.Animation.Clock> オブジェクトも作成されます。  結果として得られる <xref:System.Windows.Media.Animation.Clock> オブジェクトは、クロック オブジェクトを作成した <xref:System.Windows.Media.Animation.Timeline> オブジェクト ツリーと同じ構造のツリーに配置されます。  
  
 さまざまな型のタイムラインに対応するさまざまな型のクロックが存在します。  いくつかの <xref:System.Windows.Media.Animation.Timeline> 型とそれに対応する <xref:System.Windows.Media.Animation.Clock> 型を次の表に示します。  
  
|タイムラインの型|クロックの型|クロックの目的|  
|--------------|------------|-------------|  
|Animation \(<xref:System.Windows.Media.Animation.AnimationTimeline> から継承\)|<xref:System.Windows.Media.Animation.AnimationClock>|依存関係プロパティの出力値を生成します。|  
|<xref:System.Windows.Media.MediaTimeline>|<xref:System.Windows.Media.MediaClock>|メディア ファイルを処理します。|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|<xref:System.Windows.Media.Animation.ClockGroup>|その子 <xref:System.Windows.Media.Animation.Clock> オブジェクトをグループ化し、制御します。|  
|<xref:System.Windows.Media.Animation.Storyboard>|<xref:System.Windows.Media.Animation.ClockGroup>|その子 <xref:System.Windows.Media.Animation.Clock> オブジェクトをグループ化し、制御します。|  
  
 作成した <xref:System.Windows.Media.Animation.AnimationClock> オブジェクトはすべて、<xref:System.Windows.Media.Animation.IAnimatable.ApplyAnimationClock%2A> メソッドを使用して互換性のある依存関係プロパティに適用できます。  
  
 同じようなオブジェクトを多数アニメーション化するなど、パフォーマンスに大きな負荷がかかるシナリオでは、独自の <xref:System.Windows.Media.Animation.Clock> を管理することによってパフォーマンスを向上できます。  
  
<a name="timemanager"></a>   
## クロックとタイム マネージャー  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でオブジェクトをアニメーション化する場合、タイムラインに対して作成された <xref:System.Windows.Media.MediaPlayer.Clock%2A> オブジェクトはタイム マネージャーが管理します。  タイム マネージャーは、<xref:System.Windows.Media.MediaPlayer.Clock%2A> オブジェクトのツリーのルートであり、そのツリーの時間のフローを制御します。  タイム マネージャーは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションごとに自動的に作成され、アプリケーション開発者には表示されません。タイム マネージャーは、1 秒に何度も "タイマーを刻み" ます。1 秒あたりのタイマー刻みの実際の回数は、使用可能なシステム リソースに応じて変わります。  これらの 1 回のタイマー刻みの間、タイム マネージャーは、タイミング ツリー内のすべての <xref:System.Windows.Media.Animation.ClockState> <xref:System.Windows.Media.Animation.Clock> オブジェクトの状態を計算します。  
  
 タイム マネージャー、<xref:System.Windows.Media.Animation.AnimationClock>、およびアニメーション化された依存関係プロパティの関係を次の図に示します。  
  
 ![タイミング システム コンポーネント](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clocks-1clock1prop.png "graphicsmm\_clocks\_1clock1prop")  
プロパティのアニメーション化  
  
 タイムマネージャーは、タイマーを刻むときに、アプリケーション内のすべての <xref:System.Windows.Media.Animation.ClockState> <xref:System.Windows.Media.Animation.Clock> の時間を更新します。  <xref:System.Windows.Media.Animation.Clock> が <xref:System.Windows.Media.Animation.AnimationClock> の場合、クロックは、その作成元の <xref:System.Windows.Media.Animation.AnimationTimeline> の <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> メソッドを使用して現在の出力値を計算します。  <xref:System.Windows.Media.Animation.AnimationClock> は、現在のローカル時刻、入力値 \(通常はプロパティの基本値\)、および既定の終点の値を指定した <xref:System.Windows.Media.Animation.AnimationTimeline> を提供します。  <xref:System.Windows.DependencyObject.GetValue%2A> メソッドまたはその CLR アクセサーを使用してアニメーション化プロパティの値を取得するときに、その <xref:System.Windows.Media.Animation.AnimationClock> の出力を取得します。  
  
#### クロック グループ  
 前のセクションでは、さまざまな型のタイムラインに対応するさまざまな型の <xref:System.Windows.Media.Animation.Clock> オブジェクトを説明しました。  タイム マネージャー、<xref:System.Windows.Media.Animation.ClockGroup>、<xref:System.Windows.Media.Animation.AnimationClock>、およびアニメーション化された依存関係プロパティの関係を次の図に示します。  アニメーションおよび他のタイムラインをグループ化する <xref:System.Windows.Media.Animation.Storyboard> クラスなど、他のタイムラインをグループ化するタイムラインに対して、<xref:System.Windows.Media.Animation.ClockGroup> が作成されます。  
  
 ![タイミング システム コンポーネント](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clocks-2clock1clockgroup2prop.png "graphicsmm\_clocks\_2clock1clockgroup2prop")  
ClockGroup  
  
#### 構成  
 複数のクロックを単一のプロパティに関連付けることが可能です。この場合、各クロックは前のクロックの出力値をその基本値として使用します。  同じプロパティに適用された 3 つの <xref:System.Windows.Media.Animation.AnimationClock> オブジェクトを次の図に示します。  Clock1 は、アニメーション化されたプロパティの基本値をその入力として使用して出力を生成します。  Clock2 は、Clock1 からの出力をその入力として取得し、それを使用して出力を生成します。  Clock3 は、Clock2 からの出力をその入力として取得し、それを使用して出力を生成します。  複数のクロックが同じプロパティに同時に影響を与える場合、それらは構成チェーン内にあるものと見みなされます。  
  
 ![タイミング システム コンポーネント](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clocks-2clock1prop.png "graphicsmm\_clocks\_2clock1prop")  
構成チェーン  
  
 構成チェーン内の <xref:System.Windows.Media.Animation.AnimationClock> オブジェクトの入力および出力間の関係は作成されますが、それらのタイミング動作は影響を受けません。<xref:System.Windows.Media.Animation.Clock> オブジェクト \(<xref:System.Windows.Media.Animation.AnimationClock> オブジェクトを含む\) は、その親 <xref:System.Windows.Media.Animation.Clock> オブジェクトに対して階層型の依存関係を持ちます。  
  
 複数のクロックを同じプロパティに適用するには、<xref:System.Windows.Media.Animation.Storyboard>、アニメーション、または <xref:System.Windows.Media.Animation.AnimationClock> の適用時に <xref:System.Windows.Media.Animation.HandoffBehavior> <xref:System.Windows.Media.Animation.HandoffBehavior> を使用します。  
  
#### タイマー刻みとイベントの統合  
 出力値の計算に加え、タイム マネージャーはタイマーを刻むごとに他の作業も行います。タイム マネージャーは、各クロックの状態を確認し、必要に応じてイベントを発生させます。  
  
 タイマー刻みが頻繁に発生している間は、タイマー刻みの間隔に多くのことが行われる可能性があります。  たとえば、<xref:System.Windows.Media.Animation.Clock> が停止してから開始し、もう一度停止する可能性あります。この場合、クロックの <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> 値は 3 回変更されています。  理論的には、<xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> イベントは 1 回のタイマー刻みで複数回発生することは可能ですが、タイミング エンジンはイベントを統合して、<xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> イベントが 1 回のタイマー刻みにつき多くても 1 回だけ発生するようにします。  これはすべてのタイミング イベントに該当します。特定の 1 <xref:System.Windows.Media.Animation.Clock> オブジェクトに対して、各型のイベントは 1 回だけ発生します。  
  
 タイマー刻み間隔に、<xref:System.Windows.Media.Animation.Clock> の状態が切り替わり、元の状態に戻った場合 \(<xref:System.Windows.Media.Animation.ClockState> から <xref:System.Windows.Media.Animation.ClockState> に切り替わり、<xref:System.Windows.Media.Animation.ClockState> に戻る場合など\) でも、関連のイベントは発生します。  
  
 タイミング イベントの詳細については、「[タイミング イベントの概要](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md)」を参照してください。  
  
<a name="currentvaluesbasevaluesofproperties"></a>   
## プロパティの現在値と基本値  
 アニメーション化可能なプロパティは、基本値と現在値の 2 つの値を持つことができます。  その CLR アクセサーまたは <xref:System.Windows.DependencyObject.SetValue%2A> メソッドを使用してプロパティを設定する場合は、その基本値を設定します。  プロパティをアニメーション化しない場合、その基本値と現在値は同じになります。  
  
 プロパティをアニメーション化する場合、<xref:System.Windows.Media.Animation.AnimationClock> はプロパティの*現在*値を設定します。  <xref:System.Windows.Media.Animation.AnimationClock> が <xref:System.Windows.Media.Animation.ClockState> または <xref:System.Windows.Media.Animation.ClockState> の場合、プロパティの値をその CLR アクセサーまたは <xref:System.Windows.DependencyObject.GetValue%2A> メソッドをとおして取得すると、<xref:System.Windows.Media.Animation.AnimationClock> の出力が返されます。  プロパティの基本値は、<xref:System.Windows.Media.Animation.IAnimatable.GetAnimationBaseValue%2A> メソッドを使用して取得できます。  
  
## 参照  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [タイミング イベントの概要](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md)   
 [タイミング動作の概要](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)