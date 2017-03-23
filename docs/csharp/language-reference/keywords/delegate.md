---
title: "delegate (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "delegate_CSharpKeyword"
  - "delegate"
  - "CS0123"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "delegate キーワード [C#]"
  - "関数ポインター [C#]"
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# delegate (C# リファレンス)
デリゲート型の宣言は、メソッド シグネチャに似ています。  戻り値と任意の数のパラメーター \(任意の型\) を持ちます。  
  
```  
public delegate void TestDelegate(string message);  
public delegate int TestDelegate(MyType m, long num);  
```  
  
 `delegate` は、指定されたメソッドまたは匿名メソッドをカプセル化するために使用される参照型です。  デリゲートは C\+\+ の関数ポインターに類似していますが、タイプ セーフであり、安全です。  デリゲートの適用については、「[デリゲート \(C\# プログラミング ガイド\)](../../../csharp/programming-guide/delegates/index.md)」および「[汎用デリゲート \(C\# プログラミング ガイド\)](../../../csharp/programming-guide/generics/generic-delegates.md)」を参照してください。  
  
## 解説  
 デリゲートは、[イベント](../../../csharp/programming-guide/events/index.md)の基礎になります。  
  
 デリゲートをインスタンス化するには、デリゲートに指定されたメソッドまたは匿名メソッドを関連付けます。  詳細については、「[名前付きメソッド \(C\# プログラミング ガイド\)](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)」および「[匿名メソッド \(C\# プログラミング ガイド\)](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)」を参照してください。  
  
 デリゲートは、互換性のある戻り値の型と入力パラメーターを持つメソッドまたはラムダ式でインスタンス化する必要があります。  メソッド シグネチャで許容される範囲の詳細については、「[デリゲートの分散](../Topic/Variance%20in%20Delegates%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  匿名メソッドで使用する場合、デリゲートおよびデリゲートと関連付けるコードを共に宣言します。  デリゲートをインスタンス化するこの 2 つの方法について説明します。  
  
## 使用例  
 [!code-cs[csrefKeywordsTypes#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/delegate_1.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [参照型](../../../csharp/language-reference/keywords/reference-types.md)   
 [デリゲート](../../../csharp/programming-guide/delegates/index.md)   
 [イベント](../../../csharp/programming-guide/events/index.md)   
 [名前付きメソッドを使用したデリゲートと匿名メソッドを使用したデリゲート](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)   
 [匿名メソッド](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)