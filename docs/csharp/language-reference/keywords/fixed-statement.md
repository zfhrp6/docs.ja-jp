---
title: "fixed ステートメント (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "fixed_CSharpKeyword"
  - "fixed"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "fixed キーワード [C#]"
ms.assetid: 7ea6db08-ad49-4a7a-b934-d8c4acad1c3a
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# fixed ステートメント (C# リファレンス)
`fixed` ステートメントは、移動可能な変数がガベージ コレクターにより再配置されることを防ぎます。  `fixed` ステートメントは、[unsafe](../../../csharp/language-reference/keywords/unsafe.md) コンテキストでのみ使用できます。  `Fixed` を使用して、[固定サイズ バッファー](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)を作成することもできます。  
  
 `fixed` ステートメントは、マネージ変数へのポインターを設定し、ステートメントの実行時にマネージ変数を "固定" します。  `fixed` がない場合、ガベージ コレクションが予期できないかたちで移動可能なマネージ変数を再配置するため、マネージ変数へのポインターはほとんど役に立ちません。  C\# コンパイラの場合、`fixed` ステートメントでは、マネージ変数にポインターを割り当てることだけができます。  
  
 [!code-cs[csrefKeywordsFixedLock#1](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefFixedLock/csrefKeywordsFixedLock.cs#1)]  
  
 ポインターは、配列、文字列、固定サイズ バッファー、または変数のアドレスを使用して初期化できます。  次の例は、変数のアドレス、配列、および文字列を使用方法を示しています。  固定サイズ バッファーの詳細については、「[固定サイズ バッファー](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)」を参照してください。  
  
 [!code-cs[csrefKeywordsFixedLock#2](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefFixedLock/csrefKeywordsFixedLock.cs#2)]  
  
 同じ型の場合は、複数のポインターを初期化できます。  
  
```  
fixed (byte* ps = srcarray, pd = dstarray) {...}  
```  
  
 型の異なるポインターを初期化するには、次の例のように、`fixed` ステートメントを単純に入れ子にします。  
  
 [!code-cs[csrefKeywordsFixedLock#3](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefFixedLock/csrefKeywordsFixedLock.cs#3)]  
  
 ステートメントのコードを実行すると、固定された変数の固定が解除され、ガベージ コレクションの対象になります。  そのため、`fixed` ステートメントの外部にある変数へのポインターは指定しないでください。  
  
> [!NOTE]
>  fixed ステートメントで初期化されたポインターは変更できません。  
  
 unsafe モードでは、スタックにメモリを割り当てることができます。スタックは、ガベージ コレクションの対象にはならないので、固定は必要ありません。  詳細については、「[stackalloc \(C\# リファレンス\)](../../../csharp/language-reference/keywords/stackalloc.md)」を参照してください。  
  
## 使用例  
 [!code-cs[csrefKeywordsFixedLock#4](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefFixedLock/csrefKeywordsFixedLock.cs#4)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [安全でない](../../../csharp/language-reference/keywords/unsafe.md)   
 [固定サイズ バッファー](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)