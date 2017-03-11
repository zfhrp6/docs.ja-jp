---
title: "&lt;permission&gt; (Visual Basic) | Microsoft Docs"
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
  - "<permission> XML tag"
  - "permission XML tag"
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# &lt;permission&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

メンバーに要求されるアクセス許可について指定します。  
  
## 構文  
  
```  
<permission cref="member">description</permission>  
```  
  
#### パラメーター  
 `member`  
 現在のコンパイル環境からの呼び出しに利用できる、メンバーまたはフィールドへの参照。  コンパイラは、指定されたコード要素が存在するかどうかを確認し、`member` を出力先 XML 内で標準要素名に変換します。  `member` は二重引用符 \(" "\) で囲みます。  
  
 `description`  
 メンバーへのアクセスの説明。  
  
## 解説  
 `<permission>` タグを使用すると、メンバーのアクセスについて文書化できます。  <xref:System.Security.PermissionSet> クラスは、アクセスをメンバーに指定するために使用します。  
  
 コンパイル時に [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定してドキュメント コメントをファイルに出力します。  
  
## 使用例  
 次の例は、`<permission>` タグを使用して、`ReadFile` メソッドには <xref:System.Security.Permissions.FileIOPermission> が必要であるという説明を記述しています。  
  
 [!code-vb[VbVbcnXmlDocComments#7](../../../visual-basic/language-reference/xmldoc/codesnippet/visualbasic/permission_1.vb)]  
  
## 参照  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)