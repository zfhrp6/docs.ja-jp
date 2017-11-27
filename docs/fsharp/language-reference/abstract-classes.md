---
title: "抽象クラス (F#)"
description: "一部またはすべてのメンバーを実装しないままにして f# 抽象クラスをについて説明し、オブジェクトの種類の多様な一連の共通の機能を表します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a3dcc335-433b-4672-ac2d-ae6b11b816f3
ms.openlocfilehash: 209bcca70318db59506011b1f2bb74a09bf3814a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="abstract-classes"></a><span data-ttu-id="f29bd-104">抽象クラス</span><span class="sxs-lookup"><span data-stu-id="f29bd-104">Abstract Classes</span></span>

<span data-ttu-id="f29bd-105">*抽象クラス*実装を派生クラスによって提供されることができるように実装されていません、一部またはすべてのメンバーのままにするクラスです。</span><span class="sxs-lookup"><span data-stu-id="f29bd-105">*Abstract classes* are classes that leave some or all members unimplemented, so that implementations can be provided by derived classes.</span></span>

## <a name="syntax"></a><span data-ttu-id="f29bd-106">構文</span><span class="sxs-lookup"><span data-stu-id="f29bd-106">Syntax</span></span>

```fsharp
// Abstract class syntax.
[<AbstractClass>]
type [ accessibility-modifier ] abstract-class-name =
[ inherit base-class-or-interface-name ]
[ abstract-member-declarations-and-member-definitions ]

// Abstract member syntax.
abstract member member-name : type-signature
```

## <a name="remarks"></a><span data-ttu-id="f29bd-107">コメント</span><span class="sxs-lookup"><span data-stu-id="f29bd-107">Remarks</span></span>
<span data-ttu-id="f29bd-108">オブジェクト指向プログラミングでは、抽象クラスは、階層の基本クラスとして使用し、オブジェクトの種類の多様な一連の共通機能を表します。</span><span class="sxs-lookup"><span data-stu-id="f29bd-108">In object-oriented programming, an abstract class is used as a base class of a hierarchy, and represents common functionality of a diverse set of object types.</span></span> <span data-ttu-id="f29bd-109">"Abstract"という名前が示すように、抽象クラス多くの場合、対応していない問題ドメインの具体的なエンティティに直接できます。</span><span class="sxs-lookup"><span data-stu-id="f29bd-109">As the name "abstract" implies, abstract classes often do not correspond directly onto concrete entities in the problem domain.</span></span> <span data-ttu-id="f29bd-110">ただし、どのような多くのさまざまな具体的なエンティティが共通では関係。</span><span class="sxs-lookup"><span data-stu-id="f29bd-110">However, they do represent what many different concrete entities have in common.</span></span>

<span data-ttu-id="f29bd-111">抽象クラスがあります、`AbstractClass`属性。</span><span class="sxs-lookup"><span data-stu-id="f29bd-111">Abstract classes must have the `AbstractClass` attribute.</span></span> <span data-ttu-id="f29bd-112">実装されているし、メンバーが実装されていませんできます。</span><span class="sxs-lookup"><span data-stu-id="f29bd-112">They can have implemented and unimplemented members.</span></span> <span data-ttu-id="f29bd-113">用語の使用*抽象*クラスは、他の .NET 言語以外の場合と同様に適用するとただし、用語の使用*抽象*メソッドとプロパティに適用される場合は、少し異なりますからの f# では、他の .NET 言語で使用します。</span><span class="sxs-lookup"><span data-stu-id="f29bd-113">The use of the term *abstract* when applied to a class is the same as in other .NET languages; however, the use of the term *abstract* when applied to methods (and properties) is a little different in F# from its use in other .NET languages.</span></span> <span data-ttu-id="f29bd-114">F# でメソッドが付いている場合、`abstract`キーワード、このことを示しますメンバーと呼ばれる、エントリ、*仮想ディスパッチ スロット*、その種類の仮想関数の内部テーブルにします。</span><span class="sxs-lookup"><span data-stu-id="f29bd-114">In F#, when a method is marked with the `abstract` keyword, this indicates that a member has an entry, known as a *virtual dispatch slot*, in the internal table of virtual functions for that type.</span></span> <span data-ttu-id="f29bd-115">つまり、メソッドは、仮想ですが、`virtual`キーワードは、f# 言語では使用されません。</span><span class="sxs-lookup"><span data-stu-id="f29bd-115">In other words, the method is virtual, although the `virtual` keyword is not used in the F# language.</span></span> <span data-ttu-id="f29bd-116">キーワード`abstract`メソッドを実装するかどうかに関係なく、仮想メソッドで使用します。</span><span class="sxs-lookup"><span data-stu-id="f29bd-116">The keyword `abstract` is used on virtual methods regardless of whether the method is implemented.</span></span> <span data-ttu-id="f29bd-117">仮想ディスパッチ スロットの宣言は、そのディスパッチ スロットのメソッドの定義とは別です。</span><span class="sxs-lookup"><span data-stu-id="f29bd-117">The declaration of a virtual dispatch slot is separate from the definition of a method for that dispatch slot.</span></span> <span data-ttu-id="f29bd-118">そのため、抽象メソッドの宣言といずれかで、個別の定義の両方の組み合わせでは、仮想メソッドの宣言と他の .NET 言語での定義の f# 相当、`default`キーワードまたは`override`キーワード。</span><span class="sxs-lookup"><span data-stu-id="f29bd-118">Therefore, the F# equivalent of a virtual method declaration and definition in another .NET language is a combination of both an abstract method declaration and a separate definition, with either the `default` keyword or the `override` keyword.</span></span> <span data-ttu-id="f29bd-119">詳細と例については、次を参照してください。[メソッド](members/methods.md)です。</span><span class="sxs-lookup"><span data-stu-id="f29bd-119">For more information and examples, see [Methods](members/methods.md).</span></span>

<span data-ttu-id="f29bd-120">クラスは抽象メソッドが宣言されていますが、定義されていないことがある場合にのみ抽象と見なされます。</span><span class="sxs-lookup"><span data-stu-id="f29bd-120">A class is considered abstract only if there are abstract methods that are declared but not defined.</span></span> <span data-ttu-id="f29bd-121">そのため、抽象メソッドを持つクラスは、必ずしも抽象クラスではできません。</span><span class="sxs-lookup"><span data-stu-id="f29bd-121">Therefore, classes that have abstract methods are not necessarily abstract classes.</span></span> <span data-ttu-id="f29bd-122">クラスには、抽象メソッドが定義されていませんが、しない限りは使用しないで、 **AbstractClass**属性。</span><span class="sxs-lookup"><span data-stu-id="f29bd-122">Unless a class has undefined abstract methods, do not use the **AbstractClass** attribute.</span></span>

<span data-ttu-id="f29bd-123">前の構文で*アクセシビリティ修飾子*できます`public`、`private`または`internal`です。</span><span class="sxs-lookup"><span data-stu-id="f29bd-123">In the previous syntax, *accessibility-modifier* can be `public`, `private` or `internal`.</span></span> <span data-ttu-id="f29bd-124">詳細については、「[Access Control](access-control.md)」(アクセス制御) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f29bd-124">For more information, see [Access Control](access-control.md).</span></span>

<span data-ttu-id="f29bd-125">その他の種類と同様、基底クラスと 1 つ以上のインターフェイスの基本抽象クラスことができます。</span><span class="sxs-lookup"><span data-stu-id="f29bd-125">As with other types, abstract classes can have a base class and one or more base interfaces.</span></span> <span data-ttu-id="f29bd-126">と共に別々 の行に各基底クラスまたはインターフェイスが表示されます、`inherit`キーワード。</span><span class="sxs-lookup"><span data-stu-id="f29bd-126">Each base class or interface appears on a separate line together with the `inherit` keyword.</span></span>

<span data-ttu-id="f29bd-127">抽象クラスの種類の定義は、完全に定義されたメンバーを含めることができますが、抽象メンバーを含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="f29bd-127">The type definition of an abstract class can contain fully defined members, but it can also contain abstract members.</span></span> <span data-ttu-id="f29bd-128">抽象メンバーの構文は、前の構文で別々 に表示されます。</span><span class="sxs-lookup"><span data-stu-id="f29bd-128">The syntax for abstract members is shown separately in the previous syntax.</span></span> <span data-ttu-id="f29bd-129">この構文では、*型シグネチャ*メンバーの一覧を含む、パラメーターの順序と戻り値の型の型で区切られます`->`トークンや`*`カリー化を必要に応じてトークンとタプルパラメーター。</span><span class="sxs-lookup"><span data-stu-id="f29bd-129">In this syntax, the *type signature* of a member is a list that contains the parameter types in order and the return types, separated by `->` tokens and/or `*` tokens as appropriate for curried and tupled parameters.</span></span> <span data-ttu-id="f29bd-130">抽象メンバー型のシグネチャの構文は、署名ファイル内で使用して、Visual Studio コード エディターの IntelliSense によって表示されるのと同じです。</span><span class="sxs-lookup"><span data-stu-id="f29bd-130">The syntax for abstract member type signatures is the same as that used in signature files and that shown by IntelliSense in the Visual Studio Code Editor.</span></span>

<span data-ttu-id="f29bd-131">次のコードは、抽象クラスが 2 つ非抽象派生クラス、四角形と円形の図形を示しています。</span><span class="sxs-lookup"><span data-stu-id="f29bd-131">The following code illustrates an abstract class Shape, which has two non-abstract derived classes, Square and Circle.</span></span> <span data-ttu-id="f29bd-132">この例では、抽象クラス、メソッド、プロパティを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f29bd-132">The example shows how to use abstract classes, methods, and properties.</span></span> <span data-ttu-id="f29bd-133">この例では、抽象クラス図形は、具体的なエンティティの円、四角形の共通の要素を表します。</span><span class="sxs-lookup"><span data-stu-id="f29bd-133">In the example, the abstract class Shape represents the common elements of the concrete entities circle and square.</span></span> <span data-ttu-id="f29bd-134">(2 次元座標系) のすべての図形の一般的な機能は、抽象化されて、図形のクラスに: グリッド、回転の角度と、領域および境界のプロパティでの位置。</span><span class="sxs-lookup"><span data-stu-id="f29bd-134">The common features of all shapes (in a two-dimensional coordinate system) are abstracted out into the Shape class: the position on the grid, an angle of rotation, and the area and perimeter properties.</span></span> <span data-ttu-id="f29bd-135">これは、オーバーライドできます、位置、個々 の図形を変更できませんが、動作を除く。</span><span class="sxs-lookup"><span data-stu-id="f29bd-135">These can be overridden, except for position, the behavior of which individual shapes cannot change.</span></span>

<span data-ttu-id="f29bd-136">その対称のための回転インバリアントが、Circle クラスと同様に、回転メソッドをオーバーライドすることができます。</span><span class="sxs-lookup"><span data-stu-id="f29bd-136">The rotation method can be overridden, as in the Circle class, which is rotation invariant because of its symmetry.</span></span> <span data-ttu-id="f29bd-137">ように、Circle クラスでは、回転メソッドは何も実行しないメソッドに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="f29bd-137">So in the Circle class, the rotation method is replaced by a method that does nothing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

<span data-ttu-id="f29bd-138">**出力:**</span><span class="sxs-lookup"><span data-stu-id="f29bd-138">**Output:**</span></span>

```
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a><span data-ttu-id="f29bd-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="f29bd-139">See Also</span></span>
[<span data-ttu-id="f29bd-140">クラス</span><span class="sxs-lookup"><span data-stu-id="f29bd-140">Classes</span></span>](classes.md)

[<span data-ttu-id="f29bd-141">メンバー</span><span class="sxs-lookup"><span data-stu-id="f29bd-141">Members</span></span>](members/index.md)

[<span data-ttu-id="f29bd-142">メソッド</span><span class="sxs-lookup"><span data-stu-id="f29bd-142">Methods</span></span>](members/methods.md)

[<span data-ttu-id="f29bd-143">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f29bd-143">Properties</span></span>](members/Properties.md)
