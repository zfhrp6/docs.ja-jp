---
title: "&lt;remarks&gt; (Visual Basic) | Microsoft Docs"
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
  - "<remarks> XML tag"
  - "remarks XML tag"
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# &lt;remarks&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

メンバーの開設セクションを指定します。  
  
## 構文  
  
```  
<remarks>description</remarks>  
```  
  
#### パラメーター  
 `description`  
 メンバーの説明。  
  
## 解説  
 `<remarks>` タグを使用して、型の情報を追加し、[\<summary\>](../../../visual-basic/language-reference/xmldoc/summary.md) で指定された情報を補足します。  
  
 この情報は、オブジェクト ブラウザーに表示されます。  オブジェクト ブラウザーについては、[コードの構造の表示](/visual-studio/ide/viewing-the-structure-of-code)を参照してください。  
  
 コンパイル時に [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定してドキュメント コメントをファイルに出力します。  
  
## 使用例  
 この例では、`<remarks>` タグを使用して `UpdateRecord` メソッドの機能について説明します。  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/visualbasic/remarks_1.vb)]  
  
## 参照  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)