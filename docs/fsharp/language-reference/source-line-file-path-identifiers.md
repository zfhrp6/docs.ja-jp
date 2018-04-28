---
title: ソース行、ファイル、およびパスの識別子 (F#)
description: 組み込み f# 識別子の値を使用すると、ソースの行番号、ディレクトリ、およびコード内のファイル名へのアクセスを使用する方法を説明します。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 18a26f0aa0a0c1f9c0b448ec46eaebd540391324
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="source-line-file-and-path-identifiers"></a><span data-ttu-id="574e5-103">ソース行、ファイル、およびパスの識別子</span><span class="sxs-lookup"><span data-stu-id="574e5-103">Source Line, File, and Path Identifiers</span></span>

<span data-ttu-id="574e5-104">識別子`__LINE__`、`__SOURCE_DIRECTORY__`と`__SOURCE_FILE__`ソース行番号、ディレクトリおよびファイル名をコードにアクセスできるようにする組み込みの値は、します。</span><span class="sxs-lookup"><span data-stu-id="574e5-104">The identifiers `__LINE__`, `__SOURCE_DIRECTORY__` and `__SOURCE_FILE__` are built-in values that enable you to access the source line number, directory and file name in your code.</span></span>


## <a name="syntax"></a><span data-ttu-id="574e5-105">構文</span><span class="sxs-lookup"><span data-stu-id="574e5-105">Syntax</span></span>

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a><span data-ttu-id="574e5-106">コメント</span><span class="sxs-lookup"><span data-stu-id="574e5-106">Remarks</span></span>
<span data-ttu-id="574e5-107">型を持つこれらの各値`string`です。</span><span class="sxs-lookup"><span data-stu-id="574e5-107">Each of these values has type `string`.</span></span>

<span data-ttu-id="574e5-108">次の表では、ソース行、ファイル、および f# で使用可能なパスの識別子をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="574e5-108">The following table summarizes the source line, file, and path identifiers that are available in F#.</span></span> <span data-ttu-id="574e5-109">これらの識別子はプリプロセッサ マクロではありません。これらは、コンパイラで認識される組み込みの値です。</span><span class="sxs-lookup"><span data-stu-id="574e5-109">These identifiers are not preprocessor macros; they are built-in values that are recognized by the compiler.</span></span>

|<span data-ttu-id="574e5-110">事前定義の識別子</span><span class="sxs-lookup"><span data-stu-id="574e5-110">Predefined identifier</span></span>|<span data-ttu-id="574e5-111">説明</span><span class="sxs-lookup"><span data-stu-id="574e5-111">Description</span></span>|
|---------------------|-----------|
|`__LINE__`|<span data-ttu-id="574e5-112">現在の行番号に評価される検討`#line`ディレクティブです。</span><span class="sxs-lookup"><span data-stu-id="574e5-112">Evaluates to the current line number, considering `#line` directives.</span></span>|
|`__SOURCE_DIRECTORY__`|<span data-ttu-id="574e5-113">ソース ディレクトリの現在の完全パスに評価される検討`#line`ディレクティブです。</span><span class="sxs-lookup"><span data-stu-id="574e5-113">Evaluates to the current full path of the source directory, considering `#line` directives.</span></span>|
|`__SOURCE_FILE__`|<span data-ttu-id="574e5-114">現在のソース ファイル名とそのパスに評価される検討`#line`ディレクティブです。</span><span class="sxs-lookup"><span data-stu-id="574e5-114">Evaluates to the current source file name and its path, considering `#line` directives.</span></span>|
<span data-ttu-id="574e5-115">詳細については、`#line`ディレクティブを参照してください[コンパイラ ディレクティブ](compiler-directives.md)です。</span><span class="sxs-lookup"><span data-stu-id="574e5-115">For more information about the `#line` directive, see [Compiler Directives](compiler-directives.md).</span></span>

## <a name="example"></a><span data-ttu-id="574e5-116">例</span><span class="sxs-lookup"><span data-stu-id="574e5-116">Example</span></span>

<span data-ttu-id="574e5-117">次のコード例では、これらの値の使用を示します。</span><span class="sxs-lookup"><span data-stu-id="574e5-117">The following code example demonstrates the use of these values.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

<span data-ttu-id="574e5-118">Output:</span><span class="sxs-lookup"><span data-stu-id="574e5-118">Output:</span></span>

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a><span data-ttu-id="574e5-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="574e5-119">See Also</span></span>
[<span data-ttu-id="574e5-120">コンパイラ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="574e5-120">Compiler Directives</span></span>](compiler-directives.md)

[<span data-ttu-id="574e5-121">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="574e5-121">F# Language Reference</span></span>](index.md)
