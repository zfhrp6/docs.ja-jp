---
title: "軽減策: EventSource.WriteEvent メソッドの呼び出し | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 327a9fdb-ba8e-40f7-89e5-4c89b46e594f
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# 軽減策: EventSource.WriteEvent メソッドの呼び出し
[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] は、<xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> から派生したクラスの ETW イベント メソッドと基底クラスの <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> メソッド間のコントラクトを強制します。 ETW イベント メソッドは、<xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> メソッドをイベント メソッドに渡された同じ引数が続くイベント ID に渡す必要があります。  
  
## 影響  
 次の方法で定義される ETW イベント メソッドはコントラクトを中断します。  
  
```  
  
[Event(2, Level = EventLevel.Informational)] public void Info2(string message) { base.WriteEvent(2, message, "-"); }  
  
```  
  
 このコントラクトに違反している場合、<xref:System.IndexOutOfRangeException> オブジェクトが進行中の <xref:System.Diagnostics.Tracing.EventListener> データを読み取ると <xref:System.Diagnostics.Tracing.EventSource> 例外が実行時にスローされます。  
  
 この ETW イベント メソッドの定義は、次のパターンに従う必要があります。  
  
```  
  
[Event(2, Level = EventLevel.Informational)] public void Info2(string message) { base.WriteEvent(2, message); }  
  
```  
  
## 軽減策  
 必要なパターンに準拠するように既存のコードを変更する必要があります。  
  
 次のように、<xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> メソッドを呼び出すための 2 つのメソッドを定義して変更する必要があるコードの量を次のように最小限にできます。  
  
```  
  
[NonEvent] public void Info2(string message) { Info2Internal(message, "-"); } public void Info2Internal(string message, string prefix) { WriteEvent(2, message, prefix); }  
  
```  
  
## 参照  
 [ランタイムの変更点](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)