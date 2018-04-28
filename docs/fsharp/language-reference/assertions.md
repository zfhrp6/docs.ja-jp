---
title: アサーション (F#)
description: F# のプログラミング言語で式をテストするはデバッグ機能として 'assert' 式を使用する方法を説明します。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 195b4a34977a63d92559003b5cd0bb89490a1e7a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="assertions"></a><span data-ttu-id="524e7-103">アサーション</span><span class="sxs-lookup"><span data-stu-id="524e7-103">Assertions</span></span>

<span data-ttu-id="524e7-104">`assert`式が式のテストに使用できるデバッグ機能。</span><span class="sxs-lookup"><span data-stu-id="524e7-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="524e7-105">デバッグ モードでエラーが発生すると、アサーションによってシステム エラーのダイアログ ボックスが生成されます。</span><span class="sxs-lookup"><span data-stu-id="524e7-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="524e7-106">構文</span><span class="sxs-lookup"><span data-stu-id="524e7-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="524e7-107">コメント</span><span class="sxs-lookup"><span data-stu-id="524e7-107">Remarks</span></span>

<span data-ttu-id="524e7-108">`assert`式の型が`bool -> unit`です。</span><span class="sxs-lookup"><span data-stu-id="524e7-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="524e7-109">前の構文で*条件*ブール式をテストするを表します。</span><span class="sxs-lookup"><span data-stu-id="524e7-109">In the previous syntax, *condition* represents a Boolean expression that is to be tested.</span></span> <span data-ttu-id="524e7-110">式が評価された場合`true`実行がそのまま継続します。</span><span class="sxs-lookup"><span data-stu-id="524e7-110">If the expression evaluates to `true`, execution continues unaffected.</span></span> <span data-ttu-id="524e7-111">評価結果が場合`false`、システム エラー ダイアログ ボックスを生成します。</span><span class="sxs-lookup"><span data-stu-id="524e7-111">If it evaluates to `false`, a system error dialog box is generated.</span></span> <span data-ttu-id="524e7-112">エラー ダイアログ ボックス キャプションがあり、文字列を含む**アサーションが失敗した**です。</span><span class="sxs-lookup"><span data-stu-id="524e7-112">The error dialog box has a caption that contains the string **Assertion Failed**.</span></span> <span data-ttu-id="524e7-113">ダイアログ ボックスには、アサーション エラーが発生したことを示します。 スタック トレースが含まれています。</span><span class="sxs-lookup"><span data-stu-id="524e7-113">The dialog box contains a stack trace that indicates where the assertion failure occurred.</span></span>

<span data-ttu-id="524e7-114">デバッグ モードでコンパイルするときだけアサーション チェックが有効にします。つまり場合、定数`DEBUG`が定義されています。</span><span class="sxs-lookup"><span data-stu-id="524e7-114">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="524e7-115">プロジェクト システムで、既定では、`DEBUG`定数は、リリース構成ではなく、デバッグ構成で定義されています。</span><span class="sxs-lookup"><span data-stu-id="524e7-115">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="524e7-116">F# の例外処理を使用してアサーション失敗エラーをキャッチできません。</span><span class="sxs-lookup"><span data-stu-id="524e7-116">The assertion failure error cannot be caught by using F# exception handling.</span></span>

>[!NOTE]
<span data-ttu-id="524e7-117">`assert`関数に解決<xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="524e7-117">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="524e7-118">例</span><span class="sxs-lookup"><span data-stu-id="524e7-118">Example</span></span>

<span data-ttu-id="524e7-119">次のコード例の使用を示しています、`assert`式。</span><span class="sxs-lookup"><span data-stu-id="524e7-119">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]
    
## <a name="see-also"></a><span data-ttu-id="524e7-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="524e7-120">See Also</span></span>

[<span data-ttu-id="524e7-121">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="524e7-121">F# Language Reference</span></span>](index.md)
