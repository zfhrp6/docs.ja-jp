---
title: タイミング イベントの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- timelines [WPF]
- timing events [WPF]
ms.assetid: 597e3280-0867-4359-a97b-5b2f4149e350
ms.openlocfilehash: a48d1621e5568d556a1177578cc662813d70a283
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565488"
---
# <a name="timing-events-overview"></a>タイミング イベントの概要
このトピックで使用できる 5 つのタイミング イベントを使用する方法について説明<xref:System.Windows.Media.Animation.Timeline>と<xref:System.Windows.Media.Animation.Clock>オブジェクト。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解するには、アニメーションの作成方法と使用方法について理解している必要があります。 アニメーションを開始するを参照してください。、[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)です。  
  
 いくつかの方法でプロパティをアニメーション化する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
-   **ストーリー ボードのオブジェクトを使用して**(マークアップおよびコード): 使用することができます<xref:System.Windows.Media.Animation.Storyboard>を配置し、1 つまたは複数のオブジェクトへのアニメーションを配布するオブジェクト。 例については、次を参照してください。[ストーリー ボードを使用してプロパティをアニメーション化](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)です。  
  
-   **ローカルのアニメーションを使用して**(コードのみ): 適用できる<xref:System.Windows.Media.Animation.AnimationTimeline>アニメーション化するプロパティに直接オブジェクト。 例については、「[ストーリーボードを使用せずにプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)」を参照してください。  
  
-   **クロックを使用する**(コードのみ): クロックを明示的に作成し、アニメーション クロックを自分で均等配置することができます。  例については、次を参照してください。 [、AnimationClock を使用してプロパティをアニメーション化](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-an-animationclock.md)です。  
  
 この概要の例を使用してマークアップおよびコードで使用することができます、ため<xref:System.Windows.Media.Animation.Storyboard>オブジェクト。 ただし、説明されている概念は、プロパティをアニメーション化するためのその他の方法にも適用できます。  
  
### <a name="what-is-a-clock"></a>クロックとは  
 タイムラインは、時間のセグメントについて説明する以外は、それ自身が実際に何かを行うものではありません。 タイムラインの<xref:System.Windows.Media.Animation.Clock>実際の処理を行うオブジェクト: タイムラインの実行時のタイミングに関連する状態を保持します。 多くの場合(ストーリー ボードを使用する場合など)には、タイムラインに対してクロックが自動的に作成されます。 作成することも、<xref:System.Windows.Media.Animation.Clock>を使用して明示的に、<xref:System.Windows.Media.Animation.Timeline.CreateClock%2A>メソッドです。 詳細については<xref:System.Windows.Media.Animation.Clock>、オブジェクトを参照してください、[アニメーションおよびタイミング システムの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)です。  
  
## <a name="why-use-events"></a>イベントを使用する理由  
 1 つの例外 (最後のティックに配置されたシーク) を除いて、すべての対話型タイミング操作は非同期です。 これらがいつ実行されるかを正確に知る方法はありません。 これは、タイミング操作に依存する他のコードが存在する場合に、問題となることがあります。 たとえば、四角形をアニメーション化するタイムラインを停止する必要があるとします。 そしてタイムラインを停止した後に、四角形の色を変更するとします。  
  
 [!code-csharp[events_procedural#NeedForEventsFragment](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#needforeventsfragment)]
 [!code-vb[events_procedural#NeedForEventsFragment](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#needforeventsfragment)]  
  
 上記の例では、ストーリー ボードが停止する前に、2 行目のコードが実行される可能性があります。 これは、停止が非同期の操作であるためです。 タイムラインやクロックに停止を指示すると、タイミング エンジンの次のティックまで処理されない「停止要求」が作成されます。  
  
 タイムラインの完了後にコマンドを実行するには、タイミング イベントを使用します。 次の例では、ストーリー ボードが停止した後に四角形の色が変更されるよう、イベント ハンドラーが使用されています。  
  
 [!code-csharp[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#registerforstoryboardcurrentstateinvalidatedevent)]
 [!code-vb[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#registerforstoryboardcurrentstateinvalidatedevent)]  
[!code-csharp[events_procedural#StoryboardCurrentStateInvalidatedEvent2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#storyboardcurrentstateinvalidatedevent2)]
[!code-vb[events_procedural#StoryboardCurrentStateInvalidatedEvent2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#storyboardcurrentstateinvalidatedevent2)]  
  
 完全な例では、次を参照してください。[受信通知時に、クロックの状態の変化](../../../../docs/framework/wpf/graphics-multimedia/how-to-receive-notification-when-clock-state-changes.md)です。  
  
## <a name="public-events"></a>パブリック イベント  
 <xref:System.Windows.Media.Animation.Timeline>と<xref:System.Windows.Media.Animation.Clock>両方のクラスには、5 つのタイミング イベントが用意されています。 次の表は、これらのイベントと、それらをトリガーする条件を示したものです。  
  
|event|対話型操作のトリガー|その他のトリガー|  
|-----------|--------------------------------------|--------------------|  
|**Completed**|塗りつぶしまでスキップ|時計が完了する。|  
|**CurrentGlobalSpeedInvalidated**|一時停止、再開、シーク、速度比を設定、塗りつぶしまでスキップ、停止|クロックが反転、加速、開始、または停止する。|  
|**CurrentStateInvalidated**|開始、塗りつぶしまでスキップ、停止|クロックが開始、停止、または塗りつぶされる。|  
|**CurrentTimeInvalidated**|開始、シーク、塗りつぶしまでスキップ、停止|クロックが進行する。|  
|**RemoveRequested**|削除||  
  
## <a name="ticking-and-event-consolidation"></a>ティッキングとイベントの統合  
 内のオブジェクトをアニメーション化するときに[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、アニメーションを管理するタイミング エンジンです。 タイミング エンジンは、時間の進行状況を追跡し、それぞれのアニメーションの状態を計算します。 これにより、多数の評価パスが瞬時に作成されます。 これらの評価パスは「ティック」と呼ばれます。  
  
 ティックは頻繁に発生しますが、各ティックの間には多くのことが起こる可能性があります。 たとえば、タイムラインが停止され、開始され、再度停止された場合、その現行状態は 3 回変更されることになります。 理論上、イベントは 1 つのティックで複数回発生することができますが、タイミング エンジンではイベントが統合されるため、各イベントの発生回数はティックあたり最大で 1回となります。  
  
## <a name="registering-for-events"></a>イベントの登録  
 タイミング イベントを登録する方法は 2 つあります。 タイムラインに登録する方法と、タイムラインから作成されたクロックに登録する方法です。 クロックに直接登録する方法は非常に分かりやすいですが、これはコードからのみ実行できます。 タイムラインに登録する場合は、マークアップまたはコードからイベントを登録できます。 次のセクションでは、クロック イベントをタイムラインに登録する方法について説明します。  
  
<a name="registeringforclockeventswithatimeline"></a>   
## <a name="registering-for-clock-events-with-a-timeline"></a>クロック イベントをタイムラインに登録する  
 タイムラインの<xref:System.Windows.Media.Animation.Timeline.Completed>、 <xref:System.Windows.Media.Animation.Timeline.CurrentGlobalSpeedInvalidated>、 <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>、 <xref:System.Windows.Media.Animation.Timeline.CurrentTimeInvalidated>、および<xref:System.Windows.Media.Animation.Timeline.RemoveRequested>タイムラインは、これらのイベントが実際を持つイベント ハンドラーを関連付けるためにの登録に関連するイベントが表示されます、 <xref:System.Windows.Media.Animation.Clock>タイムラインのスペースを作成します。  
  
 登録すると、<xref:System.Windows.Media.Animation.Timeline.Completed>タイムラインでイベントをたとえばを実際にということですね、システムに登録する、<xref:System.Windows.Media.Animation.Clock.Completed>タイムラインに作成される各クロックのイベントです。 コードでは、前にこのイベントを登録する必要があります、 <xref:System.Windows.Media.Animation.Clock> ; このタイムラインの作成は、それ以外の場合、通知を受信しません。 自動的にこのような[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; パーサーが自動的に登録する前に、イベントの<xref:System.Windows.Media.Animation.Clock>を作成します。  
  
## <a name="see-also"></a>関連項目  
 [アニメーションとタイミング システムの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [タイミング動作の概要](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)
