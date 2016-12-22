---
title: "&lt;param&gt; (C# プログラミング ガイド) | Microsoft Docs"
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
  - "param"
  - "<param>"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<param> C# XML タグ"
  - "param C# XML タグ"
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &lt;param&gt; (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

## 構文  
  
```  
<param name="name">description</param>  
```  
  
#### パラメーター  
 `name`  
 メソッド パラメーターの名前。  名前は、二重引用符 \(" "\) で囲みます。  
  
 `description`  
 パラメーターの説明。  
  
## 解説  
 \<param\> タグは、メソッド宣言のコメント内で使用してメソッドのパラメーターの 1 つを説明します。  複数のパラメーターを文書化するには、複数の \<param\> タグを使用します。  
  
 \<param\> タグのテキストは、IntelliSense、オブジェクト ブラウザー、およびコード コメント Web レポートに表示されます。  
  
 コンパイル時に [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定してドキュメント コメントをファイルに出力します。  
  
## 使用例  
 [!code-cs[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ドキュメント コメントとして推奨されるタグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)