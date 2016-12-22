---
title: "XML Descendant Axis Property (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.XmlPropertyDescendantsAxis"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, accessing XML"
  - "XML descendant axis property [Visual Basic]"
  - "descendant axis property [Visual Baisc]"
  - "XML axis [Visual Basic], descendant"
  - "XML [Visual Basic], accessing"
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML Descendant Axis Property (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

<xref:System.Xml.Linq.XElement> オブジェクト、<xref:System.Xml.Linq.XDocument> オブジェクト、<xref:System.Xml.Linq.XElement> オブジェクトのコレクション、または <xref:System.Xml.Linq.XDocument> オブジェクトのコレクションの子孫へのアクセスを提供します。  
  
## 構文  
  
```  
  
object...<descendant>  
```  
  
## 指定項目  
 `object`  
 必ず指定します。  <xref:System.Xml.Linq.XElement> オブジェクト、<xref:System.Xml.Linq.XDocument> オブジェクト、<xref:System.Xml.Linq.XElement> オブジェクトのコレクション、または <xref:System.Xml.Linq.XDocument> オブジェクトのコレクションです。  
  
 ...\<  
 必ず指定します。  子孫軸プロパティの開始を示します。  
  
 `descendant`  
 必ず指定します。  アクセスする子孫ノードの名前です。\[`prefix``:`\]`name` の形式で指定します。  
  
|指定項目|Description|  
|----------|-----------------|  
|`prefix`|省略可能です。  子孫ノードの XML 名前空間プレフィックスです。  `Imports` ステートメントを使用して定義されているグローバル XML 名前空間を指定する必要があります。|  
|`name`|必ず指定します。  子孫ノードのローカル名です。  「[Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)」を参照してください。|  
  
 \>  
 必ず指定します。  子孫軸プロパティの終了を示します。  
  
## 戻り値  
 <xref:System.Xml.Linq.XElement> オブジェクトのコレクション。  
  
## 解説  
 XML 子孫軸プロパティを使用すると、<xref:System.Xml.Linq.XElement> オブジェクト、<xref:System.Xml.Linq.XDocument> オブジェクト、<xref:System.Xml.Linq.XElement> オブジェクトのコレクション、または <xref:System.Xml.Linq.XDocument> オブジェクトのコレクションの子孫ノードに、名前でアクセスできます。  返されるコレクションの最初の子孫ノードの値にアクセスするには、XML の `Value` プロパティを使用します。  詳細については、「[XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)」を参照してください。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] コンパイラは、子孫軸プロパティを <xref:System.Xml.Linq.XContainer.Descendants%2A> メソッドの呼び出しに変換します。  
  
## XML 名前空間  
 子孫軸プロパティの名前では、`Imports` ステートメントでグローバルに宣言されている XML 名前空間のみを使用できます。  XML 要素リテラル内でローカルに宣言されている XML 名前空間は使用できません。  詳細については、「[Imports Statement \(XML Namespace\)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)」を参照してください。  
  
## 使用例  
 次の例では、`contacts` オブジェクトの、`name` という名前の最初の子孫ノードの値、および `phone` という名前のすべての子孫ノードの値にアクセスする方法を示します。  
  
 [!CODE [VbXMLSamples#25](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#25)]  
  
 このコードは、次のテキストを表示します。  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## 使用例  
 次の例では、`ns` を XML 名前空間プレフィックスとして宣言します。  その後、この名前空間のプレフィックスを使用して XML リテラルを作成し、修飾名 `ns:name` を持つ最初の子ノードの値にアクセスします。  
  
 [!CODE [VbXMLSamples#26](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#26)]  
  
 このコードは、次のテキストを表示します。  
  
 `Name: Patrick Hines`  
  
## 参照  
 <xref:System.Xml.Linq.XElement>   
 [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)