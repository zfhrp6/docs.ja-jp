---
title: mc:ProcessContent 属性
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: 2e93734b8ab4aefca080736db3a512f272625271
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545254"
---
# <a name="mcprocesscontent-attribute"></a>mc:ProcessContent 属性
指定する[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]要素必要がありますもコンテンツがある関連する親要素によって処理される場合でも、直接の親要素を無視できます、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサを指定することにより[mc: Ignorable 属性](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md). `mc:ProcessContent`属性は、カスタム名前空間のマッピングとのマークアップの互換性をサポートしている[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]バージョン管理します。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...  
  mc:ProcessContent="ignorablePrefix:ThisElementCanBeIgnored"  
>  
    <ignorablePrefix:ThisElementCanBeIgnored>  
        [content]  
    </ignorablePrefix:ThisElementCanBeIgnored>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|*ignorablePrefix*|有効なプレフィックス、任意の文字列、XML 1.0 仕様に準拠します。|  
|*ignorableUri*|XML 1.0 仕様あたり、名前空間を指定する有効な URI です。|  
|*ThisElementCanBeIgnored*|要素が無視することができる[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]プロセッサの実装、基になる型は解決できない場合。|  
|*[コンテンツ]*|*ThisElementCanBeIgnored*無視とマークされています。 プロセッサが、その要素を無視する場合 *[コンテンツ]* によって処理される*オブジェクト*です。|  
  
## <a name="remarks"></a>コメント  
 既定では、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサ無視された要素内のコンテンツは無視されます。 特定の要素を指定できます`mc:ProcessContent`、および[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサが無視された要素内のコンテンツの処理を続行します。 これは通常される使用、コンテンツがいくつかのタグ、うち少なくとも 1 つが無視できるとうち少なくとも 1 つは無視内で入れ子になった場合。  
  
 たとえば、スペース区切り記号を使用して、属性に複数のプレフィックスを指定できます:`mc:ProcessContent="ignore:Element1 ignore:Element2"`です。  
  
 [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)]名前空間は、他の要素とのこの領域に記載されていない属性を定義、[!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)]です。 詳細については、次を参照してください。 [XML マークアップ互換性仕様](http://go.microsoft.com/fwlink/?LinkId=73824)です。  
  
## <a name="see-also"></a>関連項目  
 [mc:Ignorable 属性](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)  
 [XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
