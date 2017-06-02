---
title: "タイミング イベントの概要 | Microsoft Docs"
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
  - "Clock クラス"
  - "クロックのクラス"
  - "タイムライン"
  - "タイミング イベント"
ms.assetid: 597e3280-0867-4359-a97b-5b2f4149e350
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# タイミング イベントの概要
このトピックで使用できる&5; つのタイミング イベントを使用する方法について説明<xref:System.Windows.Media.Animation.Timeline>と<xref:System.Windows.Media.Animation.Clock>のオブジェクト。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解するには、作成し、アニメーションを使用する方法を理解する必要があります。 最初にアニメーションを使用してを参照してください、[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)します。  
  
 複数の方法でプロパティをアニメーション化する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
-   **Storyboard オブジェクトを使用して**(マークアップとコード): 使用する<xref:System.Windows.Media.Animation.Storyboard>を配置して、1 つまたは複数のオブジェクトにアニメーションを配布するオブジェクト。 例については、次を参照してください。[ストーリー ボードを使用して、プロパティをアニメーション化](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)します。  
  
-   **ローカル アニメーションを使用して**(コードのみ): 適用できる<xref:System.Windows.Media.Animation.AnimationTimeline>アニメーション化するプロパティに直接オブジェクトです。 例については、次を参照してください。[プロパティなしを使用して、ストーリー ボード アニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)です。  
  
-   **クロックを使用して**(コードのみ): 明示的にクロックを作成し、自分でアニメーション クロックを配布できます。  例については、次を参照してください。 [AnimationClock を使用して、プロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-an-animationclock.md)です。  
  
 この概要の例を使用してマークアップおよびコードで使用することができます、ため<xref:System.Windows.Media.Animation.Storyboard>オブジェクトです。 ただし、プロパティをアニメーション化する他の方法を説明する概念を適用できます。  
  
### <a name="what-is-a-clock"></a>クロックは何ですか。  
 タイムラインには、単独で実際に何もしない以外の時間のセグメントについて説明します。 タイムラインの<xref:System.Windows.Media.Animation.Clock>実際の処理を行うオブジェクト: タイムラインのスペースを実行時のタイミングに関連する状態を維持します。 使用してストーリー ボードなど、ほとんどの場合は、タイムラインで、クロックが自動的に作成します。 作成することも、<xref:System.Windows.Media.Animation.Clock>を使用して明示的に、 <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A>メソッドです。 詳細については<xref:System.Windows.Media.Animation.Clock>、オブジェクトを参照してください、[アニメーションおよびタイミング システムの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)します。  
  
## <a name="why-use-events"></a>イベントを使用する理由  
 1 つを除く (最後のタイマー刻みに沿ったシーク)、すべての対話型タイミング操作は非同期です。 正確に実行するときを知る方法はありません。 タイミング動作に依存するその他のコードがある場合、問題が存在することができます。 四角形をアニメーション化したタイムラインを停止するようにしたいとします。 タイムラインが停止した後は、四角形の色を変更します。  
  
 [!code-csharp[events_procedural#NeedForEventsFragment](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#needforeventsfragment)]
 [!code-vb[events_procedural#NeedForEventsFragment](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#needforeventsfragment)]  
  
 前の例で、2 つ目のコード行は、ストーリー ボードが停止する前に実行可能性があります。 停止は非同期操作であるためにです。 タイムラインまたは停止する時刻を示すには、「停止要求」のある種のタイミング エンジンの次の目盛りまで処理されていないを作成します。  
  
 タイムラインの完了後にコマンドを実行するには、イベントのタイミングを使用します。 次の例では、ストーリー ボードの再生が停止した後に、四角形の色を変更するイベント ハンドラーを使用します。  
  
 [!code-csharp[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#registerforstoryboardcurrentstateinvalidatedevent)]
 [!code-vb[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#registerforstoryboardcurrentstateinvalidatedevent)]  
[!code-csharp[events_procedural#StoryboardCurrentStateInvalidatedEvent2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#storyboardcurrentstateinvalidatedevent2)]
[!code-vb[events_procedural#StoryboardCurrentStateInvalidatedEvent2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#storyboardcurrentstateinvalidatedevent2)]  
  
 完全な例では、次を参照してください。[受信通知と、クロックの状態の変化](../../../../docs/framework/wpf/graphics-multimedia/how-to-receive-notification-when-clock-state-changes.md)します。  
  
## <a name="public-events"></a>パブリック イベント  
 <xref:System.Windows.Media.Animation.Timeline>と<xref:System.Windows.Media.Animation.Clock>両方のクラスは、5 つのイベントのタイミングを提供します。 次の表は、これらのイベントとそれらをトリガーする条件を示します。  
  
|イベント|対話型操作をトリガーします。|その他のトリガー|  
|-----------|--------------------------------------|--------------------|  
|**完了**|保留へスキップ|時計を完了します。|  
|**CurrentGlobalSpeedInvalidated**|一時停止、再開、シーク、速度比の設定を入力して、停止に進んでください。|クロックでを反転させます、高速化が開始または停止します。|  
|**CurrentStateInvalidated**|開始、停止を入力してへスキップ|クロックは、開始、停止、または入力します。|  
|**CurrentTimeInvalidated**|開始、シーク、停止を入力してへスキップ|クロック進行します。|  
|**RemoveRequested**|削除||  
  
## <a name="ticking-and-event-consolidation"></a>タイマー刻みとイベントの統合  
 内のオブジェクトをアニメーション化するときに[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アニメーションを管理するタイミング エンジンです。 タイミング エンジンは、時間の進行状況を追跡し、それぞれのアニメーションの状態を計算します。 1 秒間でこのような多くの評価パスがあったときです。 これらの評価パスは「ティック」と呼ばれます。  
  
 タイマー刻みで頻繁に発生しますは、いろいろな目盛りの間で発生する可能性があります。 たとえば、タイムライン可能性があります停止、開始されると、およびここでも、停止している場合、現在の状態変更が完了したら&3; 回です。 理論上は、イベント発生複数回、単一のティックのただし、ティックあたり最大で&1; つは各イベントを発生する可能性があるために、タイミング エンジンはイベントを統合します。  
  
## <a name="registering-for-events"></a>イベントの登録  
 タイミング イベントを登録する&2; つの方法があります。 タイムラインまたはタイムラインから作成された時刻を登録することができます。 コードからのみ実行できますが、クロックを使用して直接、イベントの登録は、かなり簡単です。 マークアップまたはコードからタイムラインを使用してイベントを登録することができます。 次のセクションでは、タイムラインでのクロック イベントに登録する方法について説明します。  
  
<a name="registeringforclockeventswithatimeline"></a>   
## <a name="registering-for-clock-events-with-a-timeline"></a>タイムラインでのクロック イベントの登録  
 タイムラインの<xref:System.Windows.Media.Animation.Timeline.Completed>、 <xref:System.Windows.Media.Animation.Timeline.CurrentGlobalSpeedInvalidated>、 <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>、 <xref:System.Windows.Media.Animation.Timeline.CurrentTimeInvalidated>、および<xref:System.Windows.Media.Animation.Timeline.RemoveRequested>タイムライン、対応するこれらのイベントが実際にイベント ハンドラーを関連付けますの登録に関連するイベントが表示されます、<xref:System.Windows.Media.Animation.Clock>タイムラインのスペースを作成します。  
  
 登録する場合、<xref:System.Windows.Media.Animation.Timeline.Completed>タイムラインでイベントをたとえば、実際にすることをシステムに登録する、<xref:System.Windows.Media.Animation.Clock.Completed>タイムラインのスペースを作成する各クロックのイベントです。 コードでは、このイベントの前に登録する必要があります、<xref:System.Windows.Media.Animation.Clock>; このタイムラインの作成は、それ以外の場合、通知を受信しません。 自動的にこの問題は発生[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; パーサーが自動的に登録する前に、イベントの<xref:System.Windows.Media.Animation.Clock>が作成されます。  
  
## <a name="see-also"></a>関連項目  
 [アニメーションおよびタイミング システムの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)   
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [タイミング動作の概要](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)