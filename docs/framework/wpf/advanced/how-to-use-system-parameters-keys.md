---
title: '方法: システム パラメーター キーを使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
ms.openlocfilehash: c94719c8268cbbdadbe6805d531540e1f34ee5d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544717"
---
# <a name="how-to-use-system-parameters-keys"></a><span data-ttu-id="c917b-102">方法: システム パラメーター キーを使用する</span><span class="sxs-lookup"><span data-stu-id="c917b-102">How to: Use System Parameters Keys</span></span>
<span data-ttu-id="c917b-103">システム リソースは、開発者がシステム設定と一貫性のあるビジュアルを作成できるようにするために、多くのシステム メトリックをリソースとして公開します。</span><span class="sxs-lookup"><span data-stu-id="c917b-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="c917b-104"><xref:System.Windows.SystemParameters> システム パラメーターの値と値へのバインドのリソース キーの両方を含むクラスは、— たとえば、<xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A>と<xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>です。</span><span class="sxs-lookup"><span data-stu-id="c917b-104"><xref:System.Windows.SystemParameters> is a class that contains both system parameter values and resource keys that bind to the values—for example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span></span> <span data-ttu-id="c917b-105">システム パラメーター メトリックは、静的なリソースとしても、動的なリソースとしても使用できます。</span><span class="sxs-lookup"><span data-stu-id="c917b-105">System parameter metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="c917b-106">アプリケーションの実行時にパラメーター メトリックを自動的に更新する場合は、動的リソースを使用します。それ以外の場合は、静的リソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="c917b-106">Use a dynamic resource if you want the parameter metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c917b-107">動的なリソースがあるキーワード*キー*プロパティ名に付加します。</span><span class="sxs-lookup"><span data-stu-id="c917b-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="c917b-108">次の例では、ボタンのスタイル設定やカスタマイズを行うために、システム パラメーター動的リソースにアクセスして使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c917b-108">The following example shows how to access and use system parameter dynamic resources to style or customize a button.</span></span> <span data-ttu-id="c917b-109">これは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]例を割り当てることで、ボタンのサイズを<xref:System.Windows.SystemParameters>ボタンの幅と高さの値。</span><span class="sxs-lookup"><span data-stu-id="c917b-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example sizes a button by assigning <xref:System.Windows.SystemParameters> values to the button's width and height.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c917b-110">例</span><span class="sxs-lookup"><span data-stu-id="c917b-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="c917b-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="c917b-111">See Also</span></span>  
 [<span data-ttu-id="c917b-112">システム ブラシで領域を塗りつぶす</span><span class="sxs-lookup"><span data-stu-id="c917b-112">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="c917b-113">SystemFonts を使用する</span><span class="sxs-lookup"><span data-stu-id="c917b-113">Use SystemFonts</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [<span data-ttu-id="c917b-114">SystemParameters を使用する</span><span class="sxs-lookup"><span data-stu-id="c917b-114">Use SystemParameters</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)
