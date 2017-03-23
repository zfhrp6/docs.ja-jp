---
title: "&lt;remarks&gt; (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "remarks"
  - "<remarks>"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<remarks> C# XML タグ"
  - "remarks C# XML タグ"
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 13
---
# &lt;remarks&gt; (C# プログラミング ガイド)
## 構文  
  
```  
<remarks>description</remarks>  
```  
  
#### パラメーター  
 `Description`  
 メンバーの説明。  
  
## 解説  
 \<remarks\> タグを使用して、型の情報を追加し、[\<summary\>](../../../csharp/programming-guide/xmldoc/summary.md) で指定された情報を補足します。  この情報は [Object Browser Window](http://msdn.microsoft.com/ja-jp/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda) に表示されます。  
  
 コンパイル時に [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定してドキュメント コメントをファイルに出力します。  
  
## 使用例  
 [!code-cs[csProgGuideDocComments#9](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/remarks_1.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ドキュメント コメントとして推奨されるタグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)