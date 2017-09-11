---
title: "共通型システムの詳細"
description: "共通型システムの詳細"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: b5482a1d-7bdc-40fe-aa45-10df930ceb5b
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 6be672acc84a76106e25b82574acad16beb4a8ac
ms.contentlocale: ja-jp
ms.lasthandoff: 03/02/2017

---

# <a name="common-type-system-in-depth"></a><span data-ttu-id="bbda1-104">共通型システムの詳細</span><span class="sxs-lookup"><span data-stu-id="bbda1-104">Common type system in depth</span></span>

<span data-ttu-id="bbda1-105">このトピックには、共通型システムの詳細を説明する次のセクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="bbda1-105">This topic contains the following sections that explore the common type system in depth:</span></span>

* [<span data-ttu-id="bbda1-106">.NET の型</span><span class="sxs-lookup"><span data-stu-id="bbda1-106">Types in .NET</span></span>](#types-in-net)

* [<span data-ttu-id="bbda1-107">型定義</span><span class="sxs-lookup"><span data-stu-id="bbda1-107">Type definitions</span></span>](#type-definitions)

* [<span data-ttu-id="bbda1-108">型のメンバー</span><span class="sxs-lookup"><span data-stu-id="bbda1-108">Type members</span></span>](#type-members)

* [<span data-ttu-id="bbda1-109">型のメンバーの特性</span><span class="sxs-lookup"><span data-stu-id="bbda1-109">Characteristics of type members</span></span>](#characteristics-of-type-members)


## <a name="types-in-net"></a><span data-ttu-id="bbda1-110">.NET の型</span><span class="sxs-lookup"><span data-stu-id="bbda1-110">Types in .NET</span></span>

<span data-ttu-id="bbda1-111">.NET に存在するすべての型は、値型と参照型のどちらかに区別されます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-111">All types in .NET are either value types or reference types.</span></span> 

<span data-ttu-id="bbda1-112">値型は、オブジェクトがその実際の値で表されるデータ型です。</span><span class="sxs-lookup"><span data-stu-id="bbda1-112">Value types are data types whose objects are represented by the object's actual value.</span></span> <span data-ttu-id="bbda1-113">変数に値型のインスタンスが割り当てられると、その変数には値の新しいコピーが代入されます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-113">If an instance of a value type is assigned to a variable, that variable is given a fresh copy of the value.</span></span>

<span data-ttu-id="bbda1-114">参照型は、オブジェクトがその実際の値を指す参照 (ポインターのようなもの) によって表されるデータ型です。</span><span class="sxs-lookup"><span data-stu-id="bbda1-114">Reference types are data types whose objects are represented by a reference (similar to a pointer) to the object's actual value.</span></span> <span data-ttu-id="bbda1-115">参照型が変数に割り当てられている場合、その変数は元の値を参照します (つまり、元の値を指します)。</span><span class="sxs-lookup"><span data-stu-id="bbda1-115">If a reference type is assigned to a variable, that variable references (points to) the original value.</span></span> <span data-ttu-id="bbda1-116">コピーは作成されません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-116">No copy is made.</span></span> 

<span data-ttu-id="bbda1-117">.NET の共通型システムは、次の&5; つの型のカテゴリをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="bbda1-117">The common type system in .NET supports the following five categories of types:</span></span>

* [<span data-ttu-id="bbda1-118">クラス</span><span class="sxs-lookup"><span data-stu-id="bbda1-118">Classes</span></span>](#classes)

* [<span data-ttu-id="bbda1-119">構造体</span><span class="sxs-lookup"><span data-stu-id="bbda1-119">Structures</span></span>](#structures)

* [<span data-ttu-id="bbda1-120">列挙型</span><span class="sxs-lookup"><span data-stu-id="bbda1-120">Enumerations</span></span>](#enumerations)

* [<span data-ttu-id="bbda1-121">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bbda1-121">Interfaces</span></span>](#interfaces)

* [<span data-ttu-id="bbda1-122">デリゲート</span><span class="sxs-lookup"><span data-stu-id="bbda1-122">Delegates</span></span>](#delegates)

### <a name="classes"></a><span data-ttu-id="bbda1-123">クラス</span><span class="sxs-lookup"><span data-stu-id="bbda1-123">Classes</span></span>

<span data-ttu-id="bbda1-124">クラスは参照型であり、他のクラスから直接派生させることも、[System.Object](xref:System.Object) から暗黙的に派生させることもできます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-124">A class is a reference type that can be derived directly from another class and that is derived implicitly from [System.Object](xref:System.Object).</span></span> <span data-ttu-id="bbda1-125">クラスは、オブジェクト (クラスのインスタンス) が実行できる操作 (メソッド、イベント、またはプロパティ) およびオブジェクトが保持するデータ (フィールド) を定義するものです。</span><span class="sxs-lookup"><span data-stu-id="bbda1-125">The class defines the operations that an object (which is an instance of the class) can perform (methods, events, or properties) and the data that the object contains (fields).</span></span> <span data-ttu-id="bbda1-126">通常、クラスは、たとえば定義のみを持ち実装は持たないインターフェイスとは対照的に、定義と実装の両方を持ちます。しかし、実装を持たないメンバーが&1; つ以上存在するクラスもあります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-126">Although a class generally includes both definition and implementation (unlike interfaces, for example, which contain only definition without implementation), it can have one or more members that have no implementation.</span></span>

<span data-ttu-id="bbda1-127">クラスが持つことのできる特性のいくつかを次の表で説明します。</span><span class="sxs-lookup"><span data-stu-id="bbda1-127">The following table describes some of the characteristics that a class may have.</span></span> <span data-ttu-id="bbda1-128">ランタイムをサポートする言語にはそれぞれ、クラスまたはクラス メンバーに対し、こうした特性の&1; つ以上を指定する手段が用意されています。</span><span class="sxs-lookup"><span data-stu-id="bbda1-128">Each language that supports the runtime provides a way to indicate that a class or class member has one or more of these characteristics.</span></span> <span data-ttu-id="bbda1-129">ただし、.NET を対象とするすべてのプログラミング言語で、これらすべての特性を利用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-129">However, individual programming languages that target .NET may not make all these characteristics available.</span></span>

<span data-ttu-id="bbda1-130">特徴</span><span class="sxs-lookup"><span data-stu-id="bbda1-130">Characteristic</span></span> | <span data-ttu-id="bbda1-131">説明</span><span class="sxs-lookup"><span data-stu-id="bbda1-131">Description</span></span>
-------------- | -----------
<span data-ttu-id="bbda1-132">sealed</span><span class="sxs-lookup"><span data-stu-id="bbda1-132">sealed</span></span> | <span data-ttu-id="bbda1-133">型から別のクラスを派生できないことを示します。</span><span class="sxs-lookup"><span data-stu-id="bbda1-133">Specifies that another class cannot be derived from this type.</span></span>
<span data-ttu-id="bbda1-134">実装</span><span class="sxs-lookup"><span data-stu-id="bbda1-134">implements</span></span> | <span data-ttu-id="bbda1-135">クラスが、インターフェイスのメンバーの実装を提供することによって、1 つ以上のインターフェイスを使用することを示します。</span><span class="sxs-lookup"><span data-stu-id="bbda1-135">Indicates that the class uses one or more interfaces by providing implementations of interface members.</span></span>
<span data-ttu-id="bbda1-136">abstract</span><span class="sxs-lookup"><span data-stu-id="bbda1-136">abstract</span></span> | <span data-ttu-id="bbda1-137">クラスをインスタンス化できないことを示します。</span><span class="sxs-lookup"><span data-stu-id="bbda1-137">Indicates that the class cannot be instantiated.</span></span> <span data-ttu-id="bbda1-138">クラスを使用するには、このクラスから別のクラスを派生させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-138">To use it, you must derive another class from it.</span></span>
<span data-ttu-id="bbda1-139">継承</span><span class="sxs-lookup"><span data-stu-id="bbda1-139">inherits</span></span> | <span data-ttu-id="bbda1-140">クラスのインスタンスを、基底クラスが指定されている任意の場所で使用できることを示します。</span><span class="sxs-lookup"><span data-stu-id="bbda1-140">Indicates that instances of the class can be used anywhere the base class is specified.</span></span> <span data-ttu-id="bbda1-141">基底クラスから継承する派生クラスは、基底クラスによって提供されるすべてのパブリック メンバーの実装を使用できます。または、派生クラスは、パブリック メンバーの実装をその独自の実装でオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-141">A derived class that inherits from a base class can use the implementation of any public members provided by the base class, or the derived class can override the implementation of the public members with its own implementation.</span></span>
<span data-ttu-id="bbda1-142">exported または not exported</span><span class="sxs-lookup"><span data-stu-id="bbda1-142">exported or not exported</span></span> | <span data-ttu-id="bbda1-143">クラスが定義されているアセンブリの外部から、そのクラスを参照できるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="bbda1-143">Indicates whether a class is visible outside the assembly in which it is defined.</span></span> <span data-ttu-id="bbda1-144">この特性は、最上位のクラスにのみ適用され、入れ子にされたクラスには適用されません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-144">This characteristic applies only to top-level classes and not to nested classes.</span></span>

> [!NOTE]
> <span data-ttu-id="bbda1-145">クラスは、親クラスまたは構造体で入れ子にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-145">A class can also be nested in a parent class or structure.</span></span> <span data-ttu-id="bbda1-146">入れ子にされたクラスにも、メンバー特性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-146">Nested classes also have member characteristics.</span></span> <span data-ttu-id="bbda1-147">詳細については、「[入れ子にされた型](#nested-types)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbda1-147">For more information, see [Nested types](#nested-types).</span></span>

<span data-ttu-id="bbda1-148">実装を持たないクラス メンバーは抽象メンバーです。</span><span class="sxs-lookup"><span data-stu-id="bbda1-148">Class members that have no implementation are abstract members.</span></span> <span data-ttu-id="bbda1-149">1 つ以上の抽象メンバーを持つクラスは、それ自体が抽象クラスとなり、新しいインスタンスを作成できません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-149">A class that has one or more abstract members is itself abstract; new instances of it cannot be created.</span></span> <span data-ttu-id="bbda1-150">ランタイムに対応する言語の中には、抽象メンバーを持たないクラスも抽象クラスとしてマークできるものがあります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-150">Some languages that target the runtime let you mark a class as abstract even if none of its members are abstract.</span></span> <span data-ttu-id="bbda1-151">抽象クラスは、派生クラスが必要に応じて継承したりオーバーライドしたりできる基本的な一連の機能をカプセル化する必要がある場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-151">You can use an abstract class when you want to encapsulate a basic set of functionality that derived classes can inherit or override when appropriate.</span></span> <span data-ttu-id="bbda1-152">抽象クラスでないクラスを具象クラスと呼びます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-152">Classes that are not abstract are referred to as concrete classes.</span></span>

<span data-ttu-id="bbda1-153">クラスで実装できるインターフェイスの数に制限はありませんが、すべてのクラスが暗黙的に継承する [System.Object](xref:System.Object) を除き、継承できる基底クラスは&1; つだけです。</span><span class="sxs-lookup"><span data-stu-id="bbda1-153">A class can implement any number of interfaces, but it can inherit from only one base class in addition to [System.Object](xref:System.Object), from which all classes inherit implicitly.</span></span> <span data-ttu-id="bbda1-154">すべてのクラスには少なくとも&1; つのコンストラクターが必要で、このコンストラクターにより、各クラスの新しいインスタンスが初期化されます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-154">All classes must have at least one constructor, which initializes new instances of the class.</span></span> <span data-ttu-id="bbda1-155">コンストラクターを明示的に定義しなかった場合、ほとんどのコンパイラでは、自動的に既定の (パラメーターなしの) コンストラクターが使用されます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-155">If you do not explicitly define a constructor, most compilers will automatically provide a default (parameterless) constructor.</span></span>

### <a name="structures"></a><span data-ttu-id="bbda1-156">構造体</span><span class="sxs-lookup"><span data-stu-id="bbda1-156">Structures</span></span>

<span data-ttu-id="bbda1-157">構造体は、[System.Object](xref:System.Object) から派生する [System.ValueType](xref:System.ValueType) から暗黙的に派生する値型です。</span><span class="sxs-lookup"><span data-stu-id="bbda1-157">A structure is a value type that derives implicitly from [System.ValueType](xref:System.ValueType), which in turn is derived from [System.Object](xref:System.Object).</span></span> <span data-ttu-id="bbda1-158">構造体は、メモリ要件が小さい値を表す場合や、厳密に型指定されたパラメーターを持つメソッドに対してパラメーターを値渡しする場合などに、非常に便利です。</span><span class="sxs-lookup"><span data-stu-id="bbda1-158">A structure is very useful for representing values whose memory requirements are small, and for passing values as by-value parameters to methods that have strongly typed parameters.</span></span> <span data-ttu-id="bbda1-159">.NET では、すべてのプリミティブ データ型 ([Boolean](xref:System.Boolean)、[Byte](xref:System.Byte)、[Char](xref:System.Char)、[DateTime](xref:System.DateTime)、[Decimal](xref:System.Decimal)、[Double](xref:System.Double)、[Int16](xref:System.Int16)、[Int32](xref:System.Int32)、[Int64](xref:System.Int64)、[SByte](xref:System.SByte)、[Single](xref:System.Single)、[UInt16](xref:System.UInt16)、[UInt32](xref:System.UInt32)、[UInt64](xref:System.UInt64)) が構造体として定義されています。</span><span class="sxs-lookup"><span data-stu-id="bbda1-159">In .NET, all primitive data types ([Boolean](xref:System.Boolean), [Byte](xref:System.Byte), [Char](xref:System.Char), [DateTime](xref:System.DateTime), [Decimal](xref:System.Decimal), [Double](xref:System.Double), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [Single](xref:System.Single), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), and [UInt64](xref:System.UInt64)) are defined as structures.</span></span>

<span data-ttu-id="bbda1-160">クラスと同様、構造体にもデータ (構造体のフィールド) と、そのデータに対して実行できる操作 (構造体のメソッド) が定義されます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-160">Like classes, structures define both data (the fields of the structure) and the operations that can be performed on that data (the methods of the structure).</span></span> <span data-ttu-id="bbda1-161">これは、[System.Object](xref:System.Object) クラスと [System.ValueType](xref:System.ValueType) クラスで定義されている仮想メソッドなどのメソッドと、値型そのものに定義されているすべてのメソッドを、構造体に対して呼び出すことができることを意味します。</span><span class="sxs-lookup"><span data-stu-id="bbda1-161">This means that you can call methods on structures, including the virtual methods defined on the [System.Object](xref:System.Object) and [System.ValueType](xref:System.ValueType) classes, and any methods defined on the value type itself.</span></span> <span data-ttu-id="bbda1-162">言い換えれば、構造体には、静的メソッドと非静的メソッドに加え、フィールド、プロパティ、およびイベントを持たせることができます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-162">In other words, structures can have fields, properties, and events, as well as static and nonstatic methods.</span></span> <span data-ttu-id="bbda1-163">構造体のインスタンスを作成したり、構造体をパラメーターとして渡したりできるほか、構造体をローカル変数として格納することも、別の値型または参照型のフィールドに格納することもできます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-163">You can create instances of structures, pass them as parameters, store them as local variables, or store them in a field of another value type or reference type.</span></span> <span data-ttu-id="bbda1-164">構造体でインターフェイスを実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-164">Structures can also implement interfaces.</span></span>

<span data-ttu-id="bbda1-165">ただし、値型は、いくつかの点でクラスとは異なります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-165">Value types also differ from classes in several respects.</span></span> <span data-ttu-id="bbda1-166">まず、値型は [System.ValueType](xref:System.ValueType) を暗黙的に継承しますが、他の型を直接継承することはできません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-166">First, although they implicitly inherit from [System.ValueType](xref:System.ValueType), they cannot directly inherit from any type.</span></span> <span data-ttu-id="bbda1-167">同様に、すべての値型には、値型から他の型が派生できないことを示す sealed 属性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-167">Similarly, all value types are sealed, which means that no other type can be derived from them.</span></span> <span data-ttu-id="bbda1-168">また、値型はコンストラクターを必要としません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-168">They also do not require constructors.</span></span>

<span data-ttu-id="bbda1-169">共通言語ランタイムは、それぞれの値型に対応するボックス化された型を提供します。ボックス化された型とは、値型と同じ状態および動作を備えたクラスのことです。</span><span class="sxs-lookup"><span data-stu-id="bbda1-169">For each value type, the common language runtime supplies a corresponding boxed type, which is a class that has the same state and behavior as the value type.</span></span> <span data-ttu-id="bbda1-170">値型のインスタンスは、[System.Object](xref:System.Object) 型のパラメーターを受け入れるメソッドに渡されると、ボックス化されます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-170">An instance of a value type is boxed when it is passed to a method that accepts a parameter of type [System.Object](xref:System.Object).</span></span> <span data-ttu-id="bbda1-171">参照渡しのパラメーターとして値型を受け入れるメソッドの呼び出しから制御が返されると、ボックス化が解除 (つまり、クラスのインスタンスから値型のインスタンスに変換) されます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-171">It is unboxed (that is, converted from an instance of a class back to an instance of a value type) when control returns from a method call that accepts a value type as a by-reference parameter.</span></span> <span data-ttu-id="bbda1-172">言語によっては、ボックス化された型が必要なときに特別な構文を使用する必要がありますが、ボックス化された型を必要に応じて自動的に使用する言語もあります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-172">Some languages require that you use special syntax when the boxed type is required; others automatically use the boxed type when it is needed.</span></span> <span data-ttu-id="bbda1-173">値型を定義するときには、ボックス化された型とボックス化解除された型の両方を定義します。</span><span class="sxs-lookup"><span data-stu-id="bbda1-173">When you define a value type, you are defining both the boxed and the unboxed type.</span></span>

### <a name="enumerations"></a><span data-ttu-id="bbda1-174">列挙体</span><span class="sxs-lookup"><span data-stu-id="bbda1-174">Enumerations</span></span>

<span data-ttu-id="bbda1-175">列挙型 (enum) は、[System.Enum](xref:System.Enum) から直接継承される値型で、基になるプリミティブ型の値に対して別名を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-175">An enumeration (enum) is a value type that inherits directly from [System.Enum](xref:System.Enum) and that supplies alternate names for the values of an underlying primitive type.</span></span> <span data-ttu-id="bbda1-176">列挙型には名前、基になる型、および一連のフィールドが存在します。基になる型は、組み込みの符号付きまたは符号なし整数型 ([Byte](xref:System.Byte)、[Int32](xref:System.Int32)、[UInt64](xref:System.UInt64) など) であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="bbda1-176">An enumeration type has a name, an underlying type that must be one of the built-in signed or unsigned integer types (such as [Byte](xref:System.Byte), [Int32](xref:System.Int32), or [UInt64](xref:System.UInt64)), and a set of fields.</span></span> <span data-ttu-id="bbda1-177">フィールドは静的リテラル フィールドで、各フィールドが&1; つの定数を表します。</span><span class="sxs-lookup"><span data-stu-id="bbda1-177">The fields are static literal fields, each of which represents a constant.</span></span> <span data-ttu-id="bbda1-178">複数のフィールドに同じ値を割り当てることもできます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-178">The same value can be assigned to multiple fields.</span></span> <span data-ttu-id="bbda1-179">その場合は、リフレクションや文字列変換を行うために、いずれかの値をプライマリ列挙値としてマークしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-179">When this occurs, you must mark one of the values as the primary enumeration value for reflection and string conversion.</span></span>

<span data-ttu-id="bbda1-180">基になる型の値を列挙型に割り当てることも、その逆も可能です (キャストは必要ありません)。</span><span class="sxs-lookup"><span data-stu-id="bbda1-180">You can assign a value of the underlying type to an enumeration and vice versa (no cast is required by the runtime).</span></span> <span data-ttu-id="bbda1-181">列挙型のインスタンスを作成し、[System.Enum](xref:System.Enum) のメソッドや、その列挙型の基となる型に定義されている任意のメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-181">You can create an instance of an enumeration and call the methods of [System.Enum](xref:System.Enum), as well as any methods defined on the enumeration's underlying type.</span></span> <span data-ttu-id="bbda1-182">しかし、言語によっては、基になる型のインスタンスが必要とされるときに、列挙型をパラメーターとして渡すことが許可されていない場合もあります (またはその逆)。</span><span class="sxs-lookup"><span data-stu-id="bbda1-182">However, some languages might not let you pass an enumeration as a parameter when an instance of the underlying type is required (or vice versa).</span></span>

<span data-ttu-id="bbda1-183">また、列挙型には次のような制限があります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-183">The following additional restrictions apply to enumerations:</span></span> 

* <span data-ttu-id="bbda1-184">独自のメソッドは定義できません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-184">They cannot define their own methods.</span></span>

* <span data-ttu-id="bbda1-185">インターフェイスを実装できません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-185">They cannot implement interfaces.</span></span>

* <span data-ttu-id="bbda1-186">プロパティまたはイベントを定義できません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-186">They cannot define properties or events.</span></span>

* <span data-ttu-id="bbda1-187">列挙型は、ジェネリック型に入れ子にされているという理由だけでジェネリックである場合を除き、ジェネリックにはなりません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-187">They cannot be generic, unless they are generic only because they are nested within a generic type.</span></span> <span data-ttu-id="bbda1-188">つまり、列挙型は、独自の型パラメーターを持つことができません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-188">That is, an enumeration cannot have type parameters of its own.</span></span> 

> [!NOTE]
> <span data-ttu-id="bbda1-189">C# で作成された入れ子にされた型 (列挙型を含む) は、それを囲むすべてのジェネリック型の型パラメーターを含むため、独自の型パラメーターは持ちませんが、ジェネリックです。</span><span class="sxs-lookup"><span data-stu-id="bbda1-189">Nested types (including enumerations) created with C# include the type parameters of all enclosing generic types, and are therefore generic even if they do not have type parameters of their own.</span></span> <span data-ttu-id="bbda1-190">詳細については、[Type.MakeGenericType](xref:System.Type.MakeGenericType(System.Type[])) のリファレンス トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbda1-190">For more information, see the [Type.MakeGenericType](xref:System.Type.MakeGenericType(System.Type[])) reference topic.</span></span> 

<span data-ttu-id="bbda1-191">[FlagsAttribute](xref:System.FlagsAttribute) 属性は、ビット フィールドと呼ばれる特別な種類の列挙型を表します。</span><span class="sxs-lookup"><span data-stu-id="bbda1-191">The [FlagsAttribute](xref:System.FlagsAttribute) attribute denotes a special kind of enumeration called a bit field.</span></span> <span data-ttu-id="bbda1-192">ランタイム自体は通常の列挙型とビット フィールドを区別しませんが、言語の中にはそれらを区別するものもあります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-192">The runtime itself does not distinguish between traditional enumerations and bit fields, but your language might do so.</span></span> <span data-ttu-id="bbda1-193">列挙型とビット フィールドが区別される場合、ビット フィールドではビットごとの演算子を使用して名前のない値を生成できますが、列挙型ではビットごとの演算子は使用できません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-193">When this distinction is made, bitwise operators can be used on bit fields, but not on enumerations, to generate unnamed values.</span></span> <span data-ttu-id="bbda1-194">通常、列挙型は、曜日、国名、地域名などの一意の要素のリストに使用されます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-194">Enumerations are generally used for lists of unique elements, such as days of the week, country or region names, and so on.</span></span> <span data-ttu-id="bbda1-195">通常、ビット フィールドは、`Red And Big And Fast` のような、特性や数量を組み合わせて示すリストに使用されます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-195">Bit fields are generally used for lists of qualities or quantities that might occur in combination, such as `Red And Big And Fast`.</span></span>

<span data-ttu-id="bbda1-196">ビット フィールドと通常の列挙型を両方とも使用する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="bbda1-196">The following example shows how to use both bit fields and traditional enumerations.</span></span>

```csharp
using System;
using System.Collections.Generic;

// A traditional enumeration of some root vegetables.
public enum SomeRootVegetables
{
    HorseRadish,
    Radish,
    Turnip
}

// A bit field or flag enumeration of harvesting seasons.
[Flags]
public enum Seasons
{
    None = 0,
    Summer = 1,
    Autumn = 2,
    Winter = 4,
    Spring = 8,
    All = Summer | Autumn | Winter | Spring
}

public class Example
{
   public static void Main()
   {
       // Hash table of when vegetables are available.
       Dictionary<SomeRootVegetables, Seasons> AvailableIn = new Dictionary<SomeRootVegetables, Seasons>();

       AvailableIn[SomeRootVegetables.HorseRadish] = Seasons.All;
       AvailableIn[SomeRootVegetables.Radish] = Seasons.Spring;
       AvailableIn[SomeRootVegetables.Turnip] = Seasons.Spring | 
            Seasons.Autumn;

       // Array of the seasons, using the enumeration.
       Seasons[] theSeasons = new Seasons[] { Seasons.Summer, Seasons.Autumn, 
            Seasons.Winter, Seasons.Spring };

       // Print information of what vegetables are available each season.
       foreach (Seasons season in theSeasons)
       {
          Console.Write(String.Format(
              "The following root vegetables are harvested in {0}:\n", 
              season.ToString("G")));
          foreach (KeyValuePair<SomeRootVegetables, Seasons> item in AvailableIn)
          {
             // A bitwise comparison.
             if (((Seasons)item.Value & season) > 0)
                 Console.Write(String.Format("  {0:G}\n", 
                      (SomeRootVegetables)item.Key));
          }
       }
   }
}
// The example displays the following output:
//    The following root vegetables are harvested in Summer:
//      HorseRadish
//    The following root vegetables are harvested in Autumn:
//      Turnip
//      HorseRadish
//    The following root vegetables are harvested in Winter:
//      HorseRadish
//    The following root vegetables are harvested in Spring:
//      Turnip
//      Radish
//      HorseRadish
```

```vb
Imports System.Collections.Generic

' A traditional enumeration of some root vegetables.
Public Enum SomeRootVegetables
   HorseRadish
   Radish
   Turnip
End Enum 

' A bit field or flag enumeration of harvesting seasons.
<Flags()> Public Enum Seasons
   None = 0
   Summer = 1
   Autumn = 2
   Winter = 4
   Spring = 8
   All = Summer Or Autumn Or Winter Or Spring
End Enum 

' Entry point.
Public Class Example
   Public Shared Sub Main()
      ' Hash table of when vegetables are available.
      Dim AvailableIn As New Dictionary(Of SomeRootVegetables, Seasons)()

      AvailableIn(SomeRootVegetables.HorseRadish) = Seasons.All
      AvailableIn(SomeRootVegetables.Radish) = Seasons.Spring
      AvailableIn(SomeRootVegetables.Turnip) = Seasons.Spring Or _
                                               Seasons.Autumn

      ' Array of the seasons, using the enumeration.
      Dim theSeasons() As Seasons = {Seasons.Summer, Seasons.Autumn, _
                                     Seasons.Winter, Seasons.Spring}

      ' Print information of what vegetables are available each season.
      For Each season As Seasons In theSeasons
         Console.WriteLine(String.Format( _
              "The following root vegetables are harvested in {0}:", _
              season.ToString("G")))
         For Each item As KeyValuePair(Of SomeRootVegetables, Seasons) In AvailableIn
            ' A bitwise comparison.
            If(CType(item.Value, Seasons) And season) > 0 Then
               Console.WriteLine("  " + _
                     CType(item.Key, SomeRootVegetables).ToString("G"))
            End If
         Next
      Next
   End Sub 
End Class 
' The example displays the following output:
'    The following root vegetables are harvested in Summer:
'      HorseRadish
'    The following root vegetables are harvested in Autumn:
'      Turnip
'      HorseRadish
'    The following root vegetables are harvested in Winter:
'      HorseRadish
'    The following root vegetables are harvested in Spring:
'      Turnip
'      Radish
'      HorseRadish
```

### <a name="interfaces"></a><span data-ttu-id="bbda1-197">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bbda1-197">Interfaces</span></span>

<span data-ttu-id="bbda1-198">インターフェイスは、"can do" 関係または "has a" 関係を指定するコントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="bbda1-198">An interface defines a contract that specifies a "can do" relationship or a "has a" relationship.</span></span> <span data-ttu-id="bbda1-199">インターフェイスは、多くの場合、比較と並べ替え ([IComparable](xref:System.IComparable) インターフェイスや [IComparable&lt;T&gt;](xref:System.IComparable%601) インターフェイス)、等価テスト ( [IEquatable&lt;T&gt;](xref:System.IEquatable%601) インターフェイス)、コレクション内の項目の列挙 ([IEnumerable](xref:System.Collections.IEnumerable) インターフェイスや [IEnumerable&lt;T&gt;](xref:System.Collections.Generic.IEnumerable%601) インターフェイス) などの機能を実装するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-199">Interfaces are often used to implement functionality, such as comparing and sorting (the [IComparable](xref:System.IComparable) and [IComparable&lt;T&gt;](xref:System.IComparable%601) interfaces), testing for equality (the [IEquatable&lt;T&gt;](xref:System.IEquatable%601) interface), or enumerating items in a collection (the [IEnumerable](xref:System.Collections.IEnumerable) and [IEnumerable&lt;T&gt;](xref:System.Collections.Generic.IEnumerable%601) interfaces).</span></span> <span data-ttu-id="bbda1-200">インターフェイスには、プロパティ、メソッド、およびイベント (すべて抽象メンバー) を設定できます。つまり、インターフェイスは、メンバーとメンバーの署名を定義しますが、インターフェイス メンバーの機能を定義するインターフェイスを実装する型に依存します。</span><span class="sxs-lookup"><span data-stu-id="bbda1-200">Interfaces can have properties, methods, and events, all of which are abstract members; that is, although the interface defines the members and their signatures, it leaves it to the type that implements the interface to define the functionality of each interface member.</span></span> <span data-ttu-id="bbda1-201">これは、インターフェイスを実装するクラスまたは構造体が、そのインターフェイスで宣言されている抽象メンバーの定義を提供する必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="bbda1-201">This means that any class or structure that implements an interface must supply definitions for the abstract members declared in the interface.</span></span> <span data-ttu-id="bbda1-202">インターフェイスは、そのインターフェイスを実装するクラスまたは構造体に対して、1 つ以上の他のインターフェイスも同時に実装するように要求できます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-202">An interface can require any implementing class or structure to also implement one or more other interfaces.</span></span>

<span data-ttu-id="bbda1-203">インターフェイスには、次のような制限があります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-203">The following restrictions apply to interfaces:</span></span> 

* <span data-ttu-id="bbda1-204">任意のアクセシビリティを指定してインターフェイスを宣言できますが、そのすべてのメンバーのアクセシビリティは public であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="bbda1-204">An interface can be declared with any accessibility, but interface members must all have public accessibility.</span></span>

* <span data-ttu-id="bbda1-205">インターフェイスでコンストラクターを定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-205">Interfaces cannot define constructors.</span></span>

* <span data-ttu-id="bbda1-206">インターフェイスでフィールドを定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-206">Interfaces cannot define fields.</span></span>

* <span data-ttu-id="bbda1-207">インターフェイスで定義できるのはインスタンスのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="bbda1-207">Interfaces can define only instance members.</span></span> <span data-ttu-id="bbda1-208">静的メンバーを定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-208">They cannot define static members.</span></span>

<span data-ttu-id="bbda1-209">各言語には、メンバーの実装をそのメンバーを要求するインターフェイスに割り当てるための規則があります。これは、複数のインターフェイスで同じシグネチャを持つメンバーを宣言でき、それらのメンバーが別個の実装を持つことができるためです。</span><span class="sxs-lookup"><span data-stu-id="bbda1-209">Each language must provide rules for mapping an implementation to the interface that requires the member, because more than one interface can declare a member with the same signature, and these members can have separate implementations.</span></span>

### <a name="delegates"></a><span data-ttu-id="bbda1-210">デリゲート</span><span class="sxs-lookup"><span data-stu-id="bbda1-210">Delegates</span></span>

<span data-ttu-id="bbda1-211">デリゲートは、C++ の関数ポインターと類似の目的で使用される参照型です。</span><span class="sxs-lookup"><span data-stu-id="bbda1-211">Delegates are reference types that serve a purpose similar to that of function pointers in C++.</span></span> <span data-ttu-id="bbda1-212">これらは、.NET のイベント ハンドラーとコールバック関数に使用されます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-212">They are used for event handlers and callback functions in .NET.</span></span> <span data-ttu-id="bbda1-213">関数ポインターとは異なり、デリゲートは安全で、検証可能で、タイプ セーフです。</span><span class="sxs-lookup"><span data-stu-id="bbda1-213">Unlike function pointers, delegates are secure, verifiable, and type safe.</span></span> <span data-ttu-id="bbda1-214">デリゲート型は、互換性のあるシグネチャを持つすべてのインスタンス メソッドまたは静的メソッドを表すことができます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-214">A delegate type can represent any instance method or static method that has a compatible signature.</span></span> 

<span data-ttu-id="bbda1-215">デリゲートのパラメーターにメソッドのパラメーターよりも限定的な型が指定された場合、両者のパラメーター間に型の互換性があると見なされます。これによって、デリゲートに渡された引数が、メソッドに対して安全に渡されることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-215">A parameter of a delegate is compatible with the corresponding parameter of a method if the type of the delegate parameter is more restrictive than the type of the method parameter, because this guarantees that an argument passed to the delegate can be passed safely to the method.</span></span>

<span data-ttu-id="bbda1-216">同様に、メソッドの戻り値の型の制限がデリゲートの戻り値の型より多いと、メソッドの戻り値がデリゲートの戻り値の型に安全にキャストされることが保証されるため、デリゲートの戻り値の型とメソッドの戻り値の型には互換性があります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-216">Similarly, the return type of a delegate is compatible with the return type of a method if the return type of the method is more restrictive than the return type of the delegate, because this guarantees that the return value of the method can be cast safely to the return type of the delegate.</span></span>

<span data-ttu-id="bbda1-217">たとえば、[IEnumerable](xref:System.Collections.IEnumerable) 型のパラメーターおよび [Object](xref:System.Object) 型の戻り値を持つデリゲートは、[Object](xref:System.Object) 型のパラメーターおよび [IEnumerable](xref:System.Collections.IEnumerable) 型の戻り値を持ったメソッドを表すことができます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-217">For example, a delegate that has a parameter of type [IEnumerable](xref:System.Collections.IEnumerable) and a return type of [Object](xref:System.Object) can represent a method that has a parameter of type [Object](xref:System.Object) and a return value of type [IEnumerable](xref:System.Collections.IEnumerable).</span></span> 

 <span data-ttu-id="bbda1-218">よく "デリゲートは、それが表すメソッドにバインドされる" と言われます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-218">A delegate is said to be bound to the method it represents.</span></span> <span data-ttu-id="bbda1-219">デリゲートは、メソッドにバインドされる以外にも、オブジェクトにバインドされる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-219">In addition to being bound to the method, a delegate can be bound to an object.</span></span> <span data-ttu-id="bbda1-220">オブジェクトはメソッドの第&1; パラメーターを表し、デリゲートが呼び出されるたびにメソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-220">The object represents the first parameter of the method, and is passed to the method every time the delegate is invoked.</span></span> <span data-ttu-id="bbda1-221">インスタンス メソッドの場合、バインドされたオブジェクトは、暗黙的な `this` パラメーター (Visual Basic では `Me`) として渡されます。静的メソッドの場合、オブジェクトは、メソッドの&1; つ目の仮パラメーターとして渡され、デリゲートのシグネチャは、その残りのパラメーターと完全に一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-221">If the method is an instance method, the bound object is passed as the implicit `this` parameter (`Me` in Visual Basic); if the method is static, the object is passed as the first formal parameter of the method, and the delegate signature must match the remaining parameters.</span></span> 
 
 <span data-ttu-id="bbda1-222">すべてのデリゲートが [System.MulticastDelegate](xref:System.MulticastDelegate) を継承し、System.MulticastDelegate は [System.Delegate](xref:System.Delegate) を継承します。</span><span class="sxs-lookup"><span data-stu-id="bbda1-222">All delegates inherit from [System.MulticastDelegate](xref:System.MulticastDelegate), which inherits from [System.Delegate](xref:System.Delegate).</span></span> <span data-ttu-id="bbda1-223">C# および Visual Basic 言語では、これらの型からの継承は許可されていません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-223">The C# and Visual Basic languages don't allow inheritance from these types.</span></span> <span data-ttu-id="bbda1-224">代わりに、デリゲートを宣言するためのキーワードが用意されています。</span><span class="sxs-lookup"><span data-stu-id="bbda1-224">Instead, they provide keywords for declaring delegates.</span></span>
 
 <span data-ttu-id="bbda1-225">デリゲートは [MulticastDelegate](xref:System.MulticastDelegate) を継承するため、デリゲートには呼び出しリストがあります。これは、デリゲートが表し、デリゲートが呼び出されたときに実行されるメソッドのリストです。</span><span class="sxs-lookup"><span data-stu-id="bbda1-225">Because delegates inherit from [MulticastDelegate](xref:System.MulticastDelegate), a delegate has an invocation list, which is a list of methods that the delegate represents and that are executed when the delegate is invoked.</span></span> <span data-ttu-id="bbda1-226">リストのすべてのメソッドは、デリゲートが呼び出されたときに指定される引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-226">All methods in the list receive the arguments supplied when the delegate is invoked.</span></span>

> [!NOTE]
> <span data-ttu-id="bbda1-227">デリゲートに戻り値が含まれていても、呼び出しリストに複数のメソッドが含まれているデリゲートに対しては、戻り値は定義されません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-227">The return value is not defined for a delegate that has more than one method in its invocation list, even if the delegate has a return type.</span></span>

<span data-ttu-id="bbda1-228">コールバック メソッドの場合のように、多くの場合、デリゲートは&1; つのメソッドのみを表すため、デリゲートを作成し、呼び出す以外の処理は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-228">In many cases, such as with callback methods, a delegate represents only one method, and the only actions you have to take are creating the delegate and invoking it.</span></span> 

<span data-ttu-id="bbda1-229">複数のメソッドを表すデリゲートの場合、.NET は [Delegate](xref:System.Delegate) と [MulticastDelegate](xref:System.MulticastDelegate) デリゲート クラスのメソッドを提供し、デリゲートの呼び出しリスト ([Delegate.Combine](xref:System.Delegate.Combine(System.Delegate,System.Delegate)) メソッド) にメソッドを追加したり、メソッド ([Delegate.Remove](xref:System.Delegate.Remove(System.Delegate,System.Delegate)) メソッド) を削除したり、呼び出しリスト ([Delegate.GetInvocationList](xref:System.Delegate.GetInvocationList) メソッド) を取得したりする操作をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="bbda1-229">For delegates that represent multiple methods, .NET provides methods of the [Delegate](xref:System.Delegate) and [MulticastDelegate](xref:System.MulticastDelegate) delegate classes to support operations such as adding a method to a delegate's invocation list (the [Delegate.Combine](xref:System.Delegate.Combine(System.Delegate,System.Delegate)) method), removing a method (the [Delegate.Remove](xref:System.Delegate.Remove(System.Delegate,System.Delegate)) method), and getting the invocation list (the [Delegate.GetInvocationList](xref:System.Delegate.GetInvocationList) method).</span></span>

> [!NOTE]
> <span data-ttu-id="bbda1-230">C# または Visual Basic では、イベント ハンドラー デリゲートに対して、これらのメソッドを使用する必要はありません。これらの言語には、イベント ハンドラーの追加および削除に使用する構文が用意されているためです。</span><span class="sxs-lookup"><span data-stu-id="bbda1-230">It is not necessary to use these methods for event-handler delegates in C# or Visual Basic, because these languages provide syntax for adding and removing event handlers.</span></span>

## <a name="type-definitions"></a><span data-ttu-id="bbda1-231">型定義</span><span class="sxs-lookup"><span data-stu-id="bbda1-231">Type definitions</span></span>

<span data-ttu-id="bbda1-232">型定義には、次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-232">A type definition includes the following:</span></span> 

* <span data-ttu-id="bbda1-233">型に対して定義される属性</span><span class="sxs-lookup"><span data-stu-id="bbda1-233">Any attributes defined on the type.</span></span>

* <span data-ttu-id="bbda1-234">型のアクセシビリティ (参照範囲)</span><span class="sxs-lookup"><span data-stu-id="bbda1-234">The type's accessibility (visibility).</span></span>

* <span data-ttu-id="bbda1-235">型の名前</span><span class="sxs-lookup"><span data-stu-id="bbda1-235">The type's name.</span></span>

* <span data-ttu-id="bbda1-236">型の基本型</span><span class="sxs-lookup"><span data-stu-id="bbda1-236">The type's base type.</span></span>

* <span data-ttu-id="bbda1-237">型が実装するインターフェイス</span><span class="sxs-lookup"><span data-stu-id="bbda1-237">Any interfaces implemented by the type.</span></span>

* <span data-ttu-id="bbda1-238">型の各メンバーの定義</span><span class="sxs-lookup"><span data-stu-id="bbda1-238">Definitions for each of the type's members.</span></span>

### <a name="attributes"></a><span data-ttu-id="bbda1-239">属性</span><span class="sxs-lookup"><span data-stu-id="bbda1-239">Attributes</span></span>

<span data-ttu-id="bbda1-240">属性を使用して、ユーザー定義のメタデータを追加できます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-240">Attributes provide additional user-defined metadata.</span></span> <span data-ttu-id="bbda1-241">属性の最も一般的な用途は、型についての補足的な情報をそのアセンブリに保存したり、型のメンバーの動作をデザイン時または実行時環境で変更したりすることです。</span><span class="sxs-lookup"><span data-stu-id="bbda1-241">Most commonly, they are used to store additional information about a type in its assembly, or to modify the behavior of a type member in either the design-time or run-time environment.</span></span> 

<span data-ttu-id="bbda1-242">属性は、それ自体が [System.Attribute](xref:System.Attribute) を継承するクラスです。</span><span class="sxs-lookup"><span data-stu-id="bbda1-242">Attributes are themselves classes that inherit from [System.Attribute](xref:System.Attribute).</span></span> <span data-ttu-id="bbda1-243">属性を使用できる言語にはそれぞれ、言語要素に属性を適用するための固有の構文があります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-243">Languages that support the use of attributes each have their own syntax for applying attributes to a language element.</span></span> <span data-ttu-id="bbda1-244">属性はほぼすべての言語要素に適用できます。具体的にどの要素に属性を適用できるかは、その属性クラスに適用されている [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-244">Attributes can be applied to almost any language element; the specific elements to which an attribute can be applied are defined by the [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) that is applied to that attribute class.</span></span>

### <a name="type-accessibility"></a><span data-ttu-id="bbda1-245">型のアクセシビリティ</span><span class="sxs-lookup"><span data-stu-id="bbda1-245">Type accessibility</span></span>

<span data-ttu-id="bbda1-246">すべての型には、他の型からのアクセシビリティを制御する修飾子があります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-246">All types have a modifier that governs their accessibility from other types.</span></span> <span data-ttu-id="bbda1-247">ランタイムによってサポートされる型のアクセシビリティについて次の表で説明します。</span><span class="sxs-lookup"><span data-stu-id="bbda1-247">The following table describes the type accessibilities supported by the runtime.</span></span>

<span data-ttu-id="bbda1-248">ユーザー補助</span><span class="sxs-lookup"><span data-stu-id="bbda1-248">Accessibility</span></span> | <span data-ttu-id="bbda1-249">説明</span><span class="sxs-lookup"><span data-stu-id="bbda1-249">Description</span></span>
------------- | -----------
<span data-ttu-id="bbda1-250">public</span><span class="sxs-lookup"><span data-stu-id="bbda1-250">public</span></span> | <span data-ttu-id="bbda1-251">すべてのアセンブリから型にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-251">The type is accessible by all assemblies.</span></span>
<span data-ttu-id="bbda1-252">アセンブリ</span><span class="sxs-lookup"><span data-stu-id="bbda1-252">assembly</span></span> | <span data-ttu-id="bbda1-253">同じアセンブリ内からだけ型にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-253">The type is accessible only from within its assembly.</span></span>

<span data-ttu-id="bbda1-254">入れ子にされた型のアクセシビリティは、その型のアクセシビリティ ドメインによって決まります。このアクセシビリティ ドメインは、そのメンバーに対して宣言されているアクセシビリティと、そのメンバーの直接のコンテナーである型のアクセシビリティ ドメインの両方によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-254">The accessibility of a nested type depends on its accessibility domain, which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="bbda1-255">ただし、入れ子にされた型のアクセシビリティ ドメインが、その型を含んでいる型のアクセシビリティ ドメインを上回ることはできません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-255">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>

<span data-ttu-id="bbda1-256">`P` というプログラム内の `T` という型で宣言された `M` という入れ子にされたメンバーのアクセシビリティ ドメインは、次のように定義されます (`M` 自体も型である可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="bbda1-256">The accessibility domain of a nested member `M` declared in a type `T`within a program `P` is defined as follows (noting that `M` might itself be a type):</span></span> 

* <span data-ttu-id="bbda1-257">`M` に対して宣言されたアクセシビリティが `public` の場合、`M` のアクセシビリティ ドメインは `T` のアクセシビリティ ドメインになります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-257">If the declared accessibility of `M` is `public`, the accessibility domain of `M` is the accessibility domain of `T`.</span></span>

* <span data-ttu-id="bbda1-258">`M` に対して宣言されているアクセシビリティが `protected internal` の場合、`M` のアクセシビリティ ドメインは、`T` のアクセシビリティ ドメインと、`P` のプログラム テキストおよび `T` の外側で宣言された `P` から派生した任意の型のプログラム テキストとの積集合になります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-258">If the declared accessibility of `M` is `protected internal`, the accessibility domain of `M` is the intersection of the accessibility domain of `T` with the program text of `P` and the program text of any type derived from `T` declared outside `P`.</span></span>

* <span data-ttu-id="bbda1-259">`M` に対して宣言されているアクセシビリティが `protected` の場合、`M` のアクセシビリティ ドメインは、`T` のアクセシビリティ ドメインと、`T` のプログラム テキストおよび `T` から派生した任意の型との積集合になります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-259">If the declared accessibility of `M` is `protected`, the accessibility domain of `M` is the intersection of the accessibility domain of `T` with the program text of `T` and any type derived from `T`.</span></span>

* <span data-ttu-id="bbda1-260">`M` に対して宣言されているアクセシビリティが `internal` の場合、`M` のアクセシビリティ ドメインは、`T` のアクセシビリティ ドメインと `P` のプログラム テキストとの積集合になります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-260">If the declared accessibility of `M` is `internal`, the accessibility domain of `M` is the intersection of the accessibility domain of `T` with the program text of`P`.</span></span>

* <span data-ttu-id="bbda1-261">`M` に対して宣言されているアクセシビリティが `private` の場合、`M` のアクセシビリティ ドメインは `T` のプログラム テキストになります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-261">If the declared accessibility of `M` is `private`, the accessibility domain of `M` is the program text of `T`.</span></span>

### <a name="type-names"></a><span data-ttu-id="bbda1-262">型名</span><span class="sxs-lookup"><span data-stu-id="bbda1-262">Type names</span></span>

<span data-ttu-id="bbda1-263">共通型システムでは、名前に関して適用される制限は次の&2; つだけです。</span><span class="sxs-lookup"><span data-stu-id="bbda1-263">The common type system imposes only two restrictions on names:</span></span> 

* <span data-ttu-id="bbda1-264">すべての名前は Unicode (16 ビット) 文字列としてエンコードされます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-264">All names are encoded as strings of Unicode (16-bit) characters.</span></span>

* <span data-ttu-id="bbda1-265">名前には、値 0x0000 (16 ビット) を埋め込むことはできません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-265">Names are not permitted to have an embedded (16-bit) value of 0x0000.</span></span>

<span data-ttu-id="bbda1-266">ただし、ほとんどの言語に型名に関する追加の制約が存在します。</span><span class="sxs-lookup"><span data-stu-id="bbda1-266">However, most languages impose additional restrictions on type names.</span></span> <span data-ttu-id="bbda1-267">すべての比較はバイト単位で行われるため、大文字と小文字を区別し、ロケールに依存しません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-267">All comparisons are done on a byte-by-byte basis, and are therefore case-sensitive and locale-independent.</span></span>

<span data-ttu-id="bbda1-268">型は、他のモジュールおよびアセンブリの型を参照する場合もありますが、1 つの .NET モジュール内で完全に定義されます </span><span class="sxs-lookup"><span data-stu-id="bbda1-268">Although a type might reference types from other modules and assemblies, a type must be fully defined within one .NET module.</span></span> <span data-ttu-id="bbda1-269">(ただし、コンパイラがサポートしていれば、複数のソース コード ファイルに分割できる場合もあります)。型名は&1; つの名前空間内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-269">(Depending on compiler support, however, it can be divided into multiple source code files.) Type names need be unique only within a namespace.</span></span> <span data-ttu-id="bbda1-270">型が完全に識別されるようにするため、その型名は、その型の実装を含んでいる名前空間によって修飾される必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-270">To fully identify a type, the type name must be qualified by the namespace that contains the implementation of the type.</span></span>

### <a name="base-types-and-interfaces"></a><span data-ttu-id="bbda1-271">基本型とインターフェイス</span><span class="sxs-lookup"><span data-stu-id="bbda1-271">Base types and interfaces</span></span>

<span data-ttu-id="bbda1-272">型は、別の型から値と動作を継承できます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-272">A type can inherit values and behaviors from another type.</span></span> <span data-ttu-id="bbda1-273">共通型システムでは、複数の基本型から継承する型を作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-273">The common type system does not allow types to inherit from more than one base type.</span></span>

<span data-ttu-id="bbda1-274">型は任意の数のインターフェイスを実装できます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-274">A type can implement any number of interfaces.</span></span> <span data-ttu-id="bbda1-275">型にインターフェイスを実装するには、そのインターフェイスのすべての仮想メンバーをその型に実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-275">To implement an interface, a type must implement all the virtual members of that interface.</span></span> <span data-ttu-id="bbda1-276">仮想メソッドは派生型によって実装でき、静的または動的に呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-276">A virtual method can be implemented by a derived type and can be invoked either statically or dynamically.</span></span>

## <a name="type-members"></a><span data-ttu-id="bbda1-277">型のメンバー</span><span class="sxs-lookup"><span data-stu-id="bbda1-277">Type members</span></span>

<span data-ttu-id="bbda1-278">ランタイムでは、型の動作と状態を指定する型のメンバーを定義できます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-278">The runtime enables you to define members of your type, which specifies the behavior and state of a type.</span></span> <span data-ttu-id="bbda1-279">型のメンバーには、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-279">Type members include the following:</span></span>

* [<span data-ttu-id="bbda1-280">フィールド</span><span class="sxs-lookup"><span data-stu-id="bbda1-280">Fields</span></span>](#fields)

* [<span data-ttu-id="bbda1-281">プロパティ</span><span class="sxs-lookup"><span data-stu-id="bbda1-281">Properties</span></span>](#properties)

* [<span data-ttu-id="bbda1-282">メソッド</span><span class="sxs-lookup"><span data-stu-id="bbda1-282">Methods</span></span>](#methods)

* [<span data-ttu-id="bbda1-283">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="bbda1-283">Constructors</span></span>](#constructors)

* [<span data-ttu-id="bbda1-284">イベント</span><span class="sxs-lookup"><span data-stu-id="bbda1-284">Events</span></span>](#events)

* [<span data-ttu-id="bbda1-285">入れ子にされた型</span><span class="sxs-lookup"><span data-stu-id="bbda1-285">Nested types</span></span>](#nested-types)

### <a name="fields"></a><span data-ttu-id="bbda1-286">フィールド</span><span class="sxs-lookup"><span data-stu-id="bbda1-286">Fields</span></span>

<span data-ttu-id="bbda1-287">フィールドは、型の状態の一部を表し、格納するものです。</span><span class="sxs-lookup"><span data-stu-id="bbda1-287">A field describes and contains part of the type's state.</span></span> <span data-ttu-id="bbda1-288">フィールドは、ランタイムがサポートする任意の型にすることができます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-288">Fields can be of any type supported by the runtime.</span></span> <span data-ttu-id="bbda1-289">通常、フィールドは、同じクラスまたはその派生クラスからしかアクセスできないように、`private` または `protected` のいずれかに設定されます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-289">Most commonly, fields are either `private` or `protected`, so that they are accessible only from within the class or from a derived class.</span></span> <span data-ttu-id="bbda1-290">フィールドの値を型の外部から変更できるようにする場合は、プロパティの set アクセサーを使用するのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="bbda1-290">If the value of a field can be modified from outside its type, a property set accessor is typically used.</span></span> <span data-ttu-id="bbda1-291">パブリックに公開されたフィールドは、通常、読み取り専用であり、次の&2; 種類に分けることができます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-291">Publicly exposed fields are usually read-only and can be of two types:</span></span> 

* <span data-ttu-id="bbda1-292">定数。その値は、デザイン時に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-292">Constants, whose value is assigned at design time.</span></span> <span data-ttu-id="bbda1-293">これらはクラスの静的メンバーですが、`static` (Visual Basic では `Shared`) キーワードを使用して定義されません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-293">These are static members of a class, although they are not defined using the `static` (`Shared` in Visual Basic) keyword.</span></span>

* <span data-ttu-id="bbda1-294">読み取り専用の変数。その値は、クラスのコンストラクターで割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-294">Read-only variables, whose values can be assigned in the class constructor.</span></span>

<span data-ttu-id="bbda1-295">次の例は、読み取り専用フィールドの&2; つの用法を示しています。</span><span class="sxs-lookup"><span data-stu-id="bbda1-295">The following example illustrates these two usages of read-only fields.</span></span>

```csharp
using System;

public class Constants
{
   public const double Pi = 3.1416;
   public readonly DateTime BirthDate;

   public Constants(DateTime birthDate)
   {
      this.BirthDate = birthDate;
   }
}

public class Example
{
   public static void Main()
   {
      Constants con = new Constants(new DateTime(1974, 8, 18));
      Console.Write(Constants.Pi + "\n");
      Console.Write(con.BirthDate.ToString("d") + "\n");
   }
}
// The example displays the following output if run on a system whose current
// culture is en-US:
//    3.1417
//    8/18/1974
```

```vb
Public Class Constants
   Public Const Pi As Double = 3.1416
   Public ReadOnly BirthDate As Date

   Public Sub New(birthDate As Date)
      Me.BirthDate = birthDate
   End Sub
End Class

Public Module Example
   Public Sub Main()
      Dim con As New Constants(#8/18/1974#)
      Console.WriteLine(Constants.Pi.ToString())
      Console.WriteLine(con.BirthDate.ToString("d"))
   End Sub
End Module
' The example displays the following output if run on a system whose current
' culture is en-US:
'    3.1417
'    8/18/1974
```

### <a name="properties"></a><span data-ttu-id="bbda1-296">プロパティ</span><span class="sxs-lookup"><span data-stu-id="bbda1-296">Properties</span></span>

<span data-ttu-id="bbda1-297">プロパティは、型の値または状態に名前を付け、そのプロパティの値を取得または設定するためのメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="bbda1-297">A property names a value or state of the type and defines methods for getting or setting the property's value.</span></span> <span data-ttu-id="bbda1-298">プロパティは、プリミティブ型、プリミティブ型のコレクション、ユーザー定義型、ユーザー定義型のコレクションにすることができます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-298">Properties can be primitive types, collections of primitive types, user-defined types, or collections of user-defined types.</span></span> <span data-ttu-id="bbda1-299">多くの場合、プロパティは、型のパブリックなインターフェイスを、その型の個々の実装とは切り離すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-299">Properties are often used to keep the public interface of a type independent from the type's actual representation.</span></span> <span data-ttu-id="bbda1-300">これにより、クラスに直接格納されていない値をプロパティに反映させたり (プロパティが計算後の値を返す場合など)、プライベート フィールドに割り当てる値を事前に検証したりすることが可能です。</span><span class="sxs-lookup"><span data-stu-id="bbda1-300">This enables properties to reflect values that are not directly stored in the class (for example, when a property returns a computed value) or to perform validation before values are assigned to private fields.</span></span> <span data-ttu-id="bbda1-301">後者のパターンを説明する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bbda1-301">The following example illustrates the latter pattern.</span></span>

```csharp
using System;

public class Person
{
   private int m_Age;

   public int Age
   { 
      get { return m_Age; }
      set {
         if (value < 0 || value > 125)
         {
            throw new ArgumentOutOfRangeException("The value of the Age property must be between 0 and 125.");
         }
         else
         {
            m_Age = value;
         }         
      }
   }
}
```

```vb
Public Class Person
   Private m_Age As Integer

   Public Property Age As Integer
      Get
         Return m_Age
      End Get
      Set
         If value < 0 Or value > 125 Then
            Throw New ArgumentOutOfRangeException("The value of the Age property must be between 0 and 125.")
         Else
            m_Age = value
         End If
      End Set
   End Property
End Class
```

<span data-ttu-id="bbda1-302">読み取り可能なプロパティを含んだ型の Microsoft Intermediate Language (MSIL) には、プロパティそのもののほかに、`get`*_propertyname* メソッドが含まれています。また、書き込み可能なプロパティを含んだ型の MSIL には、`set`*_propertyname* メソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="bbda1-302">In addition to including the property itself, the Microsoft intermediate language (MSIL) for a type that contains a readable property includes a `get`*_propertyname* method, and the MSIL for a type that contains a writable property includes a `set`*_propertyname* method.</span></span>

### <a name="methods"></a><span data-ttu-id="bbda1-303">メソッド</span><span class="sxs-lookup"><span data-stu-id="bbda1-303">Methods</span></span>

<span data-ttu-id="bbda1-304">メソッドは、その型で利用できる操作を表します。</span><span class="sxs-lookup"><span data-stu-id="bbda1-304">A method describes operations that are available on the type.</span></span> <span data-ttu-id="bbda1-305">メソッドのシグネチャは、そのメソッドのパラメーターの型および戻り値の型として許可される型を示します。</span><span class="sxs-lookup"><span data-stu-id="bbda1-305">A method's signature specifies the allowable types of all its parameters and of its return value.</span></span>

<span data-ttu-id="bbda1-306">ほとんどのメソッドでは、メソッド呼び出しに必要なパラメーターの厳密な個数が定義されていますが、いくつかのメソッドは可変個のパラメーターをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="bbda1-306">Although most methods define the precise number of parameters required for method calls, some methods support a variable number of parameters.</span></span> <span data-ttu-id="bbda1-307">このようなメソッドで最後に宣言されるパラメーターには、[ParamArrayAttribute](xref:System.ParamArrayAttribute) 属性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-307">The final declared parameter of these methods is marked with the [ParamArrayAttribute](xref:System.ParamArrayAttribute) attribute.</span></span> <span data-ttu-id="bbda1-308">通常、言語コンパイラには、C# の `params` や Visual Basic の `ParamArray` など、[ParamArrayAttribute](xref:System.ParamArrayAttribute) の明示的な使用を不要にするキーワードがあります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-308">Language compilers typically provide a keyword, such as `params` in C# and `ParamArray` in Visual Basic, that makes explicit use of [ParamArrayAttribute](xref:System.ParamArrayAttribute) unnecessary.</span></span>

### <a name="constructors"></a><span data-ttu-id="bbda1-309">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="bbda1-309">Constructors</span></span>

<span data-ttu-id="bbda1-310">コンストラクターは、クラスまたは構造体の新しいインスタンスを作成する特殊なメソッドです。</span><span class="sxs-lookup"><span data-stu-id="bbda1-310">A constructor is a special kind of method that creates new instances of a class or structure.</span></span> <span data-ttu-id="bbda1-311">他のメソッドと同様に、コンストラクターには、パラメーターを指定することができます。ただし、コンストラクターには戻り値はありません (つまり、`void` が返されます)。</span><span class="sxs-lookup"><span data-stu-id="bbda1-311">Like any other method, a constructor can include parameters; however, constructors have no return value (that is, they return `void`).</span></span> 

<span data-ttu-id="bbda1-312">クラスのソース コードに明示的にコンストラクターが定義されていない場合は、コンパイラによって既定の (パラメーターなしの) コンストラクターが追加されます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-312">If the source code for a class does not explicitly define a constructor, the compiler includes a default (parameterless) constructor.</span></span> <span data-ttu-id="bbda1-313">ただし、パラメーター化されたコンストラクターのみがクラスのソース コードで定義されている場合は、C# のコンパイラが、パラメーターなしのコンストラクターを生成しません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-313">However, if the source code for a class defines only parameterized constructors, the C# compiler doesn't generate a parameterless constructor.</span></span>

<span data-ttu-id="bbda1-314">構造体のソース コードでコンストラクターが定義される場合は、それらのコンストラクターがパラメーター化されている必要があります。構造体では既定の (パラメーターなしの) コンストラクターを定義できず、コンパイラは、構造体および他の値型のいずれに対しても、パラメーターなしのコンストラクターを生成しません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-314">If the source code for a structure defines constructors, they must be parameterized; a structure cannot define a default (parameterless) constructor, and compilers do not generate parameterless constructors for structures or other value types.</span></span> <span data-ttu-id="bbda1-315">すべての値型には、暗黙の既定コンストラクターがあります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-315">All value types do have an implicit default constructor.</span></span> <span data-ttu-id="bbda1-316">このコンストラクターは、共通言語ランタイムによって実装され、構造体のすべてのフィールドを既定の値に初期化します。</span><span class="sxs-lookup"><span data-stu-id="bbda1-316">This constructor is implemented by the common language runtime and initializes all fields of the structure to their default values.</span></span> 

### <a name="events"></a><span data-ttu-id="bbda1-317">イベント</span><span class="sxs-lookup"><span data-stu-id="bbda1-317">Events</span></span>

<span data-ttu-id="bbda1-318">イベントは、応答可能な事象 (イベント) を定義し、イベントへのサブスクライブ、イベントからのサブスクライブ解除、およびイベントの発生用のメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="bbda1-318">An event defines an incident that can be responded to, and defines methods for subscribing to, unsubscribing from, and raising the event.</span></span> <span data-ttu-id="bbda1-319">多くの場合、イベントは、他の型に対して状態の変更を通知するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-319">Events are often used to inform other types of state changes.</span></span>

### <a name="nested-types"></a><span data-ttu-id="bbda1-320">入れ子にされた型</span><span class="sxs-lookup"><span data-stu-id="bbda1-320">Nested types</span></span>

<span data-ttu-id="bbda1-321">入れ子にされた型とは、他の型のメンバーである型です。</span><span class="sxs-lookup"><span data-stu-id="bbda1-321">A nested type is a type that is a member of some other type.</span></span> <span data-ttu-id="bbda1-322">入れ子にされた型はその親の型と密に結合されているため、汎用型としては使用できません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-322">Nested types should be tightly coupled to their containing type and must not be useful as a general-purpose type.</span></span> <span data-ttu-id="bbda1-323">入れ子にされた型は、宣言型で、入れ子にされた型のインスタンスを使用したり作成したりする場合に便利で、入れ子にされた型の使用はパブリック メンバーに公開されません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-323">Nested types are useful when the declaring type uses and creates instances of the nested type, and use of the nested type is not exposed in public members.</span></span>

<span data-ttu-id="bbda1-324">入れ子にされた型は、混乱を招くおそれがあるため、特別な理由がない限り、パブリックに参照可能にすることはお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-324">Nested types are confusing to some developers and should not be publicly visible unless there is a compelling reason for visibility.</span></span> <span data-ttu-id="bbda1-325">適切にデザインされたライブラリでは、入れ子にされた型を使ってオブジェクトをインスタンス化したり、変数を宣言したりすることが必要になることはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-325">In a well-designed library, developers should rarely have to use nested types to instantiate objects or declare variables.</span></span>

## <a name="characteristics-of-type-members"></a><span data-ttu-id="bbda1-326">型のメンバーの特性</span><span class="sxs-lookup"><span data-stu-id="bbda1-326">Characteristics of type members</span></span>

<span data-ttu-id="bbda1-327">共通型システムでは、型のメンバーにさまざまな特性を適用できますが、各言語で、これらの特性がすべてサポートされている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-327">The common type system allows type members to have a variety of characteristics; however, languages are not required to support all these characteristics.</span></span> <span data-ttu-id="bbda1-328">メンバーの特性について次の表で説明します。</span><span class="sxs-lookup"><span data-stu-id="bbda1-328">The following table describes member characteristics.</span></span>

<span data-ttu-id="bbda1-329">特徴</span><span class="sxs-lookup"><span data-stu-id="bbda1-329">Characteristic</span></span> | <span data-ttu-id="bbda1-330">適用対象</span><span class="sxs-lookup"><span data-stu-id="bbda1-330">Can apply to</span></span> | <span data-ttu-id="bbda1-331">説明</span><span class="sxs-lookup"><span data-stu-id="bbda1-331">Description</span></span>
-------------- | ------------ | -----------
<span data-ttu-id="bbda1-332">abstract</span><span class="sxs-lookup"><span data-stu-id="bbda1-332">abstract</span></span> | <span data-ttu-id="bbda1-333">メソッド、プロパティ、およびイベント</span><span class="sxs-lookup"><span data-stu-id="bbda1-333">Methods, properties, and events</span></span> | <span data-ttu-id="bbda1-334">型はメソッドの実装を提供しません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-334">The type does not supply the method's implementation.</span></span> <span data-ttu-id="bbda1-335">抽象メソッドを継承または実装する型は、そのメソッドの実装を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-335">Types that inherit or implement abstract methods must supply an implementation for the method.</span></span> <span data-ttu-id="bbda1-336">唯一の例外は、派生型自体が抽象型である場合です。</span><span class="sxs-lookup"><span data-stu-id="bbda1-336">The only exception is when the derived type is itself an abstract type.</span></span> <span data-ttu-id="bbda1-337">すべての抽象メソッドは仮想メソッドです。</span><span class="sxs-lookup"><span data-stu-id="bbda1-337">All abstract methods are virtual.</span></span>
<span data-ttu-id="bbda1-338">private</span><span class="sxs-lookup"><span data-stu-id="bbda1-338">private</span></span> | <span data-ttu-id="bbda1-339">すべて</span><span class="sxs-lookup"><span data-stu-id="bbda1-339">All</span></span> | <span data-ttu-id="bbda1-340">メンバーが含まれているのと同じ型の内部、またはその型に入れ子にされた型の内部からだけアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-340">Accessible only from within the same type as the member, or within a nested type.</span></span>
<span data-ttu-id="bbda1-341">family</span><span class="sxs-lookup"><span data-stu-id="bbda1-341">family</span></span> | <span data-ttu-id="bbda1-342">すべて</span><span class="sxs-lookup"><span data-stu-id="bbda1-342">All</span></span> | <span data-ttu-id="bbda1-343">メンバーが含まれているのと同じ型の内部、およびその型を継承した派生型からアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-343">Accessible from within the same type as the member, and from derived types that inherit from it.</span></span>
<span data-ttu-id="bbda1-344">assemby</span><span class="sxs-lookup"><span data-stu-id="bbda1-344">assemby</span></span> | <span data-ttu-id="bbda1-345">すべて</span><span class="sxs-lookup"><span data-stu-id="bbda1-345">All</span></span> | <span data-ttu-id="bbda1-346">型が定義されているアセンブリ内でだけアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-346">Accessible only in the assembly in which the type is defined.</span></span>
<span data-ttu-id="bbda1-347">family and assembly</span><span class="sxs-lookup"><span data-stu-id="bbda1-347">family and assembly</span></span> | <span data-ttu-id="bbda1-348">すべて</span><span class="sxs-lookup"><span data-stu-id="bbda1-348">All</span></span> | <span data-ttu-id="bbda1-349">family アクセスと assembly アクセスの両特性を満たす型からだけアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-349">Accessible only from types that qualify for both family and assembly access.</span></span>
<span data-ttu-id="bbda1-350">family または assemby</span><span class="sxs-lookup"><span data-stu-id="bbda1-350">family or assemby</span></span> | <span data-ttu-id="bbda1-351">すべて</span><span class="sxs-lookup"><span data-stu-id="bbda1-351">All</span></span> | <span data-ttu-id="bbda1-352">family アクセスまたは assembly アクセスのいずれかの特性を満たす型からだけアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-352">Accessible only from types that qualify for either family or assembly access.</span></span>
<span data-ttu-id="bbda1-353">public</span><span class="sxs-lookup"><span data-stu-id="bbda1-353">public</span></span> | <span data-ttu-id="bbda1-354">すべて</span><span class="sxs-lookup"><span data-stu-id="bbda1-354">All</span></span> | <span data-ttu-id="bbda1-355">すべての型からアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-355">Accessible from any type.</span></span>
<span data-ttu-id="bbda1-356">final</span><span class="sxs-lookup"><span data-stu-id="bbda1-356">final</span></span> | <span data-ttu-id="bbda1-357">メソッド、プロパティ、およびイベント</span><span class="sxs-lookup"><span data-stu-id="bbda1-357">Methods, properties, and events</span></span> | <span data-ttu-id="bbda1-358">その仮想メソッドを派生型ではオーバーライドできません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-358">The virtual method cannot be overridden in a derived type.</span></span>
<span data-ttu-id="bbda1-359">initialize-only</span><span class="sxs-lookup"><span data-stu-id="bbda1-359">initialize-only</span></span> | <span data-ttu-id="bbda1-360">フィールド</span><span class="sxs-lookup"><span data-stu-id="bbda1-360">Fields</span></span> | <span data-ttu-id="bbda1-361">値を初期化することだけでき、初期化後の書き込みは実行できません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-361">The value can only be initialized, and cannot be written after initialization.</span></span>
<span data-ttu-id="bbda1-362">インスタンス</span><span class="sxs-lookup"><span data-stu-id="bbda1-362">instance</span></span> | <span data-ttu-id="bbda1-363">フィールド、メソッド、プロパティ、およびイベント</span><span class="sxs-lookup"><span data-stu-id="bbda1-363">Fields, methods, properties, and events</span></span> | <span data-ttu-id="bbda1-364">メンバーが `static` (C# )、`Shared` (Visual Basic)、`virtual` (C# )、または `Overridable` (Visual Basic) でマークされていない場合、それはインスタンス メンバーです (instance キーワードはありません)。</span><span class="sxs-lookup"><span data-stu-id="bbda1-364">If a member is not marked as `static` (C#), `Shared` (Visual Basic), `virtual` (C#), or `Overridable` (Visual Basic),  it is an instance member (there is no instance keyword).</span></span> <span data-ttu-id="bbda1-365">このようなメンバーについては、型を使用するオブジェクトと同数のコピーがメモリ内に格納されます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-365">There will be as many copies of such members in memory as there are objects that use it.</span></span>
<span data-ttu-id="bbda1-366">リテラル</span><span class="sxs-lookup"><span data-stu-id="bbda1-366">literal</span></span> | <span data-ttu-id="bbda1-367">フィールド</span><span class="sxs-lookup"><span data-stu-id="bbda1-367">Fields</span></span> | <span data-ttu-id="bbda1-368">このフィールドには、組み込みの値型の、コンパイル時点の固定値が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-368">The value assigned to the field is a fixed value, known at compile time, of a built-in value type.</span></span> <span data-ttu-id="bbda1-369">リテラル フィールドを定数と呼ぶこともあります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-369">Literal fields are sometimes referred to as constants.</span></span>
<span data-ttu-id="bbda1-370">newslot または override</span><span class="sxs-lookup"><span data-stu-id="bbda1-370">newslot or override</span></span> | <span data-ttu-id="bbda1-371">すべて</span><span class="sxs-lookup"><span data-stu-id="bbda1-371">All</span></span> | <span data-ttu-id="bbda1-372">メンバーが、同じシグネチャを持つ継承メンバーとどのようにやり取りするかを定義します。`newslot` は、同じシグネチャを持つ継承されたメンバーを隠します。`override` は、継承された仮想メソッドの定義を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-372">Defines how the member interacts with inherited members that have the same signature: `newslot` hides inherited members that have the same signature; `override` replaces the definition of an inherited virtual method.</span></span> <span data-ttu-id="bbda1-373">既定値は newslot です。</span><span class="sxs-lookup"><span data-stu-id="bbda1-373">The default is newslot.</span></span>
<span data-ttu-id="bbda1-374">静的</span><span class="sxs-lookup"><span data-stu-id="bbda1-374">static</span></span> | <span data-ttu-id="bbda1-375">フィールド、メソッド、プロパティ、およびイベント</span><span class="sxs-lookup"><span data-stu-id="bbda1-375">Fields, methods, properties, and events</span></span> | <span data-ttu-id="bbda1-376">メンバーは、型の特定のインスタンスではなく、そのメンバーが定義されている型に属します。つまり、メンバーは型がインスタンス化されていなくても存在し、その型のすべてのインスタンスによって共有されます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-376">The member belongs to the type it is defined on, not to a particular instance of the type; the member exists even if an instance of the type is not created, and it is shared among all instances of the type.</span></span>
<span data-ttu-id="bbda1-377">virtual</span><span class="sxs-lookup"><span data-stu-id="bbda1-377">virtual</span></span> | <span data-ttu-id="bbda1-378">メソッド、プロパティ、およびイベント</span><span class="sxs-lookup"><span data-stu-id="bbda1-378">Methods, properties, and events</span></span> | <span data-ttu-id="bbda1-379">メソッドは、派生型で実装でき、静的または動的に呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-379">The method can be implemented by a derived type and can be invoked either statically or dynamically.</span></span> <span data-ttu-id="bbda1-380">動的呼び出しが使用される場合は、実行時に呼び出しを行うインスタンスの型によって (コンパイル時に判明する型ではなく)、メソッドのどの実装が呼び出されるかが決定されます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-380">If dynamic invocation is used, the type of the instance that makes the call at run time (rather than the type known at compile time) determines which implementation of the method is called.</span></span> <span data-ttu-id="bbda1-381">仮想メソッドを静的に呼び出すには、目的のバージョンのメソッドを使用する型に、変数をキャストする必要が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-381">To invoke a virtual method statically, the variable might have to be cast to a type that uses the desired version of the method.</span></span>

### <a name="overloading"></a><span data-ttu-id="bbda1-382">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="bbda1-382">Overloading</span></span>

<span data-ttu-id="bbda1-383">型のメンバーには、それぞれ固有のシグネチャがあります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-383">Each type member has a unique signature.</span></span> <span data-ttu-id="bbda1-384">メソッドのシグネチャは、メソッドの名前とパラメーター リスト (メソッドの引数の順序と型) で構成されます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-384">Method signatures consist of the method name and a parameter list (the order and types of the method's arguments).</span></span> <span data-ttu-id="bbda1-385">シグネチャが同じでなければ、同じ名前を持つ複数のメソッドを&1; つの型の中で定義できます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-385">Multiple methods with the same name can be defined within a type as long as their signatures differ.</span></span> <span data-ttu-id="bbda1-386">同じ名前を持つ&2; つ以上のメソッドが定義されている場合、そのメソッドはオーバーロードされている、と言います。</span><span class="sxs-lookup"><span data-stu-id="bbda1-386">When two or more methods with the same name are defined, the method is said to be overloaded.</span></span> <span data-ttu-id="bbda1-387">たとえば、[System.Char](xref:System.Char) では、`IsDigit` メソッドがオーバーロードされています。</span><span class="sxs-lookup"><span data-stu-id="bbda1-387">For example, in [System.Char](xref:System.Char), the `IsDigit` method is overloaded.</span></span> <span data-ttu-id="bbda1-388">一方のメソッドは [Char](xref:System.Char) を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-388">One method takes a [Char](xref:System.Char).</span></span> <span data-ttu-id="bbda1-389">もう一方のメソッドは、[String](xref:System.String) および [Int32](xref:System.Int32) を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="bbda1-389">The other method takes a [String](xref:System.String) and an [Int32](xref:System.Int32).</span></span> 

> [!NOTE]
> <span data-ttu-id="bbda1-390">戻り値の型は、メソッドのシグネチャの一部として見なされません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-390">The return type is not considered part of a method's signature.</span></span> <span data-ttu-id="bbda1-391">つまり、戻り値の型が異なっているだけでは、メソッドをオーバーロードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="bbda1-391">That is, methods cannot be overloaded if they differ only by return type.</span></span>

### <a name="inheriting-overriding-and-hiding-members"></a><span data-ttu-id="bbda1-392">メンバーの継承、オーバーライド、および隠ぺい</span><span class="sxs-lookup"><span data-stu-id="bbda1-392">Inheriting, overriding, and hiding members</span></span>

<span data-ttu-id="bbda1-393">派生型は、その基本型のすべてのメンバーを継承します。つまり、基本型のすべてのメンバーは、派生型に対しても定義されており、使用可能です。</span><span class="sxs-lookup"><span data-stu-id="bbda1-393">A derived type inherits all members of its base type; that is, these members are defined on, and available to, the derived type.</span></span> <span data-ttu-id="bbda1-394">継承されたメンバーの動作または特性は、次の&2; つの方法で変更できます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-394">The behavior or qualities of inherited members can be modified in two ways:</span></span> 

* <span data-ttu-id="bbda1-395">派生型で、同じシグネチャを持つ新しいメンバーを定義することによって、継承されたメンバーを隠ぺいできます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-395">A derived type can hide an inherited member by defining a new member with the same signature.</span></span> <span data-ttu-id="bbda1-396">この方法は、public のメンバーを private に変更したり、`final` としてマークされている継承メソッドに新しい動作を定義したりするために使用します。</span><span class="sxs-lookup"><span data-stu-id="bbda1-396">This might be done to make a previously public member private or to define new behavior for an inherited method that is marked as `final`.</span></span>

* <span data-ttu-id="bbda1-397">派生型で、継承された仮想メソッドをオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-397">A derived type can override an inherited virtual method.</span></span> <span data-ttu-id="bbda1-398">オーバーライドするメソッドでは、コンパイル時点の変数の型ではなく、実行時の値の型に基づいて呼び出される、メソッドの新しい定義を提供します。</span><span class="sxs-lookup"><span data-stu-id="bbda1-398">The overriding method provides a new definition of the method that will be invoked based on the type of the value at run time rather than the type of the variable known at compile time.</span></span> <span data-ttu-id="bbda1-399">メソッドが仮想メソッドをオーバーライドできるのは、その仮想メソッドが `final` としてマークされておらず、新しいメソッドのアクセシビリティがその仮想メソッドと少なくとも同じ場合に限られます。</span><span class="sxs-lookup"><span data-stu-id="bbda1-399">A method can override a virtual method only if the virtual method is not marked as `final` and the new method is at least as accessible as the virtual method.</span></span>

## <a name="see-also"></a><span data-ttu-id="bbda1-400">関連項目</span><span class="sxs-lookup"><span data-stu-id="bbda1-400">See also</span></span>

[<span data-ttu-id="bbda1-401">.NET Framework における型変換</span><span class="sxs-lookup"><span data-stu-id="bbda1-401">Type conversion in the .NET Framework</span></span>](type-conversion.md)
