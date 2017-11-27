---
title: "例外処理 (F#)"
description: "F# の例外処理の基礎を学習し、例外処理の式と関数へのリンクを見つけてください。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ad475c4a-d94e-47d9-b27b-3ff000b65f8e
ms.openlocfilehash: b61af66e0a70fdf9b86df37418c0284957d1f99e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="exception-handling"></a><span data-ttu-id="269fd-104">例外処理</span><span class="sxs-lookup"><span data-stu-id="269fd-104">Exception Handling</span></span>

<span data-ttu-id="269fd-105">このセクションでは、F# 言語での例外処理のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="269fd-105">This section contains information about exception handling support in the F# language.</span></span>


## <a name="exception-handling-basics"></a><span data-ttu-id="269fd-106">例外処理の基礎</span><span class="sxs-lookup"><span data-stu-id="269fd-106">Exception Handling Basics</span></span>
<span data-ttu-id="269fd-107">例外処理は、.NET Framework においてエラー条件を処理するための標準的な方法です。</span><span class="sxs-lookup"><span data-stu-id="269fd-107">Exception handling is the standard way of handling error conditions in the .NET Framework.</span></span> <span data-ttu-id="269fd-108">したがって、F# を含むすべての .NET 言語でこのメカニズムがサポートされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="269fd-108">Thus, any .NET language must support this mechanism, including F#.</span></span> <span data-ttu-id="269fd-109">*例外*は、エラーに関する情報をカプセル化するオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="269fd-109">An *exception* is an object that encapsulates information about an error.</span></span> <span data-ttu-id="269fd-110">エラーが発生すると、例外が生成され、通常の実行が停止します。</span><span class="sxs-lookup"><span data-stu-id="269fd-110">When errors occur, exceptions are raised and regular execution stops.</span></span> <span data-ttu-id="269fd-111">代わりに、ランタイムによって適切な例外ハンドラーが検索されます。</span><span class="sxs-lookup"><span data-stu-id="269fd-111">Instead, the runtime searches for an appropriate handler for the exception.</span></span> <span data-ttu-id="269fd-112">検索は、現在の関数で開始され、一致するハンドラーが見つかるまで、呼び出し元のレイヤーのスタックを上位に向かって検索します。</span><span class="sxs-lookup"><span data-stu-id="269fd-112">The search starts in the current function, and proceeds up the stack through the layers of callers until a matching handler is found.</span></span> <span data-ttu-id="269fd-113">見つかったハンドラーが実行されます。</span><span class="sxs-lookup"><span data-stu-id="269fd-113">Then the handler is executed.</span></span>

<span data-ttu-id="269fd-114">また、スタックはアンワインドされているため、ランタイムによって `finally` ブロック内のコードがすべて実行されます。これにより、アンワインド プロセスでオブジェクトが適切にクリーンアップされることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="269fd-114">In addition, as the stack is unwound, the runtime executes any code in `finally` blocks, to guarantee that objects are cleaned up correctly during the unwinding process.</span></span>


## <a name="related-topics"></a><span data-ttu-id="269fd-115">関連トピック</span><span class="sxs-lookup"><span data-stu-id="269fd-115">Related Topics</span></span>

|<span data-ttu-id="269fd-116">タイトル</span><span class="sxs-lookup"><span data-stu-id="269fd-116">Title</span></span>|<span data-ttu-id="269fd-117">説明</span><span class="sxs-lookup"><span data-stu-id="269fd-117">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="269fd-118">例外の種類</span><span class="sxs-lookup"><span data-stu-id="269fd-118">Exception Types</span></span>](exception-types.md)|<span data-ttu-id="269fd-119">例外の種類を宣言する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="269fd-119">Describes how to declare an exception type.</span></span>|
|[<span data-ttu-id="269fd-120">例外: `try...with` 式</span><span class="sxs-lookup"><span data-stu-id="269fd-120">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)|<span data-ttu-id="269fd-121">例外処理をサポートする言語構成要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="269fd-121">Describes the language construct that supports exception handling.</span></span>|
|[<span data-ttu-id="269fd-122">例外: `try...finally` 式</span><span class="sxs-lookup"><span data-stu-id="269fd-122">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)|<span data-ttu-id="269fd-123">例外がスローされたときに、クリーンアップ コードをスタック アンワインドとして実行するための言語構成要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="269fd-123">Describes the language construct that enables you to execute clean-up code as the stack unwinds when an exception is thrown.</span></span>|
|[<span data-ttu-id="269fd-124">例外: `raise` 関数</span><span class="sxs-lookup"><span data-stu-id="269fd-124">Exceptions: the `raise` Function</span></span>](the-raise-Function.md)|<span data-ttu-id="269fd-125">例外オブジェクトをスローする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="269fd-125">Describes how to throw an exception object.</span></span>|
|[<span data-ttu-id="269fd-126">例外: `failwith` 関数</span><span class="sxs-lookup"><span data-stu-id="269fd-126">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)|<span data-ttu-id="269fd-127">F# の一般的な例外を生成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="269fd-127">Describes how to generate a general F# exception.</span></span>|
|[<span data-ttu-id="269fd-128">例外: `invalidArg` 関数</span><span class="sxs-lookup"><span data-stu-id="269fd-128">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)|<span data-ttu-id="269fd-129">無効な引数の例外を生成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="269fd-129">Describes how to generate an invalid argument exception.</span></span>|
