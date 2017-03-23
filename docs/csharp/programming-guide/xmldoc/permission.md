---
title: "&lt;permission&gt; (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "permission"
  - "<permission>"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<permission> C# XML タグ"
  - "permission C# XML タグ"
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
caps.latest.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 12
---
# &lt;permission&gt; (C# プログラミング ガイド)
## 構文  
  
```  
<permission cref="member">description</permission>  
```  
  
#### パラメーター  
 cref \= "`member`"  
 現在のコンパイル環境からの呼び出しに利用できる、メンバーまたはフィールドへの参照。  コンパイラは、指定されたコード要素が存在することを確認してから、`member` を出力先 XML 内で標準要素名に変換します。 *member* は二重引用符 \(" "\) で囲みます。  
  
 ジェネリック型への cref 参照の作成方法については、「[\<see\>](../../../csharp/programming-guide/xmldoc/see.md)」を参照してください。  
  
 `description`  
 メンバーへのアクセスの説明。  
  
## 解説  
 \<permission\> タグを使用すると、メンバーへのアクセスをドキュメントにできます。  <xref:System.Security.PermissionSet> クラスは、アクセスをメンバーに指定するために使用します。  
  
 コンパイル時に [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定してドキュメント コメントをファイルに出力します。  
  
## 使用例  
 [!code-cs[csProgGuideDocComments#8](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/permission_1.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ドキュメント コメントとして推奨されるタグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)