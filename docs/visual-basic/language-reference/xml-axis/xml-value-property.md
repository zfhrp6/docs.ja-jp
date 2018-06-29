---
title: XML Value プロパティ (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
ms.openlocfilehash: 927158f940d9b96cd06873c7d3e710be91b887e9
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2018
ms.locfileid: "37071619"
---
# <a name="xml-value-property-visual-basic"></a>XML Value プロパティ (Visual Basic)
コレクションの最初の要素の値にアクセスできるように<xref:System.Xml.Linq.XElement>オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
object.Value  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`object`|必須。 <xref:System.Xml.Linq.XElement> オブジェクトのコレクション。|  
  
## <a name="return-value"></a>戻り値  
 A `String` 、コレクションの最初の要素の値を格納しているか、`Nothing`コレクションが空の場合。  
  
## <a name="remarks"></a>Remarks  
 <xref:System.Xml.Linq.XElement.Value%2A>プロパティでは、最初の要素のコレクション内の値にアクセスする簡単な<xref:System.Xml.Linq.XElement>オブジェクト。 まず、このプロパティは、コレクションに少なくとも 1 つのオブジェクトが含まれているかどうかを確認します。 このプロパティを返しますのかどうか、コレクションが空、`Nothing`です。 このプロパティがの値を返しますそれ以外の場合、<xref:System.Xml.Linq.XElement.Value%2A>コレクションの最初の要素のプロパティです。  
  
> [!NOTE]
>  使用して XML 属性の値にアクセスするときに、'\@' 識別子、属性が返される値として、`String`を明示的に指定する必要はありませんし、<xref:System.Xml.Linq.XAttribute.Value%2A>プロパティです。  
  
 コレクション内の他の要素にアクセスするには、XML 拡張インデクサー プロパティを使用することができます。 詳細については、次を参照してください。[拡張インデクサー プロパティ](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)です。  
  
## <a name="inheritance"></a>継承  
 ほとんどのユーザーが実装する必要はありません<xref:System.Collections.Generic.IEnumerable%601>、およびそのためこのセクションを無視することができます。  
  
 <xref:System.Xml.Linq.XElement.Value%2A>拡張機能を実装する型のプロパティは、`IEnumerable(Of XElement)`です。 拡張メソッドのバインディングと同様には、この拡張機能プロパティのバインディング: 型、インターフェイスの 1 つを実装して"Value"という名前を持つプロパティが定義されて、そのプロパティが優先順位、拡張機能のプロパティです。 つまり、この<xref:System.Xml.Linq.XElement.Value%2A>プロパティを実装するクラスの新しいプロパティを定義することによりオーバーライドできます`IEnumerable(Of XElement)`です。  
  
## <a name="example"></a>例  
 次の例を使用する方法を示しています、<xref:System.Xml.Linq.XElement.Value%2A>プロパティのコレクションの最初のノードへのアクセスを<xref:System.Xml.Linq.XElement>オブジェクト。 例では、すべての子ノードがという名前のコレクションを取得する子軸プロパティを使用して`phone`内にある、`contact`オブジェクト。  
  
 [!code-vb[VbXMLSamples#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_1.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a>例  
 次の例は、のコレクションから、XML 属性の値を取得する方法を示しています。<xref:System.Xml.Linq.XAttribute>オブジェクト。 この例の値を表示する属性軸プロパティを使用して、`type`のすべての属性、`phone`要素。  
  
 [!code-vb[VbXMLSamples#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_2.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XElement>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Visual Basic での XML の作成](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [拡張メソッド](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [拡張インデクサー プロパティ](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)  
 [XML 子軸プロパティ](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [XML 属性軸プロパティ](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
