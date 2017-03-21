---
title: "XML 子軸プロパティ (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyChildAxis
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 89a59d00-985e-4f5c-b59f-29b47bad11cb
caps.latest.revision: 18
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 97b92f9e94ad709c4d8ce944577eb23edc84b328
ms.lasthandoff: 03/13/2017

---
# <a name="xml-child-axis-property-visual-basic"></a>XML 子軸プロパティ (Visual Basic)
次のいずれかの子にアクセス:<xref:System.Xml.Linq.XElement>オブジェクト、 <xref:System.Xml.Linq.XDocument>、オブジェクトのコレクション<xref:System.Xml.Linq.XElement>オブジェクト、または一連の<xref:System.Xml.Linq.XDocument>オブジェクト</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.<child>  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`object`|必須です。 <xref:System.Xml.Linq.XElement>オブジェクト、<xref:System.Xml.Linq.XDocument>オブジェクト、一連の<xref:System.Xml.Linq.XElement>オブジェクト、または一連の<xref:System.Xml.Linq.XDocument>オブジェクト</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>。|  
|.<|必ず指定します。 子軸プロパティの開始を示します。|  
|`child`|必須です。 フォームにアクセスする子ノードの名前は [`prefix``:`]`name`します。<br /><br /> -   `Prefix`-省略可能です。 子ノードの XML 名前空間プレフィックスです。 `Imports` ステートメントを使用して定義されているグローバル XML 名前空間を指定する必要があります。<br />-   `Name`必要です。 ローカル子ノードの名前です。 参照してください[宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)します。|  
|>|必須です。 子軸プロパティの終了を示します。|  
  
## <a name="return-value"></a>戻り値  
 コレクション<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement>。  
  
## <a name="remarks"></a>コメント  
 XML 子軸プロパティを子ノードのアクセスに使用するには名を使用して、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>オブジェクトのコレクションから、または<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>オブジェクト</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>。 返されるコレクションの最初の子ノードの値にアクセスするには、XML の `Value` プロパティを使用します。 詳細については、次を参照してください。 [XML Value プロパティ](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)します。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラでは、子軸プロパティを変換への呼び出しが、<xref:System.Xml.Linq.XContainer.Elements%2A>メソッド</xref:System.Xml.Linq.XContainer.Elements%2A>。  
  
## <a name="xml-namespaces"></a>XML 名前空間  
 子軸プロパティの名前では、`Imports` ステートメントでグローバルに宣言されている XML 名前空間プレフィックスのみを使用できます。 XML 要素リテラル内でローカルに宣言されている XML 名前空間プレフィックスは使用できません。 詳細については、次を参照してください。 [Imports ステートメント (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)します。  
  
## <a name="example"></a>例  
 次の例は、`contact` オブジェクトの `phone` という名前の子ノードにアクセスする方法を示しています。  
  
 [!code-vb[VbXMLSamples&17;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_1.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>例  
 次の例は、`contacts` オブジェクトの `contact` 子軸プロパティによって返されたコレクションの、`phone` という名前の子ノードにアクセスする方法を示しています。  
  
 [!code-vb[VbXMLSamples&#18;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_2.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>例  
 次の例では、`ns` を名前空間プレフィックスとして宣言します。 その後、この名前空間のプレフィックスを使用して XML リテラルを作成し、修飾名 `ns:name` を持つ最初の子ノードにアクセスします。  
  
 [!code-vb[VbXMLSamples&#19;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_3.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XElement>   
 [XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Visual Basic で XML を作成します。](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
