---
title: "&lt;code&gt; (Visual Basic) | Microsoft Docs"
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
  - "code XML tag"
  - "<code> XML tag"
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# &lt;code&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

テキストが複数行のコードであることを示します。  
  
## 構文  
  
```  
<code>content</code>  
```  
  
#### パラメーター  
 `content`  
 コードとしてマークするテキストです。  
  
## 解説  
 複数の行をコードとして示すには `<code>` タグを使用します。  説明内のテキストをコードとして指定する場合は、[\<c\>](../../../visual-basic/language-reference/xmldoc/c.md) タグを使用します。  
  
 コンパイル時に [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定してドキュメント コメントをファイルに出力します。  
  
## 使用例  
 この例では、&lt;code&gt; タグを使用して、`ID` フィールドの使用例を含めます。  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/visualbasic/code_1.vb)]  
  
## 参照  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)