---
title: ブール演算子 (F#)
description: F# のプログラミング言語で使用可能なブール演算子について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: f8516ceb531907400f98dc4226d2985d3119e9e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563429"
---
# <a name="boolean-operators"></a><span data-ttu-id="2f7c9-103">ブール演算子</span><span class="sxs-lookup"><span data-stu-id="2f7c9-103">Boolean Operators</span></span>

<span data-ttu-id="2f7c9-104">このトピックでは、f# 言語でブール演算子のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2f7c9-104">This topic describes the support for Boolean operators in the F# language.</span></span>


## <a name="summary-of-boolean-operators"></a><span data-ttu-id="2f7c9-105">ブール演算子の概要</span><span class="sxs-lookup"><span data-stu-id="2f7c9-105">Summary of Boolean Operators</span></span>
<span data-ttu-id="2f7c9-106">次の表は、f# 言語で使用可能なブール演算子をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="2f7c9-106">The following table summarizes the Boolean operators that are available in the F# language.</span></span> <span data-ttu-id="2f7c9-107">これらの演算子でサポートされる唯一の型は、`bool`型です。</span><span class="sxs-lookup"><span data-stu-id="2f7c9-107">The only type supported by these operators is the `bool` type.</span></span>

|<span data-ttu-id="2f7c9-108">演算子</span><span class="sxs-lookup"><span data-stu-id="2f7c9-108">Operator</span></span>|<span data-ttu-id="2f7c9-109">説明</span><span class="sxs-lookup"><span data-stu-id="2f7c9-109">Description</span></span>|
|--------|-----------|
|`not`|<span data-ttu-id="2f7c9-110">論理否定</span><span class="sxs-lookup"><span data-stu-id="2f7c9-110">Boolean negation</span></span>|
|<code>&#124;&#124;</code>|<span data-ttu-id="2f7c9-111">論理 OR</span><span class="sxs-lookup"><span data-stu-id="2f7c9-111">Boolean OR</span></span>|
|`&&`|<span data-ttu-id="2f7c9-112">ブール型の AND</span><span class="sxs-lookup"><span data-stu-id="2f7c9-112">Boolean AND</span></span>|

<span data-ttu-id="2f7c9-113">ブール値の AND および OR 演算子を実行*ショート サーキット評価*演算子の右側の式の評価、つまり、式の全体的な結果を決定する必要がある場合にのみです。</span><span class="sxs-lookup"><span data-stu-id="2f7c9-113">The Boolean AND and OR operators perform *short-circuit evaluation*, that is, they evaluate the expression on the right of the operator only when it is necessary to determine the overall result of the expression.</span></span> <span data-ttu-id="2f7c9-114">2 番目の式、`&&`に最初の式が評価された場合にのみ、演算子が評価される`true`; の 2 番目の式、`||`に最初の式が評価された場合にのみ、演算子が評価される`false`です。</span><span class="sxs-lookup"><span data-stu-id="2f7c9-114">The second expression of the `&&` operator is evaluated only if the first expression evaluates to `true`; the second expression of the `||` operator is evaluated only if the first expression evaluates to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="2f7c9-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f7c9-115">See Also</span></span>
[<span data-ttu-id="2f7c9-116">ビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="2f7c9-116">Bitwise Operators</span></span>](bitwise-operators.md)

[<span data-ttu-id="2f7c9-117">算術演算子</span><span class="sxs-lookup"><span data-stu-id="2f7c9-117">Arithmetic Operators</span></span>](arithmetic-operators.md)

[<span data-ttu-id="2f7c9-118">シンボルと演算子のリファレンス</span><span class="sxs-lookup"><span data-stu-id="2f7c9-118">Symbol and Operator Reference</span></span>](index.md)
