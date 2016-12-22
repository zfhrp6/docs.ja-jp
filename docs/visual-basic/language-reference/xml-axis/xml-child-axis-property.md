---
title: "XML Child Axis Property (Visual Basic) | Microsoft Docs"
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
  - "vb.XmlPropertyChildAxis"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, accessing XML"
  - "XML axis [Visual Basic], child"
  - "child axis property [Visual Basic]"
  - "XML child axis property [Visual Basic]"
  - "XML [Visual Basic], accessing"
ms.assetid: 89a59d00-985e-4f5c-b59f-29b47bad11cb
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML Child Axis Property (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

<xref:System.Xml.Linq.XElement> オブジェクト、<xref:System.Xml.Linq.XDocument> オブジェクト、<xref:System.Xml.Linq.XElement> オブジェクトのコレクション、または <xref:System.Xml.Linq.XDocument> オブジェクトのコレクションのいずれかの子にアクセスできます。  
  
## 構文  
  
```  
  
object.<child>  
```  
  
## 指定項目  
  
|||  
|-|-|  
|用語|定義|  
|`object`|必須。  <xref:System.Xml.Linq.XElement> オブジェクト、<xref:System.Xml.Linq.XDocument> オブジェクト、<xref:System.Xml.Linq.XElement> オブジェクトのコレクション、または <xref:System.Xml.Linq.XDocument> オブジェクトのコレクションです。|  
|.\<|必ず指定します。  子軸プロパティの開始を示します。|  
|`child`|必須。  アクセスする子ノードの名前です。\[`prefix``:`\]`name` の形式で指定します。<br /><br /> -   `Prefix` \- 省略できます。  子ノードの XML 名前空間プレフィックスです。  `Imports` ステートメントを使用して定義されているグローバル XML 名前空間を指定する必要があります。<br />-   `Name` \- 必須。  ローカル子ノードの名前です。  「[Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)」を参照してください。|  
|\>|必ず指定します。  子軸プロパティの終了を示します。|  
  
## 戻り値  
 <xref:System.Xml.Linq.XElement> オブジェクトのコレクション。  
  
## 解説  
 XML 子軸プロパティを使用すると、<xref:System.Xml.Linq.XElement> オブジェクト、<xref:System.Xml.Linq.XDocument> オブジェクト、<xref:System.Xml.Linq.XElement> オブジェクトのコレクション、または <xref:System.Xml.Linq.XDocument> オブジェクトのコレクションから子ノードに名前でアクセスできます。  返されるコレクションの最初の子ノードの値にアクセスするには、XML の `Value` プロパティを使用します。  詳細については、「[XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)」を参照してください。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] コンパイラは、子軸プロパティを <xref:System.Xml.Linq.XContainer.Elements%2A> メソッドの呼び出しに変換します。  
  
## XML 名前空間  
 子軸プロパティの名前では、`Imports` ステートメントでグローバルに宣言されている XML 名前空間プレフィックスのみを使用できます。  XML 要素リテラル内でローカルに宣言されている XML 名前空間プレフィックスは使用できません。  詳細については、「[Imports Statement \(XML Namespace\)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)」を参照してください。  
  
## 使用例  
 次の例は、`contact` オブジェクトの `phone` という名前の子ノードにアクセスする方法を示しています。  
  
 [!CODE [VbXMLSamples#17](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#17)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Home Phone = 206-555-0144`  
  
## 使用例  
 次の例は、`contacts` オブジェクトの `contact` 子軸プロパティによって返されたコレクションの、`phone` という名前の子ノードにアクセスする方法を示しています。  
  
 [!CODE [VbXMLSamples#18](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#18)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Home Phone = 206-555-0144`  
  
## 使用例  
 次の例では、`ns` を名前空間プレフィックスとして宣言します。  その後、この名前空間のプレフィックスを使用して XML リテラルを作成し、修飾名 `ns:name` を持つ最初の子ノードにアクセスします。  
  
 [!CODE [VbXMLSamples#19](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#19)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Patrick Hines`  
  
## 参照  
 <xref:System.Xml.Linq.XElement>   
 [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)