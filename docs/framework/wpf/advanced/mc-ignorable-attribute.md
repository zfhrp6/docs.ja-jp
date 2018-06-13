---
title: mc:Ignorable 属性
ms.date: 03/30/2017
helpviewer_keywords:
- mc XML namespace prefix [WPF]
- mc:Ignorable attribute
- XML [WPF], mc namespace prefix
- XAML [WPF], mc:Ignorable attribute
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: acd9a6ef-b7ca-4146-abb6-60f3b366e9ec
ms.openlocfilehash: 7b8a2ef6e27bc6b25776157e59bef04b883fcb1a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546199"
---
# <a name="mcignorable-attribute"></a>mc:Ignorable 属性
指定する[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]がマークアップ ファイルで発生した名前空間プレフィックスを無視する場合があります、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサ。 `mc:Ignorable`属性は、カスタム名前空間のマッピングとのマークアップの互換性をサポートしている[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]バージョン管理します。  
  
## <a name="xaml-attribute-usage-single-prefix"></a>XAML 属性の使用方法 (1 つのプレフィックス)  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a>XAML 属性の使用方法 (2 つのプレフィックス)  
  
```  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|*ignorablePrefix、ignorablePrefix1 などです。*|有効なプレフィックス、任意の文字列、XML 1.0 仕様に準拠します。|  
|*ignorableUri*|XML 1.0 仕様あたり、名前空間を指定する有効な URI です。|  
|*ThisElementCanBeIgnored*|要素が無視することができる[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]プロセッサの実装、基になる型は解決できない場合。|  
  
## <a name="remarks"></a>コメント  
 `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]名前空間プレフィックスは、マッピング時に使用する、推奨されるプレフィックス規則、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]互換性名前空間[!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)]です。  
  
 要素または属性として、要素名のプレフィックスの部分を識別する、`mc:Ignorable`によって処理されるときにエラーを生成しませんが、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサ。 その属性を基になる型またはプログラミング構成要素を解決できませんでした、その要素は無視されます。 ただし、無視された要素が処理されていないその要素の副作用は、追加の要素の要件の追加の解析エラーを生成する可能性がありますも。 たとえば、特定の要素のコンテンツ モデル可能性がありますが必要なときに指定された子要素が 1 つの子要素、`mc:Ignorable`プレフィックス、および指定した子要素を型に解決できませんでした、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサ可能性がありますエラーが発生します。  
  
 `mc:Ignorable` 識別子の文字列に名前空間のマッピングにのみ適用されます。 `mc:Ignorable` 名前空間のマッピングに指定のアセンブリには適用されません、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]名前空間とアセンブリ (または、現在の実行可能ファイル、アセンブリと既定)。  
  
 実装する場合、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサ、プロセッサの実装する必要がありますいないを発生させる解析または任意の要素またはとして識別されるプレフィックスで修飾された属性の型解決についてのエラーを処理`mc:Ignorable`です。 プロセッサの実装の読み込みまたは前に示した例では、1 つの子要素などの処理に失敗している、要素のセカンダリの結果は、例外が発生することができます。  
  
 既定では、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサ無視された要素内のコンテンツは無視されます。 ただし、追加の属性を指定できます[mc:ProcessContent 属性](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md)、無視された要素を次の使用可能な親要素内のコンテンツの継続的な処理を要求するようにします。  
  
 たとえば、区切り記号として 1 つ以上の空白文字を使用して、属性に複数のプレフィックスを指定できます:`mc:Ignorable="ignore1 ignore2"`です。  
  
 [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)]名前空間は、他の要素とのこの領域に記載されていない属性を定義、[!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)]です。 詳細については、次を参照してください。 [XML マークアップ互換性仕様](http://go.microsoft.com/fwlink/?LinkId=73824)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Markup.XamlReader>  
 [PresentationOptions:Freeze 属性](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)  
 [XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
