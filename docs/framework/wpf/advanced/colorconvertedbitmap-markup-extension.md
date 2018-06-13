---
title: ColorConvertedBitmap のマークアップ拡張機能
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], ColorConvertedBitmap markup extension
- ColorConvertedBitmap markup extension [WPF]
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
ms.openlocfilehash: 9b39e30cbe4e0bedc88c859f013b4d7175f7eb1a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538911"
---
# <a name="colorconvertedbitmap-markup-extension"></a><span data-ttu-id="62777-102">ColorConvertedBitmap のマークアップ拡張機能</span><span class="sxs-lookup"><span data-stu-id="62777-102">ColorConvertedBitmap Markup Extension</span></span>
<span data-ttu-id="62777-103">埋め込みのプロファイルがないビットマップ ソースを指定する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="62777-103">Provides a way to specify a bitmap source that does not have an embedded profile.</span></span> <span data-ttu-id="62777-104">カラー コンテキスト プロファイルが指定/[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]がイメージ ソースとして、[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="62777-104">Color contexts / profiles are specified by [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], as is the image source [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="62777-105">XAML 属性の使用方法</span><span class="sxs-lookup"><span data-stu-id="62777-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="62777-106">XAML 値</span><span class="sxs-lookup"><span data-stu-id="62777-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`imageSource`|<span data-ttu-id="62777-107">[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]のプロファイルになっていないビットマップ。</span><span class="sxs-lookup"><span data-stu-id="62777-107">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] of the nonprofiled bitmap.</span></span>|  
|`sourceIIC`|<span data-ttu-id="62777-108">[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]のソース プロファイルの構成。</span><span class="sxs-lookup"><span data-stu-id="62777-108">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] of the source profile configuration.</span></span>|  
|`destinationIIC`|<span data-ttu-id="62777-109">[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の移行先のプロファイルの構成</span><span class="sxs-lookup"><span data-stu-id="62777-109">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] of the destination profile configuration</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62777-110">コメント</span><span class="sxs-lookup"><span data-stu-id="62777-110">Remarks</span></span>  
 <span data-ttu-id="62777-111">このマークアップ拡張機能など、関連する一連の画像ソース プロパティの値を入力するためのものが<xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>です。</span><span class="sxs-lookup"><span data-stu-id="62777-111">This markup extension is intended to fill a related set of image-source property values such as <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.</span></span>  
  
 <span data-ttu-id="62777-112">属性構文は、このマークアップ拡張機能で使用される最も一般的な構文です。</span><span class="sxs-lookup"><span data-stu-id="62777-112">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="62777-113">`ColorConvertedBitmap` (または`ColorConvertedBitmapExtension`) 値のみ設定できます値として文字列は、最初のコンス トラクターのために、プロパティ要素構文で使用することはできません次の拡張機能の識別子。</span><span class="sxs-lookup"><span data-stu-id="62777-113">`ColorConvertedBitmap` (or `ColorConvertedBitmapExtension`) cannot be used in property element syntax, because the values can only be set as values on the initial constructor, which is the string following the extension identifier.</span></span>  
  
 <span data-ttu-id="62777-114">`ColorConvertedBitmap` はマークアップ拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="62777-114">`ColorConvertedBitmap` is a markup extension.</span></span> <span data-ttu-id="62777-115">一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。</span><span class="sxs-lookup"><span data-stu-id="62777-115">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="62777-116">すべてのマークアップ拡張機能で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用して、{、}、規則は、それぞれの属性構文内の文字、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサは、マークアップ拡張機能が、属性を処理する必要がありますを認識します。</span><span class="sxs-lookup"><span data-stu-id="62777-116">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="62777-117">詳細については、次を参照してください。[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)です。</span><span class="sxs-lookup"><span data-stu-id="62777-117">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62777-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="62777-118">See Also</span></span>  
 <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>  
 [<span data-ttu-id="62777-119">マークアップ拡張機能と WPF XAML</span><span class="sxs-lookup"><span data-stu-id="62777-119">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="62777-120">イメージングの概要</span><span class="sxs-lookup"><span data-stu-id="62777-120">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
