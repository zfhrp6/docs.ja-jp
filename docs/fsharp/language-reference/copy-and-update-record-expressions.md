---
title: "コピーして更新するレコード式 (f#)"
description: "'コピーと更新レコード式' 既存のレコードを更新プログラムをコピーするフィールドを指定および更新されたレコードを返しますを記述する方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: ChrSteinert
ms.author: phcart
ms.date: 06/04/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b5fc4ef0-64eb-4272-96a7-bb4dffbb634a
ms.openlocfilehash: 2eb51842b678780a1d6da96e237ebb92d1ea5cec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="559e6-104">レコード式のコピーと更新</span><span class="sxs-lookup"><span data-stu-id="559e6-104">Copy and Update Record Expressions</span></span>

<span data-ttu-id="559e6-105">A*コピーして更新するレコード式*を既存のレコードをコピーし、指定したフィールドを更新、更新されたレコードを返します。 式を指定します。</span><span class="sxs-lookup"><span data-stu-id="559e6-105">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>


## <a name="syntax"></a><span data-ttu-id="559e6-106">構文</span><span class="sxs-lookup"><span data-stu-id="559e6-106">Syntax</span></span>

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a><span data-ttu-id="559e6-107">コメント</span><span class="sxs-lookup"><span data-stu-id="559e6-107">Remarks</span></span>
<span data-ttu-id="559e6-108">レコードは可能な既存のレコードに更新プログラムがないように、既定では、変更できません。</span><span class="sxs-lookup"><span data-stu-id="559e6-108">Records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="559e6-109">更新されたレコードのレコードのすべてのフィールドを作成するのには、もう一度指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="559e6-109">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="559e6-110">このタスクを簡略化する、*コピーして更新するレコード式*使用できます。</span><span class="sxs-lookup"><span data-stu-id="559e6-110">To simplify this task a *copy and update record expression* can be used.</span></span> <span data-ttu-id="559e6-111">この式は、既存のレコードを受け取り、式から指定されたフィールドと、式で指定された存在しないフィールドを使用して、同じ種類の新しい 1 つを作成します。</span><span class="sxs-lookup"><span data-stu-id="559e6-111">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>
<span data-ttu-id="559e6-112">これは、既存のレコードをコピーし、可能性のあるフィールドの値の一部を変更する必要がある場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="559e6-112">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="559e6-113">新しく作成されたレコードのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="559e6-113">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="559e6-114">使用することがそのレコードのフィールドでのみ更新する場合は、*コピーして更新するレコード式*次と同様に。</span><span class="sxs-lookup"><span data-stu-id="559e6-114">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="559e6-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="559e6-115">See Also</span></span>
[<span data-ttu-id="559e6-116">レコード</span><span class="sxs-lookup"><span data-stu-id="559e6-116">Records</span></span>](records.md)

[<span data-ttu-id="559e6-117">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="559e6-117">F# Language Reference</span></span>](index.md)
