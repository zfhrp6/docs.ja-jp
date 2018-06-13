---
title: ComponentResourceKey マークアップ拡張機能
ms.date: 03/30/2017
f1_keywords:
- ComponentResourceKey
- ComponentResourceKeyExtension
helpviewer_keywords:
- ComponentResourceKey markup extension [WPF]
- XAML [WPF], ComponentResourceKey markup extension
ms.assetid: d6bcdbe6-61b3-40a7-b381-4e02185b5a85
ms.openlocfilehash: d11c26add084165eaa9fd0b319a375c4b98c7fb9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540411"
---
# <a name="componentresourcekey-markup-extension"></a>ComponentResourceKey マークアップ拡張機能
定義し、外部アセンブリから読み込まれているリソースのキーを参照します。 これには、アセンブリまたはクラスでは、明示的なリソース ディクショナリではなく、アセンブリのターゲットの種類を指定するリソースの参照が使用できます。  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a>XAML 属性の使用 (設定キー、compact)  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a>XAML 属性の使用方法の (設定キー、詳細)  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a>XAML 属性の使用方法 (要求しているリソース、compact)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a>XAML 属性の使用 (リソース要求、詳細)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`targetTypeName`|パブリック名[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]リソース アセンブリに定義されている型。|  
|`targetID`|リソースのキー。 リソースの問い合わせがあったときに`targetID`に似てなります、 [X:key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md)リソースのです。|  
  
## <a name="remarks"></a>コメント  
 使用法、上記のような {`ComponentResourceKey`} マークアップ拡張機能の使用が 2 つの場所が見つかりません。  
  
-   コントロールの作成者によって提供されるよう、テーマのリソース ディクショナリ内のキーの定義。  
  
-   テーマ リソースにアクセスするアセンブリから、ときに、コントロール テンプレートを再設定が、コントロールのテーマによって提供されるリソースからのプロパティの値を使用します。  
  
 テーマに由来するコンポーネントのリソースを参照するには、一般にお勧めを使用すること`{DynamicResource}`なく`{StaticResource}`です。 これは、使用法に表示されます。 `{DynamicResource}` ユーザーがそれ自体のテーマを変更できるためお勧めします。 コンポーネント リソース、テーマをサポートするためのコントロールの作成者の目的に最も一致する場合は、動的でもあるコンポーネント リソース参照を有効にする必要があります。  
  
 <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>リソースが実際に定義されているターゲット アセンブリに存在する型を識別します。 A`ComponentResourceKey`定義され、正確に知ることとは無関係に使用できる場所、<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>定義されますが、最終的に参照されたアセンブリから型を解決する必要があります。  
  
 一般的な使用法<xref:System.Windows.ComponentResourceKey>クラスのメンバーとして、公開されているキーを定義することです。 この使用法を使用して、<xref:System.Windows.ComponentResourceKey>クラスのコンス トラクター、マークアップ拡張機能ではありません。 詳細については、次を参照してください。 <xref:System.Windows.ComponentResourceKey>、または、このトピックの"と参照するキーのテーマ リソースの定義"セクション[コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)です。  
  
 属性構文は、一般に使用するキーを確立してを参照するキーを持つリソース、用、`ComponentResourceKey`マークアップ拡張機能です。  
  
 Compact の構文に依存、<xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType>コンス トラクターのシグネチャと、マークアップ拡張機能の位置指定パラメーターの使用法。 順序、`targetTypeName`と`targetID`が指定されたことが重要です。 冗語構文に依存、<xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType>既定のコンス トラクターとし、セット、<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>と<xref:System.Windows.ComponentResourceKey.ResourceId%2A>ことが、オブジェクト要素の場合は true。 属性の構文に似ています。 詳細な構文では、プロパティが設定されている順序は重要ではありません。 リレーションシップとこれら 2 つの選択肢 (compact と詳細な) メカニズムが詳しく説明のトピックで[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)です。  
  
 値では技術的には、`targetID`任意のオブジェクト、文字列であることがないです。 WPF で最も一般的な使用法が位置を揃える、`targetID`値、文字列であるし、このような文字列はで有効な形式を[XamlName の文法](../../../../docs/framework/xaml-services/xamlname-grammar.md)です。  
  
 `ComponentResourceKey` オブジェクトの要素の構文で使用できます。 この場合、両方の値を指定する、<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>と<xref:System.Windows.ComponentResourceKey.ResourceId%2A>プロパティは、拡張機能を正しく初期化するために必要です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]リーダー実装では、このマークアップ拡張機能の処理はによって定義された、<xref:System.Windows.ComponentResourceKey>クラスです。  
  
 `ComponentResourceKey` はマークアップ拡張機能です。 一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。 すべてのマークアップ拡張機能で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用して、{、}、規則は、それぞれの属性構文内の文字、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサは、マークアップ拡張機能が、属性を処理する必要がありますを認識します。 詳細については、次を参照してください。[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.ComponentResourceKey>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
