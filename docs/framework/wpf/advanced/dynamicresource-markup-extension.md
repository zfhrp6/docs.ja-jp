---
title: DynamicResource のマークアップ拡張機能
ms.date: 03/30/2017
f1_keywords:
- DynamicResource
- DynamicResourceExtension
helpviewer_keywords:
- XAML [WPF], DynamicResource markup extension
- DynamicResource markup extensions [WPF]
ms.assetid: 7324f243-03af-4c2b-b0db-26ac6cdfcbe4
ms.openlocfilehash: c09d009a8cc90e050f6cfb1a8d2abd5c61c5b19f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545325"
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource のマークアップ拡張機能
いずれかの値を提供[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]定義されているリソースへの参照にするには、その値を遅らせることで、プロパティの属性です。 そのリソースに対する検索の動作は、実行時の参照に似ています。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xml  
<object property="{DynamicResource key}" .../>  
```  
  
## <a name="xaml-property-element-usage"></a>XAML プロパティ要素の使用  
  
```xml  
<object>  
  <object.property>  
    <DynamicResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`key`|要求されたリソースのキー。 によってこのキーに割り当てられた最初に、 [X:key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md)リソースがマークアップでは、作成されたまたはが指定されているかどうか、`key`パラメーターを呼び出すときに<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>リソースは、コードで作成された場合。|  
  
## <a name="remarks"></a>コメント  
 A`DynamicResource`最初のコンパイル中に一時的な式を作成し、要求されたリソースの値が実際にオブジェクトを構築するために必要になるまで遅延リソースの参照。 後にこの可能性があります、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ページが読み込まれます。 リソースの値はに対する現在のページ範囲から始まるすべてのアクティブなリソース ディクショナリのキーの検索に基づくありコンパイルのプレース ホルダーの式と置き換えられます。  
  
> [!IMPORTANT]
>  依存関係プロパティの優先順位の観点から、`DynamicResource`式は、動的リソース参照が適用される位置に相当します。 プロパティを持っていたのローカル値を設定したかどうか、 `DynamicResource` 、ローカルの値として式、`DynamicResource`が完全に削除します。 詳細については、「[依存関係プロパティ値の優先順位](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)」を参照してください。  
  
 特定のリソース アクセスのシナリオに適した特に`DynamicResource`はなく、 [StaticResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)します。 参照してください[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)、相対的な利点とパフォーマンスに及ぼす影響の詳細については`DynamicResource`と`StaticResource`です。  
  
 指定した<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A>によって既存のリソースに対応する[X:key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md)ページ、アプリケーション、使用可能なコントロールのテーマと外部リソースは、またはシステム リソースのいくつかのレベルで、リソースの検索は、その順序で実行されます。 静的および動的なリソースのリソースの検索の詳細については、次を参照してください。 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)です。  
  
 リソース キーの任意の文字列で定義されている可能性があります、 [XamlName の文法](../../../../docs/framework/xaml-services/xamlname-grammar.md)です。 リソース キーもあります他のオブジェクトの種類など、<xref:System.Type>です。 A<xref:System.Type>キーがコントロールをテーマ スタイル設定するための基礎です。 詳しくは、「[コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)」を参照してください。  
  
 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] リソースの値の検索など<xref:System.Windows.FrameworkElement.FindResource%2A>で使用されると同じリソースの検索ロジックに従います`DynamicResource`です。  
  
 リソースを参照するための代替宣言的な手段は、 [StaticResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)します。  
  
 属性構文は、このマークアップ拡張機能で使用される最も一般的な構文です。 `DynamicResource` 識別子文字列の後に設定される文字列トークンは、基になる <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> 拡張クラスの <xref:System.Windows.DynamicResourceExtension> 値として割り当てられます。  
  
 `DynamicResource` オブジェクトの要素の構文で使用できます。 この例では、値を指定する、<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A>プロパティは必須です。  
  
 `DynamicResource` は、<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> プロパティをプロパティおよび値のペアとして指定する詳細出力属性使用でも使用できます。  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 詳細出力の使用は、複数の設定可能プロパティを持つ拡張機能や、一部のプロパティがオプションである場合に役立ちます。 `DynamicResource` には、必須の設定可能プロパティが 1 つしか存在しないため、このような詳細出力の使用は一般的ではありません。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサの実装でこのマークアップ拡張機能の処理が定義されている、<xref:System.Windows.DynamicResourceExtension>クラスです。  
  
 `DynamicResource` はマークアップ拡張機能です。 一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。 すべてのマークアップ拡張機能で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用して、{、}、規則は、それぞれの属性構文内の文字、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサは、マークアップ拡張機能が、属性を処理する必要がありますを認識します。 詳細については、次を参照してください。[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)です。  
  
## <a name="see-also"></a>関連項目  
 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [リソースとコード](../../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [x:Key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md)  
 [XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [StaticResource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)  
 [マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
