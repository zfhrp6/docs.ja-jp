---
title: "名前付きメソッドを使用したデリゲートと匿名メソッドを使用したデリゲート (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "デリゲート [C#], 名前付きメソッドと匿名メソッド"
  - "メソッド [C#], デリゲート"
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# 名前付きメソッドを使用したデリゲートと匿名メソッドを使用したデリゲート (C# プログラミング ガイド)
[デリゲート](../../../csharp/language-reference/keywords/delegate.md)は、名前付きメソッドに関連付けることができます。  名前付きメソッドを使用してデリゲートをインスタンス化するときは、次のようにメソッドをパラメーターとして渡します。  
  
 [!code-cs[csProgGuideDelegates#1](../../../csharp/programming-guide/delegates/codesnippet/csharp/csrefDelegates/Delegates.cs#1)]  
  
 これを名前付きメソッドの使用と言います。  名前付きメソッドで構築されたデリゲートは、[静的](../../../csharp/language-reference/keywords/static.md)メソッドもインスタンス メソッドもカプセル化できます。  旧バージョンの C\# では、名前付きメソッドを使用するのが、デリゲートをインスタンス化する唯一の方法です。  ただし、新しいメソッドを作成するのがオーバーヘッドの点で望ましくない場合、C\# では、デリゲートをインスタンス化し、デリゲートが呼び出されたときに処理するコード ブロックを直接指定できます。  ブロックには、ラムダ式と匿名メソッドのいずれかを含めることができます。  詳細については、「[匿名関数](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)」を参照してください。  
  
## 解説  
 デリゲート パラメーターとして渡すメソッドは、デリゲート宣言と同じシグネチャを持つ必要があります。  
  
 デリゲート インスタンスは、静的メソッドもインスタンス メソッドもカプセル化できます。  
  
 デリゲートは、[out](../../../csharp/language-reference/keywords/out.md) パラメーターを使用できますが、マルチキャスト イベント デリゲートでは、どのデリゲートが呼び出されるかわからないので、このパラメーターを使用することはお勧めしません。  
  
## 例 1  
 デリゲートの宣言と使用について、簡単な例を次に示します。  デリゲート `Del` とそれに関連付けられているメソッド `MultiplyNumbers` は共に同じシグネチャを持つことに注意してください。  
  
 [!code-cs[csProgGuideDelegates#2](../../../csharp/programming-guide/delegates/codesnippet/csharp/csrefDelegates/Delegates.cs#2)]  
  
## 例 2  
 次の例では、1 つのデリゲートを静的メソッドとインスタンス メソッドの両方に割り当て、各メソッドから特定の情報を戻します。  
  
 [!code-cs[csProgGuideDelegates#3](../../../csharp/programming-guide/delegates/codesnippet/csharp/csrefDelegates/Delegates.cs#3)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [デリゲート](../../../csharp/programming-guide/delegates/index.md)   
 [匿名メソッド](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)   
 [方法 : デリゲートを結合する \(マルチキャスト デリゲート\)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)   
 [イベント](../../../csharp/programming-guide/events/index.md)