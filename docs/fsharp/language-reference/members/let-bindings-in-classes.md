---
title: クラス内の let 束縛 (F#)
description: クラスの定義で 'let' 束縛を使用してプライベート フィールドや F# でクラスのプライベート関数を定義する方法を説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 1c17fe0edec14c28c9bdde86d0a2acb7c886cdf7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="let-bindings-in-classes"></a><span data-ttu-id="e3ae8-103">クラス内の let 束縛</span><span class="sxs-lookup"><span data-stu-id="e3ae8-103">let Bindings in Classes</span></span>

<span data-ttu-id="e3ae8-104">使用して、プライベート フィールドや F# でクラスのプライベート関数を定義することができます`let`クラス定義にバインドします。</span><span class="sxs-lookup"><span data-stu-id="e3ae8-104">You can define private fields and private functions for F# classes by using `let` bindings in the class definition.</span></span>


## <a name="syntax"></a><span data-ttu-id="e3ae8-105">構文</span><span class="sxs-lookup"><span data-stu-id="e3ae8-105">Syntax</span></span>

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a><span data-ttu-id="e3ae8-106">コメント</span><span class="sxs-lookup"><span data-stu-id="e3ae8-106">Remarks</span></span>
<span data-ttu-id="e3ae8-107">クラスの見出しと継承の宣言後、任意のメンバー定義の前に、前の構文が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e3ae8-107">The previous syntax appears after the class heading and inheritance declarations but before any member definitions.</span></span> <span data-ttu-id="e3ae8-108">構文は次のようにです`let`クラスがクラスで定義した名前の外部でのバインドはクラスに限定されているスコープを設定します。</span><span class="sxs-lookup"><span data-stu-id="e3ae8-108">The syntax is like that of `let` bindings outside of classes, but the names defined in a class have a scope that is limited to the class.</span></span> <span data-ttu-id="e3ae8-109">A`let`バインドによって、プライベート フィールドやデータを公開する関数または関数で公開されている、プロパティまたはメンバー メソッドを宣言します。</span><span class="sxs-lookup"><span data-stu-id="e3ae8-109">A `let` binding creates a private field or function; to expose data or functions publicly, declare a property or a member method.</span></span>

<span data-ttu-id="e3ae8-110">A`let`をバインドは静的なインスタンスと呼びます`let`バインドします。</span><span class="sxs-lookup"><span data-stu-id="e3ae8-110">A `let` binding that is not static is called an instance `let` binding.</span></span> <span data-ttu-id="e3ae8-111">インスタンス`let`バインディング オブジェクトの作成を実行します。</span><span class="sxs-lookup"><span data-stu-id="e3ae8-111">Instance `let` bindings execute when objects are created.</span></span> <span data-ttu-id="e3ae8-112">静的`let`バインディングは、型が最初に使用される前に実行することが保証されるクラスの静的初期化子の一部です。</span><span class="sxs-lookup"><span data-stu-id="e3ae8-112">Static `let` bindings are part of the static initializer for the class, which is guaranteed to execute before the type is first used.</span></span>

<span data-ttu-id="e3ae8-113">インスタンス内のコード`let`バインディングは、プライマリ コンス トラクターのパラメーターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e3ae8-113">The code within instance `let` bindings can use the primary constructor's parameters.</span></span>

<span data-ttu-id="e3ae8-114">属性およびアクセシビリティ修飾子には使用できません`let`クラスにバインドします。</span><span class="sxs-lookup"><span data-stu-id="e3ae8-114">Attributes and accessibility modifiers are not permitted on `let` bindings in classes.</span></span>

<span data-ttu-id="e3ae8-115">次のコード例がいくつかの種類を示す`let`クラスにバインドします。</span><span class="sxs-lookup"><span data-stu-id="e3ae8-115">The following code examples illustrate several types of `let` bindings in classes.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

<span data-ttu-id="e3ae8-116">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e3ae8-116">The output is as follows.</span></span>

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a><span data-ttu-id="e3ae8-117">別の方法でフィールドを作成するには</span><span class="sxs-lookup"><span data-stu-id="e3ae8-117">Alternative Ways to Create Fields</span></span>
<span data-ttu-id="e3ae8-118">使用することも、`val`プライベート フィールドを作成するキーワードです。</span><span class="sxs-lookup"><span data-stu-id="e3ae8-118">You can also use the `val` keyword to create a private field.</span></span> <span data-ttu-id="e3ae8-119">使用する場合、`val`キーワードが与えられていない値と、オブジェクトは作成されますが、既定値で初期化されます。</span><span class="sxs-lookup"><span data-stu-id="e3ae8-119">When using the `val` keyword, the field is not given a value when the object is created, but instead is initialized with a default value.</span></span> <span data-ttu-id="e3ae8-120">詳細については、次を参照してください。[明示的なフィールド: val キーワード](explicit-fields-the-val-keyword.md)です。</span><span class="sxs-lookup"><span data-stu-id="e3ae8-120">For more information, see [Explicit Fields: The val Keyword](explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="e3ae8-121">メンバー定義を使用して、キーワードを追加するクラスでプライベート フィールドを定義することも`private`を定義します。</span><span class="sxs-lookup"><span data-stu-id="e3ae8-121">You can also define private fields in a class by using a member definition and adding the keyword `private` to the definition.</span></span> <span data-ttu-id="e3ae8-122">これは、コードを書き直すことがなく、メンバーのアクセシビリティを変更する場合に役立ちます。 ことができます。</span><span class="sxs-lookup"><span data-stu-id="e3ae8-122">This can be useful if you expect to change the accessibility of a member without rewriting your code.</span></span> <span data-ttu-id="e3ae8-123">詳細については、「[Access Control](../access-control.md)」(アクセス制御) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3ae8-123">For more information, see [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e3ae8-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="e3ae8-124">See Also</span></span>
[<span data-ttu-id="e3ae8-125">メンバー</span><span class="sxs-lookup"><span data-stu-id="e3ae8-125">Members</span></span>](index.md)

[<span data-ttu-id="e3ae8-126">クラス内の `do` バインド</span><span class="sxs-lookup"><span data-stu-id="e3ae8-126">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)

[<span data-ttu-id="e3ae8-127">`let` バインド</span><span class="sxs-lookup"><span data-stu-id="e3ae8-127">`let` Bindings</span></span>](../functions/let-bindings.md)
