---
title: "方法: ハイパーリンクに下線を引くかどうかを指定する"
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
- Hyperlink control type [WPF]
ms.assetid: 3996cfe6-1dac-4835-aeb3-c719ce9cfee5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 24c3cc1bba4fd12d4a0f2ad02fa0c1b52b124381
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-whether-a-hyperlink-is-underlined"></a><span data-ttu-id="0b889-102">方法: ハイパーリンクに下線を引くかどうかを指定する</span><span class="sxs-lookup"><span data-stu-id="0b889-102">How to: Specify Whether a Hyperlink is Underlined</span></span>
<span data-ttu-id="0b889-103"><xref:System.Windows.Documents.Hyperlink>オブジェクトはインライン レベル フロー コンテンツ要素フロー コンテンツ内のハイパーリンクをホストすることができます。</span><span class="sxs-lookup"><span data-stu-id="0b889-103">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="0b889-104">既定では、<xref:System.Windows.Documents.Hyperlink>を使用して、<xref:System.Windows.TextDecoration>下線を表示するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0b889-104">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <span data-ttu-id="0b889-105"><xref:System.Windows.TextDecoration>オブジェクトができる処理を要するインスタンスを作成すると、パフォーマンスが多数ある場合に特に<xref:System.Windows.Documents.Hyperlink>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0b889-105"><xref:System.Windows.TextDecoration> objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="0b889-106">広範な利用を加えた場合<xref:System.Windows.Documents.Hyperlink>要素、するをお勧めしますように、イベントをトリガーする場合にのみ下線を表示、<xref:System.Windows.ContentElement.MouseEnter>イベント。</span><span class="sxs-lookup"><span data-stu-id="0b889-106">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="0b889-107">次の例では、"My MSN"リンクの下線は動的 — これ場合のみ表示されます、<xref:System.Windows.ContentElement.MouseEnter>イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="0b889-107">In the following example, the underline for the "My MSN" link is dynamic—it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
 <span data-ttu-id="0b889-108">![Textdecorations を表示するハイパーリンク](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span><span class="sxs-lookup"><span data-stu-id="0b889-108">![Hyperlinks displaying TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span></span>  
<span data-ttu-id="0b889-109">Textdecorations をで定義されているハイパーリンク</span><span class="sxs-lookup"><span data-stu-id="0b889-109">Hyperlinks defined with TextDecorations</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b889-110">例</span><span class="sxs-lookup"><span data-stu-id="0b889-110">Example</span></span>  
 <span data-ttu-id="0b889-111">次のマークアップのサンプルでは、<xref:System.Windows.Documents.Hyperlink>および下線を使用せずに定義されています。</span><span class="sxs-lookup"><span data-stu-id="0b889-111">The following markup sample shows a <xref:System.Windows.Documents.Hyperlink> defined with and without an underline:</span></span>  
  
 [!code-xaml[Performance#PerformanceSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 <span data-ttu-id="0b889-112">次のコード サンプルの下線を作成する方法を示しています、<xref:System.Windows.Documents.Hyperlink>上、<xref:System.Windows.ContentElement.MouseEnter>イベント、上で削除し、<xref:System.Windows.ContentElement.MouseLeave>イベント。</span><span class="sxs-lookup"><span data-stu-id="0b889-112">The following code sample shows how to create an underline for the <xref:System.Windows.Documents.Hyperlink> on the <xref:System.Windows.ContentElement.MouseEnter> event, and remove it on the <xref:System.Windows.ContentElement.MouseLeave> event.</span></span>  
  
 [!code-csharp[Performance#PerformanceSnippet15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml.cs#performancesnippet15)]
 [!code-vb[Performance#PerformanceSnippet15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/hyperlink.xaml.vb#performancesnippet15)]  
  
## <a name="see-also"></a><span data-ttu-id="0b889-113">参照</span><span class="sxs-lookup"><span data-stu-id="0b889-113">See Also</span></span>  
 <xref:System.Windows.TextDecoration>  
 <xref:System.Windows.Documents.Hyperlink>  
 [<span data-ttu-id="0b889-114">WPF アプリケーションのパフォーマンスの最適化</span><span class="sxs-lookup"><span data-stu-id="0b889-114">Optimizing WPF Application Performance</span></span>](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [<span data-ttu-id="0b889-115">文字の装飾を作成する</span><span class="sxs-lookup"><span data-stu-id="0b889-115">Create a Text Decoration</span></span>](../../../../docs/framework/wpf/advanced/how-to-create-a-text-decoration.md)
