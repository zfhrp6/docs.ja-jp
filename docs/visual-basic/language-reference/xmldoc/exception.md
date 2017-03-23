---
title: "&lt;exception&gt; (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "<exception> XML tag"
  - "exception XML tag"
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# &lt;exception&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

スローできる例外を指定します。  
  
## 構文  
  
```  
<exception cref="member">description</exception>  
```  
  
#### パラメーター  
 `member`  
 現在のコンパイル環境から利用可能な例外への参照。  コンパイラは、指定された例外が存在するかどうかを確認し、`member` を出力先 XML 内で標準要素名に変換します。  `member` は、二重引用符 \(" "\) で囲みます。  
  
 `description`  
 説明。  
  
## 解説  
 スローできる例外を指定するには `<exception>` タグを使用します。  このタグは、メソッド定義に適用されます。  
  
 コンパイル時に [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定してドキュメント コメントをファイルに出力します。  
  
## 使用例  
 この例では、`<exception>` タグを使用して、`IntDivide` 関数がスローできる例外を指定します。  
  
 [!code-vb[VbVbcnXmlDocComments#3](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/exception_1.vb)]  
  
## 参照  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)