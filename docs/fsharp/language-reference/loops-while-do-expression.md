---
title: "ループ: while...do 式 (F#)"
description: "参照してください方法、while... は式が指定されたテスト条件が true の間に反復的な実行 (ループ) を実行するために使用します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 0416ffca-7ed9-4aff-9493-e001fdba8c9b
ms.openlocfilehash: 6a186d75dcda383764949c2cd3b09bc9e3d1080a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="loops-whiledo-expression"></a><span data-ttu-id="aedd1-104">ループ: while...do 式</span><span class="sxs-lookup"><span data-stu-id="aedd1-104">Loops: while...do Expression</span></span>

<span data-ttu-id="aedd1-105">`while...do`式を使用して、指定されたテスト条件が true の間に反復的な実行 (ループ) を実行します。</span><span class="sxs-lookup"><span data-stu-id="aedd1-105">The `while...do` expression is used to perform iterative execution (looping) while a specified test condition is true.</span></span>


## <a name="syntax"></a><span data-ttu-id="aedd1-106">構文</span><span class="sxs-lookup"><span data-stu-id="aedd1-106">Syntax</span></span>

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="aedd1-107">コメント</span><span class="sxs-lookup"><span data-stu-id="aedd1-107">Remarks</span></span>
<span data-ttu-id="aedd1-108">*テスト式*が評価されます。 ある場合`true`、*式本体*を実行し、もう一度テスト式が評価されます。</span><span class="sxs-lookup"><span data-stu-id="aedd1-108">The *test-expression* is evaluated; if it is `true`, the *body-expression* is executed and the test expression is evaluated again.</span></span> <span data-ttu-id="aedd1-109">*式本体*型である必要があります`unit`です。</span><span class="sxs-lookup"><span data-stu-id="aedd1-109">The *body-expression* must have type `unit`.</span></span> <span data-ttu-id="aedd1-110">場合テスト式`false`イテレーションが終了します。</span><span class="sxs-lookup"><span data-stu-id="aedd1-110">If the test expression is `false`, the iteration ends.</span></span>

<span data-ttu-id="aedd1-111">次の例では、使用、`while...do`式。</span><span class="sxs-lookup"><span data-stu-id="aedd1-111">The following example illustrates the use of the `while...do` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

<span data-ttu-id="aedd1-112">上記のコードの出力は、1 ~ 20、ランダムな数値のうち、最後は 10 ストリームです。</span><span class="sxs-lookup"><span data-stu-id="aedd1-112">The output of the previous code is a stream of random numbers between 1 and 20, the last of which is 10.</span></span>

```
13 19 8 18 16 2 10
Found a 10!
```

>[!NOTE] 
<span data-ttu-id="aedd1-113">使用することができます`while...do`シーケンス式およびその他の計算式で、カスタマイズされたバージョンの場合、`while...do`式を使用します。</span><span class="sxs-lookup"><span data-stu-id="aedd1-113">You can use `while...do` in sequence expressions and other computation expressions, in which case a customized version of the `while...do` expression is used.</span></span> <span data-ttu-id="aedd1-114">詳細については、次を参照してください。[シーケンス](sequences.md)、[非同期ワークフロー](asynchronous-workflows.md)、および[コンピュテーション式](computation-expressions.md)です。</span><span class="sxs-lookup"><span data-stu-id="aedd1-114">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="aedd1-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="aedd1-115">See Also</span></span>
[<span data-ttu-id="aedd1-116">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="aedd1-116">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="aedd1-117">ループ: `for...in` 式</span><span class="sxs-lookup"><span data-stu-id="aedd1-117">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)

[<span data-ttu-id="aedd1-118">ループ: `for...to` 式</span><span class="sxs-lookup"><span data-stu-id="aedd1-118">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
