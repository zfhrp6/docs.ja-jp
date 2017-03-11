---
title: "Recommended XML Tags for Documentation Comments (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.XmlDocComment"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "tags, XML"
  - "XML comments, recommended tags [Visual Basic]"
  - "comments, recommended XML tags"
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# Recommended XML Tags for Documentation Comments (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コンパイラは、コード中のドキュメント コメントを処理して XML ファイルを生成できます。  専用のツールを使用すると、この XML ファイルからドキュメントを生成できます。  
  
 XML コメントは、型や型メンバーなどのコードの構成体に対して使用できます。  partial 型の場合は、型の 1 部分にのみ XML コメントを使用できます。ただし、部分型のメンバーのコメント作成に対する制限は何もありません。  
  
> [!NOTE]
>  ドキュメント コメントは名前空間には使用できません。  その理由は、1 つの名前空間に複数のアセンブリが属し、すべてのアセンブリが同時にロードされるとは限らないからです。  
  
 コンパイラは、有効な XML のタグをすべて処理します。  ユーザー ドキュメントで一般的に使用される機能を提供するタグを次の表に示します。  
  
||||  
|-|-|-|  
|[\<c\>](../../../visual-basic/language-reference/xmldoc/c.md)|[\<code\>](../../../visual-basic/language-reference/xmldoc/code.md)|[\<example\>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<exception\>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<include\>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[\<list\>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<para\>](../../../visual-basic/language-reference/xmldoc/para.md)|[\<param\>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref\>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[\<permission\>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup>|[\<remarks\>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<returns\>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|[\<see\>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup>|[\<seealso\>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup>|[\<summary\>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam\>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<value\>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 \(<sup>1</sup> コンパイラが構文を検証します。\)  
  
> [!NOTE]
>  ドキュメント コメントのテキストに山かっこを出力するには、`<` と `>` を使用します。  たとえば、文字列 `"<text in angle brackets>"` は、`<text in angle` `brackets>` と出力されます。  
  
## 参照  
 [Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)   
 [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md)   
 [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)