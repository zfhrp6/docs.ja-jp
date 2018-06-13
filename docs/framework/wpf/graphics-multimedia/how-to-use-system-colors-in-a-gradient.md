---
title: '方法 : グラデーションでシステム カラーを使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
ms.openlocfilehash: 4c3fca1db031b0dc397e9db58195b9714ff8aa9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562181"
---
# <a name="how-to-use-system-colors-in-a-gradient"></a><span data-ttu-id="80266-102">方法 : グラデーションでシステム カラーを使用する</span><span class="sxs-lookup"><span data-stu-id="80266-102">How to: Use System Colors in a Gradient</span></span>
<span data-ttu-id="80266-103">使用するシステムの色のグラデーションを使用するのには *\<SystemColor >* 色と *\<SystemColor >* の静的なプロパティを (ゼロ)、<xref:System.Windows.SystemColors>クラスを取得する、色への参照場所 *\<SystemColor >* 対象のシステム カラーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="80266-103">To use a system color in a gradient, you use the *\<SystemColor>* Color and *\<SystemColor>* ColorKey static properties of the <xref:System.Windows.SystemColors> class to obtain a reference to the color, where *\<SystemColor>* is the name of the desired system color.</span></span> <span data-ttu-id="80266-104">使用して、  *\<SystemColor >*(ゼロ) のプロパティをシステムのテーマの変更として自動的に更新される動的参照を作成するときにします。</span><span class="sxs-lookup"><span data-stu-id="80266-104">Use the *\<SystemColor>* ColorKey properties when you want to create a dynamic reference that updates automatically as the system theme changes.</span></span> <span data-ttu-id="80266-105">それ以外の場合を使用して、  *\<SystemColor >* Color プロパティです。</span><span class="sxs-lookup"><span data-stu-id="80266-105">Otherwise, use the *\<SystemColor>* Color properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80266-106">例</span><span class="sxs-lookup"><span data-stu-id="80266-106">Example</span></span>  
 <span data-ttu-id="80266-107">次の例では、動的なシステム カラー リソースを使用して、グラデーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="80266-107">The following example uses dynamic system color resources to create a gradient.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 <span data-ttu-id="80266-108">次の例では、静的なシステム カラー リソースを使用して、グラデーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="80266-108">The next example uses static system color resources to create a gradient.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="80266-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="80266-109">See Also</span></span>  
 <xref:System.Windows.SystemColors>  
 [<span data-ttu-id="80266-110">システム ブラシで領域を塗りつぶす</span><span class="sxs-lookup"><span data-stu-id="80266-110">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="80266-111">純色およびグラデーションによる塗りつぶしの概要</span><span class="sxs-lookup"><span data-stu-id="80266-111">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
