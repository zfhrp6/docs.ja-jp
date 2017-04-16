---
title: "virtualCERCall MDA | Microsoft Docs"
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
  - "virtualCERCall MDA"
  - "virtual CER calls"
  - "constrained execution regions"
  - "CER calls"
  - "managed debugging assistants (MDAs), CER calls"
ms.assetid: 1eb18c7a-f5e0-443f-80fb-67bfbb047da2
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# virtualCERCall MDA
`virtualCERCall` マネージ デバッグ アシスタント \(MDA\) は、制約された実行領域 \(CER: Constrained Execution Region\) 呼び出し先内の呼び出しサイトが仮想ターゲット \(つまり、最終でない仮想メソッドの呼び出しまたはインターフェイスを使用した呼び出し\) を参照していることを示す警告としてアクティブになります。  共通言語ランタイム \(CLR: Common Language Runtime\) では、中間言語とメタデータ分析のみに基づいて、これらの呼び出しの対象メソッドを予測することはできません。  その結果、コール ツリーを CER グラフの一部として作成できず、そのサブツリーにおけるスレッドの中止を自動的に回避できません。  この MDA は、実行時に呼び出し対象の計算に必要な追加情報が明らかになると、<xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> メソッドを明示的に呼び出して CER を拡張する必要がある場合に警告を行います。  
  
## 症状  
 スレッドが中止されている場合や、アプリケーション ドメインがアンロードされている場合に、CER が実行されません。  
  
## 原因  
 自動的に作成できない仮想メソッドの呼び出しが CER に含まれています。  
  
## 解決策  
 仮想メソッドの <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> を呼び出します。  
  
## ランタイムへの影響  
 この MDA は、CLR への影響はありません。  
  
## 出力  
  
```  
Method 'MethodWithCer', while executing within a constrained execution region, makes a call  
at IL offset 0x0024 to 'VirtualMethod', which is virtual and cannot be prepared automatically  
at compile time. The caller must ensure this method is prepared explicitly at  
runtime before entering the constrained execution region.  
method name="VirtualMethod"  
declaringType name="VirtualCERCall+MyClass"  
  declaringModule name="mda"  
    callsite name="MethodWithCer" offset="0x0024"  
```  
  
## 構成  
  
```  
<mdaConfig>  
  <assistants>  
    < VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## 使用例  
  
```  
class MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    virtual void VirtualMethod()  
    {  
        ...  
    }  
}  
  
class MyDerivedClass : MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    override void VirtualMethod()  
    {  
        ...  
    }  
}  
  
void MethodWithCer(MyClass object)  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    try  
    {  
        ...  
    }  
    finally  
    {  
        // Start of the CER.  
  
        // Cannot tell at analysis time whether object is a MyClass  
        // or a MyDerivedClass, so we do not know which version of   
        // VirtualMethod we are going to call.  
        object.VirtualMethod();  
    }  
}  
```  
  
## 参照  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [相互運用マーシャリング](../../../docs/framework/interop/interop-marshaling.md)