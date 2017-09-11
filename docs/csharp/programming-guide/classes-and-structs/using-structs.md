---
title: "構造体の使用 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
caps.latest.revision: 28
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
ms.openlocfilehash: 67fa4f764e6e40041e4b8e37eccbd1adb2b509d3
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="using-structs-c-programming-guide"></a><span data-ttu-id="22cd7-102">構造体の使用 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="22cd7-102">Using Structs (C# Programming Guide)</span></span>
<span data-ttu-id="22cd7-103">`struct` 型は、 `Point`、 `Rectangle`、 `Color`などの軽量のオブジェクトを表すのに適しています。</span><span class="sxs-lookup"><span data-stu-id="22cd7-103">The `struct` type is suitable for representing lightweight objects such as `Point`, `Rectangle`, and `Color`.</span></span> <span data-ttu-id="22cd7-104">点を表すには [自動実装プロパティ](../../../csharp/language-reference/keywords/class.md) がある [クラス](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)を使用するのと同じくらい便利ですが、シナリオによっては [構造体](../../../csharp/language-reference/keywords/struct.md) を使用する方がより効率的です。</span><span class="sxs-lookup"><span data-stu-id="22cd7-104">Although it is just as convenient to represent a point as a [class](../../../csharp/language-reference/keywords/class.md) with [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), a [struct](../../../csharp/language-reference/keywords/struct.md) might be more efficient in some scenarios.</span></span> <span data-ttu-id="22cd7-105">たとえば、1,000 個の `Point` オブジェクトから成る配列を宣言する場合は、各オブジェクトの参照用に追加のメモリを割り当てます。この場合、構造体であれば処理上の負荷を抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="22cd7-105">For example, if you declare an array of 1000 `Point` objects, you will allocate additional memory for referencing each object; in this case, a struct would be less expensive.</span></span> <span data-ttu-id="22cd7-106">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] には <xref:System.Drawing.Point>という名前のオブジェクトが含まれているため、この例の構造体には代わりに "CoOrds" という名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="22cd7-106">Because the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] contains an object called <xref:System.Drawing.Point>, the struct in this example is named "CoOrds" instead.</span></span>  
  
 <span data-ttu-id="22cd7-107">[!code-cs[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="22cd7-107">[!code-cs[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]</span></span>  
  
 <span data-ttu-id="22cd7-108">構造体に既定の (パラメーターなしの) コンストラクターを定義するとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="22cd7-108">It is an error to define a default (parameterless) constructor for a struct.</span></span> <span data-ttu-id="22cd7-109">また、構造体の本体のインスタンス フィールドを初期化した場合もエラーになります。</span><span class="sxs-lookup"><span data-stu-id="22cd7-109">It is also an error to initialize an instance field in a struct body.</span></span> <span data-ttu-id="22cd7-110">構造体メンバーを初期化するには、パラメーター化されたコンストラクターを使用するか、構造体を宣言した後で個別にメンバーにアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="22cd7-110">You can initialize struct members only by using a parameterized constructor or by accessing the members individually after the struct is declared.</span></span> <span data-ttu-id="22cd7-111">プライベート メンバーや、その他のアクセスできないメンバーは、コンストラクター内でのみ初期化できます。</span><span class="sxs-lookup"><span data-stu-id="22cd7-111">Any private or otherwise inaccessible members can be initialized only in a constructor.</span></span>  
  
 <span data-ttu-id="22cd7-112">[new](../../../csharp/language-reference/keywords/new.md) 演算子を使用して struct オブジェクトを作成すると、オブジェクトが作成されて適切なコンストラクターが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="22cd7-112">When you create a struct object using the [new](../../../csharp/language-reference/keywords/new.md) operator, it gets created and the appropriate constructor is called.</span></span> <span data-ttu-id="22cd7-113">クラスとは異なり、構造体は `new` 演算子を使用せずにインスタンス化できます。</span><span class="sxs-lookup"><span data-stu-id="22cd7-113">Unlike classes, structs can be instantiated without using the `new` operator.</span></span> <span data-ttu-id="22cd7-114">このような場合、コンストラクターの呼び出しが行われないため、割り当てがより効率的になります。</span><span class="sxs-lookup"><span data-stu-id="22cd7-114">In such a case, there is no constructor call, which makes the allocation more efficient.</span></span> <span data-ttu-id="22cd7-115">ただし、各フィールドは未割り当てのままになり、すべてのフィールドが初期化されるまではオブジェクトを使用できません。</span><span class="sxs-lookup"><span data-stu-id="22cd7-115">However, the fields will remain unassigned and the object cannot be used until all of the fields are initialized.</span></span>  
  
 <span data-ttu-id="22cd7-116">構造体に参照型がメンバーとして含まれている場合は、メンバーの既定のコンストラクターを明示的に呼び出す必要があります。そうしないと、メンバーは未割り当てのままになり、構造体は使用できません</span><span class="sxs-lookup"><span data-stu-id="22cd7-116">When a struct contains a reference type as a member, the default constructor of the member must be invoked explicitly, otherwise the member remains unassigned and the struct cannot be used.</span></span> <span data-ttu-id="22cd7-117">(結果として、コンパイル エラー CS0171 が発生します)。</span><span class="sxs-lookup"><span data-stu-id="22cd7-117">(This results in compiler error CS0171.)</span></span>  
  
 <span data-ttu-id="22cd7-118">クラスには継承がありますが、構造体には継承がありません。</span><span class="sxs-lookup"><span data-stu-id="22cd7-118">There is no inheritance for structs as there is for classes.</span></span> <span data-ttu-id="22cd7-119">構造体は、他の構造体やクラスから継承できず、基本クラスになることはできません。</span><span class="sxs-lookup"><span data-stu-id="22cd7-119">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="22cd7-120">ただし、構造体は、基本クラス <xref:System.Object>から継承します。</span><span class="sxs-lookup"><span data-stu-id="22cd7-120">Structs, however, inherit from the base class <xref:System.Object>.</span></span> <span data-ttu-id="22cd7-121">構造体は、クラスの場合とまったく同じ方法でインターフェイスを実装できます。</span><span class="sxs-lookup"><span data-stu-id="22cd7-121">A struct can implement interfaces, and it does that exactly as classes do.</span></span>  
  
 <span data-ttu-id="22cd7-122">`struct`キーワードを使用してクラスを宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="22cd7-122">You cannot declare a class using the keyword `struct`.</span></span> <span data-ttu-id="22cd7-123">C# では、クラスと構造体は、意味が異なります。</span><span class="sxs-lookup"><span data-stu-id="22cd7-123">In C#, classes and structs are semantically different.</span></span> <span data-ttu-id="22cd7-124">構造体は値型ですが、クラスは参照型です。</span><span class="sxs-lookup"><span data-stu-id="22cd7-124">A struct is a value type, while a class is a reference type.</span></span> <span data-ttu-id="22cd7-125">詳細については、「 [Value Types (値型)](../../../csharp/language-reference/keywords/value-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22cd7-125">For more information, see [Value Types](../../../csharp/language-reference/keywords/value-types.md).</span></span>  
  
 <span data-ttu-id="22cd7-126">参照型の機能が必要な場合以外は、小さいクラスを構造体として宣言した方が、システムによってより効率的に処理される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="22cd7-126">Unless you need reference-type semantics, a small class may be more efficiently handled by the system if you declare it as a struct instead.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="22cd7-127">例 1</span><span class="sxs-lookup"><span data-stu-id="22cd7-127">Example 1</span></span>  
  
### <a name="description"></a><span data-ttu-id="22cd7-128">説明</span><span class="sxs-lookup"><span data-stu-id="22cd7-128">Description</span></span>  
 <span data-ttu-id="22cd7-129">既定のコンストラクターとパラメーター化されたコンストラクターの両方を使用した `struct` の初期化の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="22cd7-129">This example demonstrates `struct` initialization using both default and parameterized constructors.</span></span>  
  
### <a name="code"></a><span data-ttu-id="22cd7-130">コード</span><span class="sxs-lookup"><span data-stu-id="22cd7-130">Code</span></span>  
 <span data-ttu-id="22cd7-131">[!code-cs[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="22cd7-131">[!code-cs[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]</span></span>  
  
 <span data-ttu-id="22cd7-132">[!code-cs[csProgGuideObjects#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="22cd7-132">[!code-cs[csProgGuideObjects#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_2.cs)]</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="22cd7-133">例 2</span><span class="sxs-lookup"><span data-stu-id="22cd7-133">Example 2</span></span>  
  
### <a name="description"></a><span data-ttu-id="22cd7-134">説明</span><span class="sxs-lookup"><span data-stu-id="22cd7-134">Description</span></span>  
 <span data-ttu-id="22cd7-135">構造体に固有の機能を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="22cd7-135">This example demonstrates a feature that is unique to structs.</span></span> <span data-ttu-id="22cd7-136">この例では、 `new` 演算子を使用せずに CoOrds オブジェクトを作成しています。</span><span class="sxs-lookup"><span data-stu-id="22cd7-136">It creates a CoOrds object without using the `new` operator.</span></span> <span data-ttu-id="22cd7-137">`struct` を `class`という単語に置き換えた場合、プログラムはコンパイルされません。</span><span class="sxs-lookup"><span data-stu-id="22cd7-137">If you replace the word `struct` with the word `class`, the program will not compile.</span></span>  
  
### <a name="code"></a><span data-ttu-id="22cd7-138">コード</span><span class="sxs-lookup"><span data-stu-id="22cd7-138">Code</span></span>  
 <span data-ttu-id="22cd7-139">[!code-cs[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="22cd7-139">[!code-cs[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]</span></span>  
  
 <span data-ttu-id="22cd7-140">[!code-cs[csProgGuideObjects#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="22cd7-140">[!code-cs[csProgGuideObjects#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_3.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22cd7-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="22cd7-141">See Also</span></span>  
 <span data-ttu-id="22cd7-142">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="22cd7-142">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="22cd7-143">[クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="22cd7-143">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 [<span data-ttu-id="22cd7-144">構造体</span><span class="sxs-lookup"><span data-stu-id="22cd7-144">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)

