---
title: コピーして更新するレコード式 (f#)
description: "'コピーと更新レコード式' 既存のレコードを更新プログラムをコピーするフィールドを指定および更新されたレコードを返しますを記述する方法を説明します。"
author: ChrSteinert
ms.author: phcart
ms.date: 06/04/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 98a515b5f053e9339588157185848e8315a580f4
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="cdaef-103">レコード式のコピーと更新</span><span class="sxs-lookup"><span data-stu-id="cdaef-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="cdaef-104">A*コピーして更新するレコード式*を既存のレコードをコピーし、指定したフィールドを更新、更新されたレコードを返します。 式を指定します。</span><span class="sxs-lookup"><span data-stu-id="cdaef-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>


## <a name="syntax"></a><span data-ttu-id="cdaef-105">構文</span><span class="sxs-lookup"><span data-stu-id="cdaef-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a><span data-ttu-id="cdaef-106">コメント</span><span class="sxs-lookup"><span data-stu-id="cdaef-106">Remarks</span></span>
<span data-ttu-id="cdaef-107">レコードは可能な既存のレコードに更新プログラムがないように、既定では、変更できません。</span><span class="sxs-lookup"><span data-stu-id="cdaef-107">Records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="cdaef-108">更新されたレコードのレコードのすべてのフィールドを作成するのには、もう一度指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cdaef-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="cdaef-109">このタスクを簡略化する、*コピーして更新するレコード式*使用できます。</span><span class="sxs-lookup"><span data-stu-id="cdaef-109">To simplify this task a *copy and update record expression* can be used.</span></span> <span data-ttu-id="cdaef-110">この式は、既存のレコードを受け取り、式から指定されたフィールドと、式で指定された存在しないフィールドを使用して、同じ種類の新しい 1 つを作成します。</span><span class="sxs-lookup"><span data-stu-id="cdaef-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>
<span data-ttu-id="cdaef-111">これは、既存のレコードをコピーし、可能性のあるフィールドの値の一部を変更する必要がある場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="cdaef-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="cdaef-112">新しく作成されたレコードのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="cdaef-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="cdaef-113">使用することがそのレコードのフィールドでのみ更新する場合は、*コピーして更新するレコード式*次と同様に。</span><span class="sxs-lookup"><span data-stu-id="cdaef-113">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="cdaef-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="cdaef-114">See Also</span></span>
[<span data-ttu-id="cdaef-115">レコード</span><span class="sxs-lookup"><span data-stu-id="cdaef-115">Records</span></span>](records.md)

[<span data-ttu-id="cdaef-116">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="cdaef-116">F# Language Reference</span></span>](index.md)
