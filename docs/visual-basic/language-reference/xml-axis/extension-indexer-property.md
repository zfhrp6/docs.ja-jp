---
title: "Extension Indexer Property (Visual Basic) | Microsoft Docs"
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
  - "vb.XmlPropertyExtensionIndexer"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, accessing XML"
  - "XML extension indexer [Visual Basic]"
  - "extension indexer [Visual Basic]"
  - "XML [Visual Basic], accessing"
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Extension Indexer Property (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

コレクション内の個別の要素へのアクセスを提供します。  
  
## 構文  
  
```  
  
object(index)  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`object`|必ず指定します。  クエリ可能なコレクションです。  つまり、<xref:System.Collections.Generic.IEnumerable%601> または <xref:System.Linq.IQueryable%601> を実装するコレクションです。|  
|\(|必ず指定します。  インデクサー プロパティの開始を示します。|  
|`index`|必ず指定します。  コレクションの要素の 0 から始まる位置を指定する整数式です。|  
|\)|必ず指定します。  インデクサー プロパティの終了を示します。|  
  
## 戻り値  
 コレクション内の指定した位置にあるオブジェクト、またはインデックスが範囲外の場合は `Nothing`。  
  
## 解説  
 拡張インデクサー プロパティを使用すると、コレクションの個別の要素にアクセスできます。  このインデクサー プロパティは、通常、XML 軸プロパティの出力に対して使用します。  XML 子軸プロパティおよび XML 子孫軸プロパティは、<xref:System.Xml.Linq.XElement> オブジェクトのコレクションまたは属性値を返します。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] コンパイラは、拡張インデクサー プロパティを `ElementAtOrDefault` メソッドの呼び出しに変換します。配列インデクサーとは異なり、`ElementAtOrDefault` メソッドはインデクサーが範囲外であれば `Nothing` を返します。  この動作は、コレクションの要素の数を簡単に特定できない場合に便利です。  
  
 このインデクサー プロパティは、<xref:System.Collections.Generic.IEnumerable%601> または <xref:System.Linq.IQueryable%601> を実装するコレクションの拡張プロパティと似ています。拡張プロパティは、コレクションにインデクサーまたは既定のプロパティがない場合にのみ使用されます。  
  
 <xref:System.Xml.Linq.XElement> オブジェクトまたは <xref:System.Xml.Linq.XAttribute> オブジェクトのコレクションの最初の要素の値にアクセスするには、XML の `Value` プロパティを使用できます。  詳細については、「[XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)」を参照してください。  
  
## 使用例  
 次の例では、拡張インデクサーを使用して、<xref:System.Xml.Linq.XElement> オブジェクトのコレクションの 2 番目の子ノードにアクセスする方法を示します。  コレクションには、子軸プロパティを使用してアクセスします。子軸プロパティは、`contact` オブジェクト内にある `phone` という名前のすべての子要素を取得します。  
  
 [!CODE [VbXMLSamples#24](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#24)]  
  
 このコードは、次のテキストを表示します。  
  
 `Second phone number: 425-555-0145`  
  
## 参照  
 <xref:System.Xml.Linq.XElement>   
 [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)