---
title: "&lt;c&gt; (C# プログラミング ガイド) | Microsoft Docs"
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
  - "c"
  - "<c>"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<c> C# XML タグ"
  - "c C# XML タグ"
  - "コード, マーキング (テキストの) [C#]"
  - "テキスト, マーキング (コードとして) [C#]"
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &lt;c&gt; (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

## 構文  
  
```  
<c>text</c>  
```  
  
#### パラメーター  
 `text`  
 コードとして指定するテキスト。  
  
## 解説  
 \<c\> タグを使用すると、説明内のテキストをコードとして指定できます。  コードとして複数行を指定する場合は、[\<code\>](../../../csharp/programming-guide/xmldoc/code.md) タグを使用します。  
  
 コンパイル時に [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定してドキュメント コメントをファイルに出力します。  
  
## 使用例  
 [!code-cs[csProgGuideDocComments#2](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/code-inline_1.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ドキュメント コメントとして推奨されるタグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)