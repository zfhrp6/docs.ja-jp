---
title: XML 子孫軸プロパティ (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyDescendantsAxis
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
ms.openlocfilehash: 0f3c42b5134b058c010ca4c7a5ee7c24627c65fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xml-descendant-axis-property-visual-basic"></a>XML 子孫軸プロパティ (Visual Basic)
次の子孫にアクセスできるように:<xref:System.Xml.Linq.XElement>オブジェクト、<xref:System.Xml.Linq.XDocument>オブジェクト、コレクションの<xref:System.Xml.Linq.XElement>オブジェクト、または一連の<xref:System.Xml.Linq.XDocument>オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
object...<descendant>  
```  
  
## <a name="parts"></a>指定項目  
 `object`  
 必須です。 <xref:System.Xml.Linq.XElement> オブジェクト、<xref:System.Xml.Linq.XDocument> オブジェクト、<xref:System.Xml.Linq.XElement> オブジェクトのコレクション、または <xref:System.Xml.Linq.XDocument> オブジェクトのコレクションです。  
  
 ...<  
 必ず指定します。 子孫軸プロパティの開始を示します。  
  
 `descendant`  
 必須です。 アクセスする場合、フォームの子孫ノードの名前 [`prefix``:`]`name`です。  
  
|パーツ|説明|  
|----------|-----------------|  
|`prefix`|省略可能です。 子孫のノードの XML 名前空間プレフィックス。 使用して定義されているグローバル XML 名前空間にある必要があります、`Imports`ステートメントです。|  
|`name`|必須です。 子孫のノードのローカル名。 参照してください[宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)です。|  
  
 \>  
 必須です。 子孫軸プロパティの終了を示します。  
  
## <a name="return-value"></a>戻り値  
 <xref:System.Xml.Linq.XElement> オブジェクトのコレクション。  
  
## <a name="remarks"></a>コメント  
 名を使用して子孫ノードにアクセスする XML 子孫軸プロパティを使用することができます、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>オブジェクトのコレクションから、または<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>オブジェクト。 XML を使用して`Value`返されるコレクションの最初の子孫ノードの値にアクセスするプロパティです。 詳細については、次を参照してください。 [XML Value プロパティ](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)です。  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]コンパイラでは、descendant 軸のプロパティを変換への呼び出しに、<xref:System.Xml.Linq.XContainer.Descendants%2A>メソッドです。  
  
## <a name="xml-namespaces"></a>XML 名前空間  
 子孫軸プロパティの名前でグローバルに宣言された XML 名前空間のみを使用できます、`Imports`ステートメントです。 XML 要素リテラル内にローカルに宣言されている XML 名前空間は使用できません。 詳細については、次を参照してください。 [Imports ステートメント (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)です。  
  
## <a name="example"></a>例  
 次の例は、という名前の最初の子孫ノードの値にアクセスする方法を示しています。`name`という名前のすべての子孫ノードの値および`phone`から、`contacts`オブジェクト。  
  
 [!code-vb[VbXMLSamples#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>例  
 次の例では、`ns` を名前空間プレフィックスとして宣言します。 XML リテラルを作成し、修飾名を持つ最初の子ノードの値にアクセスする、名前空間のプレフィックスを使用して`ns:name`です。  
  
 [!code-vb[VbXMLSamples#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XElement>  
 [XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Visual Basic での XML の作成](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
