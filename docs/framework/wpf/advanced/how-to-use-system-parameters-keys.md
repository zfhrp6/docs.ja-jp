---
title: "方法: システム パラメーター キーを使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2b5f45f386c58b0577a2716c6fe1396f4c44f4ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-system-parameters-keys"></a><span data-ttu-id="bd72c-102">方法: システム パラメーター キーを使用する</span><span class="sxs-lookup"><span data-stu-id="bd72c-102">How to: Use System Parameters Keys</span></span>
<span data-ttu-id="bd72c-103">システム リソースは、開発者がシステム設定と一貫性のあるビジュアルを作成できるようにするために、多くのシステム メトリックをリソースとして公開します。</span><span class="sxs-lookup"><span data-stu-id="bd72c-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="bd72c-104"><xref:System.Windows.SystemParameters>システム パラメーターの値と値へのバインドのリソース キーの両方を含むクラスは、— たとえば、<xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A>と<xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>です。</span><span class="sxs-lookup"><span data-stu-id="bd72c-104"><xref:System.Windows.SystemParameters> is a class that contains both system parameter values and resource keys that bind to the values—for example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span></span> <span data-ttu-id="bd72c-105">システム パラメーター メトリックは、静的なリソースとしても、動的なリソースとしても使用できます。</span><span class="sxs-lookup"><span data-stu-id="bd72c-105">System parameter metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="bd72c-106">アプリケーションの実行時にパラメーター メトリックを自動的に更新する場合は、動的リソースを使用します。それ以外の場合は、静的リソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="bd72c-106">Use a dynamic resource if you want the parameter metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd72c-107">動的なリソースがあるキーワード*キー*プロパティ名に付加します。</span><span class="sxs-lookup"><span data-stu-id="bd72c-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="bd72c-108">次の例では、ボタンのスタイル設定やカスタマイズを行うために、システム パラメーター動的リソースにアクセスして使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bd72c-108">The following example shows how to access and use system parameter dynamic resources to style or customize a button.</span></span> <span data-ttu-id="bd72c-109">これは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]例を割り当てることで、ボタンのサイズを<xref:System.Windows.SystemParameters>ボタンの幅と高さの値。</span><span class="sxs-lookup"><span data-stu-id="bd72c-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example sizes a button by assigning <xref:System.Windows.SystemParameters> values to the button's width and height.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd72c-110">例</span><span class="sxs-lookup"><span data-stu-id="bd72c-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="bd72c-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="bd72c-111">See Also</span></span>  
 [<span data-ttu-id="bd72c-112">システム ブラシで領域を塗りつぶす</span><span class="sxs-lookup"><span data-stu-id="bd72c-112">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="bd72c-113">SystemFonts を使用する</span><span class="sxs-lookup"><span data-stu-id="bd72c-113">Use SystemFonts</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [<span data-ttu-id="bd72c-114">SystemParameters を使用する</span><span class="sxs-lookup"><span data-stu-id="bd72c-114">Use SystemParameters</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)
