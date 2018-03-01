---
title: "方法: SystemParameters を使用する"
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
- classes [WPF], SystemParameters
ms.assetid: 02e7a5de-94eb-4953-b91c-52e6c872ad5b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ec333fbc30374ff6f8e2e7674ab332644ff7aad0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-systemparameters"></a><span data-ttu-id="aa97b-102">方法: SystemParameters を使用する</span><span class="sxs-lookup"><span data-stu-id="aa97b-102">How to: Use SystemParameters</span></span>
<span data-ttu-id="aa97b-103">この例は、アクセスしのプロパティを使用する方法を示しています。<xref:System.Windows.SystemParameters>スタイルまたはボタンをカスタマイズするためにします。</span><span class="sxs-lookup"><span data-stu-id="aa97b-103">This example shows how to access and use the properties of <xref:System.Windows.SystemParameters> in order to style or customize a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa97b-104">例</span><span class="sxs-lookup"><span data-stu-id="aa97b-104">Example</span></span>  
 <span data-ttu-id="aa97b-105">システム リソースは、システム設定と一貫性のあるビジュアルを作成できるようにするために、いくつかのシステムに基づく設定をリソースとして公開します。</span><span class="sxs-lookup"><span data-stu-id="aa97b-105">System resources expose several system based settings as resources in order to help you create visuals that are consistent with system settings.</span></span> <span data-ttu-id="aa97b-106"><xref:System.Windows.SystemParameters>システム パラメーターの値のプロパティと値へのバインドのリソース キーの両方を含むクラスです。</span><span class="sxs-lookup"><span data-stu-id="aa97b-106"><xref:System.Windows.SystemParameters> is a class that contains both system parameter value properties, and resource keys that bind to the values.</span></span> <span data-ttu-id="aa97b-107">たとえば、<xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A>は、<xref:System.Windows.SystemParameters>プロパティの値と<xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>は、対応するリソース キー。</span><span class="sxs-lookup"><span data-stu-id="aa97b-107">For example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> is a <xref:System.Windows.SystemParameters> property value and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> is the corresponding resource key.</span></span>  
  
 <span data-ttu-id="aa97b-108">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]のメンバーを使用することができます<xref:System.Windows.SystemParameters>静的プロパティの使用状況、または (キーとして静的プロパティの値) の動的リソース参照のいずれかとして。</span><span class="sxs-lookup"><span data-stu-id="aa97b-108">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can use the members of <xref:System.Windows.SystemParameters> as either a static property usage, or a dynamic resource references (with the static property value as the key).</span></span> <span data-ttu-id="aa97b-109">アプリケーションの実行時にシステムに基づく値を自動的に更新する場合は、動的リソース参照を使用します。それ以外の場合は、静的参照を使用します。</span><span class="sxs-lookup"><span data-stu-id="aa97b-109">Use a dynamic resource reference if you want the system based value to update automatically while the application runs; otherwise, use a static reference.</span></span> <span data-ttu-id="aa97b-110">リソース キーは、サフィックスを持ちます`Key`プロパティ名に付加します。</span><span class="sxs-lookup"><span data-stu-id="aa97b-110">Resource keys have the suffix `Key` appended to the property name.</span></span>  
  
 <span data-ttu-id="aa97b-111">次の例は、アクセスおよびの静的な値を使用する方法を示しています。<xref:System.Windows.SystemParameters>スタイルを設定したり、ボタンをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="aa97b-111">The following example shows how to access and use the static values of <xref:System.Windows.SystemParameters> to style or customize a button.</span></span> <span data-ttu-id="aa97b-112">このマークアップの例を適用して、ボタンのサイズを<xref:System.Windows.SystemParameters>をボタンの値。</span><span class="sxs-lookup"><span data-stu-id="aa97b-112">This markup example sizes a button by applying <xref:System.Windows.SystemParameters> values to a button.</span></span>  
  
 [!code-xaml[SystemRes_snip#ParameterStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#parameterstaticresources)]  
  
 <span data-ttu-id="aa97b-113">値を使用する<xref:System.Windows.SystemParameters>コードでは、静的参照または動的リソース参照を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="aa97b-113">To use the values of <xref:System.Windows.SystemParameters> in code, you do not have to use either static references or dynamic resource references.</span></span> <span data-ttu-id="aa97b-114">代わりの値を使用して、<xref:System.Windows.SystemParameters>クラスです。</span><span class="sxs-lookup"><span data-stu-id="aa97b-114">Instead, use the values of the <xref:System.Windows.SystemParameters> class.</span></span> <span data-ttu-id="aa97b-115">静的なプロパティの実行時の動作として定義されていますキー以外のプロパティが明らか[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ように、システムによってホストされているがリアルタイムでプロパティを再評価され、ユーザーによる値の変更システム アカウントでは適切です。</span><span class="sxs-lookup"><span data-stu-id="aa97b-115">Although the non-key properties are apparently defined as static properties, the runtime behavior of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as hosted by the system will reevaluate the properties in realtime, and will properly account for user-driven changes to system values.</span></span> <span data-ttu-id="aa97b-116">次の例を使用してボタンの高さと幅を設定する方法を示します<xref:System.Windows.SystemParameters>値。</span><span class="sxs-lookup"><span data-stu-id="aa97b-116">The following example shows how to set the width and height of a button by using <xref:System.Windows.SystemParameters> values.</span></span>  
  
 [!code-csharp[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#parameterresourcescode)]
 [!code-vb[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#parameterresourcescode)]  
  
## <a name="see-also"></a><span data-ttu-id="aa97b-117">参照</span><span class="sxs-lookup"><span data-stu-id="aa97b-117">See Also</span></span>  
 <xref:System.Windows.SystemParameters>  
 [<span data-ttu-id="aa97b-118">システム ブラシで領域を塗りつぶす</span><span class="sxs-lookup"><span data-stu-id="aa97b-118">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="aa97b-119">SystemFonts を使用する</span><span class="sxs-lookup"><span data-stu-id="aa97b-119">Use SystemFonts</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [<span data-ttu-id="aa97b-120">システム パラメーター キーを使用する</span><span class="sxs-lookup"><span data-stu-id="aa97b-120">Use System Parameters Keys</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-system-parameters-keys.md)  
 [<span data-ttu-id="aa97b-121">方法トピック</span><span class="sxs-lookup"><span data-stu-id="aa97b-121">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
