---
title: "XML Value Property (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.XmlPropertyExtensionValue"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Value property [Visual Basic]"
  - "Visual Basic code, accessing XML"
  - "XML axis [Visual Basic], Value"
  - "XML Value property [Visual Basic]"
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# XML Value Property (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

<xref:System.Xml.Linq.XElement> オブジェクトのコレクションの最初の要素の値へのアクセスを提供します。  
  
## 構文  
  
```  
  
object.Value  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`object`|必ず指定します。  <xref:System.Xml.Linq.XElement> オブジェクトのコレクションです。|  
  
## 戻り値  
 コレクションの最初の要素の値を含む `String`。コレクションが空の場合は `Nothing` です。  
  
## 解説  
 <xref:System.Xml.Linq.XElement.Value%2A> プロパティを使用すると、<xref:System.Xml.Linq.XElement> オブジェクトのコレクションの最初の要素の値に簡単にアクセスできます。  このプロパティは、コレクションに少なくとも 1 つのオブジェクトが含まれているかどうかを最初にチェックします。  コレクションが空の場合、このプロパティは `Nothing` を返します。  それ以外の場合、このプロパティは、コレクションの最初の要素の <xref:System.Xml.Linq.XElement.Value%2A> プロパティの値を返します。  
  
> [!NOTE]
>  '@' 識別子を使用してXML 属性の値にアクセスすると、属性値は `String` として返され、<xref:System.Xml.Linq.XAttribute.Value%2A> プロパティを明示的に指定する必要はありません。  
  
 コレクションの他の要素にアクセスするには、XML 拡張インデクサー プロパティを使用できます。  詳細については、「[Extension Indexer Property](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)」を参照してください。  
  
## 継承  
 ほとんどのユーザーは <xref:System.Collections.Generic.IEnumerable%601> を実装する必要がないので、このセクションは無視してもかまいません。  
  
 <xref:System.Xml.Linq.XElement.Value%2A> プロパティは、`IEnumerable(Of XElement)` を実装する型の拡張プロパティです。  この拡張プロパティのバインディングは、拡張メソッドのバインディングに似ています。型がいずれかのインターフェイスを実装し、"Value" という名前のプロパティを定義した場合、そのプロパティが拡張プロパティに優先します。  つまり、この <xref:System.Xml.Linq.XElement.Value%2A> プロパティは、`IEnumerable(Of XElement)` を実装するクラスに新しいプロパティを定義することによってオーバーライドできます。  
  
## 使用例  
 次の例は、<xref:System.Xml.Linq.XElement.Value%2A> プロパティを使用して <xref:System.Xml.Linq.XElement> オブジェクトのコレクションの最初のノードにアクセスする方法を示しています。  この例では、子軸プロパティを使用して、`contact` オブジェクトの中の `phone` という名前のすべての子ノードのコレクションを取得します。  
  
 [!code-vb[VbXMLSamples#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_1.vb)]  
  
 このコードは、次のテキストを表示します。  
  
 `Phone number: 206-555-0144`  
  
## 使用例  
 次の例は、<xref:System.Xml.Linq.XAttribute> オブジェクトのコレクションから XML 属性の値を取得する方法を示しています。  この例では、属性軸プロパティを使用して、すべての `phone` 要素の `type` 属性の値を表示します。  
  
 [!code-vb[VbXMLSamples#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_2.vb)]  
  
 このコードは、次のテキストを表示します。  
  
 `home`  
  
 `work`  
  
## 参照  
 <xref:System.Xml.Linq.XElement>   
 <xref:System.Collections.Generic.IEnumerable%601>   
 [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [拡張メソッド](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)   
 [Extension Indexer Property](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)   
 [XML Child Axis Property](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)   
 [XML Attribute Axis Property](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)