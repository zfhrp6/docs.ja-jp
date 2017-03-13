---
title: "ポインター変換 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ポインター [C#], 変換"
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# ポインター変換 (C# プログラミング ガイド)
定義済みの暗黙のポインター変換を次の表に示します。  暗黙の変換は、メソッドの呼び出しや代入ステートメントなど、多くの状況で発生することがあります。  
  
## 暗黙のポインター変換  
  
|変換前|目的|  
|---------|--------|  
|任意のポインター型|void\*|  
|null|任意のポインター型|  
  
 明示的なポインター変換には暗黙の変換がなく、キャスト式を使用して変換を実行します。  これらの変換を次に示します。  
  
## 明示的なポインター変換  
  
|変換前|目的|  
|---------|--------|  
|任意のポインター型|他の任意のポインター型|  
|sbyte、byte、short、ushort、int、uint、long、ulong|任意のポインター型|  
|任意のポインター型|sbyte、byte、short、ushort、int、uint、long、ulong|  
  
## 使用例  
 次の例では、`int` へのポインターを `byte` へのポインターに変換しています。  このポインターは、変数のアドレスの最下位バイトを指すことに注意してください。  結果を `int` のサイズ \(4 バイト\) だけ連続してインクリメントすると、変数の残りのバイトを表示できます。  
  
 [!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-cs[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ポインター式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [型](../../../csharp/language-reference/keywords/types.md)   
 [安全でない](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)