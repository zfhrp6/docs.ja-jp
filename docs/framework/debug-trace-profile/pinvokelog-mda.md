---
title: "pInvokeLog MDA | Microsoft Docs"
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
  - "signatures, platform invoke"
  - "MDAs (managed debugging assistants), platform invoke"
  - "platform invoke, run-time errors"
  - "platform invoke log"
  - "PInvokeLog MDA"
  - "managed debugging assistants (MDAs), platform invoke"
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# pInvokeLog MDA
`pInvokeLog` マネージ デバッグ アシスタント \(MDA: Managed Debugging Assistant\) は、実行中に使用された一意のプラットフォーム呼び出しシグネチャごとにアクティブ化されます。  
  
## ランタイムへの影響  
 この MDA は、CLR への影響はありません。  
  
## 出力  
 実行中に使用されたプラットフォーム呼び出しシグネチャを示すメッセージです。  
  
## 構成  
 それぞれの一致要素は、プラットフォーム呼び出しが行われた .dll ファイルをフィルター処理します。  
  
```  
<mdaConfig>  
  <assistants>  
    <pInvokeLog>  
      <filter>  
        <match dllName="user32.dll"/>  
        <match dllName="kernel32.dll"/>  
      </filter>  
    </pInvokeLog>  
  </assistants>  
</mdaConfig>  
```  
  
## 参照  
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [アンマネージ DLL 関数の処理](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)