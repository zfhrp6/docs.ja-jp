---
title: "匿名関数 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "匿名関数 [C#]"
  - "匿名メソッド [C#]"
  - "ラムダ式 [C#], 匿名関数として"
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# 匿名関数 (C# プログラミング ガイド)
匿名関数は、デリゲート型になるところであればどこでも使用できる "インライン" ステートメントまたは式です。  これを使用すると、名前付きデリゲートの初期化や、名前付きデリゲート型の代わりにメソッド パラメーターとして渡すことができます。  
  
 匿名関数には 2 種類あり、次のトピックでそれぞれ個別に説明しています。  
  
-   [ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
-   [匿名メソッド](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
    > [!NOTE]
    >  ラムダ式は、式ツリーのほかにデリゲートにもバインドできます。  
  
## C\# におけるデリゲートの進化  
 C\# 1.0 では、コードの他の場所で定義されたメソッドを使用して明示的に初期化することにより、デリゲートのインスタンスを作成していました。  C\# 2.0 で匿名メソッドの概念が導入され、デリゲート呼び出しで実行できる名前のないインライン ステートメント ブロックを作成できるようになりました。  C\# 3.0 ではラムダ式が導入されました。ラムダ式は匿名メソッドと似た概念ですが、表現できる範囲が広がり、より簡潔になりました。  この 2 つの機能を総称して*匿名関数*と言います。  一般に、Version 3.5 以降の [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] を対象とするアプリケーションは、ラムダ式を使用する必要があります。  
  
 次の例は、C\# 1.0 から C\# 3.0 までのデリゲート作成の進化を示しています。  
  
 [!code-cs[csProgGuideLINQ#65](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csRef30LangFeatures_2.cs#65)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [ステートメント、式、および演算子](../../../csharp/programming-guide/statements-expressions-operators/index.md)   
 [ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
 [デリゲート](../../../csharp/programming-guide/delegates/index.md)   
 [式ツリー](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)