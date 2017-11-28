---
title: "エントリ ポイント (F#)"
description: "実行が正式に開始、実行可能ファイルとしてコンパイルされた f# プログラムのエントリ ポイントを設定する方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 91455443-ff9d-4510-a7e9-1560bdcd0bb0
ms.openlocfilehash: 685fd4da67119aa5fcaaffd142a0a17c8f5dc7f6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="entry-point"></a><span data-ttu-id="f8dbf-104">エントリ ポイント</span><span class="sxs-lookup"><span data-stu-id="f8dbf-104">Entry Point</span></span>

<span data-ttu-id="f8dbf-105">このトピックでは、f# のプログラムにエントリ ポイントを設定するために使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f8dbf-105">This topic describes the method that you use to set the entry point to an F# program.</span></span>


## <a name="syntax"></a><span data-ttu-id="f8dbf-106">構文</span><span class="sxs-lookup"><span data-stu-id="f8dbf-106">Syntax</span></span>

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a><span data-ttu-id="f8dbf-107">コメント</span><span class="sxs-lookup"><span data-stu-id="f8dbf-107">Remarks</span></span>
<span data-ttu-id="f8dbf-108">前の構文で*let 関数バインド*内の関数の定義、`let`バインドします。</span><span class="sxs-lookup"><span data-stu-id="f8dbf-108">In the previous syntax, *let-function-binding* is the definition of a function in a `let` binding.</span></span>

<span data-ttu-id="f8dbf-109">実行可能ファイルの実行が正式な開始位置としてコンパイルされたプログラムへのエントリ ポイントです。</span><span class="sxs-lookup"><span data-stu-id="f8dbf-109">The entry point to a program that is compiled as an executable file is where execution formally starts.</span></span> <span data-ttu-id="f8dbf-110">適用することで、f# アプリケーションへのエントリ ポイントを指定する、`EntryPoint`属性をプログラムの`main`関数。</span><span class="sxs-lookup"><span data-stu-id="f8dbf-110">You specify the entry point to an F# application by applying the `EntryPoint` attribute to the program's `main` function.</span></span> <span data-ttu-id="f8dbf-111">この関数 (を使用して作成された、`let`バインディング)、前回のコンパイル済みファイルの最後の関数でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="f8dbf-111">This function (created by using a `let` binding) must be the last function in the last compiled file.</span></span> <span data-ttu-id="f8dbf-112">最後のコンパイル済みファイルは、プロジェクトの最後のファイルまたはコマンドラインに渡される最後のファイルです。</span><span class="sxs-lookup"><span data-stu-id="f8dbf-112">The last compiled file is the last file in the project or the last file that is passed to the command line.</span></span>

<span data-ttu-id="f8dbf-113">エントリ ポイント関数が型`string array -> int`です。</span><span class="sxs-lookup"><span data-stu-id="f8dbf-113">The entry point function has type `string array -> int`.</span></span> <span data-ttu-id="f8dbf-114">コマンドラインで指定された引数に渡される、`main`文字列の配列内の関数。</span><span class="sxs-lookup"><span data-stu-id="f8dbf-114">The arguments provided on the command line are passed to the `main` function in the array of strings.</span></span> <span data-ttu-id="f8dbf-115">配列の最初の要素が最初の引数です。他の言語であるために、実行可能ファイルの名前は、配列に含まれていません。</span><span class="sxs-lookup"><span data-stu-id="f8dbf-115">The first element of the array is the first argument; the name of the executable file is not included in the array, as it is in some other languages.</span></span> <span data-ttu-id="f8dbf-116">戻り値は、プロセスの終了コードとして使用します。</span><span class="sxs-lookup"><span data-stu-id="f8dbf-116">The return value is used as the exit code for the process.</span></span> <span data-ttu-id="f8dbf-117">0 は、成功; 通常ことを示します。0 以外の値は、エラーを表します。</span><span class="sxs-lookup"><span data-stu-id="f8dbf-117">Zero usually indicates success; nonzero values indicate an error.</span></span> <span data-ttu-id="f8dbf-118">0 以外のリターン コードの特定の意味の規則はありません。これらのリターン コードの意味は、アプリケーション固有です。</span><span class="sxs-lookup"><span data-stu-id="f8dbf-118">There is no convention for the specific meaning of nonzero return codes; the meanings of the return codes are application-specific.</span></span>

<span data-ttu-id="f8dbf-119">次の例では、単純な`main`関数。</span><span class="sxs-lookup"><span data-stu-id="f8dbf-119">The following example illustrates a simple `main` function.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/entry-point/snippet501.fs)]

<span data-ttu-id="f8dbf-120">このコードを次のコマンドラインを実行すると`EntryPoint.exe 1 2 3`出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f8dbf-120">When this code is executed with the command line `EntryPoint.exe 1 2 3`, the output is as follows.</span></span>

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a><span data-ttu-id="f8dbf-121">暗黙のエントリ ポイント</span><span class="sxs-lookup"><span data-stu-id="f8dbf-121">Implicit Entry Point</span></span>
<span data-ttu-id="f8dbf-122">No があるときに**EntryPoint**を明示的に最上位レベルのバインディングは、最後のファイルをコンパイル、エントリ ポイントを示す属性は、エントリ ポイントとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="f8dbf-122">When a program has no **EntryPoint** attribute that explicitly indicates the entry point, the top level bindings in the last file to be compiled are used as the entry point.</span></span>


## <a name="see-also"></a><span data-ttu-id="f8dbf-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8dbf-123">See Also</span></span>
[<span data-ttu-id="f8dbf-124">関数</span><span class="sxs-lookup"><span data-stu-id="f8dbf-124">Functions</span></span>](index.md)

[<span data-ttu-id="f8dbf-125">let バインド</span><span class="sxs-lookup"><span data-stu-id="f8dbf-125">let Bindings</span></span>](let-bindings.md)
