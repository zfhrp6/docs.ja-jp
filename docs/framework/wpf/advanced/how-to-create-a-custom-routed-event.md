---
title: '方法 : カスタム ルーティング イベントを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], creating
- events [WPF], routing
ms.assetid: b79f459a-1c3f-4045-b2d4-1659cc8eaa3c
ms.openlocfilehash: a8aa038008ed93cedfe49fde4e0269712b4fb19a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543707"
---
# <a name="how-to-create-a-custom-routed-event"></a><span data-ttu-id="763e0-102">方法 : カスタム ルーティング イベントを作成する</span><span class="sxs-lookup"><span data-stu-id="763e0-102">How to: Create a Custom Routed Event</span></span>
<span data-ttu-id="763e0-103">イベントのルーティングをサポートするために、カスタム イベントを登録する必要があります、<xref:System.Windows.RoutedEvent>を使用して、<xref:System.Windows.EventManager.RegisterRoutedEvent%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="763e0-103">For your custom event to support event routing, you need to register a <xref:System.Windows.RoutedEvent> using the <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> method.</span></span> <span data-ttu-id="763e0-104">この例では、カスタム ルーティング イベント作成の基本を紹介します。</span><span class="sxs-lookup"><span data-stu-id="763e0-104">This example demonstrates the basics of creating a custom routed event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="763e0-105">例</span><span class="sxs-lookup"><span data-stu-id="763e0-105">Example</span></span>  
 <span data-ttu-id="763e0-106">次の例に示すように、最初に登録する、<xref:System.Windows.RoutedEvent>を使用して、<xref:System.Windows.EventManager.RegisterRoutedEvent%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="763e0-106">As shown in the following example, you first register a <xref:System.Windows.RoutedEvent> using the <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> method.</span></span> <span data-ttu-id="763e0-107">慣例により、<xref:System.Windows.RoutedEvent>静的フィールドの名前サフィックスを末尾***イベント***です。</span><span class="sxs-lookup"><span data-stu-id="763e0-107">By convention, the <xref:System.Windows.RoutedEvent> static field name should end with the suffix ***Event***.</span></span> <span data-ttu-id="763e0-108">この例では、イベントの名前は`Tap`イベントのルーティング方法で、<xref:System.Windows.RoutingStrategy.Bubble>です。</span><span class="sxs-lookup"><span data-stu-id="763e0-108">In this example, the name of the event is `Tap` and the routing strategy of the event is <xref:System.Windows.RoutingStrategy.Bubble>.</span></span> <span data-ttu-id="763e0-109">登録呼び出し後、イベントの add-and-remove [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] イベント アクセサーを提供できます。</span><span class="sxs-lookup"><span data-stu-id="763e0-109">After the registration call, you can provide add-and-remove [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] event accessors for the event.</span></span>  
  
 <span data-ttu-id="763e0-110">この特別な例では `OnTap` 仮想メソッド経由でイベントが発生していますが、イベントの発生や変更に対するイベントの反応の仕方はニーズによって変わります。</span><span class="sxs-lookup"><span data-stu-id="763e0-110">Note that even though the event is raised through the `OnTap` virtual method in this particular example, how you raise your event or how your event responds to changes depends on your needs.</span></span>  
  
 <span data-ttu-id="763e0-111">この例は、の全体のサブクラスを基本的には実装にも注意してください<xref:System.Windows.Controls.Button>; そのサブクラスの個別のアセンブリとしてビルドし、は別にカスタム クラスとしてインスタンス化し、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ページ。</span><span class="sxs-lookup"><span data-stu-id="763e0-111">Note also that this example basically implements an entire subclass of <xref:System.Windows.Controls.Button>; that subclass is built as a separate assembly and then instantiated as a custom class on a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="763e0-112">これはサブクラス化されたコントロールを他のコントロールで構成されたツリーに挿入できるという概念を示すものです。この状況では、このようなコントロールのカスタム イベントには、あらゆるネイティブ [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 要素とまったく同じイベント ルーティング機能が与えられます。</span><span class="sxs-lookup"><span data-stu-id="763e0-112">This is to illustrate the concept that subclassed controls can be inserted into trees composed of other controls, and that in this situation, custom events on these controls have the very same event routing capabilities as any native [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] element does.</span></span>  
  
 [!code-csharp[RoutedEventCustom#CustomClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xaml[RoutedEventCustom#Page](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 <span data-ttu-id="763e0-113">トンネリング イベントが作成されて、同じ方法ですが、 <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> 'éý'<xref:System.Windows.RoutingStrategy.Tunnel>登録呼び出しで。</span><span class="sxs-lookup"><span data-stu-id="763e0-113">Tunneling events are created the same way, but with <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> set to <xref:System.Windows.RoutingStrategy.Tunnel> in the registration call.</span></span> <span data-ttu-id="763e0-114">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のトンネル イベントには接頭辞として "Preview" という単語が付く決まりになっています。</span><span class="sxs-lookup"><span data-stu-id="763e0-114">By convention, tunneling events in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] are prefixed with the word "Preview".</span></span>  
  
 <span data-ttu-id="763e0-115">バブリング イベントの動作例については、「[ルーティング イベントを処理する](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="763e0-115">To see an example of how bubbling events work, see [Handle a Routed Event](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="763e0-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="763e0-116">See Also</span></span>  
 [<span data-ttu-id="763e0-117">ルーティング イベントの概要</span><span class="sxs-lookup"><span data-stu-id="763e0-117">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="763e0-118">入力の概要</span><span class="sxs-lookup"><span data-stu-id="763e0-118">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [<span data-ttu-id="763e0-119">コントロールの作成の概要</span><span class="sxs-lookup"><span data-stu-id="763e0-119">Control Authoring Overview</span></span>](../../../../docs/framework/wpf/controls/control-authoring-overview.md)
