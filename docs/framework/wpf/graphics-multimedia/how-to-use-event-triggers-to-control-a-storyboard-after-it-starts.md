---
title: '方法 : 開始後のストーリーボードをイベント トリガーを使用して制御する'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: c864668026c4f8bb58a4d6c4c36f96fb07445a9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="d4a09-102">方法 : 開始後のストーリーボードをイベント トリガーを使用して制御する</span><span class="sxs-lookup"><span data-stu-id="d4a09-102">How to: Use Event Triggers to Control a Storyboard After It Starts</span></span>
<span data-ttu-id="d4a09-103">この例では、制御、<xref:System.Windows.Media.Animation.Storyboard>開始後にします。</span><span class="sxs-lookup"><span data-stu-id="d4a09-103">This example shows how to control a <xref:System.Windows.Media.Animation.Storyboard> after it starts.</span></span> <span data-ttu-id="d4a09-104">開始する、<xref:System.Windows.Media.Animation.Storyboard>を使用して[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用して<xref:System.Windows.Media.Animation.BeginStoryboard>オブジェクトとを開始し、ストーリー ボードのプロパティにアニメーションを配布します。</span><span class="sxs-lookup"><span data-stu-id="d4a09-104">To start a <xref:System.Windows.Media.Animation.Storyboard> by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Media.Animation.BeginStoryboard>, which distributes the animations to the objects and properties they animate and then starts the storyboard.</span></span> <span data-ttu-id="d4a09-105">割り当てる場合<xref:System.Windows.Media.Animation.BeginStoryboard>名前を指定してその<xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A>プロパティ、おくことで制御可能なストーリー ボードです。</span><span class="sxs-lookup"><span data-stu-id="d4a09-105">If you give <xref:System.Windows.Media.Animation.BeginStoryboard> a name by specifying its <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> property, you make it a controllable storyboard.</span></span> <span data-ttu-id="d4a09-106">対話的に制御できますストーリー ボードを開始後にします。</span><span class="sxs-lookup"><span data-stu-id="d4a09-106">You can then interactively control the storyboard after it starts.</span></span>  
  
 <span data-ttu-id="d4a09-107">と共に次のストーリー ボード操作を使用して<xref:System.Windows.EventTrigger>ストーリー ボードを制御するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d4a09-107">Use the following storyboard actions together with <xref:System.Windows.EventTrigger> objects to control a storyboard.</span></span>  
  
-   <span data-ttu-id="d4a09-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: ストーリー ボードを一時停止します。</span><span class="sxs-lookup"><span data-stu-id="d4a09-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pauses the storyboard.</span></span>  
  
-   <span data-ttu-id="d4a09-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: 一時停止しているストーリー ボードを再開します。</span><span class="sxs-lookup"><span data-stu-id="d4a09-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Resumes a paused storyboard.</span></span>  
  
-   <span data-ttu-id="d4a09-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: ストーリー ボードの速度を変更します。</span><span class="sxs-lookup"><span data-stu-id="d4a09-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Changes the storyboard speed.</span></span>  
  
-   <span data-ttu-id="d4a09-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: 1 つがある場合は、その保留期間の終了をストーリー ボードを進めます。</span><span class="sxs-lookup"><span data-stu-id="d4a09-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Advances a storyboard to the end of its fill period, if it has one.</span></span>  
  
-   <span data-ttu-id="d4a09-112"><xref:System.Windows.Media.Animation.StopStoryboard>: ストーリー ボードを停止します。</span><span class="sxs-lookup"><span data-stu-id="d4a09-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Stops the storyboard.</span></span>  
  
-   <span data-ttu-id="d4a09-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: リソースの解放、ストーリー ボードを削除します。</span><span class="sxs-lookup"><span data-stu-id="d4a09-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Removes the storyboard, freeing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4a09-114">例</span><span class="sxs-lookup"><span data-stu-id="d4a09-114">Example</span></span>  
 <span data-ttu-id="d4a09-115">次の例では、制御可能なストーリー ボード操作を使用して、ストーリー ボードを対話的に制御します。</span><span class="sxs-lookup"><span data-stu-id="d4a09-115">The following example uses controllable storyboard actions to interactively control a storyboard.</span></span>  
  
 <span data-ttu-id="d4a09-116">**注:** コードを使用してストーリー ボードの制御の例を参照してください[、ストーリー ボードの後に、開始メソッドを使用してその対話型制御](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md)です。</span><span class="sxs-lookup"><span data-stu-id="d4a09-116">**Note:** To see an example of controlling a storyboard by using code, see [Control a Storyboard After It Starts Using Its Interactive Methods](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
 [!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 <span data-ttu-id="d4a09-117">その他の例では、次を参照してください。、[アニメーション サンプル ギャラリー](http://go.microsoft.com/fwlink/?LinkID=159969)です。</span><span class="sxs-lookup"><span data-stu-id="d4a09-117">For additional examples, see the [Animation Example Gallery](http://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4a09-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4a09-118">See Also</span></span>  
 <xref:System.Windows.Media.Animation.ResumeStoryboard>  
 <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>  
 <xref:System.Windows.Media.Animation.SkipStoryboardToFill>  
 <xref:System.Windows.Media.Animation.PauseStoryboard>  
 <xref:System.Windows.Media.Animation.StopStoryboard>  
 <xref:System.Windows.Media.Animation.SeekStoryboard>  
 [<span data-ttu-id="d4a09-119">対話型メソッドを使用してストーリーボードを開始後に制御する</span><span class="sxs-lookup"><span data-stu-id="d4a09-119">Control a Storyboard After It Starts Using Its Interactive Methods</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md)  
 [<span data-ttu-id="d4a09-120">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="d4a09-120">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="d4a09-121">ストーリーボードの概要</span><span class="sxs-lookup"><span data-stu-id="d4a09-121">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
