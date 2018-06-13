---
title: x:Reference のマークアップ拡張機能
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: 960f5c0e4192df72090c1a571dfc2fc5e3fd8ba3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562246"
---
# <a name="xreference-markup-extension"></a>x:Reference のマークアップ拡張機能
XAML マークアップの他の場所で宣言されているインスタンスを参照します。 要素の参照を参照`x:Name`です。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<object property="{x:Reference instancexName}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>XAML オブジェクト要素の使用方法  
  
```xaml  
<object>  
  <object.property>  
    <x:Reference Name="instancexName"/>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`instancexName`|`x:Name`値 (またはの値、 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-プロパティを識別) の参照先のインスタンス。|  
  
## <a name="remarks"></a>コメント  
 `x:Reference` WPF などの特定のフレームワークで実装された場合は要素の参照の概念の XAML 言語レベルのサポートを提供します。  
  
## <a name="xreference-and-wpf"></a>X:reference と WPF  
 WPF XAML 2006 では、要素の参照は、フレームワーク レベルの機能のによってアドレス指定<xref:System.Windows.Data.Binding.ElementName%2A>バインドします。 ほとんどの WPF アプリケーションおよびシナリオ、<xref:System.Windows.Data.Binding.ElementName%2A>バインディングを引き続き使用します。 この一般的なガイダンスの例外は、データ コンテキストまたは不可能な場合のデータ バインディングを構成するスコープの他の考慮事項があるおよびマークアップのコンパイルが関係していない、ケースにすることがあります。  
  
 `x:Reference` XAML 2009 では、コンス トラクターが定義されます。 WPF では XAML 2009 の機能を使用できますが、WPF マークアップ コンパイルされていない XAML に限定されます。 マークアップ コンパイルされた XAML、および XAML の BAML 形式は、現在、XAML 2009 言語のキーワードと機能をサポートしていません。
