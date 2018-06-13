---
title: x:Shared 属性
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: bee37735382249d2919ef870ca495e6096532352
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563798"
---
# <a name="xshared-attribute"></a>x:Shared 属性
設定すると`false`、WPF リソース検索の動作を変更して、属性付きのリソースに対して要求が、同じインスタンスのすべての要求を共有することがなく各要求の新しいインスタンスを作成できるようにします。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a>コメント  
 `x:Shared` XAML 言語の XAML 名前空間にマップされは、.NET Framework XAML サービスおよびその XAML リーダーによって、有効な XAML 言語要素として認識します。 ただし、示された機能`x:Shared`WPF アプリケーションと WPF XAML パーサーは、関連するだけです。 WPF では、`x:Shared`は WPF 内に存在するオブジェクトに適用された場合のみ、属性として使用<xref:System.Windows.ResourceDictionary>です。 他の使用法は解析例外やその他のエラーをスローしませんが、効果はありません。  
  
 意味`x:Shared`XAML 言語仕様で指定されていません。 .NET Framework XAML サービスに基づいて構築されるなど、他の XAML 実装は、必ずしもリソース共有のサポートを提供しません。 このような XAML 実装でも使用されているサポート framework で同様の動作を提供できます`x:Shared`値。  
  
 WPF では、既定値`x:Shared`リソースに対する`true`です。 この条件は、任意の特定のリソース要求が同じインスタンスを常を返すことを意味します。  
  
 など、API、リソースを使用して返されるオブジェクトを変更した<xref:System.Windows.FrameworkElement.FindResource%2A>、内で直接オブジェクトを変更するか、 <xref:System.Windows.ResourceDictionary>、元のリソースを変更します。 そのリソースへの参照が動的リソース参照と、そのリソースの消費者は、変更されたリソースを取得します。  
  
 リソースへの参照が、静的リソース参照、に対する変更により、リソース[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]処理時間は、関係ありません。 動的リソース参照と静的の詳細については、次を参照してください。 [XAML リソース](../../../docs/framework/wpf/advanced/xaml-resources.md)です。  
  
 明示的に指定する`x:Shared="true"`はあまり一般的には、既定ではないためです。 直接コードに相当`x:Shared`WPF でオブジェクト モデルこれは、XAML の使用方法を指定するだけ処理する必要が既定の WPF 動作するか、読み込みパスでの中間の XAML ノード ストリームで .NET Framework XAML Se を使用して処理する場合。ターゲット、およびその XAML リーダー。  
  
 シナリオ`x:Shared="false"`定義するかどうかは、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>リソースとしてのクラスを派生し、コンテンツ モデルに要素のリソースを導入します。 `x:Shared="false"` 複数回、同じコレクションに導入する、要素のリソースを有効に (など、 <xref:System.Windows.Controls.UIElementCollection>)。 せず`x:Shared="false"`これは無効なコレクションには、その内容の一意性が強制されるためです。 ただし、`x:Shared="false"`動作は同じインスタンスを返す代わりに、リソースの別の同一インスタンスを作成します。  
  
 別のシナリオとして`x:Shared="false"`を使用するかどうか、<xref:System.Windows.Freezable>アニメーション値がアニメーションあたりごとにリソースを変更するリソース。  
  
 文字列の処理`false`大文字小文字は区別されません。  
  
 WPF では、`x:Shared`のみ、次の条件下で有効です。  
  
-   <xref:System.Windows.ResourceDictionary>で項目を含む`x:Shared`コンパイルする必要があります。 <xref:System.Windows.ResourceDictionary> Loose XAML 内にすることはできませんまたはテーマを使用します。  
  
-   <xref:System.Windows.ResourceDictionary> 、項目を含む他の中で入れ子にする必要がありますいない<xref:System.Windows.ResourceDictionary>です。 たとえば、使用することはできません`x:Shared`内のアイテム、<xref:System.Windows.ResourceDictionary>内にある、<xref:System.Windows.Style>にではない、<xref:System.Windows.ResourceDictionary>項目。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.ResourceDictionary>  
 [XAML リソース](../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [基本要素](../../../docs/framework/wpf/advanced/base-elements.md)
