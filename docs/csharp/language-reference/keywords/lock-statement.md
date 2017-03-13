---
title: "lock ステートメント (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "lock_CSharpKeyword"
  - "lock"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "lock キーワード [C#]"
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
caps.latest.revision: 43
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 43
---
# lock ステートメント (C# リファレンス)
`lock` キーワードは、指定のオブジェクトに対する相互排他ロックを取得し、ステートメントを実行し、ロックを解放するステートメント ブロックをクリティカル セクションとしてマークします。  次の例では `lock` のステートメントが含まれています。  
  
```  
  
class Account  
{  
    decimal balance;  
    private Object thisLock = new Object();  
  
    public void Withdraw(decimal amount)  
    {  
        lock (thisLock)  
        {  
            if (amount > balance)  
            {  
                throw new Exception("Insufficient funds");  
            }  
            balance -= amount;  
        }  
    }  
}  
  
```  
  
 詳細については、「[スレッドの同期](../Topic/Thread%20Synchronization%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
## 解説  
 `lock` キーワードによって、あるスレッドがコードのクリティカル セクションになっているときは、別のスレッドはクリティカル セクションにはなりません。  ロックされたコードを別のスレッドが使おうとすると、オブジェクトが解放されるまで待機 \(ブロック\) します。  
  
 スレッドについては、「[スレッド](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md)」で説明します。  
  
 `lock` キーワードは、ブロックの最初に <xref:System.Threading.Monitor.Enter%2A> を呼び出し、ブロックの最後に <xref:System.Threading.Monitor.Exit%2A> を呼び出します。  <xref:System.Threading.ThreadInterruptedException> は <xref:System.Threading.Thread.Interrupt%2A> が `lock` のステートメントを入力するまで待機しているスレッドを中断するとがスローされます。  
  
 一般に、`public` 型またはコードの制御範囲外にあるインスタンスに対してロックしないようにしてください。  `lock (this)`、`lock (typeof (MyType))`、および `lock ("myLock")` などの一般的な構造は、このガイドラインに反しています。  
  
-   インスタンスに対してパブリックにアクセスできる場合には、`lock (this)` が問題になります。  
  
-   `MyType` に対してパブリックにアクセスできる場合には、`lock (typeof (MyType))` が問題になります。  
  
-   プロセス内で同じ文字列を使用する他のコードは同じロックを共有するので、`lock("myLock")` が問題になります。  
  
 ロックする `private` オブジェクトを定義するか、すべてのインスタンスに共通するデータを保護するために `private static` オブジェクト変数を定義することをお勧めします。  
  
 `lock` のステートメントの本体で [待機します。](../../../csharp/language-reference/keywords/await.md) のキーワードを使用できません。  
  
## 使用例  
 C\# でのロックされていないスレッドの簡単な使用例を次に示します。  
  
 [!code-cs[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]  
  
## 使用例  
 次の例では、スレッドおよび `lock` が使用されています。  `lock` ステートメントが存在する限り、ステートメント ブロックはクリティカル セクションであり、`balance` は負の数にはなりません。  
  
 [!code-cs[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 <xref:System.Reflection.MethodImplAttributes>   
 <xref:System.Threading.Mutex>   
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [スレッド](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [ステートメントのキーワード](../../../csharp/language-reference/keywords/statement-keywords.md)   
 [監視](../Topic/Monitors.md)   
 [Interlocked Operations](../Topic/Interlocked%20Operations.md)   
 [AutoResetEvent](../Topic/AutoResetEvent.md)   
 [スレッドの同期](../Topic/Thread%20Synchronization%20\(C%23%20and%20Visual%20Basic\).md)