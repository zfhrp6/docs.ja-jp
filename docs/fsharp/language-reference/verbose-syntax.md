---
title: 冗語構文 (F#)
description: F# のプログラミング言語の詳細および軽量構文の違いについて説明します。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: fd040a66a789bc6717fd14e6a9f28274c9e3542b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="verbose-syntax"></a><span data-ttu-id="f89ae-103">冗語構文</span><span class="sxs-lookup"><span data-stu-id="f89ae-103">Verbose Syntax</span></span>

<span data-ttu-id="f89ae-104">2 つの形式の構文がある多くの構成要素、f# 言語で使用可能な:*冗語構文*と*軽量構文*です。</span><span class="sxs-lookup"><span data-stu-id="f89ae-104">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="f89ae-105">冗語構文では、一般的に使用されていなくても、インデントを受けにくくするという利点があります。</span><span class="sxs-lookup"><span data-stu-id="f89ae-105">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="f89ae-106">その他のキーワードと同様に、軽量構文が短いとインデントの先頭と末尾、コンス トラクターを使用ではなく`begin`、 `end`、`in`のようにします。</span><span class="sxs-lookup"><span data-stu-id="f89ae-106">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="f89ae-107">既定の構文は、軽量構文です。</span><span class="sxs-lookup"><span data-stu-id="f89ae-107">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="f89ae-108">このトピックは、軽量構文が有効でない場合に、f# の構成要素の構文を説明します。</span><span class="sxs-lookup"><span data-stu-id="f89ae-108">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="f89ae-109">冗語構文は、常に有効に、軽量構文を有効にした場合でも使用できるようにも冗語構文の一部の構造体。</span><span class="sxs-lookup"><span data-stu-id="f89ae-109">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="f89ae-110">使用して軽量構文を無効にすることができます、`#light "off"`ディレクティブです。</span><span class="sxs-lookup"><span data-stu-id="f89ae-110">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>


## <a name="table-of-constructs"></a><span data-ttu-id="f89ae-111">構成要素の表</span><span class="sxs-lookup"><span data-stu-id="f89ae-111">Table of Constructs</span></span>
<span data-ttu-id="f89ae-112">次の表のコンテキストで、軽量と詳細な f# 言語構成要素の構文を示していますが、2 つの形式間の差がある場合。</span><span class="sxs-lookup"><span data-stu-id="f89ae-112">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="f89ae-113">この表で、山かっこ (&lt;&gt;) 構文のユーザーが指定した要素を囲みます。</span><span class="sxs-lookup"><span data-stu-id="f89ae-113">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="f89ae-114">さらに詳細な構文については、これらの構成要素内で使用される各言語構成要素のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f89ae-114">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>



<table>
<tr>
<th><span data-ttu-id="f89ae-115">言語構成要素</span><span class="sxs-lookup"><span data-stu-id="f89ae-115">Language construct</span></span></th>
<th><span data-ttu-id="f89ae-116">軽量構文</span><span class="sxs-lookup"><span data-stu-id="f89ae-116">Lightweight syntax</span></span></th>
<th><span data-ttu-id="f89ae-117">冗語構文</span><span class="sxs-lookup"><span data-stu-id="f89ae-117">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="f89ae-118">複合式</span><span class="sxs-lookup"><span data-stu-id="f89ae-118">compound expressions</span></span>
</td>
<td>

```xml
<expression1>
<expression2>
```
</td><td>

```
<expression1>; <expression2>
```

</td>
</tr>
<tr><td>


<span data-ttu-id="f89ae-119">入れ子になった`let`バインド</span><span class="sxs-lookup"><span data-stu-id="f89ae-119">nested `let` bindings</span></span>

</td><td>
```
let f x =
    let a = 1
    let b = 2
    x + a + b
```

</td><td>

```
let f x =
    let a = 1 in
    let b = 2 in
    x + a + b
```

</td>
</tr>
<tr><td>
<span data-ttu-id="f89ae-120">コード ブロック</span><span class="sxs-lookup"><span data-stu-id="f89ae-120">code block</span></span>
</td><td>

```
(
    <expression1>
    <expression2>
)
```

</td><td>

```
begin
    <expression1>;
    <expression2>;
end
```
</td>
</tr>
<tr><td>
`for...do`
</td><td>

```
for counter = start to finish do
    ...
```

</td><td>

```
for counter = start to finish do
    ...
done
```

</td>
</tr>
<tr><td>
`while...do`
</td><td>

```
while <condition> do
    ...
```

</td><td>

```
while <condition> do
    ...
done
```

</td>
</tr>
<tr><td>
`for...in`
</td><td>

```
for var in start .. finish do
    ...
```

</td><td>

```
for var in start .. finish do
    ...
done
```

</td>
</tr>
<tr><td>
`do`
</td><td>

```
do
    ...
```

</td><td>

```
do
    ...
in
```

</td>
</tr>
<tr><td><span data-ttu-id="f89ae-121">レコード</span><span class="sxs-lookup"><span data-stu-id="f89ae-121">record</span></span>
</td><td>

```
type <record-name> =
    {
        <field-declarations>
    }
    <value-or-member-definitions>
```

</td><td>

```
type <record-name> =
    {
        <field-declarations>
    }
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="f89ae-122">class</span><span class="sxs-lookup"><span data-stu-id="f89ae-122">class</span></span>
</td><td><span data-ttu-id="f89ae-123">
```
type <class-name>(<params>) = ... ```

</span><span class="sxs-lookup"><span data-stu-id="f89ae-123">
```
type <class-name>(<params>) = ... ```

</span></span></td><td>

```
type <class-name>(<params>) =
    class
        ...
    end
```
</td>
</tr>
<tr><td><span data-ttu-id="f89ae-124">構造体</span><span class="sxs-lookup"><span data-stu-id="f89ae-124">structure</span></span></td><td>

```
[<StructAttribute>]
type <structure-name> =
    ...
```
</td><td>

```
type <structure-name> =
    struct
        ...
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="f89ae-125">判別共用体</span><span class="sxs-lookup"><span data-stu-id="f89ae-125">discriminated union</span></span></td><td>

```
type <union-name> =
    | ...
    | ...
    ...
    <value-or-member definitions>
```
</td><td>

```
type <union-name> =
    | ...
    | ...
    ...
    with
        <value-or-member-definitions>
    end    
```

</td>
</tr>
<tr><td><span data-ttu-id="f89ae-126">interface</span><span class="sxs-lookup"><span data-stu-id="f89ae-126">interface</span></span></td><td>

```
type <interface-name> =
    ...
```
</td><td>

```
type <interface-name> =
    interface
        ...
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="f89ae-127">オブジェクト式</span><span class="sxs-lookup"><span data-stu-id="f89ae-127">object expression</span></span></td><td>

```
{ new <type-name>
    with
        <value-or-member-definitions>
        <interface-implementations>
}
```

</td><td>

```
{ new <type-name>
    with
        <value-or-member-definitions>
    end
    <interface-implementations>
}
```

</td>
</tr>
<tr><td><span data-ttu-id="f89ae-128">インターフェイスの実装</span><span class="sxs-lookup"><span data-stu-id="f89ae-128">interface implementation</span></span></td><td>

```
interface <interface-name>
    with
        <value-or-member-definitions>
```

</td><td>

```
interface <interface-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="f89ae-129">型拡張機能</span><span class="sxs-lookup"><span data-stu-id="f89ae-129">type extension</span></span></td><td>

```
type <type-name>
    with
        <value-or-member-definitions>
```

</td><td>

```
type <type-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="f89ae-130">name</span><span class="sxs-lookup"><span data-stu-id="f89ae-130">module</span></span></td><td>

```
module <module-name> =
    ...
```

</td><td>

```
module <module-name> =
    begin
        ...
    end
```

</td>
</tr>
</table>



## <a name="see-also"></a><span data-ttu-id="f89ae-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="f89ae-131">See Also</span></span>
[<span data-ttu-id="f89ae-132">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="f89ae-132">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="f89ae-133">コンパイラ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="f89ae-133">Compiler Directives</span></span>](compiler-directives.md)

[<span data-ttu-id="f89ae-134">コードのフォーマットに関するガイドライン</span><span class="sxs-lookup"><span data-stu-id="f89ae-134">Code Formatting Guidelines</span></span>](code-formatting-guidelines.md)
