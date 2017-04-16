---
title: "例外処理の保護 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "コード セキュリティ, 例外処理"
  - "例外処理, セキュリティ"
  - "安全なコーディング, 例外処理"
  - "セキュリティ [.NET Framework], 例外処理"
ms.assetid: 1f3da743-9742-47ff-96e6-d0dd1e9e1c19
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 10
---
# 例外処理の保護
Visual C\+\+ と Visual Basic では、**finally** ステートメントの前に、スタックの最上位にあるフィルター式が実行されます。  このフィルターに対応した **catch** ブロックは、**finally** ステートメントの後に実行されます。  詳細については、「[ユーザー フィルター例外の使用](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md)」を参照してください。  このセクションでは、この順番に関するセキュリティについて調べます。  フィルター ステートメントと **finally** ステートメントの実行順序を示す次の架空のサンプル コードについて考慮します。  
  
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
  
 このコードの出力を次に示します。  
  
```  
Throw  
Filter  
Finally  
Catch  
```  
  
 フィルターは **finally** ステートメントの前に実行されるため、セキュリティの問題は状態を変更する任意のコードによってもたらされ、他のコードの実行を利用される可能性があります。  たとえば、次のようになります。  
  
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
  
 この架空のコードでは、スタックの上位にあるフィルターが任意のコードを実行できます。  同じような効果を持つ処理の別の例として、他の ID の一時的な偽装があります。この偽装では、いくつかのセキュリティ チェックを迂回する内部フラグが設定されるか、スレッドに対応するカルチャが変更されます。  解決方法として、例外ハンドラーを導入し、コードの変更を呼び出し元のフィルター ブロックからスレッド状態に分離することをお勧めします。  しかし、例外ハンドラーを正しく導入することが重要で、これができないと問題は解決されません。  次の例では、UI カルチャを切り替えますが、どのような種類のスレッド状態の変更も同様に公開されます。  
  
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
  
 このケースの正しい解決方法は、既存の **try**\/**finally** ブロックを **try**\/**catch** ブロック内にラップすることです。  **catch\-throw** 句を既存の **try**\/**finally** ブロックに単に導入するだけでは、問題は解決されません。この例を次に示します。  
  
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
  
 **finally** ステートメントは `FilterFunc` が制御を取得する前に実行されないため、この例では問題を解決できません。  
  
 呼び出し元の例外フィルター ブロックで例外を発生させる前に、**finally** 句を実行することによって問題を解決する例を次に示します。  
  
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
  
## 参照  
 [安全なコーディングのガイドライン](../../../docs/standard/security/secure-coding-guidelines.md)