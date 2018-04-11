---
title: lock ステートメント (C# リファレンス)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
caps.latest.revision: 43
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eb48c2b1554ad2817406eaef42b4cb336ea46862
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="lock-statement-c-reference"></a>lock ステートメント (C# リファレンス)
`lock` キーワードは、ステートメント ブロックをクリティカル セクションとして指定します。このためには、特定のオブジェクトの相互排他ロックを取得し、ステートメントを実行して、ロックを解放します。 次の例では、`lock` ステートメントが使用されています。  
  
```csharp  
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
  
 詳細については、「[スレッドの同期](../../programming-guide/concepts/threading/thread-synchronization.md)」を参照してください。  
  
## <a name="remarks"></a>コメント  
 `lock` キーワードは、コードのクリティカル セクションに複数のスレッドが同時に進入することを防ぐ働きをします。 これから実行しようとしているコードがロックされている場合、別のスレッドは、そのオブジェクトが解放されるまで待機 (ブロック) 状態になります。  
  
 スレッド処理については、「[スレッド処理](../../programming-guide/concepts/threading/index.md)」を参照してください。  
  
 `lock` キーワードは、ブロックの先頭で <xref:System.Threading.Monitor.Enter%2A> を呼び出し、ブロックの末尾で <xref:System.Threading.Monitor.Exit%2A> を呼び出します。 `lock` ステートメントの実行を待っているスレッドを <xref:System.Threading.Thread.Interrupt%2A> で中断すると、<xref:System.Threading.ThreadInterruptedException> がスローされます。  
  
 一般に、`public` 型 (つまり、コードの制御が及ばないインスタンス) をロックすることは避けてください。 `lock (this)`、`lock (typeof (MyType))`、`lock ("myLock")` は、このガイドラインに違反する代表的なコンストラクトです。  
  
-   `lock (this)` は、このインスタンスにパブリックにアクセスできる場合に問題となります。  
  
-   `lock (typeof (MyType))` は、`MyType` にパブリックにアクセスできる場合に問題となります。  
  
-   `lock("myLock")` が問題となる理由は、同じ文字列を使用するコードがプロセス内に他にも存在した場合、そのコードも同じロックを共有するためです。  
  
 `private` オブジェクトを定義してロックの適用対象を限定するか、`private static` オブジェクト変数を定義して、すべてのインスタンスに共通するデータを保護することをお勧めします。  
  
 `lock` ステートメントの本体で [await](../../../csharp/language-reference/keywords/await.md) キーワードを使用することはできません。  
  
## <a name="example"></a>例  
 次のサンプルでは、C# でロックされていないスレッドの簡単な使用例を示しています。  
  
 [!code-csharp[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]  
  
## <a name="example"></a>例  
 次のサンプルでは、スレッドと `lock` を使用しています。 `lock` ステートメントが存在する限り、このステートメント ブロックはクリティカル セクションとなり、`balance` が負の数になることはありません。  
  
 [!code-csharp[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Reflection.MethodImplAttributes>  
 <xref:System.Threading.Mutex>  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [スレッド化](../../programming-guide/concepts/threading/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [ステートメントのキーワード](../../../csharp/language-reference/keywords/statement-keywords.md)  
 <xref:System.Threading.Monitor>  
 [インタロックされた操作](../../../standard/threading/interlocked-operations.md)  
 [AutoResetEvent](../../../standard/threading/autoresetevent.md)  
 [スレッドの同期](../../programming-guide/concepts/threading/thread-synchronization.md)
