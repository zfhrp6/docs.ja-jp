---
title: "invalidGCHandleCookie MDA | Microsoft Docs"
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
  - "MDAs (managed debugging assistants), invalid cookies"
  - "cookies, invalid"
  - "managed debugging assistants (MDAs), invalid cookies"
  - "InvalidGCHandleCookie MDA"
  - "invalid cookies"
ms.assetid: 613ad742-3c11-401d-a6b3-893ceb8de4f8
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# invalidGCHandleCookie MDA
`invalidGCHandleCookie` マネージ デバッグ アシスタント \(MDA: Managed Debugging Assistant\) は、無効な <xref:System.IntPtr> クッキーから <xref:System.Runtime.InteropServices.GCHandle> への変換が試行されたときにアクティブ化されます。  
  
## 症状  
 <xref:System.IntPtr> から <xref:System.Runtime.InteropServices.GCHandle> を使用または取得しようとしたときに、アクセス違反やメモリ破損などの未定義の動作が発生します。  
  
## 原因  
 クッキーが元来、 <xref:System.Runtime.InteropServices.GCHandle> から作成されていないか、既に解放された <xref:System.Runtime.InteropServices.GCHandle> であるか、異なるアプリケーション ドメインの <xref:System.Runtime.InteropServices.GCHandle> に対するクッキーであるか、または<xref:System.Runtime.InteropServices.GCHandle> としてネイティブ コードにマーシャリングされたが、キャストが試行された <xref:System.IntPtr> として CLR に返されたため、クッキーが無効になっている可能性があります。  
  
## 解決策  
 <xref:System.Runtime.InteropServices.GCHandle> に有効な <xref:System.IntPtr> クッキーを指定します。  
  
## ランタイムへの影響  
 この MDA を有効にすると、返されるクッキー値は MDA が無効のときに返されるクッキー値と異なるため、デバッガーはオブジェクトまでのルートをたどることができなくなります。  
  
## 出力  
 無効な <xref:System.IntPtr> クッキー値が報告されます。  
  
## 構成  
  
```  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## 参照  
 <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>   
 <xref:System.Runtime.InteropServices.GCHandle>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)