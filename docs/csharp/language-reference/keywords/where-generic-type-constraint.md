---
title: "where (ジェネリック型制約) (C# リファレンス) | Microsoft Docs"
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
  - "whereconstraint"
  - "whereconstraint_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "where (ジェネリック型の制約) [C#]"
ms.assetid: d7aa871b-0714-416a-bab2-96f87ada4310
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# where (ジェネリック型制約) (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

ジェネリック型定義では、`where` 句は、ジェネリック宣言で定義されている型パラメーターの引数として使用できる型に対する制約を指定します。  たとえば、型パラメーター `T` が <xref:System.IComparable%601> インターフェイスを実装するように `MyGenericClass` ジェネリック クラスを宣言できます。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
> [!NOTE]
>  クエリ式での where 句の詳細については、「[where 句](../../../visual-basic/language-reference/queries/where-clause.md)」を参照してください。  
  
 `where` 句には、インターフェイス制約だけでなく基本クラス制約も指定できます。基本クラス制約は、ジェネリック型の型引数として使用する型には、基本クラスとして指定されているクラスまたは基本クラス自体が含まれている必要があることを指定します。  このような制約を使用する場合は、型パラメーターに関する制約よりも前に制約を記述する必要があります。  
  
 [!code-cs[csrefKeywordsContextual#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_1.cs)]  
  
 `where` 句には、コンストラクター制約も指定できます。  新しい演算子を使用して型パラメーターのインスタンスを作成できますが、このようにインスタンスを作成するには、コンストラクター制約 `new()` によって型パラメーターに制約を指定する必要があります。  [new\(\) 制約](../../../csharp/language-reference/keywords/new-constraint.md)に基づいて、コンパイラは、指定されている型引数には、アクセス可能なパラメーターなしの \(または既定の\) コンストラクターが必要であることを認識します。  次に例を示します。  
  
 [!code-cs[csrefKeywordsContextual#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_2.cs)]  
  
 `new()` 制約は、`where` 句の最後に記述します。  
  
 複数の型パラメーターがある場合には、型パラメーターごとに `where` 句を 1 つずつ使用します。次に例を示します。  
  
 [!code-cs[csrefKeywordsContextual#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_3.cs)]  
  
 次に示すように、ジェネリック メソッドの型パラメーターにも制約を適用できます。  
  
```  
public bool MyMethod<T>(T t) where T : IMyInterface { }  
```  
  
 デリゲートに対する型パラメーター制約の構文は、メソッドの構文と同じである点に注意してください。  
  
```  
delegate T MyDelegate<T>() where T : new()  
```  
  
 ジェネリック デリゲートについては、「[汎用デリゲート \(C\# プログラミング ガイド\)](../../../csharp/programming-guide/generics/generic-delegates.md)」を参照してください。  
  
 制約の構文と使い方の詳細については、「[型パラメーターの制約 \(C\# プログラミング ガイド\)](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)」を参照してください。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [new 制約](../../../csharp/language-reference/keywords/new-constraint.md)   
 [型パラメーターの制約](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)