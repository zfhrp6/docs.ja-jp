---
title: x:XData 組み込み XAML 型
ms.date: 03/30/2017
f1_keywords:
- x:XData
- XData
- xXData
helpviewer_keywords:
- XAML [XAML Services], x:XData directive element
- XData in XAML [XAML Services]
- x:XData XAML directive element [XAML Services]
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
ms.openlocfilehash: 3a16379fd6104342529723bf6d0bc9fb4762cf92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565364"
---
# <a name="xxdata-intrinsic-xaml-type"></a>x:XData 組み込み XAML 型
XAML の運用環境での XML データ アイランドの配置を有効にします。 内の XML 要素`x:XData`機能を実行する既定の XAML 名前空間の一部、またはその他の XAML 名前空間かのように XAML プロセッサで扱うことはできません。 `x:XData` 整形式の任意の XML を含めることができます。  
  
## <a name="xaml-object-element-usage"></a>XAML オブジェクト要素の使用方法  
  
```  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`elementDataRoot`|囲まれたデータ アイランドの単一のルート要素です。 ほとんどの最終的なコンシューマーの単一のルートがない XML が無効と見なされます。 具体的には、単一のルートは、必要な場合、`x:XData`では、XML データ ソースの WPF または他の多くのテクノロジにも、XML ソース データ バインディングを使用します。|  
|`[elementData]`|任意。 XML データを表す XML です。 要素のデータとして格納できる要素の任意の数と、入れ子になった要素は、他の要素に含まれていることができます。ただし、XML の一般的な規則が適用されます。|  
  
## <a name="remarks"></a>コメント  
 内の XML 要素、`x:XData`オブジェクトには、すべての可能な名前空間およびプレフィックス内でデータを含む XMLDOM の再を宣言できます。  
  
 XML データにプログラムでアクセスし、`x:XData`組み込み XAML 型を .NET Framework XAML サービスでは、<xref:System.Windows.Markup.XData>クラスです。  
  
## <a name="wpf-usage-notes"></a>WPF の使用上の注意  
 `x:XData`オブジェクトは、主の子オブジェクトとして使用、 <xref:System.Windows.Data.XmlDataProvider>、または別の方法としての子オブジェクトとして、<xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType>プロパティ (XAML では、これは通常構文で表されるプロパティ要素)。  
  
 データは、新しい既定の XML 名前空間 (空の文字列に設定) にデータ アイランド内のベースの XML 名前空間を再定義しなければなりません通常します。 これは、単純なデータ諸島ための最も簡単な<xref:System.Windows.Data.Binding.XPath%2A>参照およびデータにバインドするために使用する式は、プレフィックスを含めることを避けることができます。 複雑なデータ アイランドは、データの複数のプレフィックスを定義して、ルートにある XML 名前空間の特定のプレフィックスを使用して可能性があります。 この場合、すべて<xref:System.Windows.Data.Binding.XPath%2A>式の参照は、適切な名前空間マッピング プレフィックスを含める必要があります。 詳しくは、「 [データ バインディングの概要](../../../docs/framework/wpf/data/data-binding-overview.md)」をご覧ください。  
  
 技術的には、`x:XData`型のプロパティの内容として使用できる<xref:System.Xml.Serialization.IXmlSerializable>です。 ただし、<xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType>のみ著名な実装です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Data.XmlDataProvider>  
 [データ バインディングの概要](../../../docs/framework/wpf/data/data-binding-overview.md)  
 [バインドのマークアップ拡張機能](../../../docs/framework/wpf/advanced/binding-markup-extension.md)
