---
title: '方法 : 要素に装飾をバインドする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
ms.openlocfilehash: fb419ee5a57e81e7e3bc72ae04fd200703b80cd3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-bind-an-adorner-to-an-element"></a><span data-ttu-id="df657-102">方法 : 要素に装飾をバインドする</span><span class="sxs-lookup"><span data-stu-id="df657-102">How to: Bind an Adorner to an Element</span></span>
<span data-ttu-id="df657-103">この例は、指定された装飾をプログラムでバインドする方法を示します<xref:System.Windows.UIElement>です。</span><span class="sxs-lookup"><span data-stu-id="df657-103">This example shows how to programmatically bind an adorner to a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df657-104">例</span><span class="sxs-lookup"><span data-stu-id="df657-104">Example</span></span>  
 <span data-ttu-id="df657-105">特定の装飾にバインドする<xref:System.Windows.UIElement>、これらの手順に従います。</span><span class="sxs-lookup"><span data-stu-id="df657-105">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="df657-106">呼び出す、`static`メソッド<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>を取得する、<xref:System.Windows.Documents.AdornerLayer>オブジェクトに対して、<xref:System.Windows.UIElement>を装飾します。</span><span class="sxs-lookup"><span data-stu-id="df657-106">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="df657-107"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> 指定した位置を開始、ビジュアル ツリーを調べて**UIElement**、し、見つかった最初の装飾層を返します。</span><span class="sxs-lookup"><span data-stu-id="df657-107"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified **UIElement**, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="df657-108">(装飾層が見つからない場合、メソッドにより null が返されます)。</span><span class="sxs-lookup"><span data-stu-id="df657-108">(If no adorner layers are found, the method returns null.)</span></span>  
  
2.  <span data-ttu-id="df657-109">呼び出す、<xref:System.Windows.Documents.AdornerLayer.Add%2A>装飾をターゲットにバインドするメソッド**UIElement**です。</span><span class="sxs-lookup"><span data-stu-id="df657-109">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target **UIElement**.</span></span>  
  
 <span data-ttu-id="df657-110">次の例に (上記) SimpleCircleAdorner、<xref:System.Windows.Controls.TextBox>という*myTextBox*です。</span><span class="sxs-lookup"><span data-stu-id="df657-110">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  <span data-ttu-id="df657-111">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を使用して、装飾を別の要素にバインドする方法は、現在サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="df657-111">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df657-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="df657-112">See Also</span></span>  
 [<span data-ttu-id="df657-113">装飾の概要</span><span class="sxs-lookup"><span data-stu-id="df657-113">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
