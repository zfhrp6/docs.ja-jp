---
title: "ThemeDictionary のマークアップ拡張機能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ThemeDictionaryExtension
- ThemeDictionary
helpviewer_keywords:
- ThemeDictionary markup extension [WPF]
- XAML [WPF], ThemeDictionary markup extension
ms.assetid: aa75e10b-13dd-4989-972d-51bab63a05e2
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45f878ce89dcf76ae800ade10a0e67f019741f65
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="themedictionary-markup-extension"></a><span data-ttu-id="1eb4e-102">ThemeDictionary のマークアップ拡張機能</span><span class="sxs-lookup"><span data-stu-id="1eb4e-102">ThemeDictionary Markup Extension</span></span>
<span data-ttu-id="1eb4e-103">カスタム コントロールの作成者やサード パーティ製コントロールをコントロールのスタイル設定に使用するテーマ固有のリソース ディクショナリを読み込めませんを統合するアプリケーションの手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="1eb4e-103">Provides a way for custom control authors or applications that integrate third-party controls to load theme-specific resource dictionaries to use in styling the control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="1eb4e-104">XAML 属性の使用方法</span><span class="sxs-lookup"><span data-stu-id="1eb4e-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="1eb4e-105">XAML オブジェクト要素の使用方法</span><span class="sxs-lookup"><span data-stu-id="1eb4e-105">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="1eb4e-106">XAML 値</span><span class="sxs-lookup"><span data-stu-id="1eb4e-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`assemblyUri`|<span data-ttu-id="1eb4e-107">[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]テーマ情報を格納するアセンブリのです。</span><span class="sxs-lookup"><span data-stu-id="1eb4e-107">The [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] of the assembly that contains theme information.</span></span> <span data-ttu-id="1eb4e-108">通常、これは、パッケージのより大きなパッケージ内のアセンブリを参照する URI です。</span><span class="sxs-lookup"><span data-stu-id="1eb4e-108">Typically, this is a pack URI that references an assembly in the larger package.</span></span> <span data-ttu-id="1eb4e-109">アセンブリ リソースとパッケージの Uri は、展開に関する問題を簡略化します。</span><span class="sxs-lookup"><span data-stu-id="1eb4e-109">Assembly resources and pack URIs simplify deployment issues.</span></span> <span data-ttu-id="1eb4e-110">詳細については、次を参照してください。 [WPF のパック Uri](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)です。</span><span class="sxs-lookup"><span data-stu-id="1eb4e-110">For more information see [Pack URIs in WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1eb4e-111">コメント</span><span class="sxs-lookup"><span data-stu-id="1eb4e-111">Remarks</span></span>  
 <span data-ttu-id="1eb4e-112">1 つだけの特定のプロパティ値を入力するためのものは、この拡張機能: 値を<xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="1eb4e-112">This extension is intended to fill only one specific property value: a value for <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="1eb4e-113">この拡張機能を使用すると、される場合にのみを使用するいくつかのスタイルを含む単一リソース専用のアセンブリを指定することができます、 [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] Luna テーマがアクティブ、ためには、他のスタイル、ユーザーのシステムにテーマを適用します。</span><span class="sxs-lookup"><span data-stu-id="1eb4e-113">By using this extension, you can specify a single resources-only assembly that contains some styles to use only when the [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] theme is applied to the user's system, other styles when Luna theme is active, and so on.</span></span> <span data-ttu-id="1eb4e-114">この拡張機能を使用すると、コントロールに固有のリソース ディクショナリの内容に自動的に無効にして再読み込みするために必要なときに別のテーマの特定をします。</span><span class="sxs-lookup"><span data-stu-id="1eb4e-114">By using this extension, the contents of a control-specific resource dictionary can be automatically invalidated and reloaded to be specific for another theme when required.</span></span>  
  
 <span data-ttu-id="1eb4e-115">`assemblyUri`文字列 (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A>プロパティの値) を特定のテーマに適用するディクショナリを識別する名前付け規則の基礎を形成します。</span><span class="sxs-lookup"><span data-stu-id="1eb4e-115">The `assemblyUri` string (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property value) forms the basis of a naming convention that identifies which dictionary applies for a particular theme.</span></span> <span data-ttu-id="1eb4e-116"><xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>のロジック`ThemeDictionary`生成することによって、規則を完了する、[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]プリコンパイル済みのリソース アセンブリ内に含まれるように特定のテーマのディクショナリのバリアント型を指しています。</span><span class="sxs-lookup"><span data-stu-id="1eb4e-116">The <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> logic for `ThemeDictionary` completes the convention by generating a [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] that points to a particular theme dictionary variant, as contained within a precompiled resource assembly.</span></span> <span data-ttu-id="1eb4e-117">この規則、または一般的なコントロールのスタイル設定と、概念としてページ/アプリケーション レベルのスタイル設定のテーマの相互作用を記述するについては、完全にここで説明しません。</span><span class="sxs-lookup"><span data-stu-id="1eb4e-117">Describing this convention, or theme interactions with general control styling and page/application level styling as a concept, is not covered fully here.</span></span> <span data-ttu-id="1eb4e-118">使用するための基本的なシナリオ`ThemeDictionary`を指定する、<xref:System.Windows.ResourceDictionary.Source%2A>のプロパティ、`ResourceDictionary`アプリケーション レベルで宣言します。</span><span class="sxs-lookup"><span data-stu-id="1eb4e-118">The basic scenario for using `ThemeDictionary` is to specify the <xref:System.Windows.ResourceDictionary.Source%2A> property of a `ResourceDictionary` declared at the application level.</span></span> <span data-ttu-id="1eb4e-119">指定すると、[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]によるアセンブリの`ThemeDictionary`拡張機能ではなく、直接[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]、拡張機能のロジックはシステムのテーマが変更されるたびに適用される無効化ロジックを提供します。</span><span class="sxs-lookup"><span data-stu-id="1eb4e-119">When you provide a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for the assembly through a `ThemeDictionary` extension rather than as a direct [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], the extension logic will provide invalidation logic that applies whenever the system theme changes.</span></span>  
  
 <span data-ttu-id="1eb4e-120">属性構文は、このマークアップ拡張機能で使用される最も一般的な構文です。</span><span class="sxs-lookup"><span data-stu-id="1eb4e-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="1eb4e-121">`ThemeDictionary` 識別子文字列の後に設定される文字列トークンは、基になる <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> 拡張クラスの <xref:System.Windows.ThemeDictionaryExtension> 値として割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="1eb4e-121">The string token provided after the `ThemeDictionary` identifier string is assigned as the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> value of the underlying <xref:System.Windows.ThemeDictionaryExtension> extension class.</span></span>  
  
 <span data-ttu-id="1eb4e-122">`ThemeDictionary`オブジェクトの要素の構文にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="1eb4e-122">`ThemeDictionary` may also be used in object element syntax.</span></span> <span data-ttu-id="1eb4e-123">この例では、値を指定する、<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A>プロパティは必須です。</span><span class="sxs-lookup"><span data-stu-id="1eb4e-123">In this case, specifying the value of the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property is required.</span></span>  
  
 <span data-ttu-id="1eb4e-124">`ThemeDictionary` は、<xref:System.Windows.Markup.StaticExtension.Member%2A> プロパティをプロパティおよび値のペアとして指定する詳細出力属性使用でも使用できます。</span><span class="sxs-lookup"><span data-stu-id="1eb4e-124">`ThemeDictionary` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.Markup.StaticExtension.Member%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 <span data-ttu-id="1eb4e-125">詳細出力の使用は、複数の設定可能プロパティを持つ拡張機能や、一部のプロパティがオプションである場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1eb4e-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="1eb4e-126">`ThemeDictionary` には、必須の設定可能プロパティが 1 つしか存在しないため、このような詳細出力の使用は一般的ではありません。</span><span class="sxs-lookup"><span data-stu-id="1eb4e-126">Because `ThemeDictionary` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="1eb4e-127">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサの実装でこのマークアップ拡張機能の処理が定義されている、<xref:System.Windows.ThemeDictionaryExtension>クラスです。</span><span class="sxs-lookup"><span data-stu-id="1eb4e-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.ThemeDictionaryExtension> class.</span></span>  
  
 <span data-ttu-id="1eb4e-128">`ThemeDictionary` はマークアップ拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="1eb4e-128">`ThemeDictionary` is a markup extension.</span></span> <span data-ttu-id="1eb4e-129">一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。</span><span class="sxs-lookup"><span data-stu-id="1eb4e-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="1eb4e-130">すべてのマークアップ拡張機能で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用して、{、}、規則は、それぞれの属性構文内の文字、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサは、マークアップ拡張機能が、属性を処理する必要がありますを認識します。</span><span class="sxs-lookup"><span data-stu-id="1eb4e-130">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="1eb4e-131">詳細については、次を参照してください。[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)です。</span><span class="sxs-lookup"><span data-stu-id="1eb4e-131">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1eb4e-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="1eb4e-132">See Also</span></span>  
 [<span data-ttu-id="1eb4e-133">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="1eb4e-133">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="1eb4e-134">XAML の概要 (WPF)</span><span class="sxs-lookup"><span data-stu-id="1eb4e-134">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="1eb4e-135">マークアップ拡張機能と WPF XAML</span><span class="sxs-lookup"><span data-stu-id="1eb4e-135">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="1eb4e-136">WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル</span><span class="sxs-lookup"><span data-stu-id="1eb4e-136">WPF Application Resource, Content, and Data Files</span></span>](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
