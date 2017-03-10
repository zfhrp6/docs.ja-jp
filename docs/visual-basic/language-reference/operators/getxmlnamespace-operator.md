---
title: "GetXmlNamespace Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.GetXmlNamespace"
  - "GetXmlNamespace"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "GetXmlNamespace operator"
  - "GetXmlNamespace keyword"
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# GetXmlNamespace Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

指定した XML 名前空間プレフィックスに対応する <xref:System.Xml.Linq.XNamespace> オブジェクトを取得します。  
  
## 構文  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## 指定項目  
 `xmlNamespacePrefix`  
 省略可能です。  XML 名前空間プレフィックスを示す文字列。  指定する場合、この文字列は有効な XML 識別子である必要があります。  詳細については、「[Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)」を参照してください。  プレフィックスを指定しないと、既定の名前空間が返されます。  既定の名前空間が指定されていない場合は、空の名前空間が返されます。  
  
## 戻り値  
 XML 名前空間プレフィックスに対応する <xref:System.Xml.Linq.XNamespace> オブジェクト。  
  
## 解説  
 `GetXmlNamespace` 演算子は、XML 名前空間プレフィックス `xmlNamespacePrefix` に対応する <xref:System.Xml.Linq.XNamespace> オブジェクトを取得します。  
  
 XML 名前空間プレフィックスは、XML リテラルおよび XML 軸プロパティで直接使用できます。  ただし、コードで使用する前に、`GetXmlNamespace` 演算子を使用して名前空間プレフィックスを <xref:System.Xml.Linq.XNamespace> オブジェクトに変換する必要があります。  非修飾要素名を <xref:System.Xml.Linq.XNamespace> オブジェクトに追加することで、完全修飾された <xref:System.Xml.Linq.XName> オブジェクトを取得できます。[!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] の多くのメソッドでは、このオブジェクトが必要です。  
  
## 使用例  
 次の例では、`ns` を XML 名前空間プレフィックスとしてインポートします。  その後、この名前空間のプレフィックスを使用して XML リテラルを作成し、修飾名 `ns:phone` を持つ最初の子ノードにアクセスします。  次に、この子ノードを `ShowName` サブルーチンに渡します。このサブルーチンは、`GetXmlNamespace` 演算子を使用して修飾名を作成します。  その後、`ShowName` サブルーチンから <xref:System.Xml.Linq.XNode.Ancestors%2A> メソッドに修飾名を渡して、親の `ns:contact` ノードを取得します。  
  
 [!code-vb[VbXMLSamples#38](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/getxmlnamespace-operator_1.vb)]  
  
 `TestGetXmlNamespace.RunSample()` を呼び出すと、次のテキストを含むメッセージ ボックスが表示されます。  
  
 `Name: Patrick Hines`  
  
## 参照  
 [Imports Statement \(XML Namespace\)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [Accessing XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)