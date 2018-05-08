---
title: x:Uid ディレクティブ
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
ms.openlocfilehash: 667b722097d091902cb65f2e6f0485a039f8a2ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="xuid-directive"></a>x:Uid ディレクティブ
マークアップ要素の一意の識別子を提供します。 多くのシナリオでは、この一意の識別子を XAML ローカリゼーション プロセスやツールによって使用されます。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<object x:Uid="identifier"... />  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`identifier`|手動で作成されたまたは自動生成された文字列を指定する必要がありますで一意であるファイルによってが解釈されるときに、`x:Uid`コンシューマー。|  
  
## <a name="remarks"></a>コメント  
 [MS-XAML] の`x:Uid`ディレクティブとして定義されます。 詳細については、次を参照してください。 [ \[MS-XAML\]セクション 5.3.6](http://go.microsoft.com/fwlink/?LinkId=114525)です。  
  
 `x:Uid` 不連続`x:Name`両方に説明した XAML ローカリゼーション シナリオのためおよびローカライズに使用される識別子のプログラミング モデルへの影響の依存関係があるないように`x:Name`です。 また、 `x:Name` XAML 名前スコープの; によって拘束されますただし、`x:Uid`一意性の強制の XAML 定義されている言語概念によって制御されていません。 広い意味 (ローカリゼーション プロセスの一部ではないプロセッサ) での XAML プロセッサは、の一意性を適用するのには必要ありません`x:Uid`値。 その責任は元の値には、概念的にです。 一意性の期待値`x:Uid`1 つの XAML ソース内の値が不適切な専用のグローバル化のプロセスやツールなどの値のコンシューマーです。 一般的な一意性モデルは`x:Uid`値は、XAML を表す XML でエンコードされたファイル内で一意です。  
  
 適用する特定の XAML スキーマの大幅な知識があるツールを選択できます`x:Uid`のみのすべてのケースのマークアップでテキスト文字列値が検出された場所の代わりに、ローカライズ可能な文字列を true です。  
  
 フレームワークは、のエイリアスである場合は、そのオブジェクト モデルで特定のプロパティを指定できます`x:Uid`属性を適用することによって<xref:System.Windows.Markup.UidPropertyAttribute>を定義する型。 フレームワークは、特定のプロパティを指定する場合は両方とも指定する有効な`x:Uid`と同じオブジェクトのエイリアスのメンバーです。 両方`x:Uid`とエイリアスのメンバーが指定されると、通常、.NET Framework XAML サービス API をスロー<xref:System.Xaml.XamlDuplicateMemberException>この場合にします。  
  
## <a name="wpf-usage-notes"></a>WPF の使用上の注意  
 役割の詳細については`x:Uid`WPF ローカリゼーション処理および XAML の BAML 形式では、「 [WPF のグローバリゼーション](../../../docs/framework/wpf/advanced/globalization-for-wpf.md)または <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
 <xref:Microsoft.Build.Tasks.Windows.UidManager>  
 [WPF のグローバリゼーション](../../../docs/framework/wpf/advanced/globalization-for-wpf.md)
