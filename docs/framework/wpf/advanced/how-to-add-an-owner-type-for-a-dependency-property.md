---
title: "方法 : 依存関係プロパティの所有者の種類を追加する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], adding as owners of dependency properties
- dependency properties [WPF], adding classes as owners of
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 079f08e1c330b710748ea6bb1aab8ccfb7ae7016
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a><span data-ttu-id="3c366-102">方法 : 依存関係プロパティの所有者の種類を追加する</span><span class="sxs-lookup"><span data-stu-id="3c366-102">How to: Add an Owner Type for a Dependency Property</span></span>
<span data-ttu-id="3c366-103">この例では、異なる種類の登録されている依存関係プロパティの所有者としてクラスを追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3c366-103">This example shows how to add a class as an owner of a dependency property registered for a different type.</span></span> <span data-ttu-id="3c366-104">これには、手順を実行して、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]リーダーとプロパティ システムの両方のプロパティの追加の所有者として、クラスを認識することができます。</span><span class="sxs-lookup"><span data-stu-id="3c366-104">By doing this, the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader and property system are both able to recognize the class as an additional owner of the property.</span></span> <span data-ttu-id="3c366-105">必要に応じて、所有者として追加すると、型固有のメタデータを提供する追加のクラスができます。</span><span class="sxs-lookup"><span data-stu-id="3c366-105">Adding as owner optionally allows the adding class to provide type-specific metadata.</span></span>  
  
 <span data-ttu-id="3c366-106">次の例では、`StateProperty`はプロパティでは登録、`MyStateControl`クラスです。</span><span class="sxs-lookup"><span data-stu-id="3c366-106">In the following example, `StateProperty` is a property registered by the `MyStateControl` class.</span></span> <span data-ttu-id="3c366-107">クラス`UnrelatedStateControl`の所有者として追加自体、`StateProperty`を使用して、<xref:System.Windows.DependencyProperty.AddOwner%2A>メソッド、具体的には、署名を使用するように、追加の型に存在する依存関係プロパティの新しいメタデータは、します。</span><span class="sxs-lookup"><span data-stu-id="3c366-107">The class `UnrelatedStateControl` adds itself as an owner of the `StateProperty` using the <xref:System.Windows.DependencyProperty.AddOwner%2A> method, specifically using the signature that allows for new metadata for the dependency property as it exists on the adding type.</span></span> <span data-ttu-id="3c366-108">通知を提供する[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]に示した例のようなプロパティのアクセサーでは、[依存関係プロパティを実装して](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md)などとして再追加するクラスに依存関係プロパティの識別子を公開所有者。</span><span class="sxs-lookup"><span data-stu-id="3c366-108">Notice that you should provide [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] accessors for the property similar to the example shown in the [Implement a Dependency Property](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md) example, as well as re-expose the dependency property identifier on the class being added as owner.</span></span>  
  
 <span data-ttu-id="3c366-109">ラッパーの依存関係プロパティは機能を使用したプログラムによるアクセスの観点から<xref:System.Windows.DependencyObject.GetValue%2A>または<xref:System.Windows.DependencyObject.SetValue%2A>です。</span><span class="sxs-lookup"><span data-stu-id="3c366-109">Without wrappers, the dependency property would still work from the perspective of programmatic access using <xref:System.Windows.DependencyObject.GetValue%2A> or <xref:System.Windows.DependencyObject.SetValue%2A>.</span></span> <span data-ttu-id="3c366-110">通常では、このプロパティのシステム動作を並列たいが、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]プロパティのラッパー。</span><span class="sxs-lookup"><span data-stu-id="3c366-110">But you typically want to parallel this property-system behavior with the [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] property wrappers.</span></span> <span data-ttu-id="3c366-111">ラッパーをプログラムでは、依存関係プロパティを設定するが容易し、可能としてプロパティを設定する[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]属性。</span><span class="sxs-lookup"><span data-stu-id="3c366-111">The wrappers make it easier to set the dependency property programmatically, and make it possible to set the properties as [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attributes.</span></span>  
  
 <span data-ttu-id="3c366-112">既定のメタデータをオーバーライドする方法を調べるには、次を参照してください。[依存関係プロパティのメタデータをオーバーライド](../../../../docs/framework/wpf/advanced/how-to-override-metadata-for-a-dependency-property.md)です。</span><span class="sxs-lookup"><span data-stu-id="3c366-112">To find out how to override default metadata, see [Override Metadata for a Dependency Property](../../../../docs/framework/wpf/advanced/how-to-override-metadata-for-a-dependency-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c366-113">例</span><span class="sxs-lookup"><span data-stu-id="3c366-113">Example</span></span>  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a><span data-ttu-id="3c366-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c366-114">See Also</span></span>  
 [<span data-ttu-id="3c366-115">カスタム依存関係プロパティ</span><span class="sxs-lookup"><span data-stu-id="3c366-115">Custom Dependency Properties</span></span>](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [<span data-ttu-id="3c366-116">依存関係プロパティの概要</span><span class="sxs-lookup"><span data-stu-id="3c366-116">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
