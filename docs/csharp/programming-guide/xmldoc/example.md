---
title: "&lt;example&gt; (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<example>"
  - "example"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<example> C# XML タグ"
  - "example C# XML タグ"
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &lt;example&gt; (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

## 構文  
  
```  
<example>description</example>  
```  
  
#### パラメーター  
 `description`  
 サンプル コードの説明。  
  
## 解説  
 \<example\> タグでは、メソッドやその他のライブラリ メンバーの使用例を指定します。  通常は、[\<code\>](../../../csharp/programming-guide/xmldoc/code.md) タグも使用します。  
  
 コンパイル時に [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定してドキュメント コメントをファイルに出力します。  
  
## 使用例  
 [!code-cs[csProgGuideDocComments#3](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/example_1.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ドキュメント コメントとして推奨されるタグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)