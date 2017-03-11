---
title: "new 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "new 演算子キーワード [C#]"
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
caps.latest.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 22
---
# new 演算子 (C# リファレンス)
オブジェクトを作成し、コンストラクターを呼び出します。  次に例を示します。  
  
```  
Class1 obj  = new Class1();  
```  
  
 匿名型のインスタンスの作成にも使用できます。  
  
```  
var query = from cust in customers  
            select new {Name = cust.Name, Address = cust.PrimaryAddress};  
```  
  
 `new` 演算子を使用して、値型の既定コンストラクターを呼び出すこともできます。  次に例を示します。  
  
```  
int i = new int();  
```  
  
 このステートメントでは、`i` は `int` 型の既定値 `0` に初期化されます。  このステートメントは次のステートメントと同じ効果があります。  
  
```  
int i = 0;  
```  
  
 既定値の一覧については、「[既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md)」を参照してください。  
  
 [構造体](../../../csharp/language-reference/keywords/struct.md)の既定のコンストラクターを宣言すると、エラーが発生します。これは、すべての値型には、暗黙的にパブリックな既定のコンストラクターがあるためです。  パラメーター付きのコンストラクターを struct 型で宣言してその初期値を設定することは可能ですが、この手順が必要になるのは、既定以外の値が必要な場合のみです。  
  
 構造体のような値型オブジェクトはスタック領域に作成され、クラスのような参照型オブジェクトはヒープ領域に作成されます。  どちらの型のオブジェクトも自動的に破棄されますが、値型に基づくオブジェクトは、スコープの適用範囲の外になると破棄され、参照型に基づくオブジェクトは、そのオブジェクトへの最後の参照が削除された後に随時破棄されます。  大量のメモリ、ファイル ハンドル、ネットワーク接続などの固定リソースを消費する参照型では、オブジェクトができるだけすぐに破棄されるように、確定的な終了処理を採用することが望ましい場合があります。  詳細については、「[using ステートメント](../../../csharp/language-reference/keywords/using-statement.md)」を参照してください。  
  
 `new` 演算子はオーバーロードできません。  
  
 `new` 演算子によるメモリ割り当てが失敗した場合は、<xref:System.OutOfMemoryException> 例外がスローされます。  
  
## 使用例  
 次の例では、`struct` オブジェクトとクラス オブジェクトは、`new` 演算子で作成および初期化されてから、値が代入されます。  既定値と代入値が表示されます。  
  
 [!code-cs[csrefKeywordsOperator#7](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsOperator/csrefKeywordsOperators.cs#7)]  
  
 この例では、文字列の既定値が `null` です。  このため、文字列の既定値は出力されません。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [演算子のキーワード](../../../csharp/language-reference/keywords/operator-keywords.md)   
 [new](../../../csharp/language-reference/keywords/new.md)   
 [匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)