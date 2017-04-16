---
title: "dllMainReturnsFalse MDA | Microsoft Docs"
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
  - "managed debugging assistants (MDAs), DllMain returns false"
  - "DllMainReturnsFalse MDA"
  - "DllMain function"
  - "MDAs (managed debugging assistants), DllMain returns false"
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
caps.latest.revision: 12
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 12
---
# dllMainReturnsFalse MDA
`dllMainReturnsFalse` マネージ デバッグ アシスタント \(MDA: Managed Debugging Assistant\) は、ユーザー アセンブリのマネージ `DllMain` 関数が DLL\_PROCESS\_ATTACH という理由で呼び出され、FALSE を返した場合にアクティブ化されます。  
  
## 症状  
 `DllMain` 関数が FALSE を返し、適切に実行されなかったことを示します。  通常、`DllMain` 関数には重要な初期化コードが含まれているため、これにより非決定性の問題が生じることがあります。  
  
## 原因  
 読み込み時にDLL 初期化で、`DllMain` 関数が理由 DLL\_PROCESS\_ATTACH で呼び出されました。  FALSE が返された場合、DLL 初期化に失敗したことを表します。  
  
## 解決策  
 失敗した DLL の `DllMain` 関数のコードを分析し、初期化エラーの原因を特定します。  
  
## ランタイムへの影響  
 この MDA は、CLR への影響はありません。  `DllMain` の戻り値に関するデータを報告するだけです。  
  
## 出力  
 理由 DLL\_PROCESS\_ATTACH で呼び出された `DllMain` 関数が FALSE を返したことを示すメッセージです。  この MDA は、`DllMain` がマネージ コードで実装されている場合だけ、アクティブ化されます。  
  
## 構成  
  
```  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## 参照  
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)