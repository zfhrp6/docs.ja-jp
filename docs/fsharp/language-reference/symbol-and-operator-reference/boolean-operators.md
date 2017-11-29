---
title: "ブール演算子 (F#)"
description: "F# のプログラミング言語で使用可能なブール演算子について説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f79370b8-4bc2-4704-b514-d392c80942bd
ms.openlocfilehash: 63588f2e371bf2c0f15de0b8a26a46be82f832c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="boolean-operators"></a><span data-ttu-id="a364c-104">ブール演算子</span><span class="sxs-lookup"><span data-stu-id="a364c-104">Boolean Operators</span></span>

<span data-ttu-id="a364c-105">このトピックでは、f# 言語でブール演算子のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a364c-105">This topic describes the support for Boolean operators in the F# language.</span></span>


## <a name="summary-of-boolean-operators"></a><span data-ttu-id="a364c-106">ブール演算子の概要</span><span class="sxs-lookup"><span data-stu-id="a364c-106">Summary of Boolean Operators</span></span>
<span data-ttu-id="a364c-107">次の表は、f# 言語で使用可能なブール演算子をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="a364c-107">The following table summarizes the Boolean operators that are available in the F# language.</span></span> <span data-ttu-id="a364c-108">これらの演算子でサポートされる唯一の型は、`bool`型です。</span><span class="sxs-lookup"><span data-stu-id="a364c-108">The only type supported by these operators is the `bool` type.</span></span>

|<span data-ttu-id="a364c-109">演算子</span><span class="sxs-lookup"><span data-stu-id="a364c-109">Operator</span></span>|<span data-ttu-id="a364c-110">説明</span><span class="sxs-lookup"><span data-stu-id="a364c-110">Description</span></span>|
|--------|-----------|
|`not`|<span data-ttu-id="a364c-111">論理否定</span><span class="sxs-lookup"><span data-stu-id="a364c-111">Boolean negation</span></span>|
|<code>&#124;&#124;</code>|<span data-ttu-id="a364c-112">論理 OR</span><span class="sxs-lookup"><span data-stu-id="a364c-112">Boolean OR</span></span>|
|`&&`|<span data-ttu-id="a364c-113">ブール型の AND</span><span class="sxs-lookup"><span data-stu-id="a364c-113">Boolean AND</span></span>|

<span data-ttu-id="a364c-114">ブール値の AND および OR 演算子を実行*ショート サーキット評価*演算子の右側の式の評価、つまり、式の全体的な結果を決定する必要がある場合にのみです。</span><span class="sxs-lookup"><span data-stu-id="a364c-114">The Boolean AND and OR operators perform *short-circuit evaluation*, that is, they evaluate the expression on the right of the operator only when it is necessary to determine the overall result of the expression.</span></span> <span data-ttu-id="a364c-115">2 番目の式、`&&`に最初の式が評価された場合にのみ、演算子が評価される`true`; の 2 番目の式、`||`に最初の式が評価された場合にのみ、演算子が評価される`false`です。</span><span class="sxs-lookup"><span data-stu-id="a364c-115">The second expression of the `&&` operator is evaluated only if the first expression evaluates to `true`; the second expression of the `||` operator is evaluated only if the first expression evaluates to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="a364c-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="a364c-116">See Also</span></span>
[<span data-ttu-id="a364c-117">ビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="a364c-117">Bitwise Operators</span></span>](bitwise-operators.md)

[<span data-ttu-id="a364c-118">算術演算子</span><span class="sxs-lookup"><span data-stu-id="a364c-118">Arithmetic Operators</span></span>](arithmetic-operators.md)

[<span data-ttu-id="a364c-119">シンボルと演算子のリファレンス</span><span class="sxs-lookup"><span data-stu-id="a364c-119">Symbol and Operator Reference</span></span>](index.md)
