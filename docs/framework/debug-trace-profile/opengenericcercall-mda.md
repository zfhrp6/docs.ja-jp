---
title: "openGenericCERCall MDA | Microsoft Docs"
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
  - "MDAs (managed debugging assistants), CER calls"
  - "open generic CER calls"
  - "constrained execution regions"
  - "openGenericCERCall MDA"
  - "CER calls"
  - "managed debugging assistants (MDAs), CER calls"
  - "generics [.NET Framework], open generic CER calls"
ms.assetid: da3e4ff3-2e67-4668-9720-fa776c97407e
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# openGenericCERCall MDA
`openGenericCERCall` マネージ デバッグ アシスタントは、ルート メソッドにジェネリック型変数を持つ制約された実行領域 \(CER: Constrained Execution Region\) グラフが JIT コンパイル時またはネイティブ イメージ生成時に処理されている場合に、少なくとも 1 つのジェネリック型変数がオブジェクト参照型であることを警告するためにアクティブ化されます。  
  
## 症状  
 スレッドが中止されたときや、アプリケーション ドメインがアンロードされたときに、CER が実行されません。  
  
## 原因  
 JIT コンパイル時には、処理結果のコードが共有され、オブジェクト参照型変数がそれぞれ任意のオブジェクト参照型になる可能性があるため、オブジェクト参照型を含むインスタンス化は代理にすぎません。  これにより、一部のランタイム リソースを前もって準備することが妨げられることがあります。  
  
 特に、ジェネリック型変数を含むメソッドは、バックグラウンドでリソースを非効率的に割り当てる可能性があります。  これらのメソッドは、ジェネリック辞書エントリと呼ばれます。  たとえば、`T` がジェネリック型変数である `List<T> list = new List<T>();`  というステートメントの場合、ランタイムは、実行時に正確なインスタンス化 \(`List<Object>, List<String>` `` など\) を検索する必要があり、さらにその作成が必要になる場合があります。  この操作は、メモリ不足など、開発者が制御できないさまざまな理由で失敗することがあります。  
  
 この MDA は、JIT コンパイル時にのみアクティブになり、正確なインスタンス化が存在するときにはアクティブになりません。  
  
 この MDA がアクティブになるときは、CER が不正なインスタンス化に対して機能しないという症状が発生する可能性があります。  実際、MDA がアクティブになる状況下では、ランタイムは CER の実装を試みません。  そのため、開発者が CER の共有インスタンス化を使用している場合、目的の CER の領域内で発生した JIT コンパイル エラー、ジェネリック型の読み込みエラー、スレッドの中止などはキャッチされません。  
  
## 解決策  
 CER が存在する可能性があるメソッドには、オブジェクト参照型であるジェネリック型変数を使用しないでください。  
  
## ランタイムへの影響  
 この MDA は、CLR への影響はありません。  
  
## 出力  
 この MDA の出力サンプルを次に示します。  
  
 `Method 'GenericMethodWithCer', which contains at least one constrained execution region, cannot be prepared automatically since it has one or more unbound generic type parameters.`  
  
 `The caller must ensure this method is prepared explicitly at run time prior to execution.`  
  
 `method name="GenericMethodWithCer"`  
  
 `declaringType name="OpenGenericCERCall"`  
  
## 構成  
  
```  
<mdaConfig>  
  <assistants>  
    <openGenericCERCall/>  
  </assistants>  
</mdaConfig>  
```  
  
## 使用例  
 CER コードは実行されません。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Runtime.CompilerServices;  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        CallGenericMethods();  
    }  
    static void CallGenericMethods()  
    {  
        // This call is correct. The instantiation of the method  
        // contains only nonreference types.  
        MyClass.GenericMethodWithCer<int>();  
  
        // This call is incorrect. A shared version of the method that  
        // cannot be completely analyzed will be JIT-compiled. The   
        // MDA will be activated at JIT-compile time, not at run time.  
        MyClass.GenericMethodWithCer<String>();  
    }  
}  
  
    class MyClass  
{  
    public static void GenericMethodWithCer<T>()  
    {  
        RuntimeHelpers.PrepareConstrainedRegions();  
        try  
        {  
  
        }  
        finally  
        {  
            // This is the start of the CER.  
            Console.WriteLine("In finally block.");  
        }  
    }  
}  
```  
  
## 参照  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>   
 <xref:System.Runtime.ConstrainedExecution>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)