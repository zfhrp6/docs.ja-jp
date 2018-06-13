---
title: '方法 : ストーリーボード アニメーション間で HandoffBehavior を指定する'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF], handoff behavior between animations
- animation [WPF], handoff behavior between
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
ms.openlocfilehash: c4728dc1cb4eeeff55e533b8d91e4512d9cc1d94
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560552"
---
# <a name="how-to-specify-handoffbehavior-between-storyboard-animations"></a><span data-ttu-id="66c7b-102">方法 : ストーリーボード アニメーション間で HandoffBehavior を指定する</span><span class="sxs-lookup"><span data-stu-id="66c7b-102">How to: Specify HandoffBehavior Between Storyboard Animations</span></span>
<span data-ttu-id="66c7b-103">この例では、ストーリー ボードのアニメーション間ハンドオフ動作を指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="66c7b-103">This example shows how to specify handoff behavior between storyboard animations.</span></span> <span data-ttu-id="66c7b-104"><xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>のプロパティ<xref:System.Windows.Media.Animation.BeginStoryboard>新しいアニメーションを指定するプロパティに既に適用されている既存の対話します。</span><span class="sxs-lookup"><span data-stu-id="66c7b-104">The <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> property of <xref:System.Windows.Media.Animation.BeginStoryboard> specifies how new animations interact with any existing ones that are already applied to a property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66c7b-105">例</span><span class="sxs-lookup"><span data-stu-id="66c7b-105">Example</span></span>  
 <span data-ttu-id="66c7b-106">次の例では、上にマウス カーソルが移動時に拡大し、カーソルが休暇から移動したときに小さくなる 2 つのボタンを作成します。</span><span class="sxs-lookup"><span data-stu-id="66c7b-106">The following example creates two buttons that enlarge when the mouse cursor moves over them and become smaller when the cursor moves away.</span></span> <span data-ttu-id="66c7b-107">ボタンの上にマウス カーソルをすばやく削除すると、最初の 1 つを完了する前に 2 番目のアニメーションが適用されます。</span><span class="sxs-lookup"><span data-stu-id="66c7b-107">If you mouse over a button and then quickly remove the cursor, the second animation will be applied before the first one is finished.</span></span> <span data-ttu-id="66c7b-108">間の違いを表示できる次のように 2 つのアニメーションが重なっている場合は、<xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>値<xref:System.Windows.Media.Animation.HandoffBehavior.Compose>と<xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>です。</span><span class="sxs-lookup"><span data-stu-id="66c7b-108">It is when two animations overlap like this that you can see the difference between the <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> values of <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> and <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.</span></span> <span data-ttu-id="66c7b-109">値<xref:System.Windows.Media.Animation.HandoffBehavior.Compose>より滑らかな切り替え時の値にアニメーションが原因と重複するアニメーションを組み合わせて<xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>新しいアニメーションをすぐに、以前に重複するアニメーションを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="66c7b-109">A value of <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> combines the overlapping animations causing a smoother transition between animations while a value of <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> causes the new animation to immediately replace the earlier overlapping animation.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#HandoffBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="66c7b-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="66c7b-110">See Also</span></span>  
 <xref:System.Windows.Media.Animation.BeginStoryboard>  
 <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>  
 [<span data-ttu-id="66c7b-111">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="66c7b-111">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="66c7b-112">アニメーションおよびタイミング</span><span class="sxs-lookup"><span data-stu-id="66c7b-112">Animation and Timing</span></span>](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="66c7b-113">方法トピック</span><span class="sxs-lookup"><span data-stu-id="66c7b-113">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
