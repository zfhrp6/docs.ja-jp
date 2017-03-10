---
title: ". 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
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
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# . 演算子 (C# リファレンス)
ドット演算子 \(`.`\) は、メンバー アクセスに使用します。  ドット演算子は、型または名前空間のメンバーを指定します。  たとえば、ドット演算子を使用して、.NET Framework クラス ライブラリ内の特定のメソッドにアクセスします。  
  
 [!code-cs[csRefOperators#16](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#16)]  
  
 たとえば、次のクラスを考えます。  
  
 [!code-cs[csRefOperators#17](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#17)]  
  
 [!code-cs[csRefOperators#18](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#18)]  
  
 変数 `s` には、`a` と `b` という 2 つのメンバーがあります。それらのメンバーにアクセスするためにドット演算子を使用します。  
  
 [!code-cs[csRefOperators#19](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#19)]  
  
 ドットは修飾名にも使用します。修飾名とは、属している名前空間やインターフェイスなどを示す名前のことです。  
  
 [!code-cs[csRefOperators#20](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#20)]  
  
 using ディレクティブを使用すると、名前の修飾を省略できます。  
  
 [!code-cs[csRefOperators#21](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#21)]  
  
 ただし、識別子があいまいな場合は、修飾する必要があります。  
  
 [!code-cs[csRefOperators#22](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#22)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)