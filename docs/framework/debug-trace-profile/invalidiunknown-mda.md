---
title: "invalidIUnknown MDA | Microsoft Docs"
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
  - "MDAs (managed debugging assistants), invalid IUnknown pointer"
  - "InvalidIUnknown MDA"
  - "invalid IUnknown pointers"
  - "IUnknown pointers"
  - "managed debugging assistants (MDAs), invalid IUnknown pointer"
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# invalidIUnknown MDA
`invalidIUnknown` マネージ デバッグ アシスタント \(MDA: Managed Debugging Assistant\) は、無効な `IUnknown` ポインターがネイティブ コードからマネージ コードに渡されるとアクティブ化されます。  `IUnknown` インターフェイスが照会されたときに、`IUnknown` は、成功したことを返すことができませんでした。  
  
## 症状  
 引数のマーシャリング中に COM インターフェイス ポインターをマーシャリングすると、予期しないエラーが発生します。  
  
## 原因  
 CLR に渡された COM インターフェイスで、`QueryInterface` の実装が正しくありません。  
  
## 解像度  
 `QueryInterface` の実装を修正します。  
  
## ランタイムへの影響  
 この MDA は CLR に影響しません。  
  
## 出力  
 エラーの説明です。  
  
## 構成  
  
```  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## 参照  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [相互運用マーシャリング](../../../docs/framework/interop/interop-marshaling.md)