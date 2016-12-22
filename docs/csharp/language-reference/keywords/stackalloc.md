---
title: "stackalloc (C# リファレンス) | Microsoft Docs"
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
  - "stackalloc_CSharpKeyword"
  - "stackalloc"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "stackalloc キーワード [C#]"
ms.assetid: adc04c28-3ed2-4326-807a-7545df92b852
caps.latest.revision: 27
caps.handback.revision: 27
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# stackalloc (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`stackalloc` キーワードは、unsafe コード コンテキストで、スタックにメモリ ブロックを割り当てるために使用されます。  
  
```  
int* block = stackalloc int[100];  
```  
  
## 解説  
 このキーワードは、ローカル変数初期化子でだけ有効です。  次のコードはコンパイル エラーになります。  
  
```  
int* block;  
// The following assignment statement causes compiler errors. You  
// can use stackalloc only when declaring and initializing a local   
// variable.  
block = stackalloc int[100];  
```  
  
 ポインター型が使用されるので、`stackalloc` は [unsafe](../../../csharp/language-reference/keywords/unsafe.md) コンテキストを必要とします。  詳細については、「[unsafe コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md)」を参照してください。  
  
 `stackalloc` は、C ランタイム ライブラリの [\_alloca](/visual-cpp/c-runtime-library/reference/alloca) に似ています。  
  
 フィボナッチの数列の最初の 20 個の数値を計算して表示するコード例を次に示します。  それぞれの数値は、前の 2 つの数値の和になっています。  このコードでは、`int` 型の要素を 20 個保持するのに十分なサイズを持つメモリ ブロックが、ヒープではなくスタックに割り当てられます。  割り当てられたブロックのアドレスは、`fib` ポインターに格納されます。  このメモリは、ガベージ コレクションの対象外であるため、[fixed](../../../csharp/language-reference/keywords/fixed-statement.md) を使用して固定する必要はありません。  メモリ ブロックの有効期間は、このブロックを定義するメソッドの有効期間に限定されます。  メソッドから制御が戻る前にメモリを解放することはできません。  
  
## 使用例  
 [!code-cs[csrefKeywordsOperator#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/stackalloc_1.cs)]  
  
## セキュリティ  
 アンセーフ コードは、セーフ コードほど安全ではありません。  ただし、`stackalloc` を使用すると、共通言語ランタイム \(CLR: Common Language Runtime\) のバッファー オーバーラン検出機能が自動的に有効になります。  バッファー オーバーランが検出されると、悪意のあるコードが実行される可能性を最小限に抑えるため、プロセスはできる限り迅速に終了されます。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [演算子のキーワード](../../../csharp/language-reference/keywords/operator-keywords.md)   
 [unsafe コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md)