---
title: "暗黙的に型指定される配列 (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "配列 [C#], 暗黙的に型指定される"
  - "C# 言語, 暗黙的に型指定される配列"
  - "暗黙的に型指定される配列 [C#]"
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 暗黙的に型指定される配列 (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

配列初期化子に指定された要素から配列インスタンスの型が推論される、暗黙的に型指定される配列を作成できます。  暗黙的に型指定される変数の規則が、暗黙的に型指定される配列にも適用されます。  詳細については、「[暗黙的に型指定されるローカル変数](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)」を参照してください。  
  
 通常、暗黙的に型指定される配列は、匿名型、オブジェクト初期化子、およびコレクション初期化子と共に、クエリ式で使用されます。  
  
 暗黙的に型指定される配列の作成方法の例を次に示します。  
  
 [!code-cs[csProgGuideLINQ#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_1.cs)]  
  
 前の例の暗黙的に型指定される配列では、初期化ステートメントの左側に角かっこは使用されていません。  また、ジャグ配列は、1 次元配列と同じように `new []` を使用して初期化されます。  
  
## オブジェクト初期化子で暗黙的に型指定される配列  
 配列が含まれた匿名型を作成する場合、その型のオブジェクト初期化子で配列を暗黙的に型指定する必要があります。  次の例では、`contacts` は匿名型の暗黙的に型指定された配列で、それぞれに `PhoneNumbers` という名前の配列が含まれています。  オブジェクト初期化子の内部に `var` キーワードは使用されていません。  
  
 [!code-cs[csProgGuideLINQ#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_2.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [暗黙的に型指定されるローカル変数](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)   
 [配列](../../../csharp/programming-guide/arrays/index.md)   
 [匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [オブジェクト初期化子とコレクション初期化子](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)   
 [var](../../../csharp/language-reference/keywords/var.md)   
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)