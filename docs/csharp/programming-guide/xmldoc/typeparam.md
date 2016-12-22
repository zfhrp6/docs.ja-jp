---
title: "&lt;typeparam&gt; (C# プログラミング ガイド) | Microsoft Docs"
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
  - "typeparam"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<typeparam> C# XML タグ"
  - "typeparam C# XML タグ"
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &lt;typeparam&gt; (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

## 構文  
  
```  
<typeparam name="name">description</typeparam>  
```  
  
#### パラメーター  
 `name`  
 型パラメーターの名前です。  名前は、二重引用符 \(" "\) で囲みます。  
  
 `description`  
 型パラメーターの説明です。  
  
## 解説  
 ジェネリック型またはジェネリック メソッドを宣言して型パラメーターを説明する場合、コメントに `<typeparam>` タグを使用します。  ジェネリック型またはジェネリック メソッドの型パラメーターごとに、タグを追加します。  
  
 詳細については、「[ジェネリック](../../../visual-basic/reference/command-line-compiler/index.md)」を参照してください。  
  
 `<typeparam>` タグのテキストは、[Object Browser Window](http://msdn.microsoft.com/ja-jp/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda) コード コメント Web レポートである、IntelliSense に表示されます。  
  
 コンパイル時に [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定してドキュメント コメントをファイルに出力します。  
  
## 使用例  
 [!code-cs[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparam_1.cs)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ドキュメント コメントとして推奨されるタグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)