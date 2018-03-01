---
title: "方法 : PriorityBinding を実装する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0e6ab8826f2298a8660a85d739fbe3456374b476
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-implement-prioritybinding"></a><span data-ttu-id="815fe-102">方法 : PriorityBinding を実装する</span><span class="sxs-lookup"><span data-stu-id="815fe-102">How to: Implement PriorityBinding</span></span>
<span data-ttu-id="815fe-103"><xref:System.Windows.Data.PriorityBinding>[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]のバインドの一覧を指定することによって動作します。</span><span class="sxs-lookup"><span data-stu-id="815fe-103"><xref:System.Windows.Data.PriorityBinding> in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] works by specifying a list of bindings.</span></span> <span data-ttu-id="815fe-104">バインディングのリストの順序は、最高の優先度から最も低い優先順位。</span><span class="sxs-lookup"><span data-stu-id="815fe-104">The list of bindings is ordered from highest priority to lowest priority.</span></span> <span data-ttu-id="815fe-105">最高の優先度のバインドが値を返す場合が正常に処理される際はありませんリスト内の他のバインディングを処理する必要。</span><span class="sxs-lookup"><span data-stu-id="815fe-105">If the highest priority binding returns a value successfully when it is processed then there is never a need to process the other bindings in the list.</span></span> <span data-ttu-id="815fe-106">最高の優先度のバインドに評価される時間がかかる場合がある可能性があります、優先順位の高いバインドが正常に値を返すまで、正常に値を返す次の最も優先度が使用されます。</span><span class="sxs-lookup"><span data-stu-id="815fe-106">It could be the case that the highest priority binding takes a long time to be evaluated, the next highest priority that returns a value successfully will be used until a binding of a higher priority returns a value successfully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="815fe-107">例</span><span class="sxs-lookup"><span data-stu-id="815fe-107">Example</span></span>  
 <span data-ttu-id="815fe-108">示すためにどのように<xref:System.Windows.Data.PriorityBinding>の動作、`AsyncDataSource`次の 3 つのプロパティでオブジェクトが作成されました: `FastDP`、`SlowerDP`と`SlowestDP`です。</span><span class="sxs-lookup"><span data-stu-id="815fe-108">To demonstrate how <xref:System.Windows.Data.PriorityBinding> works, the `AsyncDataSource` object has been created with the following three properties: `FastDP`, `SlowerDP`, and `SlowestDP`.</span></span>  
  
 <span data-ttu-id="815fe-109">Get アクセサー`FastDP`の値を返します、`_fastDP`データ メンバーです。</span><span class="sxs-lookup"><span data-stu-id="815fe-109">The get accessor of `FastDP` returns the value of the `_fastDP` data member.</span></span>  
  
 <span data-ttu-id="815fe-110">Get アクセサー `SlowerDP` 3 秒間の値を返す前に待機する、`_slowerDP`データ メンバーです。</span><span class="sxs-lookup"><span data-stu-id="815fe-110">The get accessor of `SlowerDP` waits for 3 seconds before returning the value of the `_slowerDP` data member.</span></span>  
  
 <span data-ttu-id="815fe-111">Get アクセサー`SlowestDP`を 5 秒間の値を返す前に待機する、`_slowestDP`データ メンバーです。</span><span class="sxs-lookup"><span data-stu-id="815fe-111">The get accessor of `SlowestDP` waits for 5 seconds before returning the value of the `_slowestDP` data member.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="815fe-112">この例はデモ目的でのみです。</span><span class="sxs-lookup"><span data-stu-id="815fe-112">This example is for demonstration purposes only.</span></span> <span data-ttu-id="815fe-113">[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)]ガイドライン推奨桁違いフィールド セットよりも低速であるプロパティを定義します。</span><span class="sxs-lookup"><span data-stu-id="815fe-113">The [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] guidelines recommend against defining properties that are orders of magnitude slower than a field set would be.</span></span> <span data-ttu-id="815fe-114">詳細については、次を参照してください。 [NIB: プロパティとの間の選択とメソッド](http://msdn.microsoft.com/library/55825e8f-7e2e-448a-9505-7217cc91b1af)です。</span><span class="sxs-lookup"><span data-stu-id="815fe-114">For more information, see [NIB: Choosing Between Properties and Methods](http://msdn.microsoft.com/library/55825e8f-7e2e-448a-9505-7217cc91b1af).</span></span>  
  
 [!code-csharp[PriorityBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <span data-ttu-id="815fe-115"><xref:System.Windows.Controls.TextBlock.Text%2A>プロパティ上にバインドされて`AsyncDS`を使用して<xref:System.Windows.Data.PriorityBinding>:</span><span class="sxs-lookup"><span data-stu-id="815fe-115">The <xref:System.Windows.Controls.TextBlock.Text%2A> property binds to the above `AsyncDS` using <xref:System.Windows.Data.PriorityBinding>:</span></span>  
  
 [!code-xaml[PriorityBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="815fe-116">バインディング エンジンが処理するときに、<xref:System.Windows.Data.Binding>オブジェクト、1 つ目で始まっている<xref:System.Windows.Data.Binding>にバインドされている、`SlowestDP`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="815fe-116">When the binding engine processes the <xref:System.Windows.Data.Binding> objects, it starts with the first <xref:System.Windows.Data.Binding>, which is bound to the `SlowestDP` property.</span></span> <span data-ttu-id="815fe-117">ときにこの<xref:System.Windows.Data.Binding>は、処理は返されません、値が正常にため、これがスリープ状態 5 (秒単位) のため、次へ<xref:System.Windows.Data.Binding>要素を処理します。</span><span class="sxs-lookup"><span data-stu-id="815fe-117">When this <xref:System.Windows.Data.Binding> is processed, it does not return a value successfully because it is sleeping for 5 seconds, so the next <xref:System.Windows.Data.Binding> element is processed.</span></span> <span data-ttu-id="815fe-118">次<xref:System.Windows.Data.Binding>は正常に完了しなかった値が 3 秒間スリープ状態にあるためです。</span><span class="sxs-lookup"><span data-stu-id="815fe-118">The next <xref:System.Windows.Data.Binding> does not return a value successfully because it is sleeping for 3 seconds.</span></span> <span data-ttu-id="815fe-119">バインディング エンジンは、次のステップに移動<xref:System.Windows.Data.Binding>にバインドされている要素、`FastDP`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="815fe-119">The binding engine then moves onto the next <xref:System.Windows.Data.Binding> element, which is bound to the `FastDP` property.</span></span> <span data-ttu-id="815fe-120">これは、 <xref:System.Windows.Data.Binding> "高速 Value"の値を返します。</span><span class="sxs-lookup"><span data-stu-id="815fe-120">This <xref:System.Windows.Data.Binding> returns the value "Fast Value".</span></span> <span data-ttu-id="815fe-121"><xref:System.Windows.Controls.TextBlock>値"Fast"が表示されます。</span><span class="sxs-lookup"><span data-stu-id="815fe-121">The <xref:System.Windows.Controls.TextBlock> now displays the value "Fast Value".</span></span>  
  
 <span data-ttu-id="815fe-122">3 秒が経過した後、 `SlowerDP` "低速 Value"の値を返します。</span><span class="sxs-lookup"><span data-stu-id="815fe-122">After 3 seconds elapses, the `SlowerDP` property returns the value "Slower Value".</span></span> <span data-ttu-id="815fe-123"><xref:System.Windows.Controls.TextBlock> "低速 Value"の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="815fe-123">The <xref:System.Windows.Controls.TextBlock> then displays the value "Slower Value".</span></span>  
  
 <span data-ttu-id="815fe-124">5 秒が経過した後、 `SlowestDP` "最も低速な Value"の値を返します。</span><span class="sxs-lookup"><span data-stu-id="815fe-124">After 5 seconds elapses, the `SlowestDP` property returns the value "Slowest Value".</span></span> <span data-ttu-id="815fe-125">そのバインディングは、最初に表示されているために、最高の優先順位をでいます。</span><span class="sxs-lookup"><span data-stu-id="815fe-125">That binding has the highest priority because it is listed first.</span></span> <span data-ttu-id="815fe-126"><xref:System.Windows.Controls.TextBlock> "最も低速な Value"の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="815fe-126">The <xref:System.Windows.Controls.TextBlock> now displays the value "Slowest Value".</span></span>  
  
 <span data-ttu-id="815fe-127">参照してください<xref:System.Windows.Data.PriorityBinding>については、バインドからの成功の戻り値と見なされます。</span><span class="sxs-lookup"><span data-stu-id="815fe-127">See <xref:System.Windows.Data.PriorityBinding> for information about what is considered a successful return value from a binding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="815fe-128">参照</span><span class="sxs-lookup"><span data-stu-id="815fe-128">See Also</span></span>  
 <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="815fe-129">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="815fe-129">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="815fe-130">方法トピック</span><span class="sxs-lookup"><span data-stu-id="815fe-130">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
