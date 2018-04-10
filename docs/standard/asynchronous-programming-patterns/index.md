---
title: 非同期プログラミングのパターン
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- asynchronous design patterns, .NET Framework
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 42298bc8e3101b03f6c3e03fec453b72cd959efb
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="asynchronous-programming-patterns"></a><span data-ttu-id="71c46-102">非同期プログラミングのパターン</span><span class="sxs-lookup"><span data-stu-id="71c46-102">Asynchronous Programming Patterns</span></span>

<span data-ttu-id="71c46-103">.NET Framework は、非同期操作を実行するための 3 つのパターンを提供します。</span><span class="sxs-lookup"><span data-stu-id="71c46-103">The .NET Framework provides three patterns for performing asynchronous operations:</span></span>  
  
- <span data-ttu-id="71c46-104">非同期プログラミング モデル (APM) パターン (<xref:System.IAsyncResult> パターンとも呼ばれます)。非同期操作には `Begin` メソッドと `End` メソッドが必要です (たとえば、非同期書き込み操作の場合は `BeginWrite` と `EndWrite`)。</span><span class="sxs-lookup"><span data-stu-id="71c46-104">Asynchronous Programming Model (APM) pattern (also called the <xref:System.IAsyncResult> pattern), where asynchronous operations require `Begin` and `End` methods (for example, `BeginWrite` and `EndWrite` for asynchronous write operations).</span></span> <span data-ttu-id="71c46-105">このパターンは、新規の開発では推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="71c46-105">This pattern is no longer recommended for new development.</span></span> <span data-ttu-id="71c46-106">詳細については、「[非同期プログラミング モデル (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71c46-106">For more information, see [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md).</span></span>  
  
- <span data-ttu-id="71c46-107">イベント ベースの非同期パターン (EAP)。`Async` サフィックスを持つメソッドと、1 つ以上のイベント、イベント ハンドラー デリゲート型、および `EventArg` 派生型を必要とします。</span><span class="sxs-lookup"><span data-stu-id="71c46-107">Event-based Asynchronous Pattern (EAP), which requires a method that has the `Async` suffix, and also requires one or more events, event handler delegate types, and `EventArg`-derived types.</span></span> <span data-ttu-id="71c46-108">EAP は、.NET Framework 2.0 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="71c46-108">EAP was introduced in the .NET Framework 2.0.</span></span> <span data-ttu-id="71c46-109">新規の開発では推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="71c46-109">It is no longer recommended for new development.</span></span> <span data-ttu-id="71c46-110">詳細については、「[イベント ベースの非同期パターン (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71c46-110">For more information, see [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  
  
- <span data-ttu-id="71c46-111">タスク ベースの非同期パターン (TAP)。1 つのメソッドを使用して非同期操作の開始と完了を表します。</span><span class="sxs-lookup"><span data-stu-id="71c46-111">Task-based Asynchronous Pattern (TAP), which uses a single method to represent the initiation and completion of an asynchronous operation.</span></span> <span data-ttu-id="71c46-112">TAP は .NET Framework 4 で導入され、.NET Framework での非同期プログラミングに推奨されるアプローチです。</span><span class="sxs-lookup"><span data-stu-id="71c46-112">TAP was introduced in the .NET Framework 4 and is the recommended approach to asynchronous programming in the .NET Framework.</span></span> <span data-ttu-id="71c46-113">C# の [async](~/docs/csharp/language-reference/keywords/async.md) キーワードと [await](~/docs/csharp/language-reference/keywords/await.md) キーワード、および Visual Basic 言語の [Async](~/docs/visual-basic/language-reference/modifiers/async.md) 演算子と [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) 演算子により、TAP の言語サポートが追加されます。</span><span class="sxs-lookup"><span data-stu-id="71c46-113">The [async](~/docs/csharp/language-reference/keywords/async.md) and [await](~/docs/csharp/language-reference/keywords/await.md) keywords in C# and the [Async](~/docs/visual-basic/language-reference/modifiers/async.md) and [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) operators in Visual Basic Language add language support for TAP.</span></span> <span data-ttu-id="71c46-114">詳細については、「[タスク ベースの非同期パターン (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71c46-114">For more information, see [Task-based Asynchronous Pattern (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span>  
  
## <a name="comparing-patterns"></a><span data-ttu-id="71c46-115">パターンの比較</span><span class="sxs-lookup"><span data-stu-id="71c46-115">Comparing Patterns</span></span>  

<span data-ttu-id="71c46-116">3 つのパターンで非同期操作がどのようにモデリングされるかを簡単に比較するために、指定された量のデータを、指定のバッファーの指定されたオフセットに読み込む `Read` メソッドを考えます。</span><span class="sxs-lookup"><span data-stu-id="71c46-116">For a quick comparison of how the three patterns model asynchronous operations, consider a `Read` method that reads a specified amount of data into a provided buffer starting at a specified offset:</span></span>  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  
  
<span data-ttu-id="71c46-117">APM の場合は、このメソッドにより `BeginRead` メソッドと `EndRead` メソッドが公開されます。</span><span class="sxs-lookup"><span data-stu-id="71c46-117">The APM counterpart of this method would expose the `BeginRead` and `EndRead` methods:</span></span>  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,   
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  
  
<span data-ttu-id="71c46-118">EAP の場合は次の型とメンバーのセットが公開されます。</span><span class="sxs-lookup"><span data-stu-id="71c46-118">The EAP counterpart would expose the following set of types and members:</span></span>  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
<span data-ttu-id="71c46-119">TAP の場合は次の単一の `ReadAsync` メソッドが公開されます。</span><span class="sxs-lookup"><span data-stu-id="71c46-119">The TAP counterpart would expose the following single `ReadAsync` method:</span></span>  
  
```csharp  
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```  
  
<span data-ttu-id="71c46-120">TAP、APM、および EAP の包括的な説明については、次のセクションに記載のリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="71c46-120">For a comprehensive discussion of TAP, APM, and EAP, see the links provided in the next section.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="71c46-121">関連トピック</span><span class="sxs-lookup"><span data-stu-id="71c46-121">Related topics</span></span>

| <span data-ttu-id="71c46-122">タイトル</span><span class="sxs-lookup"><span data-stu-id="71c46-122">Title</span></span> | <span data-ttu-id="71c46-123">説明</span><span class="sxs-lookup"><span data-stu-id="71c46-123">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="71c46-124">非同期プログラミング モデル (APM)</span><span class="sxs-lookup"><span data-stu-id="71c46-124">Asynchronous Programming Model (APM)</span></span>](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) | <span data-ttu-id="71c46-125"><xref:System.IAsyncResult> インターフェイスを使用して非同期動作を提供するレガシ モデルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="71c46-125">Describes the legacy model that uses the <xref:System.IAsyncResult> interface to provide asynchronous behavior.</span></span> <span data-ttu-id="71c46-126">このモデルは新規の開発では推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="71c46-126">This model is no longer recommended for new development.</span></span> |
| [<span data-ttu-id="71c46-127">イベント ベースの非同期パターン (EAP)</span><span class="sxs-lookup"><span data-stu-id="71c46-127">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) | <span data-ttu-id="71c46-128">非同期動作を提供するイベント ベースのレガシ モデルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="71c46-128">Describes the event-based legacy model for providing asynchronous behavior.</span></span> <span data-ttu-id="71c46-129">このモデルは新規の開発では推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="71c46-129">This model is no longer recommended for new development.</span></span> |
| [<span data-ttu-id="71c46-130">タスク ベースの非同期パターン (TAP)</span><span class="sxs-lookup"><span data-stu-id="71c46-130">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) | <span data-ttu-id="71c46-131"><xref:System.Threading.Tasks> 名前空間に基づく新しい非同期パターンについて説明します。</span><span class="sxs-lookup"><span data-stu-id="71c46-131">Describes the new asynchronous pattern based on the <xref:System.Threading.Tasks> namespace.</span></span> <span data-ttu-id="71c46-132">このモデルは、.NET Framework 4 以降のバージョンでの非同期プログラミングで推奨されるアプローチです。</span><span class="sxs-lookup"><span data-stu-id="71c46-132">This model is the recommended approach to asynchronous programming in the .NET Framework 4 and later versions.</span></span> |

## <a name="see-also"></a><span data-ttu-id="71c46-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="71c46-133">See also</span></span>

<span data-ttu-id="71c46-134">[C# の非同期プログラミングの詳細](~/docs/csharp/async.md) </span><span class="sxs-lookup"><span data-stu-id="71c46-134">[Asynchronous programming in C#](~/docs/csharp/async.md) </span></span>  
<span data-ttu-id="71c46-135">[F# の非同期プログラミング](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md) </span><span class="sxs-lookup"><span data-stu-id="71c46-135">[Async Programming in F#](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md) </span></span>  
[<span data-ttu-id="71c46-136">Async および Await を使用した非同期プログラミング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71c46-136">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/concepts/async/index.md)
