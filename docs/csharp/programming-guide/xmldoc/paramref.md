---
title: "&lt;paramref&gt; (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "paramref"
  - "<paramref>"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<paramref> C# XML タグ"
  - "paramref C# XML タグ"
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
caps.latest.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 12
---
# &lt;paramref&gt; (C# プログラミング ガイド)
## 構文  
  
```  
<paramref name="name"/>  
```  
  
#### パラメーター  
 `name`  
 参照するパラメーターの名前。  名前は、二重引用符 \(" "\) で囲みます。  
  
## 解説  
 \<paramref\> タグを使用すると、\<summary\> ブロックや \<remarks\> ブロックなどのコード コメント内の単語をパラメーターの参照として指定できます。  XML ファイルは、この単語に太字や斜体などの異なる書式を設定するように処理できます。  
  
 コンパイル時に [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定してドキュメント コメントをファイルに出力します。  
  
## 使用例  
 [!code-cs[csProgGuideDocComments#7](../../../csharp/programming-guide/xmldoc/codesnippet/csharp/paramref_1.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ドキュメント コメントとして推奨されるタグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)