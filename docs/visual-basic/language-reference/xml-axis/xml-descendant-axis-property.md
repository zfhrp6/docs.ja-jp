---
title: "XML 子孫軸プロパティ (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyDescendantsAxis
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Baisc]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 434dc90c643381bdc27b2da54a7418e39bf15e98
ms.lasthandoff: 03/13/2017

---
# <a name="xml-descendant-axis-property-visual-basic"></a>XML 子孫軸プロパティ (Visual Basic)
次の子孫へのアクセスを提供:<xref:System.Xml.Linq.XElement>オブジェクト、 <xref:System.Xml.Linq.XDocument>、オブジェクトのコレクション<xref:System.Xml.Linq.XElement>オブジェクト、または一連の<xref:System.Xml.Linq.XDocument>オブジェクト</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>。  
  
## <a name="syntax"></a>構文  
  
```  
  
object...<descendant>  
```  
  
## <a name="parts"></a>指定項目  
 `object`  
 必須です。 <xref:System.Xml.Linq.XElement>オブジェクト、<xref:System.Xml.Linq.XDocument>オブジェクト、一連の<xref:System.Xml.Linq.XElement>オブジェクト、または一連の<xref:System.Xml.Linq.XDocument>オブジェクト</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>。  
  
 ...<  
 必ず指定します。 子孫軸プロパティの開始を示します。  
  
 `descendant`  
 必須です。 アクセスして、フォームの子孫ノードの名前 [`prefix``:`]`name`します。  
  
|パーツ|説明|  
|----------|-----------------|  
|`prefix`|省略可能です。 子孫ノードの XML 名前空間プレフィックス。 グローバル XML 名前空間を使用して定義されている必要があります、`Imports`ステートメントです。|  
|`name`|必須です。 子孫ノードのローカル名。 参照してください[宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)します。|  
  
 \>  
 必須です。 子孫軸プロパティの終了を示します。  
  
## <a name="return-value"></a>戻り値  
 コレクション<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement>。  
  
## <a name="remarks"></a>コメント  
 XML 子孫軸プロパティを使用するには名を使用して子孫ノードにアクセスする、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>オブジェクトのコレクションから、または<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>オブジェクト</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>。 XML を使用して`Value`返されるコレクション内の最初の子孫ノードの値にアクセスするプロパティです。 詳細については、次を参照してください。 [XML Value プロパティ](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)します。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラでは、子孫軸プロパティを変換への呼び出しに、<xref:System.Xml.Linq.XContainer.Descendants%2A>メソッド</xref:System.Xml.Linq.XContainer.Descendants%2A>。  
  
## <a name="xml-namespaces"></a>XML 名前空間  
 子孫軸プロパティの名前でグローバルに宣言された XML 名前空間だけを使用できます、`Imports`ステートメントです。 XML 要素リテラル内にローカルに宣言されている XML 名前空間は使用できません。 詳細については、次を参照してください。 [Imports ステートメント (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)します。  
  
## <a name="example"></a>例  
 次の例は、という名前の最初の子孫ノードの値にアクセスする方法を示しています。`name`という名前のすべての子孫ノードの値と`phone`から、`contacts`オブジェクトです。  
  
 [!code-vb[VbXMLSamples&#25;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>例  
 次の例では、`ns` を名前空間プレフィックスとして宣言します。 使用して、名前空間のプレフィックスを XML リテラルを作成し、修飾名を持つ最初の子ノードの値にアクセス`ns:name`します。  
  
 [!code-vb[VbXMLSamples #&26;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XElement>   
 [XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Visual Basic で XML を作成します。](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
