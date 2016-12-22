---
title: "&lt;typeparam&gt; (Visual Basic) | Microsoft Docs"
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
  - "typeparam XML tag"
  - "<typeparam> XML tag"
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;typeparam&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

型パラメーターの名前と説明を定義します。  
  
## 構文  
  
```  
<typeparam name="name">description</typeparam>  
```  
  
#### パラメーター  
 `name`  
 型パラメーターの名前です。  名前は、二重引用符 \(" "\) で囲みます。  
  
 `description`  
 型パラメーターの説明です。  
  
## 解説  
 ジェネリック型またはジェネリック メンバー宣言のコメント内で `<typeparam>` タグを使用すると、型パラメーターの 1 つについての説明を記述できます。  
  
 コンパイル時に [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定してドキュメント コメントをファイルに出力します。  
  
## 使用例  
 `<typeparam>` タグを使って `id` パラメーターの説明を記述する例を次に示します。  
  
 [!code-vb[VbVbcnXmlDocComments#8](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/typeparam_1.vb)]  
  
## 参照  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)