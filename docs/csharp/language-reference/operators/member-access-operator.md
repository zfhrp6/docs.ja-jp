---
title: ". 演算子 (C# リファレンス) | Microsoft Docs"
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
  - "._CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - ". 演算子 [C#]"
  - "ドット演算子 (.) [C#]"
  - "メンバー アクセス演算子 (.) [C#]"
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# . 演算子 (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

ドット演算子 \(`.`\) は、メンバー アクセスに使用します。  ドット演算子は、型または名前空間のメンバーを指定します。  たとえば、ドット演算子を使用して、.NET Framework クラス ライブラリ内の特定のメソッドにアクセスします。  
  
 [!CODE [csRefOperators#16](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#16)]  
  
 たとえば、次のクラスを考えます。  
  
 [!CODE [csRefOperators#17](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#17)]  
  
 [!CODE [csRefOperators#18](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#18)]  
  
 変数 `s` には、`a` と `b` という 2 つのメンバーがあります。それらのメンバーにアクセスするためにドット演算子を使用します。  
  
 [!CODE [csRefOperators#19](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#19)]  
  
 ドットは修飾名にも使用します。修飾名とは、属している名前空間やインターフェイスなどを示す名前のことです。  
  
 [!CODE [csRefOperators#20](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#20)]  
  
 using ディレクティブを使用すると、名前の修飾を省略できます。  
  
 [!CODE [csRefOperators#21](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#21)]  
  
 ただし、識別子があいまいな場合は、修飾する必要があります。  
  
 [!CODE [csRefOperators#22](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#22)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)