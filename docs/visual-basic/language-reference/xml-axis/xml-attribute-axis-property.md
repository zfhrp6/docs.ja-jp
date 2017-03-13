---
title: "XML Attribute Axis Property (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.XmlPropertyAttributeAxis"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "attribute axis property [Visual Basic]"
  - "Visual Basic code, accessing XML"
  - "XML attribute axis property [Visual Basic]"
  - "XML axis [Visual Basic], attribute"
  - "XML [Visual Basic], accessing"
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 23
---
# XML Attribute Axis Property (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

<xref:System.Xml.Linq.XElement> オブジェクトの属性の値、または <xref:System.Xml.Linq.XElement> オブジェクトのコレクション内の最初の要素へのアクセスを提供します。  
  
## 構文  
  
```  
  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## 指定項目  
 `object`  
 必ず指定します。  <xref:System.Xml.Linq.XElement> オブジェクトまたは <xref:System.Xml.Linq.XElement> オブジェクトのコレクション。  
  
 .@  
 必ず指定します。  属性軸プロパティの開始を示します。  
  
 \<  
 省略可能です。  `attribute` が [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の有効な識別子でない場合に、属性の名前の開始を示します。  
  
 `attribute`  
 必ず指定します。  アクセスする属性の名前。名前の書式は \[`prefix`:\]`name` です。  
  
|指定項目|Description|  
|----------|-----------------|  
|`prefix`|省略可能です。  属性の XML 名前空間プレフィックス。  `Imports` ステートメントを使用して定義されているグローバル XML 名前空間を指定する必要があります。|  
|`name`|必ず指定します。  ローカル属性名です。  「[Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)」を参照してください。|  
  
 \>  
 省略可能です。  `attribute` が [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の有効な識別子でない場合に、属性の名前の終了を示します。  
  
## 戻り値  
 `attribute` の値を格納している文字列。  属性の名前が存在しない場合は `Nothing` が返されます。  
  
## 解説  
 XML 属性軸プロパティを使用して、<xref:System.Xml.Linq.XElement> オブジェクトの属性の値に名前でアクセスできます。または、<xref:System.Xml.Linq.XElement> オブジェクトのコレクション内の最初の要素の属性の値にアクセスできます。  属性値は名前で取得できます。または、新しい名前の前に @ 識別子を付けて指定することで、要素に新しい属性を追加できます。  
  
 @ 識別子を使用して XML 属性を参照すると、属性値は文字列として返され、<xref:System.Xml.Linq.XAttribute.Value%2A> プロパティを明示的に指定する必要はありません。  
  
 XML 属性の名前付け規則は、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 識別子の名前付け規則とは異なります。Visual Basic 識別子として有効ではない名前を持つ XML 属性にアクセスするには、名前を山かっこ \(\< と \>\) で囲みます。  
  
## XML 名前空間  
 属性軸プロパティの名前には、`Imports` ステートメントを使用してグローバルに宣言された XML 名前空間プレフィックスだけを使用できます。  XML 要素リテラル内でローカルに宣言されている XML 名前空間プレフィックスは使用できません。  詳細については、「[Imports Statement \(XML Namespace\)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)」を参照してください。  
  
## 使用例  
 次の例は、`type` という名前の XML 属性の値を、`phone` という名前の XML 要素のコレクションから取得する方法を示します。  
  
 [!code-vb[VbXMLSamples#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]  
  
 このコードは、次のテキストを表示します。  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## 使用例  
 次の例は、XML 要素の属性を宣言によって XML の一部として作成する方法と、<xref:System.Xml.Linq.XElement> オブジェクトのインスタンスに属性を追加することによって動的に作成する方法の両方を示しています。  `type` 属性は宣言によって作成され、`owne` 属性は動的に作成されます。  
  
 [!code-vb[VbXMLSamples#44](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]  
  
 このコードは、次のテキストを表示します。  
  
```  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## 使用例  
 次の例では、山かっこを使用した構文によって、`number-type` という名前の XML 属性の値を取得します。この名前は、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の有効な識別子ではありません。  
  
 [!code-vb[VbXMLSamples#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]  
  
 このコードは、次のテキストを表示します。  
  
 `Phone type: work`  
  
## 使用例  
 次の例では、`ns` を XML 名前空間プレフィックスとして宣言します。  その後、この名前空間のプレフィックスを使用して XML リテラルを作成し、修飾名 "`ns:name`" を持つ最初の子ノードにアクセスします。  
  
 [!code-vb[VbXMLSamples#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]  
  
 このコードは、次のテキストを表示します。  
  
 `Phone type: home`  
  
## 参照  
 <xref:System.Xml.Linq.XElement>   
 [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)