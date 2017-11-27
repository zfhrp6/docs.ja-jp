---
title: "冗語構文 (F#)"
description: "F# のプログラミング言語の詳細および軽量構文の違いについて説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 0a6792b3-b312-4453-a025-21d9760eee5d
ms.openlocfilehash: 2cef359a879897825733a3186be97b38896f5953
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="verbose-syntax"></a><span data-ttu-id="6952f-104">冗語構文</span><span class="sxs-lookup"><span data-stu-id="6952f-104">Verbose Syntax</span></span>

<span data-ttu-id="6952f-105">2 つの形式の構文がある多くの構成要素、f# 言語で使用可能な:*冗語構文*と*軽量構文*です。</span><span class="sxs-lookup"><span data-stu-id="6952f-105">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="6952f-106">冗語構文では、一般的に使用されていなくても、インデントを受けにくくするという利点があります。</span><span class="sxs-lookup"><span data-stu-id="6952f-106">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="6952f-107">その他のキーワードと同様に、軽量構文が短いとインデントの先頭と末尾、コンス トラクターを使用ではなく`begin`、 `end`、`in`のようにします。</span><span class="sxs-lookup"><span data-stu-id="6952f-107">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="6952f-108">既定の構文は、軽量構文です。</span><span class="sxs-lookup"><span data-stu-id="6952f-108">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="6952f-109">このトピックは、軽量構文が有効でない場合に、f# の構成要素の構文を説明します。</span><span class="sxs-lookup"><span data-stu-id="6952f-109">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="6952f-110">冗語構文は、常に有効に、軽量構文を有効にした場合でも使用できるようにも冗語構文の一部の構造体。</span><span class="sxs-lookup"><span data-stu-id="6952f-110">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="6952f-111">使用して軽量構文を無効にすることができます、`#light "off"`ディレクティブです。</span><span class="sxs-lookup"><span data-stu-id="6952f-111">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>


## <a name="table-of-constructs"></a><span data-ttu-id="6952f-112">構成要素の表</span><span class="sxs-lookup"><span data-stu-id="6952f-112">Table of Constructs</span></span>
<span data-ttu-id="6952f-113">次の表のコンテキストで、軽量と詳細な f# 言語構成要素の構文を示していますが、2 つの形式間の差がある場合。</span><span class="sxs-lookup"><span data-stu-id="6952f-113">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="6952f-114">この表で、山かっこ (&lt;&gt;) 構文のユーザーが指定した要素を囲みます。</span><span class="sxs-lookup"><span data-stu-id="6952f-114">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="6952f-115">さらに詳細な構文については、これらの構成要素内で使用される各言語構成要素のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6952f-115">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>



<table>
<tr>
<th><span data-ttu-id="6952f-116">言語構成要素</span><span class="sxs-lookup"><span data-stu-id="6952f-116">Language construct</span></span></th>
<th><span data-ttu-id="6952f-117">軽量構文</span><span class="sxs-lookup"><span data-stu-id="6952f-117">Lightweight syntax</span></span></th>
<th><span data-ttu-id="6952f-118">冗語構文</span><span class="sxs-lookup"><span data-stu-id="6952f-118">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="6952f-119">複合式</span><span class="sxs-lookup"><span data-stu-id="6952f-119">compound expressions</span></span>
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


<span data-ttu-id="6952f-120">入れ子になった`let`バインド</span><span class="sxs-lookup"><span data-stu-id="6952f-120">nested `let` bindings</span></span>

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
<span data-ttu-id="6952f-121">コード ブロック</span><span class="sxs-lookup"><span data-stu-id="6952f-121">code block</span></span>
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
<tr><td><span data-ttu-id="6952f-122">レコード</span><span class="sxs-lookup"><span data-stu-id="6952f-122">record</span></span>
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
<tr><td><span data-ttu-id="6952f-123">class</span><span class="sxs-lookup"><span data-stu-id="6952f-123">class</span></span>
</td><td><span data-ttu-id="6952f-124">
```
type <class-name>(<params>) = ... ```

</span><span class="sxs-lookup"><span data-stu-id="6952f-124">
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
<tr><td><span data-ttu-id="6952f-125">構造体</span><span class="sxs-lookup"><span data-stu-id="6952f-125">structure</span></span></td><td>

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
<tr><td><span data-ttu-id="6952f-126">判別共用体</span><span class="sxs-lookup"><span data-stu-id="6952f-126">discriminated union</span></span></td><td>

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
<tr><td><span data-ttu-id="6952f-127">interface</span><span class="sxs-lookup"><span data-stu-id="6952f-127">interface</span></span></td><td>

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
<tr><td><span data-ttu-id="6952f-128">オブジェクト式</span><span class="sxs-lookup"><span data-stu-id="6952f-128">object expression</span></span></td><td>

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
<tr><td><span data-ttu-id="6952f-129">インターフェイスの実装</span><span class="sxs-lookup"><span data-stu-id="6952f-129">interface implementation</span></span></td><td>

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
<tr><td><span data-ttu-id="6952f-130">型拡張機能</span><span class="sxs-lookup"><span data-stu-id="6952f-130">type extension</span></span></td><td>

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
<tr><td><span data-ttu-id="6952f-131">name</span><span class="sxs-lookup"><span data-stu-id="6952f-131">module</span></span></td><td>

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



## <a name="see-also"></a><span data-ttu-id="6952f-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="6952f-132">See Also</span></span>
[<span data-ttu-id="6952f-133">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="6952f-133">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="6952f-134">コンパイラ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="6952f-134">Compiler Directives</span></span>](compiler-directives.md)

[<span data-ttu-id="6952f-135">コードのフォーマットに関するガイドライン</span><span class="sxs-lookup"><span data-stu-id="6952f-135">Code Formatting Guidelines</span></span>](code-formatting-guidelines.md)
