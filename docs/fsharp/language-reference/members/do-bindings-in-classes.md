---
title: "クラス内の do 束縛 (F#)"
description: "F# を使用して、'do'、オブジェクトが作成されたとき、または型が最初に使用されるときにアクションを実行するクラス定義にバインドする方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 78987cb8-bdba-46e2-b5b2-994c83fe42c4
ms.openlocfilehash: f9582338306d87c3dd799425083037cc95b31b1e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="do-bindings-in-classes"></a><span data-ttu-id="ce020-104">クラス内の do 束縛</span><span class="sxs-lookup"><span data-stu-id="ce020-104">do Bindings in Classes</span></span>

<span data-ttu-id="ce020-105">A`do`オブジェクトを作成するときや、静的なクラス定義のバインディングにアクションを実行します`do`バインディング型を使用する場合最初。</span><span class="sxs-lookup"><span data-stu-id="ce020-105">A `do` binding in a class definition performs actions when the object is constructed or, for a static `do` binding, when the type is first used.</span></span>


## <a name="syntax"></a><span data-ttu-id="ce020-106">構文</span><span class="sxs-lookup"><span data-stu-id="ce020-106">Syntax</span></span>

```fsharp
[static] do expression
```

## <a name="remarks"></a><span data-ttu-id="ce020-107">コメント</span><span class="sxs-lookup"><span data-stu-id="ce020-107">Remarks</span></span>
<span data-ttu-id="ce020-108">A`do`と共に、または後に、バインディングが表示されます`let`バインディングが、クラス定義内のメンバー定義の前にします。</span><span class="sxs-lookup"><span data-stu-id="ce020-108">A `do` binding appears together with or after `let` bindings but before member definitions in a class definition.</span></span> <span data-ttu-id="ce020-109">`do`キーワードは省略可能です`do`バインド モジュール レベルでは省略可能です`do`クラス定義にバインドします。</span><span class="sxs-lookup"><span data-stu-id="ce020-109">Although the `do` keyword is optional for `do` bindings at the module level, it is not optional for `do` bindings in a class definition.</span></span>

<span data-ttu-id="ce020-110">任意のすべてのオブジェクトの構築、特定の種類、非静的`do`バインドおよび非静的`let`バインディングは、クラス定義内に出現する順序で実行されます。</span><span class="sxs-lookup"><span data-stu-id="ce020-110">For the construction of every object of any given type, non-static `do` bindings and non-static `let` bindings are executed in the order in which they appear in the class definition.</span></span> <span data-ttu-id="ce020-111">複数`do`バインドが 1 つの型で発生することができます。</span><span class="sxs-lookup"><span data-stu-id="ce020-111">Multiple `do` bindings can occur in one type.</span></span> <span data-ttu-id="ce020-112">非静的`let`バインドおよび非静的`do`バインディングが、プライマリ コンス トラクターの本体になります。</span><span class="sxs-lookup"><span data-stu-id="ce020-112">The non-static `let` bindings and the non-static `do` bindings become the body of the primary constructor.</span></span> <span data-ttu-id="ce020-113">静的でないコード`do`束縛セクションでは、プライマリ コンス トラクターのパラメーター、および任意の値やで定義されている関数を参照できます、`let`束縛セクションでします。</span><span class="sxs-lookup"><span data-stu-id="ce020-113">The code in the non-static `do` bindings section can reference the primary constructor parameters and any values or functions that are defined in the `let` bindings section.</span></span>

<span data-ttu-id="ce020-114">非静的`do`バインドは、クラスには、自己識別子で定義されている限り、クラスのメンバーにアクセスできる、`as`見出し、およびそれらのメンバーのすべての使用は、クラスに対して、自己識別子で修飾されて限りクラス内のキーワードです。</span><span class="sxs-lookup"><span data-stu-id="ce020-114">Non-static `do` bindings can access members of the class as long as the class has a self identifier that is defined by an `as` keyword in the class heading, and as long as all uses of those members are qualified with the self identifier for the class.</span></span>

<span data-ttu-id="ce020-115">`let`バインドはメンバーが期待どおりに動作する保証するために必要な多くの場合、クラスのプライベート フィールドを初期化する`do`バインドは通常の後に記述`let`でコードのバインディング、`do`バインドできます完全に初期化されたオブジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="ce020-115">Because `let` bindings initialize the private fields of a class, which is often necessary to guarantee that members behave as expected, `do` bindings are usually put after `let` bindings so that code in the `do` binding can execute with a fully initialized object.</span></span> <span data-ttu-id="ce020-116">コードでは、初期化が完了する前に、メンバーを使用しようとするとする InvalidOperationException が発生します。</span><span class="sxs-lookup"><span data-stu-id="ce020-116">If your code attempts to use a member before the initialization is complete, an InvalidOperationException is raised.</span></span>

<span data-ttu-id="ce020-117">静的`do`バインディングは、静的メンバーを参照できますか、外側のフィールドは、クラスが、メンバーまたはフィールドをインスタンス化できません。</span><span class="sxs-lookup"><span data-stu-id="ce020-117">Static `do` bindings can reference static members or fields of the enclosing class but not instance members or fields.</span></span> <span data-ttu-id="ce020-118">静的`do`バインディング クラスが最初に使用される前に実行することが保証されると、クラスの静的初期化子の一部になります。</span><span class="sxs-lookup"><span data-stu-id="ce020-118">Static `do` bindings become part of the static initializer for the class, which is guaranteed to execute before the class is first used.</span></span>

<span data-ttu-id="ce020-119">属性は無視されます`do`型にバインドします。</span><span class="sxs-lookup"><span data-stu-id="ce020-119">Attributes are ignored for `do` bindings in types.</span></span> <span data-ttu-id="ce020-120">属性のコードで実行するために必要な`do`、バインドする必要がありますに適用される、プライマリ コンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="ce020-120">If an attribute is required for code that executes in a `do` binding, it must be applied to the primary constructor.</span></span>

<span data-ttu-id="ce020-121">次のコードでは、クラスには、静的な`do`バインドおよび非静的`do`バインドします。</span><span class="sxs-lookup"><span data-stu-id="ce020-121">In the following code, a class has a static `do` binding and a non-static `do` binding.</span></span> <span data-ttu-id="ce020-122">オブジェクトが 2 つのパラメーターを持つコンス トラクターを持つ`a`と`b`で 2 つのプライベート フィールドが定義されていると、`let`クラスにバインドします。</span><span class="sxs-lookup"><span data-stu-id="ce020-122">The object has a constructor that has two parameters, `a` and `b`, and two private fields are defined in the `let` bindings for the class.</span></span> <span data-ttu-id="ce020-123">2 つのプロパティも定義します。</span><span class="sxs-lookup"><span data-stu-id="ce020-123">Two properties are also defined.</span></span> <span data-ttu-id="ce020-124">これらはすべてのスコープから、静的でない`do`バインディング セクションで、それらすべての値を出力する行で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="ce020-124">All of these are in scope in the non-static `do` bindings section, as is illustrated by the line that prints all those values.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

<span data-ttu-id="ce020-125">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ce020-125">The output is as follows.</span></span>

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a><span data-ttu-id="ce020-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="ce020-126">See Also</span></span>
[<span data-ttu-id="ce020-127">メンバー</span><span class="sxs-lookup"><span data-stu-id="ce020-127">Members</span></span>](index.md)

[<span data-ttu-id="ce020-128">クラス</span><span class="sxs-lookup"><span data-stu-id="ce020-128">Classes</span></span>](../classes.md)

[<span data-ttu-id="ce020-129">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="ce020-129">Constructors</span></span>](constructors.md)

[<span data-ttu-id="ce020-130">クラス内の `let` バインド</span><span class="sxs-lookup"><span data-stu-id="ce020-130">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)

[<span data-ttu-id="ce020-131">`do`バインド</span><span class="sxs-lookup"><span data-stu-id="ce020-131">`do` Bindings</span></span>](../functions/do-Bindings.md)
