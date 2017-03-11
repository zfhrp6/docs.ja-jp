---
title: "&lt;exception&gt; (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "exception"
  - "<exception>"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<exception> C# XML タグ"
  - "exception C# XML タグ"
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# &lt;exception&gt; (C# プログラミング ガイド)
## 構文  
  
```  
<exception cref="member">description</exception>  
```  
  
#### パラメーター  
 cref \= "`member`"  
 現在のコンパイル環境から利用可能な例外への参照。  コンパイラは、指定された例外が存在するかどうかを確認し、`member` を出力先 XML 内で標準要素名に変換します。  `member` は、二重引用符 \(" "\) で囲みます。  
  
 ジェネリック型への cref 参照の作成方法の詳細については、「[\<see\>](../../../csharp/programming-guide/xmldoc/see.md)」を参照してください。  
  
 `description`  
 例外の説明。  
  
## 解説  
 \<exception\> タグを使用すると、スローできる例外を指定できます。  このタグは、メソッド、プロパティ、イベント、およびインデクサーの定義に適用できます。  
  
 コンパイル時に [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定してドキュメント コメントをファイルに出力します。  
  
 例外処理の詳細については、「[例外と例外処理](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)」を参照してください。  
  
## 使用例  
 [!code-cs[csProgGuideDocComments#4](../../../csharp/programming-guide/xmldoc/codesnippet/csharp/exception_1.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ドキュメント コメントとして推奨されるタグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)