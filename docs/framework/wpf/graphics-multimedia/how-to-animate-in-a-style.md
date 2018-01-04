---
title: "方法 : スタイル内でアニメーション化を行う"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2aabe24b77a9016b5b8119646c80ea84eb73acb9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-in-a-style"></a><span data-ttu-id="88e46-102">方法 : スタイル内でアニメーション化を行う</span><span class="sxs-lookup"><span data-stu-id="88e46-102">How to: Animate in a Style</span></span>
<span data-ttu-id="88e46-103">この例では、スタイル内でプロパティをアニメーション化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="88e46-103">This example shows how to animate properties within a style.</span></span> <span data-ttu-id="88e46-104">スタイル内でアニメーション化するときに、スタイルが定義されているフレームワーク要素のみが直接対象となることができます。</span><span class="sxs-lookup"><span data-stu-id="88e46-104">When animating within a style, only the framework element for which the style is defined can be targeted directly.</span></span> <span data-ttu-id="88e46-105">Freezable オブジェクトを対象にする必要があります「ドット ダウン」スタイルを指定した要素のプロパティからです。</span><span class="sxs-lookup"><span data-stu-id="88e46-105">To target a freezable object, you must "dot down" from a property of the styled element.</span></span>  
  
 <span data-ttu-id="88e46-106">次の例では、複数のアニメーションのスタイル内で定義されているし、に適用される、<xref:System.Windows.Controls.Button>です。</span><span class="sxs-lookup"><span data-stu-id="88e46-106">In the following example, several animations are defined within a style and applied to a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="88e46-107">部分的に半透明とバックエンドを不透明なから消えてしまう場合、ユーザーがマウス ボタンの上、もう一度、繰り返しです。</span><span class="sxs-lookup"><span data-stu-id="88e46-107">When the user moves the mouse over the button, it fades from opaque to partially translucent and back again, repeatedly.</span></span> <span data-ttu-id="88e46-108">ユーザーがボタンをマウスを動かしたときに完全に不透明になります。</span><span class="sxs-lookup"><span data-stu-id="88e46-108">When the user moves the mouse off the button, it becomes completely opaque.</span></span> <span data-ttu-id="88e46-109">ボタンがクリックされたときに、背景色は白して戻すオレンジ色から変更します。</span><span class="sxs-lookup"><span data-stu-id="88e46-109">When the button is clicked, its background color changes from orange to white and back again.</span></span> <span data-ttu-id="88e46-110"><xref:System.Windows.Media.SolidColorBrush>を描画するため、ボタンを直接対象ことはできません、下のボタンの dotting 使用してアクセスされた<xref:System.Windows.Controls.Control.Background%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="88e46-110">Because the <xref:System.Windows.Media.SolidColorBrush> used to paint the button can't be targeted directly, it is accessed by dotting down from the button's <xref:System.Windows.Controls.Control.Background%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88e46-111">例</span><span class="sxs-lookup"><span data-stu-id="88e46-111">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]  
  
 <span data-ttu-id="88e46-112">スタイル内でアニメーション化するときに、存在しないオブジェクトはターゲットに考えられることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="88e46-112">Note that when animating within a style, it's possible to target objects that don't exist.</span></span> <span data-ttu-id="88e46-113">たとえば、自分のスタイルを使用して、<xref:System.Windows.Media.SolidColorBrush>ボタンの背景のプロパティを設定するが、ある時点で、スタイルをオーバーライドされ、ボタンの背景に設定されている、<xref:System.Windows.Media.LinearGradientBrush>です。</span><span class="sxs-lookup"><span data-stu-id="88e46-113">For example, suppose your style uses a <xref:System.Windows.Media.SolidColorBrush> to set a Button's background property, but at some point the style is overridden and the button's background is set with a <xref:System.Windows.Media.LinearGradientBrush>.</span></span>  <span data-ttu-id="88e46-114">アニメーション化しようとして、<xref:System.Windows.Media.SolidColorBrush>例外をスローしません、アニメーションはサイレント モードで失敗します。</span><span class="sxs-lookup"><span data-stu-id="88e46-114">Trying to animate the <xref:System.Windows.Media.SolidColorBrush> won't throw an exception; the animation will simply fail silently.</span></span>  
  
 <span data-ttu-id="88e46-115">構文を対象とするストーリー ボードの詳細については、次を参照してください。、[ストーリー ボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="88e46-115">Fore more information about storyboard targeting syntax, see the [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span> <span data-ttu-id="88e46-116">アニメーションの詳細については、次を参照してください。、[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="88e46-116">For more information about animation, see the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span> <span data-ttu-id="88e46-117">スタイルの詳細については、次を参照してください。、[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)です。</span><span class="sxs-lookup"><span data-stu-id="88e46-117">For more information about styles, see the [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>
