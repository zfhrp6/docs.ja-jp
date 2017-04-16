---
title: "Asynchronous Programming Patterns | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "asynchronous design patterns, .NET Framework"
  - ".NET Framework, asynchronous design patterns"
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
caps.latest.revision: 5
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 5
---
# Asynchronous Programming Patterns
.NET Framework は、非同期操作を実行するための 3 つのパターンを提供します。  
  
-   非同期プログラミング モデル \(APM\) パターン \(<xref:System.IAsyncResult> パターンとも呼ばれます\)。非同期操作には `Begin` メソッドと `End` メソッドが必要です \(たとえば、非同期書き込み操作の場合は `BeginWrite` と `EndWrite`\)。  このパターンは、新規の開発では推奨されなくなりました。  詳細については、「[Asynchronous Programming Model \(APM\)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md)」を参照してください。  
  
-   イベント ベースの非同期パターン \(EAP\)。`Async` サフィックスを持つメソッドと、1 つ以上のイベント、イベント ハンドラー デリゲート型、および `EventArg` 派生型を必要とします。  EAP は、.NET Framework 2.0 で導入されました。  新規の開発では推奨されなくなりました。  詳細については、「[Event\-based Asynchronous Pattern \(EAP\)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)」を参照してください。  
  
-   タスク ベースの非同期パターン \(TAP\)。1 つのメソッドを使用して非同期操作の開始と完了を表します。  TAP は .NET Framework 4 で導入され、.NET Framework での非同期プログラミングに推奨されるアプローチです。  C\# の [async](../Topic/async%20\(C%23%20Reference\).md) キーワードと [await](../Topic/await%20\(C%23%20Reference\).md) キーワード、および Visual Basic 言語の [Async](../Topic/Async%20\(Visual%20Basic\).md) 演算子と [Await](../Topic/Await%20Operator%20\(Visual%20Basic\).md) 演算子により、TAP の言語サポートが追加されます。  詳細については、「[Task\-based Asynchronous Pattern \(TAP\)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)」を参照してください。  
  
## パターンの比較  
 3 つのパターンで非同期操作がどのようにモデリングされるかを簡単に比較するために、指定された量のデータを、指定のバッファーの指定されたオフセットに読み込む `Read` メソッドを考えます。  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  
  
 APM の場合は、このメソッドにより `BeginRead` メソッドと `EndRead` メソッドが公開されます。  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,   
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  
  
 EAP の場合は次の型とメンバーのセットが公開されます。  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
 TAP の場合は次の単一の `ReadAsync` メソッドが公開されます。  
  
```csharp  
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```  
  
 TAP、APM、および EAP の包括的な説明については、次のセクションに記載のリンクを参照してください。  
  
## 関連トピック  
  
|タイトル|説明|  
|----------|--------|  
|[Asynchronous Programming Model \(APM\)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md)|<xref:System.IAsyncResult> インターフェイスを使用して非同期動作を提供するレガシ モデルについて説明します。  このモデルは新規の開発では推奨されなくなりました。|  
|[Event\-based Asynchronous Pattern \(EAP\)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)|非同期動作を提供するイベント ベースのレガシ モデルについて説明します。  このモデルは新規の開発では推奨されなくなりました。|  
|[Task\-based Asynchronous Pattern \(TAP\)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|<xref:System.Threading.Tasks> 名前空間に基づく新しい非同期パターンについて説明します。  このモデルは、.NET Framework 4 以降のバージョンでの非同期プログラミングで推奨されるアプローチです。|