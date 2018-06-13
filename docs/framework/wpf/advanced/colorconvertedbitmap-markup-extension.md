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
# <a name="colorconvertedbitmap-markup-extension"></a>ColorConvertedBitmap のマークアップ拡張機能
埋め込みのプロファイルがないビットマップ ソースを指定する方法を提供します。 カラー コンテキスト プロファイルが指定/[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]がイメージ ソースとして、[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]です。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" .../>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`imageSource`|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]のプロファイルになっていないビットマップ。|  
|`sourceIIC`|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]のソース プロファイルの構成。|  
|`destinationIIC`|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の移行先のプロファイルの構成|  
  
## <a name="remarks"></a>コメント  
 このマークアップ拡張機能など、関連する一連の画像ソース プロパティの値を入力するためのものが<xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>です。  
  
 属性構文は、このマークアップ拡張機能で使用される最も一般的な構文です。 `ColorConvertedBitmap` (または`ColorConvertedBitmapExtension`) 値のみ設定できます値として文字列は、最初のコンス トラクターのために、プロパティ要素構文で使用することはできません次の拡張機能の識別子。  
  
 `ColorConvertedBitmap` はマークアップ拡張機能です。 一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。 すべてのマークアップ拡張機能で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用して、{、}、規則は、それぞれの属性構文内の文字、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサは、マークアップ拡張機能が、属性を処理する必要がありますを認識します。 詳細については、次を参照してください。[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>  
 [マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [イメージングの概要](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
