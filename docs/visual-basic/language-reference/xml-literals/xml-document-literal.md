---
title: "XML Document Literal (Visual Basic) | Microsoft Docs"
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
  - "vb.XmlLiteralDocument"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "XML document literal [Visual Basic]"
  - "XML literals [Visual Basic], document"
  - "XML documents [Visual Basic], creating"
  - "document literal [Visual Basic]"
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML Document Literal (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

<xref:System.Xml.Linq.XDocument> オブジェクトを表すリテラルです。  
  
## 構文  
  
```  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`encoding`|省略可能です。  ドキュメントが使用するエンコーディングを宣言するリテラル テキスト。|  
|`standalone`|省略可能です。  リテラル テキスト。  "yes" または "no" を指定する必要があります。|  
|`piCommentList`|省略可能です。  XML 処理命令と XML コメントの一覧。  形式は次のとおりです。<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> 各 `piComment` ``  は次のいずれかです。<br /><br /> -   [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).<br />-   [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).|  
|`rootElement`|必ず指定します。  ドキュメントのルート要素。  次のいずれかの形式です。<br /><br /> <ul><li>[XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</li><li>`<%=` `elementExp` `%>` の形式の埋め込み式。  `elementExp` は次のいずれかを返します。<br /><br /> <ul><li><xref:System.Xml.Linq.XElement> オブジェクト。</li><li>1 つの <xref:System.Xml.Linq.XElement> オブジェクトと、任意の数の <xref:System.Xml.Linq.XProcessingInstruction> オブジェクトおよび <xref:System.Xml.Linq.XComment> オブジェクトを含むコレクション。</li></ul></li></ul><br /> 詳細については、「[Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)」を参照してください。|  
  
## 戻り値  
 <xref:System.Xml.Linq.XDocument> オブジェクト。  
  
## 解説  
 XML ドキュメント リテラルは、リテラルの先頭にある XML 宣言で識別されます。  各 XML ドキュメント リテラルのルート XML 要素は 1 つだけである必要がありますが、XML 処理命令と XML コメントはいくつでもかまいません。  
  
 XML ドキュメント リテラルは、XML 要素の中では使用できません。  
  
> [!NOTE]
>  XML リテラルは、行継続文字なしで複数の行に記述できます。  これにより、XML ドキュメントから内容をコピーし、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] プログラムに直接貼り付けることができます。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] コンパイラは、XML ドキュメント リテラルを、<xref:System.Xml.Linq.XDocument.%23ctor%2A> コンストラクターと <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> コンストラクターの呼び出しに変換します。  
  
## 使用例  
 次の例では、XML 宣言、処理命令、コメント、および別の要素を格納する要素がある XML ドキュメントを作成します。  
  
 [!CODE [VbXMLSamples#30](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#30)]  
  
## 参照  
 <xref:System.Xml.Linq.XElement>   
 <xref:System.Xml.Linq.XProcessingInstruction>   
 <xref:System.Xml.Linq.XComment>   
 <xref:System.Xml.Linq.XDocument>   
 [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)   
 [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)   
 [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)