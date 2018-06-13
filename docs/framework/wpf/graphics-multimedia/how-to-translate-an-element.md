---
title: '方法 : 要素を変換する'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: 0089f294c54662d1ea4929ec25c08464072cbdde
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561944"
---
# <a name="how-to-translate-an-element"></a><span data-ttu-id="ff84b-102">方法 : 要素を変換する</span><span class="sxs-lookup"><span data-stu-id="ff84b-102">How to: Translate an Element</span></span>
<span data-ttu-id="ff84b-103">この例では変換 (移動) 要素を使用して、<xref:System.Windows.Media.TranslateTransform>です。</span><span class="sxs-lookup"><span data-stu-id="ff84b-103">This example shows how to translate (move) an element by using a <xref:System.Windows.Media.TranslateTransform>.</span></span>  
  
 <span data-ttu-id="ff84b-104"><xref:System.Windows.Media.TranslateTransform>クラスは、絶対位置指定をサポートしていないパネル内の要素を移動するために特に便利です。</span><span class="sxs-lookup"><span data-stu-id="ff84b-104">The <xref:System.Windows.Media.TranslateTransform> class is especially useful for moving elements inside panels that do not support absolute positioning.</span></span> <span data-ttu-id="ff84b-105">適用することで、たとえば、<xref:System.Windows.Media.TranslateTransform>を<xref:System.Windows.UIElement.RenderTransform%2A>要素のプロパティ内の要素を移動することができます、<xref:System.Windows.Controls.StackPanel>または<xref:System.Windows.Controls.DockPanel>です。</span><span class="sxs-lookup"><span data-stu-id="ff84b-105">For example, by applying a <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of an element, you can move an element within a <xref:System.Windows.Controls.StackPanel> or <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="ff84b-106">使用して、<xref:System.Windows.Media.TranslateTransform.X%2A>のプロパティ、 <xref:System.Windows.Media.TranslateTransform> (ピクセル単位) を x 軸に要素を移動する量を指定します。</span><span class="sxs-lookup"><span data-stu-id="ff84b-106">Use the <xref:System.Windows.Media.TranslateTransform.X%2A> property of the <xref:System.Windows.Media.TranslateTransform> to specify the amount, in pixels, to move the element along the x-axis.</span></span> <span data-ttu-id="ff84b-107">使用して、<xref:System.Windows.Media.TranslateTransform.Y%2A>プロパティ (ピクセル単位) を y 軸に沿った要素を移動する量を指定します。</span><span class="sxs-lookup"><span data-stu-id="ff84b-107">Use the <xref:System.Windows.Media.TranslateTransform.Y%2A> property to specify the amount, in pixels, to move the element along the y-axis.</span></span> <span data-ttu-id="ff84b-108">最後に、適用、<xref:System.Windows.Media.TranslateTransform>を<xref:System.Windows.UIElement.RenderTransform%2A>要素のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="ff84b-108">Finally, apply the <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="ff84b-109">次の例では、<xref:System.Windows.Media.TranslateTransform>下に移動する要素を 50 ピクセルを左右に 50 ピクセルです。</span><span class="sxs-lookup"><span data-stu-id="ff84b-109">The following example uses a <xref:System.Windows.Media.TranslateTransform> to move an element 50 pixels to the right and 50 pixels down.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff84b-110">例</span><span class="sxs-lookup"><span data-stu-id="ff84b-110">Example</span></span>  
 [!code-xaml[transformsSample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 <span data-ttu-id="ff84b-111">完全なサンプルについては、「[2-D 変換のサンプル](http://go.microsoft.com/fwlink/?LinkID=158252)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ff84b-111">For the complete sample, see [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff84b-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff84b-112">See Also</span></span>  
 [<span data-ttu-id="ff84b-113">変換の概要</span><span class="sxs-lookup"><span data-stu-id="ff84b-113">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
