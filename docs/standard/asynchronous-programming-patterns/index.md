---
title: 非同期プログラミングのパターン
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET Framework
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86ed48361e0868d9e2fa2b79b1c5fa8955018bef
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="asynchronous-programming-patterns"></a>非同期プログラミングのパターン

.NET Framework は、非同期操作を実行するための 3 つのパターンを提供します。  
  
- 非同期プログラミング モデル (APM) パターン (<xref:System.IAsyncResult> パターンとも呼ばれます)。非同期操作には `Begin` メソッドと `End` メソッドが必要です (たとえば、非同期書き込み操作の場合は `BeginWrite` と `EndWrite`)。 このパターンは、新規の開発では推奨されなくなりました。 詳細については、「[非同期プログラミング モデル (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md)」を参照してください。  
  
- イベント ベースの非同期パターン (EAP)。`Async` サフィックスを持つメソッドと、1 つ以上のイベント、イベント ハンドラー デリゲート型、および `EventArg` 派生型を必要とします。 EAP は、.NET Framework 2.0 で導入されました。 新規の開発では推奨されなくなりました。 詳細については、「[イベント ベースの非同期パターン (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)」を参照してください。  
  
- タスク ベースの非同期パターン (TAP)。1 つのメソッドを使用して非同期操作の開始と完了を表します。 TAP は .NET Framework 4 で導入され、.NET Framework での非同期プログラミングに推奨されるアプローチです。 C# の [async](~/docs/csharp/language-reference/keywords/async.md) キーワードと [await](~/docs/csharp/language-reference/keywords/await.md) キーワード、および Visual Basic 言語の [Async](~/docs/visual-basic/language-reference/modifiers/async.md) 演算子と [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) 演算子により、TAP の言語サポートが追加されます。 詳細については、「[タスク ベースの非同期パターン (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)」を参照してください。  
  
## <a name="comparing-patterns"></a>パターンの比較  

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
  
## <a name="related-topics"></a>関連トピック

| Title | 説明 |
| ----- | ----------- |
| [非同期プログラミング モデル (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) | <xref:System.IAsyncResult> インターフェイスを使用して非同期動作を提供するレガシ モデルについて説明します。 このモデルは新規の開発では推奨されなくなりました。 |
| [イベント ベースの非同期パターン (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) | 非同期動作を提供するイベント ベースのレガシ モデルについて説明します。 このモデルは新規の開発では推奨されなくなりました。 |
| [タスク ベースの非同期パターン (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) | <xref:System.Threading.Tasks> 名前空間に基づく新しい非同期パターンについて説明します。 このモデルは、.NET Framework 4 以降のバージョンでの非同期プログラミングで推奨されるアプローチです。 |

## <a name="see-also"></a>関連項目

[C# の非同期プログラミングの詳細](~/docs/csharp/async.md)   
[F# の非同期プログラミング](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)   
[Async および Await を使用した非同期プログラミング (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/async/index.md)
