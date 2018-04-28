---
title: 'ループ: for...to 式 (F#)'
description: 参照してくださいか f# データ型.. ループでループ変数の値の範囲を反復処理に式を使用します。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 95a8960d71c82c01118d2e71479fc0ec5298a02b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="loops-forto-expression"></a><span data-ttu-id="acf9a-103">ループ: for...to 式</span><span class="sxs-lookup"><span data-stu-id="acf9a-103">Loops: for...to Expression</span></span>

<span data-ttu-id="acf9a-104">`for...to`ループでループ変数の値の範囲を反復処理する式を使用します。</span><span class="sxs-lookup"><span data-stu-id="acf9a-104">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>


## <a name="syntax"></a><span data-ttu-id="acf9a-105">構文</span><span class="sxs-lookup"><span data-stu-id="acf9a-105">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="acf9a-106">コメント</span><span class="sxs-lookup"><span data-stu-id="acf9a-106">Remarks</span></span>
<span data-ttu-id="acf9a-107">識別子の型がの型から推論されます、*開始*と*完了*式。</span><span class="sxs-lookup"><span data-stu-id="acf9a-107">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="acf9a-108">これらの式の型は、32 ビット整数値である必要があります。</span><span class="sxs-lookup"><span data-stu-id="acf9a-108">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="acf9a-109">式では技術的には、`for...to`命令型プログラミング言語では、従来のステートメントのようにします。</span><span class="sxs-lookup"><span data-stu-id="acf9a-109">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="acf9a-110">戻り値の型、*式本体*する必要があります`unit`です。</span><span class="sxs-lookup"><span data-stu-id="acf9a-110">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="acf9a-111">次の例では、さまざまな使用、`for...to`式。</span><span class="sxs-lookup"><span data-stu-id="acf9a-111">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="acf9a-112">このコードの出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="acf9a-112">The output of the previous code is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="acf9a-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="acf9a-113">See Also</span></span>
[<span data-ttu-id="acf9a-114">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="acf9a-114">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="acf9a-115">ループ: `for...in` 式</span><span class="sxs-lookup"><span data-stu-id="acf9a-115">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)

[<span data-ttu-id="acf9a-116">ループ: `while...do` 式</span><span class="sxs-lookup"><span data-stu-id="acf9a-116">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
