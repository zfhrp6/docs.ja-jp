---
title: 例外処理の保護
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- code security, exception handling
- security [.NET Framework], exception handling
- secure coding, exception handling
- exception handling, security
ms.assetid: 1f3da743-9742-47ff-96e6-d0dd1e9e1c19
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fe978930a9f84e0084f79f5fe585a1ecc3bf4eb2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393043"
---
# <a name="securing-exception-handling"></a>例外処理の保護
Visual C および Visual Basic では、スタックをさらにフィルター式を実行前に、 **finally**ステートメントです。 **キャッチ**に関連付けられているブロックの後にそのフィルターが実行される、**最後に**ステートメントです。 詳細については、次を参照してください。[ユーザー フィルター例外](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md)です。 このセクションでは、この注文のセキュリティへの影響を調べます。 どのフィルター ステートメント内での順序を示す次の擬似コード例について考えますと**最後に**ステートメントを実行します。  
  
```cpp  
void Main()   
{  
    try   
    {  
        Sub();  
    }   
    except (Filter())   
    {  
        Console.WriteLine("catch");  
    }  
}  
bool Filter () {  
    Console.WriteLine("filter");  
    return true;  
}  
void Sub()   
{  
    try   
    {  
        Console.WriteLine("throw");  
        throw new Exception();  
    }   
    finally   
    {  
        Console.WriteLine("finally");  
    }  
}                        
```  
  
 このコードは、次を出力します。  
  
```  
Throw  
Filter  
Finally  
Catch  
```  
  
 フィルターを実行する前に、 **finally**ステートメントでは、セキュリティの問題は状態を他のコードの実行が利点かかる場合がありますを変更することによってもたらされるようにします。 例えば:  
  
```cpp  
try   
{  
    Alter_Security_State();  
    // This means changing anything (state variables,  
    // switching unmanaged context, impersonation, and   
    // so on) that could be exploited if malicious   
    // code ran before state is restored.  
    Do_some_work();  
}   
finally   
{  
    Restore_Security_State();  
    // This simply restores the state change above.  
}  
```  
  
 次の擬似コードは、任意のコードを実行するスタックの上位フィルターを使用できます。 同様の効果を持つ処理の他の例は、いくつかのセキュリティ チェックをバイパスする内部フラグの設定、他の id の一時的な権限の借用またはスレッドに関連付けられているカルチャを変更します。 スレッドの状態を呼び出し元のフィルター ブロックから、コードの変更を分離する例外ハンドラーを導入することをお勧めします。 ただし、例外ハンドラーを正しく導入することが重要ですか、この問題は修正されません。 次の例は、UI カルチャを切り替えるが任意の種類のスレッド状態の変更を同様に公開される可能性があります。  
  
```cpp  
YourObject.YourMethod()  
{  
   CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
   try {  
      Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
      // Do something that throws an exception.  
}  
   finally {  
      Thread.CurrentThread.CurrentUICulture = saveCulture;  
   }  
}  
```  
  
```vb  
Public Class UserCode  
   Public Shared Sub Main()  
      Try  
         Dim obj As YourObject = new YourObject  
         obj.YourMethod()  
      Catch e As Exception When FilterFunc  
         Console.WriteLine("An error occurred: '{0}'", e)  
         Console.WriteLine("Current Culture: {0}",   
Thread.CurrentThread.CurrentUICulture)  
      End Try  
   End Sub  
  
   Public Function FilterFunc As Boolean  
      Console.WriteLine("Current Culture: {0}", Thread.CurrentThread.CurrentUICulture)  
      Return True  
   End Sub  
  
End Class  
```  
  
 修正プログラムがここでは、既存をラップする**を再試行してください**/**finally**のブロック、**を再試行してください**/**キャッチ**ブロックです。 簡単に把握、 **catch throw**既存に句**再試行**/**最後に**の次の例に示すように、ブロックで、問題が解決しません。  
  
```cpp  
YourObject.YourMethod()  
{  
    CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
  
    try   
    {  
        Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
        // Do something that throws an exception.  
    }  
    catch { throw; }  
    finally   
    {  
        Thread.CurrentThread.CurrentUICulture = saveCulture;  
    }  
}  
```  
  
 問題が解決しない、 **finally**する前にステートメントが実行、`FilterFunc`コントロールを取得します。  
  
 次の例では、問題を修正するようにすることで、 **finally**句が呼び出し元の例外フィルター ブロックの例外を提供する前に実行します。  
  
```cpp  
YourObject.YourMethod()  
{  
    CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
    try    
    {  
        try   
        {  
            Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
            // Do something that throws an exception.  
        }  
        finally   
        {  
            Thread.CurrentThread.CurrentUICulture = saveCulture;  
        }  
    }  
    catch { throw; }  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [安全なコーディングのガイドライン](../../../docs/standard/security/secure-coding-guidelines.md)
