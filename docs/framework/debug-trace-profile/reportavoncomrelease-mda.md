---
title: "reportAvOnComRelease MDA | Microsoft Docs"
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
  - "MDAs (managed debugging assistants), reference counting errors"
  - "exceptions, reference counting errors"
  - "ReportAvOnComRelease MDA"
  - "COM release access violations"
  - "user reference counting errors"
  - "managed debugging assistants (MDAs), reference counting errors"
  - "report access violation on Com release"
  - "reference counting errors"
ms.assetid: a2b86b63-08b2-4943-b344-3c2cf46ccd31
caps.latest.revision: 15
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 15
---
# reportAvOnComRelease MDA
COM 相互運用を実行していて、COM の生呼び出しと組み合わせた `reportAvOnComRelease` または <xref:System.Runtime.InteropServices.Marshal.Release%2A> メソッドを使用しているときに、ユーザー参照カウントのエラーが原因で例外がスローされると、<xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> マネージ デバッグ アシスタント \(MDA\) がアクティブ化されます。  
  
## 症状  
 アクセス違反およびメモリ破損が発生します。  
  
## 原因  
 COM 相互運用を実行していて、生の COM 呼び出しと組み合わせた <xref:System.Runtime.InteropServices.Marshal.Release%2A> または <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> メソッドを使用しているときに、ユーザー参照カウントのエラーが原因で例外がスローされることがあります。  通常、この例外は破棄されます。これは、破棄しないと CLR でアクセス違反が発生し、ダウンしてしまうためです。  このアシスタントが有効な場合は、そのような例外を単に破棄するのではなく、検出して報告できます。  
  
## 解決策  
 参照カウントのコードを調べてエラーを探します。また、オブジェクトのネイティブ クライアントに参照カウントのエラーがないかどうかも調べます。  
  
## ランタイムへの影響  
 2 つのモードを利用できます。  `allowAv` 属性が `true` の場合、アシスタントは、ランタイムがアクセス違反を破棄しないようにします。  `allowAv` が `false` の場合 \(既定\)、ランタイムはアクセス違反を破棄しますが、例外がスローされて破棄されたことを通知する警告メッセージがユーザーに報告されます。  
  
## 出力  
 可能な場合、出力には COM インターフェイス ポインターの元の vtable が含まれます。  それ以外の場合は、情報メッセージが表示されます。  
  
## 構成  
  
```  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## 参照  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [相互運用マーシャリング](../../../docs/framework/interop/interop-marshaling.md)