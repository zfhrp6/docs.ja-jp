---
title: "&lt;seealso&gt; (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "cref"
  - "<seealso>"
  - "seealso"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<seealso> C# XML タグ"
  - "cref [C#]"
  - "cref [C#], 参照"
  - "クロス リファレンス [C#], タグ"
  - "seealso C# XML タグ"
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
caps.latest.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 11
---
# &lt;seealso&gt; (C# プログラミング ガイド)
## 構文  
  
```  
<seealso cref="member"/>  
```  
  
#### パラメーター  
 cref \= "`member`"  
 現在のコンパイル環境からの呼び出しに利用できる、メンバーまたはフィールドへの参照。  コンパイラは、指定されたコード要素が存在することを確認してから、`member` を出力先 XML 内の要素名に渡します。`member` は、二重引用符 \(" "\) で囲みます。  
  
 ジェネリック型への cref 参照の作成方法については、「[\<see\>](../../../csharp/programming-guide/xmldoc/see.md)」を参照してください。  
  
## 解説  
 \<seealso\> タグを使用すると、「参照」のセクションに示すテキストを指定できます。  テキスト内でリンクを指定するには、[\<see\>](../../../csharp/programming-guide/xmldoc/see.md) タグを使用します。  
  
 コンパイル時に [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定してドキュメント コメントをファイルに出力します。  
  
## 使用例  
 \<seealso\> タグの使用例については、「[\<summary\>](../../../csharp/programming-guide/xmldoc/summary.md)」を参照してください。  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ドキュメント コメントとして推奨されるタグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)