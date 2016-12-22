---
title: "&lt;paramref&gt; (Visual Basic) | Microsoft Docs"
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
  - "paramref XML tag"
  - "<paramref> XML tag"
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;paramref&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

WORD をパラメーターとしてフォーマットします。  
  
## 構文  
  
```  
<paramref name="name"/>  
```  
  
#### パラメーター  
 `name`  
 参照するパラメーターの名前。  名前は、二重引用符 \(" "\) で囲みます。  
  
## 解説  
 `<paramref>` タグを使用すると、WORD をパラメーターとして指定できます。  XML ファイルを処理するときに、このパラメーターに対して独立した書式を設定できます。  
  
 コンパイル時に [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定してドキュメント コメントをファイルに出力します。  
  
## 使用例  
 この例では、`<paramref>` タグを使用して `id` パラメーターを参照します。  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/paramref_1.vb)]  
  
## 参照  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)