---
title: "&lt;para&gt; (Visual Basic) | Microsoft Docs"
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
  - "<para> XML tag"
  - "para XML tag"
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# &lt;para&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

コンテンツが段落として書式設定されていることを示します。  
  
## 構文  
  
```  
<para>content</para>  
```  
  
#### パラメーター  
 `content`  
 段落のテキスト。  
  
## 解説  
 `<para>` タグは、[\<summary\>](../../../visual-basic/language-reference/xmldoc/summary.md)、[\<remarks\>](../../../visual-basic/language-reference/xmldoc/remarks.md)、[\<returns\>](../../../visual-basic/language-reference/xmldoc/returns.md) などのタグの中で使用され、テキストに構造体を追加します。  
  
 コンパイル時に [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定してドキュメント コメントをファイルに出力します。  
  
## 使用例  
 この例では、`<para>` タグを使用して、`UpdateRecord` メソッドの解説セクションを 2 つの段落に分割します。  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/visualbasic/para_1.vb)]  
  
## 参照  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)