---
title: "コンストラクター (C# プログラミング ガイド)"
ms.date: 2017-05-05
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
caps.latest.revision: 23
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 400afcda2fe30bf0e3621ee4c4247486e01d3ee4
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="constructors-c-programming-guide"></a><span data-ttu-id="3f9fb-102">コンストラクター (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="3f9fb-102">Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="3f9fb-103">[クラス](../../../csharp/language-reference/keywords/class.md)または[構造体](../../../csharp/language-reference/keywords/struct.md)を作成するたびに、コンストラクターが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3f9fb-103">Whenever a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="3f9fb-104">クラスまたは構造体には、異なる引数を取るコンストラクターが複数含まれていることがあります。</span><span class="sxs-lookup"><span data-stu-id="3f9fb-104">A class or struct may have multiple constructors that take different arguments.</span></span> <span data-ttu-id="3f9fb-105">プログラマーはコンストラクターを利用することで、既定値を設定したり、インスタンス化を制限したり、柔軟で読みやすいコードを記述したりできます。</span><span class="sxs-lookup"><span data-stu-id="3f9fb-105">Constructors enable the programmer to set default values, limit instantiation, and write code that is flexible and easy to read.</span></span> <span data-ttu-id="3f9fb-106">詳細と例については、「[コンストラクターの使用](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)」と「[インスタンス コンストラクター](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f9fb-106">For more information and examples, see [Using Constructors](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) and [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  

## <a name="default-constructors"></a><span data-ttu-id="3f9fb-107">既定のコンストラクター</span><span class="sxs-lookup"><span data-stu-id="3f9fb-107">Default constructors</span></span>
  
<span data-ttu-id="3f9fb-108">クラスにコンストラクターを指定しない場合、C# では既定でコンストラクターが 1 つ作成されます。そのコンストラクターによりオブジェクトがインスタンス化され、「[既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md)」の一覧にある既定値にメンバー変数が設定されます。</span><span class="sxs-lookup"><span data-stu-id="3f9fb-108">If you don't provide a constructor for your class, C# creates one by default that instantiates the object and sets member variables to the default values as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="3f9fb-109">構造体にコンストラクターを指定しない場合、C# では、*暗黙的既定コンストラクター*を利用し、「[既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md)」の一覧にある既定値に値の型の各フィールドが自動的に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="3f9fb-109">If you don't provide a constructor for your struct, C# relies on an *implicit default constructor* to automatically initialize each field of a value type to its default value as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="3f9fb-110">詳細と例については、「[インスタンス コンストラクター](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f9fb-110">For more information and examples, see [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  

## <a name="constructor-syntax"></a><span data-ttu-id="3f9fb-111">コンストラクターの構文</span><span class="sxs-lookup"><span data-stu-id="3f9fb-111">Constructor syntax</span></span>

<span data-ttu-id="3f9fb-112">コンストラクターは、名前がその型の名前と同じメソッドです。</span><span class="sxs-lookup"><span data-stu-id="3f9fb-112">A constructor is a method whose name is the same as the name of its type.</span></span> <span data-ttu-id="3f9fb-113">メソッド シグネチャには、メソッド名とそのパラメーター リストだけが含まれます。戻り値の型は含まれません。</span><span class="sxs-lookup"><span data-stu-id="3f9fb-113">Its method signature includes only the method name and its parameter list; it does not include a return type.</span></span> <span data-ttu-id="3f9fb-114">次の例は、`Person` という名前のクラスのコンストラクターを示しています。</span><span class="sxs-lookup"><span data-stu-id="3f9fb-114">The following example shows the constructor for a class named `Person`.</span></span>

<span data-ttu-id="3f9fb-115">[!code-cs[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="3f9fb-115">[!code-cs[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]</span></span>  

<span data-ttu-id="3f9fb-116">コンストラクターを 1 つのステートメントとして実装できる場合、[式の本体の定義](../statements-expressions-operators/expression-bodied-members.md)を利用できます。</span><span class="sxs-lookup"><span data-stu-id="3f9fb-116">If a constructor can be implemented as a single statement, you can use an [expression body definition](../statements-expressions-operators/expression-bodied-members.md).</span></span> <span data-ttu-id="3f9fb-117">次の例では、コンストラクターに *name* という名前の文字列パラメーターが 1 つある `Location` クラスが定義されています。</span><span class="sxs-lookup"><span data-stu-id="3f9fb-117">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="3f9fb-118">式の本体の定義により `locationName` フィールドに引数が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="3f9fb-118">The expression body definition assigns the argument to the `locationName` field.</span></span>

<span data-ttu-id="3f9fb-119">[!code-cs[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="3f9fb-119">[!code-cs[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]</span></span>  

## <a name="static-constructors"></a><span data-ttu-id="3f9fb-120">静的コンストラクター</span><span class="sxs-lookup"><span data-stu-id="3f9fb-120">Static constructors</span></span>

<span data-ttu-id="3f9fb-121">前の例には、表示されるすべてのインスタンス コンストラクターがあり、それが新しいオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="3f9fb-121">The previous examples have all shown instance constructors, which create a new object.</span></span> <span data-ttu-id="3f9fb-122">クラスまたは構造体には静的コンストラクターを与えることもできます。静的コンストラクターは型の静的メンバーを初期化します。</span><span class="sxs-lookup"><span data-stu-id="3f9fb-122">A class or struct can also have a static constructor, which initializes static members of the type.</span></span>  <span data-ttu-id="3f9fb-123">静的コンストラクターにはパラメーターがありません。</span><span class="sxs-lookup"><span data-stu-id="3f9fb-123">Static constructors are parameterless.</span></span> <span data-ttu-id="3f9fb-124">静的コンストラクターを指定して静的フィールドを初期化しない場合、C# コンパイラは、「[既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md)」の一覧にある既定値に静的フィールドを初期化する既定の静的コンストラクターを与えます。</span><span class="sxs-lookup"><span data-stu-id="3f9fb-124">If you don't provide a static constructor to initialize static fields, the C# compiler will supply a default static constructor that initializes static fields to their default value as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> 

<span data-ttu-id="3f9fb-125">次の例では、静的コンストラクターを使用して静的フィールドを初期化しています。</span><span class="sxs-lookup"><span data-stu-id="3f9fb-125">The following example uses a static constructor to initialize a static field.</span></span>

<span data-ttu-id="3f9fb-126">[!code-cs[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]</span><span class="sxs-lookup"><span data-stu-id="3f9fb-126">[!code-cs[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]</span></span>  

<span data-ttu-id="3f9fb-127">式の本体の定義で静的コンストラクターを定義することもできます。次の例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3f9fb-127">You can also define a static constructor with an expression body definition, as the following example shows.</span></span> 

<span data-ttu-id="3f9fb-128">[!code-cs[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]</span><span class="sxs-lookup"><span data-stu-id="3f9fb-128">[!code-cs[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]</span></span>  

<span data-ttu-id="3f9fb-129">詳細と例については、「[静的コンストラクター](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f9fb-129">For more information and examples, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3f9fb-130">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="3f9fb-130">In This Section</span></span>  
 [<span data-ttu-id="3f9fb-131">コンストラクターの使用</span><span class="sxs-lookup"><span data-stu-id="3f9fb-131">Using Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
  
 [<span data-ttu-id="3f9fb-132">インスタンス コンストラクター</span><span class="sxs-lookup"><span data-stu-id="3f9fb-132">Instance Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)  
  
 [<span data-ttu-id="3f9fb-133">プライベート コンストラクター</span><span class="sxs-lookup"><span data-stu-id="3f9fb-133">Private Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/private-constructors.md)  
  
 [<span data-ttu-id="3f9fb-134">静的コンストラクター</span><span class="sxs-lookup"><span data-stu-id="3f9fb-134">Static Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)  
  
 [<span data-ttu-id="3f9fb-135">方法: コピー コンストラクターを記述する</span><span class="sxs-lookup"><span data-stu-id="3f9fb-135">How to: Write a Copy Constructor</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a><span data-ttu-id="3f9fb-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f9fb-136">See Also</span></span>  
 <span data-ttu-id="3f9fb-137">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="3f9fb-137">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="3f9fb-138">[クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="3f9fb-138">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="3f9fb-139">[ファイナライザー](../../../csharp/programming-guide/classes-and-structs/destructors.md) </span><span class="sxs-lookup"><span data-stu-id="3f9fb-139">[Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md) </span></span>  
 <span data-ttu-id="3f9fb-140">[static](../../../csharp/language-reference/keywords/static.md) </span><span class="sxs-lookup"><span data-stu-id="3f9fb-140">[static](../../../csharp/language-reference/keywords/static.md) </span></span>  
 [<span data-ttu-id="3f9fb-141">初期化子がコンストラクターとは反対の順序で実行される理由その 1</span><span class="sxs-lookup"><span data-stu-id="3f9fb-141">Why Do Initializers Run In The Opposite Order As Constructors? Part One</span></span>](http://go.microsoft.com/fwlink/?LinkId=112374)

