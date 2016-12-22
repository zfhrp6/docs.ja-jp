---
title: "&lt;see&gt; (C# プログラミング ガイド) | Microsoft Docs"
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
  - "<see>"
  - "see"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<see> C# XML タグ"
  - "cref [C#], <see> タグ"
  - "クロス リファレンス [C#]"
  - "see C# XML タグ"
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &lt;see&gt; (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

## 構文  
  
```  
<see cref="member"/>  
```  
  
#### パラメーター  
 cref \= "`member`"  
 現在のコンパイル環境からの呼び出しに利用できる、メンバーまたはフィールドへの参照。  コンパイラは、指定されたコード要素が存在するかどうかを確認し、`member` を出力 XML 内の要素名に渡します。*member* は、二重引用符 \(" "\) で囲みます。  
  
## 解説  
 \<see\> タグを使用すると、テキスト内でリンクを指定できます。  テキストが参照セクションに配置されていることを示すには、[\<seealso\>](../../../csharp/programming-guide/xmldoc/seealso.md) を使用します。  コード要素のドキュメント ページへの内部ハイパーリンクを作成するには、[cref 属性](../../../csharp/programming-guide/xmldoc/cref-attribute.md)を使用します。  
  
 コンパイル時に [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定してドキュメント コメントをファイルに出力します。  
  
 次の例では、summary セクション内の \<see\> タグを示しています。  
  
 [!code-cs[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/see_1.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ドキュメント コメントとして推奨されるタグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)