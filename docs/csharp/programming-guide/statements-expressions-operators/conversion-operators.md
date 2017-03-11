---
title: "変換演算子 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 言語、変換演算子"
  - "変換演算子 [C#]"
  - "演算子 [C#]、変換"
  - "ユーザー定義変換 [C#]"
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
caps.latest.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 22
---
# 変換演算子 (C# プログラミング ガイド)
C\# では、クラスや構造体で変換を宣言して、他のクラスや構造体と基本型との相互変換を行うことができます。  変換は演算子のように定義でき、変換先の型に応じた名前が付けられます。  変換対象の引数の型または変換結果の型のうち両方ではなく一方は、包含型である必要があります。  
  
 [!code-cs[csProgGuideStatements#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/conversion-operators_1.cs)]  
  
## 変換演算子の概要  
 変換演算子には、次の特徴があります。  
  
-   `implicit` として宣言された変換は、必要に応じて自動的に行われます。  
  
-   `explicit` として宣言された変換では、キャストを呼び出す必要があります。  
  
-   変換はすべて `static` として宣言する必要があります。  
  
## 関連項目  
 詳細情報  
  
-   [変換演算子の使用](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
-   [キャストと型変換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [方法 : 構造体間にユーザー定義の変換を実装する](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [explicit](../../../csharp/language-reference/keywords/explicit.md)  
  
-   [implicit](../../../csharp/language-reference/keywords/implicit.md)  
  
-   [static](../../../csharp/language-reference/keywords/static.md)  
  
## 参照  
 <xref:System.Convert>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [、C のチェーン ユーザー定義の明示的な変換](http://go.microsoft.com/fwlink/?LinkId=112384)