---
title: "invalidVariant MDA | Microsoft Docs"
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
  - "MDAs (managed debugging assistants), invalid variant"
  - "VARIANT type errors"
  - "InvalidVariant MDA"
  - "invalid VARIANT types"
  - "managed debugging assistants (MDAs), invalid variant"
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
caps.latest.revision: 11
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 11
---
# invalidVariant MDA
`invalidVariant` マネージ デバッグ アシスタント \(MDA: Managed Debugging Assistant\) は、ネイティブ コードまたはアンマネージ コードからマネージ コードへの呼び出し時に、無効な `VARIANT` 構造体が見つかるとアクティブ化されます。  
  
## 症状  
 `VARIANT` からオブジェクトへのマーシャリングを含む、ネイティブ コードとマネージ コードの間の遷移中に、予期しない動作が発生します。  
  
## 原因  
 ネイティブ コードが、不適切な `VARIANT` 構造体をマネージ コードに渡しています。  ランタイムは、この `VARIANT` をオブジェクトにマーシャリングしようとし、`VARIANT` が有効でない場合に MDA がアクティブ化されます。  無効な `VARIANT` には、`VARTYPE` VT\_EMPTY &#124; VT\_BYREF の `VARIANT` や、`VARTYPE` VT\_VARIANT の `VARIANT` などがあります。  
  
## 解決策  
 `VARIANT` を渡すネイティブ コードまたはアンマネージ コードでは、`VARIANT` の形式と初期化が正しいことを確認する必要があります。  
  
## ランタイムへの影響  
 この MDA は、ランタイムの動作への影響はありません。  
  
## 出力  
 無効な `VARIANT` がアンマネージ モジュールによりマネージ コードに渡されたことを、ランタイムが検出したことを示す MDA メッセージです。  
  
## 構成  
  
```  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## 参照  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [相互運用マーシャリング](../../../docs/framework/interop/interop-marshaling.md)