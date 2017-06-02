---
title: "jitCompilationStart MDA | Microsoft Docs"
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
  - "JIT compilation"
  - "MDAs (managed debugging assistants), JIT compilation"
  - "JitCompilationStart MDA"
  - "managed debugging assistants (MDAs), JIT compilation"
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
caps.latest.revision: 11
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 11
---
# jitCompilationStart MDA
`jitCompilationStart` マネージ デバッグ アシスタント \(MDA:Managed Debugging Assistant\) は、Just\-In\-Time \(JIT\) コンパイラが関数のコンパイルを開始したことを報告するためにアクティブ化されます。  
  
## 症状  
 mscorjit.dll がプロセスに読み込まれたため、既にネイティブ イメージの形式内にあるプログラムのワーキング セットのサイズが増加します。  
  
## 原因  
 プログラムが依存するアセンブリの一部が、ネイティブ形式に生成されていないか、正しく登録されていません。  
  
## 解決策  
 この MDA を有効にすると、JIT コンパイルされた関数を確認できます。  関数を含むアセンブリがネイティブ形式に生成され、正しく登録されているかどうかを確認します。  
  
## ランタイムへの影響  
 この MDA は、メソッドが JIT コンパイルされる直前に、メッセージを記録します。そのため、この MDA を有効にすると、パフォーマンスに大きな影響を与えます。  メソッドがインラインである場合、この MDA は別のメッセージを生成しないことに注意してください。  
  
## 出力  
 サンプル出力を次のコード例に示します。  この出力例では、アセンブリ Test で、クラス "ns2.CO" のメソッド "m" が JIT コンパイルされたことを示します。  
  
```  
method name="Test!ns2.C0::m"  
```  
  
## 構成  
 最初に JIT コンパイルされたときに報告されたメソッドをフィルター処理するために使用できるさまざまなフィルターを、次の構成ファイルに示します。  name 属性の値を \* に設定すると、報告されたすべてのメソッドを指定できます。  
  
```  
<mdaConfig>  
  <assistants>  
    <jitCompilationStart>  
      <methods>  
        <match name="C0::m" />  
        <match name="MyMethod" />  
        <match name="C2::*" />  
        <match name="ns0::*" />  
        <match name="ns1.C0::*" />  
        <match name="ns2.C0::m" />  
        <match name="ns2.C0+N0::m" />  
      </methods>  
    </jitCompilationStart >  
  </assistants>  
</mdaConfig>  
```  
  
## 使用例  
 前の構成ファイルで使用するコード サンプルを次に示します。  
  
```  
using System;  
using System.Reflection;  
using System.Runtime.CompilerServices;  
using System.Runtime.InteropServices;  
  
public class Entry  
{  
    public static void Main(string[] args)  
    {  
        C0.m();  
        C1.MyMethod();  
        C2.m();  
  
        ns0.C0.m();  
        ns0.C0.N0.m();  
        ns0.C1.m();  
  
        ns1.C0.m();  
        ns1.C0.N0.m();  
  
        ns2.C0.m();  
        ns2.C0.N0.m();  
    }  
}  
  
public class C0  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
public class C1  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void MyMethod() { }  
}  
  
public class C2  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
namespace ns0  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
  
    public class C1  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
    }  
}  
  
namespace ns1  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
  
namespace ns2  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
```  
  
## 参照  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [相互運用マーシャリング](../../../docs/framework/interop/interop-marshaling.md)