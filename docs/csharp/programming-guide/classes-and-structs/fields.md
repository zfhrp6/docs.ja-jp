---
title: "フィールド (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- fields [C#]
ms.assetid: 3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7
caps.latest.revision: 29
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8eef9bb644a28c69a1db59dcba3c12c9e3fa86b0
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="fields-c-programming-guide"></a><span data-ttu-id="379d1-102">フィールド (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="379d1-102">Fields (C# Programming Guide)</span></span>
<span data-ttu-id="379d1-103">*フィールド*とは、[クラス](../../../csharp/language-reference/keywords/class.md)または[構造体](../../../csharp/language-reference/keywords/struct.md)で直接宣言される任意の型の変数です。</span><span class="sxs-lookup"><span data-stu-id="379d1-103">A *field* is a variable of any type that is declared directly in a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md).</span></span> <span data-ttu-id="379d1-104">フィールドは、それを含んでいる型の*メンバー*です。</span><span class="sxs-lookup"><span data-stu-id="379d1-104">Fields are *members* of their containing type.</span></span>  
  
 <span data-ttu-id="379d1-105">クラスまたは構造体には、インスタンス フィールドと静的フィールドのいずれか、またはその両方が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="379d1-105">A class or struct may have instance fields or static fields or both.</span></span> <span data-ttu-id="379d1-106">インスタンス フィールドは、型のインスタンスに固有です。</span><span class="sxs-lookup"><span data-stu-id="379d1-106">Instance fields are specific to an instance of a type.</span></span> <span data-ttu-id="379d1-107">たとえば、クラス T と、そのクラスのインスタンス フィールド F があるとします。型 T のオブジェクトを 2 つ作成した場合、他方のオブジェクトの値に影響を与えることなく、各オブジェクトの F の値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="379d1-107">If you have a class T, with an instance field F, you can create two objects of type T, and modify the value of F in each object without affecting the value in the other object.</span></span> <span data-ttu-id="379d1-108">これとは対照的に、クラス自体に属する静的フィールドは、そのクラスのすべてのインスタンスで共有されます。</span><span class="sxs-lookup"><span data-stu-id="379d1-108">By contrast, a static field belongs to the class itself, and is shared among all instances of that class.</span></span> <span data-ttu-id="379d1-109">インスタンス A に加えられた変更は、インスタンス B と C がフィールドにアクセスした場合、これらのインスタンスでただちに確認されます。</span><span class="sxs-lookup"><span data-stu-id="379d1-109">Changes made from instance A will be visibly immediately to instances B and C if they access the field.</span></span>  
  
 <span data-ttu-id="379d1-110">通常、フィールドは、プライベートまたは保護されたアクセシビリティを持つ変数に対してのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="379d1-110">Generally, you should use fields only for variables that have private or protected accessibility.</span></span> <span data-ttu-id="379d1-111">クラスからクライアント コードに公開するデータは、[メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)、[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)、[インデクサー](../../../csharp/programming-guide/indexers/index.md)を使用して提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="379d1-111">Data that your class exposes to client code should be provided through [methods](../../../csharp/programming-guide/classes-and-structs/methods.md), [properties](../../../csharp/programming-guide/classes-and-structs/properties.md) and [indexers](../../../csharp/programming-guide/indexers/index.md).</span></span> <span data-ttu-id="379d1-112">これらの構成要素を使用して、内部フィールドに間接的にアクセスすることで、無効な値が入力されることを防止できます。</span><span class="sxs-lookup"><span data-stu-id="379d1-112">By using these constructs for indirect access to internal fields, you can guard against invalid input values.</span></span> <span data-ttu-id="379d1-113">パブリック プロパティによって公開されるデータを格納するプライベート フィールドは、*バッキング ストア*または*バッキング フィールド*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="379d1-113">A private field that stores the data exposed by a public property is called a *backing store* or *backing field*.</span></span>  
  
 <span data-ttu-id="379d1-114">一般に、フィールドは、複数のクラス メソッドからアクセスできるようにする必要があり、かつ 1 つのメソッドの有効期間より長く保持する必要があるデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="379d1-114">Fields typically store the data that must be accessible to more than one class method and must be stored for longer than the lifetime of any single method.</span></span> <span data-ttu-id="379d1-115">たとえば、暦の日付を表すクラスには、月、日、年を表す 3 つの整数フィールドが存在します。</span><span class="sxs-lookup"><span data-stu-id="379d1-115">For example, a class that represents a calendar date might have three integer fields: one for the month, one for the day, and one for the year.</span></span> <span data-ttu-id="379d1-116">1 つのメソッドのスコープ外で使用されることのない変数は、メソッド本体内で*ローカル変数*として宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="379d1-116">Variables that are not used outside the scope of a single method should be declared as *local variables* within the method body itself.</span></span>  
  
 <span data-ttu-id="379d1-117">フィールドは、フィールドのアクセス レベル、フィールドの型、フィールドの名前の順に指定して、クラス ブロック内で宣言します。</span><span class="sxs-lookup"><span data-stu-id="379d1-117">Fields are declared in the class block by specifying the access level of the field, followed by the type of the field, followed by the name of the field.</span></span> <span data-ttu-id="379d1-118">例:</span><span class="sxs-lookup"><span data-stu-id="379d1-118">For example:</span></span>  
  
 <span data-ttu-id="379d1-119">[!code-cs[csProgGuideObjects#61](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="379d1-119">[!code-cs[csProgGuideObjects#61](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_1.cs)]</span></span>  
  
 <span data-ttu-id="379d1-120">オブジェクト内のフィールドにアクセスするには、`objectname.fieldname` のように、オブジェクト名の後にピリオドを追加し、その後にフィールド名を続けます。</span><span class="sxs-lookup"><span data-stu-id="379d1-120">To access a field in an object, add a period after the object name, followed by the name of the field, as in `objectname.fieldname`.</span></span> <span data-ttu-id="379d1-121">例:</span><span class="sxs-lookup"><span data-stu-id="379d1-121">For example:</span></span>  
  
 <span data-ttu-id="379d1-122">[!code-cs[csProgGuideObjects#62](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="379d1-122">[!code-cs[csProgGuideObjects#62](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_2.cs)]</span></span>  
  
 <span data-ttu-id="379d1-123">フィールドには、フィールドの宣言時に代入演算子を使用して初期値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="379d1-123">A field can be given an initial value by using the assignment operator when the field is declared.</span></span> <span data-ttu-id="379d1-124">たとえば、`day` フィールドに `"Monday"` を自動的に代入するには、次の例のように `day` を宣言します。</span><span class="sxs-lookup"><span data-stu-id="379d1-124">To automatically assign the `day` field to `"Monday"`, for example, you would declare `day` as in the following example:</span></span>  
  
 <span data-ttu-id="379d1-125">[!code-cs[csProgGuideObjects#63](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="379d1-125">[!code-cs[csProgGuideObjects#63](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_3.cs)]</span></span>  
  
 <span data-ttu-id="379d1-126">フィールドは、オブジェクト インスタンスのコンストラクターが呼び出される直前に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="379d1-126">Fields are initialized immediately before the constructor for the object instance is called.</span></span> <span data-ttu-id="379d1-127">コンストラクターがフィールドの値を代入すると、フィールドの宣言時に指定された値はすべて上書きされます。</span><span class="sxs-lookup"><span data-stu-id="379d1-127">If the constructor assigns the value of a field, it will overwrite any value given during field declaration.</span></span> <span data-ttu-id="379d1-128">詳細については、「[コンストラクターの使用](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="379d1-128">For more information, see [Using Constructors](../../../csharp/programming-guide/classes-and-structs/using-constructors.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="379d1-129">フィールドの初期化子は、他のインスタンス フィールドを参照できません。</span><span class="sxs-lookup"><span data-stu-id="379d1-129">A field initializer cannot refer to other instance fields.</span></span>  
  
 <span data-ttu-id="379d1-130">フィールドは、[public](../../../csharp/language-reference/keywords/public.md)、[private](../../../csharp/language-reference/keywords/private.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、または `protected internal` とマークできます。</span><span class="sxs-lookup"><span data-stu-id="379d1-130">Fields can be marked as [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), or `protected internal`.</span></span> <span data-ttu-id="379d1-131">これらのアクセス修飾子により、クラスのユーザーがフィールドにアクセスする方法が定義されます。</span><span class="sxs-lookup"><span data-stu-id="379d1-131">These access modifiers define how users of the class can access the fields.</span></span> <span data-ttu-id="379d1-132">詳細については、「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="379d1-132">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="379d1-133">必要に応じて、フィールドを[静的](../../../csharp/language-reference/keywords/static.md)に宣言することもできます。</span><span class="sxs-lookup"><span data-stu-id="379d1-133">A field can optionally be declared [static](../../../csharp/language-reference/keywords/static.md).</span></span> <span data-ttu-id="379d1-134">その場合、クラスのインスタンスが存在しなくても、呼び出し元がいつでもフィールドを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="379d1-134">This makes the field available to callers at any time, even if no instance of the class exists.</span></span> <span data-ttu-id="379d1-135">詳細については、「[静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="379d1-135">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="379d1-136">フィールドを [readonly](../../../csharp/language-reference/keywords/readonly.md) として宣言することもできます。</span><span class="sxs-lookup"><span data-stu-id="379d1-136">A field can be declared [readonly](../../../csharp/language-reference/keywords/readonly.md).</span></span> <span data-ttu-id="379d1-137">読み取り専用フィールドには、初期化時またはコンストラクターによる以外は、値を代入できません。</span><span class="sxs-lookup"><span data-stu-id="379d1-137">A read-only field can only be assigned a value during initialization or in a constructor.</span></span> <span data-ttu-id="379d1-138">`static``readonly` フィールドは基本的に定数と同じですが、C# コンパイラが静的な読み取り専用フィールドの値にアクセスできるのは実行時のみで、コンパイル時はアクセスできない点が異なります。</span><span class="sxs-lookup"><span data-stu-id="379d1-138">A `static``readonly` field is very similar to a constant, except that the C# compiler does not have access to the value of a static read-only field at compile time, only at run time.</span></span> <span data-ttu-id="379d1-139">詳細については、「[定数](../../../csharp/programming-guide/classes-and-structs/constants.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="379d1-139">For more information, see [Constants](../../../csharp/programming-guide/classes-and-structs/constants.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="379d1-140">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="379d1-140">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="379d1-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="379d1-141">See Also</span></span>  
 <span data-ttu-id="379d1-142">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="379d1-142">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="379d1-143">[クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="379d1-143">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="379d1-144">[コンストラクターの使用](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) </span><span class="sxs-lookup"><span data-stu-id="379d1-144">[Using Constructors](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) </span></span>  
 <span data-ttu-id="379d1-145">[継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md) </span><span class="sxs-lookup"><span data-stu-id="379d1-145">[Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md) </span></span>  
 <span data-ttu-id="379d1-146">[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="379d1-146">[Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span></span>  
 [<span data-ttu-id="379d1-147">抽象クラスとシール クラス、およびクラス メンバー</span><span class="sxs-lookup"><span data-stu-id="379d1-147">Abstract and Sealed Classes and Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)

