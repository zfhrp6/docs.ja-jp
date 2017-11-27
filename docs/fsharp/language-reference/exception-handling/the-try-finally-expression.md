---
title: "例外: try...finally 式 (F#)"
description: "学習方法、f# 'try… 最後に' 式では、コード ブロックの例外をスローする場合でも、クリーンアップ コードを実行することができます。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: af06b20c-8d87-4496-a0aa-6fdfe8b3a786
ms.openlocfilehash: 2e2445c42bf8129ea81beef56cb725ac0e37d202
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-the-tryfinally-expression"></a><span data-ttu-id="aa97c-104">例外: try...finally 式</span><span class="sxs-lookup"><span data-stu-id="aa97c-104">Exceptions: The try...finally Expression</span></span>

<span data-ttu-id="aa97c-105">`try...finally`式では、コード ブロックの例外をスローする場合でも、クリーンアップ コードを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="aa97c-105">The `try...finally` expression enables you to execute clean-up code even if a block of code throws an exception.</span></span>


## <a name="syntax"></a><span data-ttu-id="aa97c-106">構文</span><span class="sxs-lookup"><span data-stu-id="aa97c-106">Syntax</span></span>

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a><span data-ttu-id="aa97c-107">コメント</span><span class="sxs-lookup"><span data-stu-id="aa97c-107">Remarks</span></span>
<span data-ttu-id="aa97c-108">`try...finally`でコードを実行する式を使用できます*expression2*の実行中に例外を生成するかどうかに関係なく上記の構文で*expression1*です。</span><span class="sxs-lookup"><span data-stu-id="aa97c-108">The `try...finally` expression can be used to execute the code in *expression2* in the preceding syntax regardless of whether an exception is generated during the execution of *expression1*.</span></span>

<span data-ttu-id="aa97c-109">型*expression2* ; 式全体の値には含まれません、例外が発生していないときに返される型の最後の値は、 *expression1*です。</span><span class="sxs-lookup"><span data-stu-id="aa97c-109">The type of *expression2* does not contribute to the value of the whole expression; the type returned when an exception does not occur is the last value in *expression1*.</span></span> <span data-ttu-id="aa97c-110">例外が発生した場合、値は返されません、コール スタックを [次へ] の一致する例外ハンドラーに制御フローを転送します。</span><span class="sxs-lookup"><span data-stu-id="aa97c-110">When an exception does occur, no value is returned and the flow of control transfers to the next matching exception handler up the call stack.</span></span> <span data-ttu-id="aa97c-111">例外ハンドラーが見つからない場合、プログラムが終了します。</span><span class="sxs-lookup"><span data-stu-id="aa97c-111">If no exception handler is found, the program terminates.</span></span> <span data-ttu-id="aa97c-112">プログラムは終了し、コードまたは一致するハンドラーのコードが実行される前に、`finally`分岐が実行されます。</span><span class="sxs-lookup"><span data-stu-id="aa97c-112">Before the code in a matching handler is executed or the program terminates, the code in the `finally` branch is executed.</span></span>

<span data-ttu-id="aa97c-113">次の例では、使用、`try...finally`式。</span><span class="sxs-lookup"><span data-stu-id="aa97c-113">The following code demonstrates the use of the `try...finally` expression.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

<span data-ttu-id="aa97c-114">コンソールへの出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="aa97c-114">The output to the console is as follows.</span></span>

```
Closing stream
Exception handled.
```

<span data-ttu-id="aa97c-115">出力からわかるように、ストリームが閉じられた外側の例外が処理された、およびファイル`test.txt`テキストを含む`test1`バッファーがフラッシュされ、場合でも、例外の転送をディスクに書き込まれることを示します外側の例外ハンドラーに制御します。</span><span class="sxs-lookup"><span data-stu-id="aa97c-115">As you can see from the output, the stream was closed before the outer exception was handled, and the file `test.txt` contains the text `test1`, which indicates that the buffers were flushed and written to disk even though the exception transferred control to the outer exception handler.</span></span>

<span data-ttu-id="aa97c-116">なお、`try...with`コンストラクトでは、個別の`try...finally`を構築します。</span><span class="sxs-lookup"><span data-stu-id="aa97c-116">Note that the `try...with` construct is a separate construct from the `try...finally` construct.</span></span> <span data-ttu-id="aa97c-117">そのため、コードでは、両方が必要な場合、`with`ブロックと`finally`ブロックを次のコード例のように、2 つの構造を入れ子にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa97c-117">Therefore, if your code requires both a `with` block and a `finally` block, you have to nest the two constructs, as in the following code example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

<span data-ttu-id="aa97c-118">コンピュテーション式のコンテキストでシーケンス式と非同期のワークフローを含む**try… finally**式は、カスタム実装を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="aa97c-118">In the context of computation expressions, including sequence expressions and asynchronous workflows, **try...finally** expressions can have a custom implementation.</span></span> <span data-ttu-id="aa97c-119">詳細については、次を参照してください。[コンピュテーション式](../computation-expressions.md)です。</span><span class="sxs-lookup"><span data-stu-id="aa97c-119">For more information, see [Computation Expressions](../computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="aa97c-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="aa97c-120">See Also</span></span>
[<span data-ttu-id="aa97c-121">例外処理</span><span class="sxs-lookup"><span data-stu-id="aa97c-121">Exception Handling</span></span>](index.md)

[<span data-ttu-id="aa97c-122">例外: `try...with` 式</span><span class="sxs-lookup"><span data-stu-id="aa97c-122">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
