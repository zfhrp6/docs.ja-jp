---
title: "ループ: for...to 式 (F#)"
description: "参照してくださいか f# データ型.. ループでループ変数の値の範囲を反復処理に式を使用します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e14c38d9-b1ef-4b7f-be9a-fb6ef6708e02
ms.openlocfilehash: 1a1d71d30b5e87e4691a78acd5032de9419399db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="loops-forto-expression"></a><span data-ttu-id="509dd-104">ループ: for...to 式</span><span class="sxs-lookup"><span data-stu-id="509dd-104">Loops: for...to Expression</span></span>

<span data-ttu-id="509dd-105">`for...to`ループでループ変数の値の範囲を反復処理する式を使用します。</span><span class="sxs-lookup"><span data-stu-id="509dd-105">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>


## <a name="syntax"></a><span data-ttu-id="509dd-106">構文</span><span class="sxs-lookup"><span data-stu-id="509dd-106">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="509dd-107">コメント</span><span class="sxs-lookup"><span data-stu-id="509dd-107">Remarks</span></span>
<span data-ttu-id="509dd-108">識別子の型がの型から推論されます、*開始*と*完了*式。</span><span class="sxs-lookup"><span data-stu-id="509dd-108">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="509dd-109">これらの式の型は、32 ビット整数値である必要があります。</span><span class="sxs-lookup"><span data-stu-id="509dd-109">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="509dd-110">式では技術的には、`for...to`命令型プログラミング言語では、従来のステートメントのようにします。</span><span class="sxs-lookup"><span data-stu-id="509dd-110">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="509dd-111">戻り値の型、*式本体*する必要があります`unit`です。</span><span class="sxs-lookup"><span data-stu-id="509dd-111">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="509dd-112">次の例では、さまざまな使用、`for...to`式。</span><span class="sxs-lookup"><span data-stu-id="509dd-112">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="509dd-113">このコードの出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="509dd-113">The output of the previous code is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="509dd-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="509dd-114">See Also</span></span>
[<span data-ttu-id="509dd-115">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="509dd-115">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="509dd-116">ループ: `for...in` 式</span><span class="sxs-lookup"><span data-stu-id="509dd-116">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)

[<span data-ttu-id="509dd-117">ループ: `while...do` 式</span><span class="sxs-lookup"><span data-stu-id="509dd-117">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
