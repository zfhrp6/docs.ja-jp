---
title: "&lt;seealso&gt; (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "<seealso> XML tag"
  - "seealso XML tag"
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;seealso&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

「参照」のセクションに示すリンクを指定します。  
  
## 構文  
  
```  
<seealso cref="member"/>  
```  
  
#### パラメーター  
 `member`  
 現在のコンパイル環境からの呼び出しに利用できる、メンバーまたはフィールドへの参照。  コンパイラは、指定されたコード要素が存在するかどうかを確認し、`member` を出力 XML 内の要素名に渡します。  `member` は、二重引用符 \(" "\) で囲みます。  
  
## 解説  
 `<seealso>` タグを使用すると、「参照」セクションに示すテキストを指定できます。  テキスト内でリンクを指定するには、[\<see\>](../../../visual-basic/language-reference/xmldoc/see.md) タグを使用します。  
  
 コンパイル時に [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定してドキュメント コメントをファイルに出力します。  
  
## 使用例  
 次の例は、`DoesRecordExist` の remarks セクションで `<seealso>` タグを使用して、`UpdateRecord` メソッドを参照します。  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/seealso_1.vb)]  
  
## 参照  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)