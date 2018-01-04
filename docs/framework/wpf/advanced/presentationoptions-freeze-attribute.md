---
title: "PresentationOptions:Freeze 属性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cb305c69cec7c4e4766153ae64d37b19ab0bccea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="presentationoptionsfreeze-attribute"></a><span data-ttu-id="1aba0-102">PresentationOptions:Freeze 属性</span><span class="sxs-lookup"><span data-stu-id="1aba0-102">PresentationOptions:Freeze Attribute</span></span>
<span data-ttu-id="1aba0-103">セット、<xref:System.Windows.Freezable.IsFrozen%2A>状態`true`に含まれている<xref:System.Windows.Freezable>要素。</span><span class="sxs-lookup"><span data-stu-id="1aba0-103">Sets the <xref:System.Windows.Freezable.IsFrozen%2A> state to `true` on the containing <xref:System.Windows.Freezable> element.</span></span> <span data-ttu-id="1aba0-104">既定の動作、<xref:System.Windows.Freezable>せず、`PresentationOptions:Freeze`属性が指定される<xref:System.Windows.Freezable.IsFrozen%2A>は`false`負荷時、および [全般] に依存<xref:System.Windows.Freezable>実行時に動作します。</span><span class="sxs-lookup"><span data-stu-id="1aba0-104">Default behavior for a <xref:System.Windows.Freezable> without the `PresentationOptions:Freeze` attribute specified is that <xref:System.Windows.Freezable.IsFrozen%2A> is `false` at load time, and dependent on general <xref:System.Windows.Freezable> behavior at runtime.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="1aba0-105">XAML 属性の使用方法</span><span class="sxs-lookup"><span data-stu-id="1aba0-105">XAML Attribute Usage</span></span>  
  
```  
<object  
  xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="PresentationOptions">  
    <freezableElement PresentationOptions:Freeze="true"/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="1aba0-106">XAML 値</span><span class="sxs-lookup"><span data-stu-id="1aba0-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`PresentationOptions`|<span data-ttu-id="1aba0-107">名前空間プレフィックス、XML 1.0 仕様あたり、任意の有効なプレフィックス文字列になります。</span><span class="sxs-lookup"><span data-stu-id="1aba0-107">An XML namespace prefix, which can be any valid prefix string, per the XML 1.0 specification.</span></span> <span data-ttu-id="1aba0-108">プレフィックス`PresentationOptions`はこのドキュメントで識別する目的で使用します。</span><span class="sxs-lookup"><span data-stu-id="1aba0-108">The prefix `PresentationOptions` is used for identification purposes in this documentation.</span></span>|  
|`freezableElement`|<span data-ttu-id="1aba0-109">いずれかをインスタンス化する要素の派生クラス<xref:System.Windows.Freezable>です。</span><span class="sxs-lookup"><span data-stu-id="1aba0-109">An element that instantiates any derived class of <xref:System.Windows.Freezable>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1aba0-110">コメント</span><span class="sxs-lookup"><span data-stu-id="1aba0-110">Remarks</span></span>  
 <span data-ttu-id="1aba0-111">`Freeze`属性は、唯一の属性またはで他のプログラミング要素が定義されている、 `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` XML 名前空間。</span><span class="sxs-lookup"><span data-stu-id="1aba0-111">The `Freeze` attribute is the only attribute or other programming element defined in the `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` XML namespace.</span></span> <span data-ttu-id="1aba0-112">`Freeze`に指定できるは、無視できるを使用できるように具体的には、この特別な名前空間の属性が存在する[mc: Ignorable 属性](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)ルート要素の宣言の一部として。</span><span class="sxs-lookup"><span data-stu-id="1aba0-112">The `Freeze` attribute exists in this special namespace specifically so that it can be designated as ignorable, using [mc:Ignorable Attribute](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) as part of the root element declarations.</span></span> <span data-ttu-id="1aba0-113">理由を`Freeze`無視することである必要がありますではないすべて[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサの実装は、固定するのには、 <xref:System.Windows.Freezable> ; の読み込み時にこの機能はの一部、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]仕様です。</span><span class="sxs-lookup"><span data-stu-id="1aba0-113">The reason that `Freeze` must be able to be ignorable is because not all [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementations are able to freeze a <xref:System.Windows.Freezable> at load time; this capability is not part of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] specification.</span></span>  
  
 <span data-ttu-id="1aba0-114">処理する機能、`Freeze`属性は、具体的に組み込まれている、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を処理するプロセッサ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]のアプリケーションをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="1aba0-114">The ability to process the `Freeze` attribute is specifically built in to the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor that processes [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] for compiled applications.</span></span> <span data-ttu-id="1aba0-115">属性は、クラスによってサポートされていませんし、属性構文が拡張または変更します。</span><span class="sxs-lookup"><span data-stu-id="1aba0-115">The attribute is not supported by any class, and the attribute syntax is not extensible or modifiable.</span></span> <span data-ttu-id="1aba0-116">実装する場合、独自[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサの固定の動作をすることができます、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサの処理時に、`Freeze`属性に<xref:System.Windows.Freezable>読み込み時に要素。</span><span class="sxs-lookup"><span data-stu-id="1aba0-116">If you are implementing your own [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor you can choose to parallel the freezing behavior of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor when processing the `Freeze` attribute on <xref:System.Windows.Freezable> elements at load time.</span></span>  
  
 <span data-ttu-id="1aba0-117">すべての値、`Freeze`以外の属性`true`(いない大文字小文字を区別)、読み込み時にエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="1aba0-117">Any value for the `Freeze` attribute other than `true` (not case sensitive) generates a load time error.</span></span> <span data-ttu-id="1aba0-118">(を指定する、`Freeze`属性に`false`、エラーではありません設定するため、既定ではない`false`何も行われません)。</span><span class="sxs-lookup"><span data-stu-id="1aba0-118">(Specifying the `Freeze` attribute as `false` is not an error, but that is already the default, so setting to `false` does nothing).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aba0-119">参照</span><span class="sxs-lookup"><span data-stu-id="1aba0-119">See Also</span></span>  
 <xref:System.Windows.Freezable>  
 [<span data-ttu-id="1aba0-120">Freezable オブジェクトの概要</span><span class="sxs-lookup"><span data-stu-id="1aba0-120">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="1aba0-121">mc:Ignorable 属性</span><span class="sxs-lookup"><span data-stu-id="1aba0-121">mc:Ignorable Attribute</span></span>](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)
