---
title: "reentrancy MDA | Microsoft Docs"
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
  - "unmanaged code, debugging"
  - "transitioning threads unmanaged to managed code"
  - "reentrancy MDA"
  - "reentrancy without an orderly transition"
  - "managed debugging assistants (MDAs), reentrancy"
  - "illegal reentrancy"
  - "MDAs (managed debugging assistants), reentrancy"
  - "threading [.NET Framework], managed debugging assistants"
  - "managed code, debugging"
  - "native debugging, MDAs"
ms.assetid: 7240c3f3-7df8-4b03-bbf1-17cdce142d45
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# reentrancy MDA
`reentrancy` マネージ デバッグ アシスタント \(MDA: Managed Debugging Assistant\) は、マネージ コードからネイティブ コードへの以前の切り替えが順序正しい遷移によって行われなかった場合に、ネイティブ コードからマネージ コードへの遷移を実行しようとするとアクティブになります。  
  
## 症状  
 ネイティブ コードからマネージ コードに遷移するときに、オブジェクト ヒープが破損したり、その他の重大なエラーが発生したりします。  
  
 ネイティブ コードとマネージ コードの間で両方向に切り替わるスレッドでは、正しい順序で遷移を実行する必要があります。  ただし、ベクトル化例外ハンドラーなど、オペレーティング システムの下位の機能拡張ポイントでは、正しい順序で遷移を実行しなくてもマネージ コードからネイティブ コードに切り替えることができます。このような切り替えは、共通言語ランタイム \(CLR\) ではなく、オペレーティング システムの制御に従います。これらの機能拡張ポイント内で実行されるネイティブ コードでは、マネージ コードへのコールバックを避ける必要があります。  
  
## 原因  
 ベクトル化例外ハンドラーなどの、オペレーティング システムの下位の機能拡張ポイントが、マネージ コードの実行時にアクティブになっています。この機能拡張ポイントを介して呼び出されたアプリケーション コードが、マネージ コードへのコールバックを実行しようとしています。  
  
 この問題の原因は、常にアプリケーション コードにあります。  
  
## 解決策  
 スタック トレースを調べて、この MDA をアクティブにしているスレッドがないか確認します。そのスレッドが、マネージ コードへの無効な呼び出しを試みています。スタック トレースを調べることにより、該当する機能拡張ポイントを使用しているアプリケーション コード、この機能拡張ポイントを提供しているオペレーティング システム コード、および機能拡張ポイントによって中断されたマネージ コードが明らかになります。  
  
 たとえば、ベクトル化例外ハンドラーの内部からマネージ コードの呼び出しを試みると MDA がアクティブになります。スタックをチェックすると、オペレーティング システムの例外処理コードと一部のマネージ コードが、<xref:System.DivideByZeroException> や <xref:System.AccessViolationException> などの例外の原因となっていることがわかります。  
  
 この場合、ベクトル化例外ハンドラーをアンマネージ コードに完全に実装することが適切な解決策です。  
  
## ランタイムへの影響  
 この MDA は、CLR への影響はありません。  
  
## 出力  
 この MDA によって、無効な再入が試みられていることが報告されます。スレッドのスタックをチェックし、この問題の原因と解決方法を判断します。  出力例を次に示します。  
  
```  
Additional Information: Attempting to call into managed code without   
transitioning out first.  Do not attempt to run managed code inside   
low-level native extensibility points. Managed Debugging Assistant   
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## 構成  
  
```  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## 使用例  
 次のコード例では、<xref:System.AccessViolationException> がスローされます。この例外がスローされると、ベクター例外処理をサポートする Windows の各バージョンでは、マネージ ベクトル化例外ハンドラーが呼び出されます。`reentrancy` MDA が有効になっていると、オペレーティング システムのベクトル化例外処理サポート コードから `MyHandler` の呼び出しが試みられたときに、この MDA がアクティブになります。  
  
```  
using System;  
public delegate int ExceptionHandler(IntPtr ptrExceptionInfo);  
  
public class Reenter   
{  
    public static ExceptionHandler keepAlive;  
  
    [System.Runtime.InteropServices.DllImport("kernel32", ExactSpelling=true,   
        CharSet=System.Runtime.InteropServices.CharSet.Auto)]  
    public static extern IntPtr AddVectoredExceptionHandler(int bFirst,   
        ExceptionHandler handler);  
  
    static int MyHandler(IntPtr ptrExceptionInfo)   
    {  
        // EXCEPTION_CONTINUE_SEARCH  
        return 0;  
    }  
    void Run() {}  
  
    static void Main()   
    {  
        keepAlive = new ExceptionHandler(Reenter.MyHandler);  
        IntPtr ret = AddVectoredExceptionHandler(1, keepAlive);  
        try   
        {  
            // Dispatch on null should AV.  
            Reenter r = null;   
            r.Run();  
        }   
        catch { }  
    }  
}  
```  
  
## 参照  
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)