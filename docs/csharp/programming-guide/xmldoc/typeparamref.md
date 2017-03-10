---
title: "&lt;typeparamref&gt; (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "typeparamref"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<typeparamref> C# XML タグ"
  - "typeparamref C# XML タグ"
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# &lt;typeparamref&gt; (C# プログラミング ガイド)
## 構文  
  
```  
<typeparamref name="name"/>  
```  
  
#### パラメーター  
 `name`  
 型パラメーターの名前です。  名前は、二重引用符 \(" "\) で囲みます。  
  
## 解説  
 ジェネリック型とジェネリック メソッドの型パラメーターの詳細については、「[ジェネリック \(C\# プログラミング ガイド\)](../../../csharp/programming-guide/generics/index.md)」を参照してください。  
  
 ドキュメント ファイルを使用するときに何らかの方法で単語の書式 \(斜体など\) を指定するには、このタグを使用します。  
  
 コンパイル時に [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定してドキュメント コメントをファイルに出力します。  
  
## 使用例  
 [!code-cs[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/csharp/typeparamref_1.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ドキュメント コメントとして推奨されるタグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)