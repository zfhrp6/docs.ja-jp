---
title: "XML Processing Instruction Literal (Visual Basic) | Microsoft Docs"
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
  - "vb.XmlLiteralProcessingInstruction"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "XML literals [Visual Basic], processing instruction"
  - "XML processing instruction literal [Visual Basic]"
  - "processing instruction literal [Visual Basic]"
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML Processing Instruction Literal (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

<xref:System.Xml.Linq.XProcessingInstruction> オブジェクトを表すリテラルです。  
  
## 構文  
  
```  
<?piName [ = piData ] ?>  
```  
  
## 指定項目  
 `<?`  
 必ず指定します。  XML 処理命令リテラルの開始を示します。  
  
 `piName`  
 必ず指定します。  処理命令の対象のアプリケーションを示す名前です。  "xml" または "XML" で始めることはできません。  
  
 `piData`  
 省略可能です。  `piName` により対象として指定されているアプリケーションが XML ドキュメントを処理する方法を示す文字列です。  
  
 `?>`  
 必ず指定します。  処理命令の終了を示します。  
  
## 戻り値  
 <xref:System.Xml.Linq.XProcessingInstruction> オブジェクト。  
  
## 解説  
 XML 処理命令リテラルは、アプリケーションが XML ドキュメントを処理する方法を示します。  アプリケーションは、XML ドキュメントを読み込むときに、XML 処理命令をチェックして、ドキュメントの処理方法を決定できます。  アプリケーションは、`piName` と `piData` の意味を解釈します。  
  
 XML ドキュメント リテラルは、XML 処理命令と似た構文を使用します。  詳細については、「[XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)」を参照してください。  
  
> [!NOTE]
>  `piName` 要素は、"xml" または "XML" という文字列で始まることはできません。これらの識別子は、XML 1.0 仕様で予約されています。  
  
 XML 処理命令リテラルは、変数に代入したり、XML ドキュメント リテラルに含めたりすることができます。  
  
> [!NOTE]
>  XML リテラルは、行継続文字なしで複数の行に記述できます。  これにより、XML ドキュメントから内容をコピーし、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] プログラムに直接貼り付けることができます。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] コンパイラは、XML 処理命令リテラルを、<xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> コンストラクターの呼び出しに変換します。  
  
## 使用例  
 XML ドキュメントのスタイルシートを示す処理命令を作成する例を次に示します。  
  
 [!CODE [VbXMLSamples#28](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#28)]  
  
## 参照  
 <xref:System.Xml.Linq.XProcessingInstruction>   
 [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)