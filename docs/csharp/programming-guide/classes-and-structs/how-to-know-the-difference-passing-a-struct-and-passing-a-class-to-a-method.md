---
title: "方法 : メソッドに構造体を渡すこととクラス参照を渡すことの違いを理解する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- structs [C#], passing as method parameter
- passing parameters [C#], structs vs. classes
- methods [C#], passing classes vs. structs
ms.assetid: 9c1313a6-32a8-4ea7-a59f-450f66af628b
caps.latest.revision: 25
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
ms.openlocfilehash: 1a4508c8765ac678fd371180cb0c3ece3e1d9a44
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-know-the-difference-between-passing-a-struct-and-passing-a-class-reference-to-a-method-c-programming-guide"></a><span data-ttu-id="92067-102">方法 : メソッドに構造体を渡すこととクラス参照を渡すことの違いを理解する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="92067-102">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method (C# Programming Guide)</span></span>
<span data-ttu-id="92067-103">次の例では、メソッドに[構造体](../../../csharp/language-reference/keywords/struct.md)を渡すことと[クラス](../../../csharp/language-reference/keywords/class.md) インスタンスを渡すことの違いを示します。</span><span class="sxs-lookup"><span data-stu-id="92067-103">The following example demonstrates how passing a [struct](../../../csharp/language-reference/keywords/struct.md) to a method differs from passing a [class](../../../csharp/language-reference/keywords/class.md) instance to a method.</span></span> <span data-ttu-id="92067-104">この例では、両方の引数 (構造体とクラス インスタンス) が値によって渡され、両方のメソッドが引数の 1 つのフィールドの値を変更します。</span><span class="sxs-lookup"><span data-stu-id="92067-104">In the example, both of the arguments (struct and class instance) are passed by value, and both methods change the value of one field of the argument.</span></span> <span data-ttu-id="92067-105">ただし、2 つのメソッドの結果は同じではありません。構造体を渡した場合に渡される内容と、クラスのインスタンスを渡した場合に渡される内容が異なるためです。</span><span class="sxs-lookup"><span data-stu-id="92067-105">However, the results of the two methods are not the same because what is passed when you pass a struct differs from what is passed when you pass an instance of a class.</span></span>  
  
 <span data-ttu-id="92067-106">構造体は[値型](../../../csharp/language-reference/keywords/value-types.md)であるため、メソッドに[構造体が値によって渡される](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)と、メソッドは構造体引数のコピーを受け取って操作します。</span><span class="sxs-lookup"><span data-stu-id="92067-106">Because a struct is a [value type](../../../csharp/language-reference/keywords/value-types.md), when you [pass a struct by value](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md) to a method, the method receives and operates on a copy of the struct argument.</span></span> <span data-ttu-id="92067-107">メソッドは、呼び出し側メソッドの元の構造体にはアクセスできないため、どのような場合でもこの構造体を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="92067-107">The method has no access to the original struct in the calling method and therefore can't change it in any way.</span></span> <span data-ttu-id="92067-108">メソッドで変更できるのはコピーのみです。</span><span class="sxs-lookup"><span data-stu-id="92067-108">The method can change only the copy.</span></span>  
  
 <span data-ttu-id="92067-109">クラス インスタンスは、値型ではなく、[参照型](../../../csharp/language-reference/keywords/reference-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="92067-109">A class instance is a [reference type](../../../csharp/language-reference/keywords/reference-types.md), not a value type.</span></span> <span data-ttu-id="92067-110">メソッドに[参照型が値によって渡される](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)と、メソッドはクラス インスタンスへの参照のコピーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="92067-110">When [a reference type is passed by value](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md) to a method, the method receives a copy of the reference to the class instance.</span></span> <span data-ttu-id="92067-111">つまり、メソッドは、インスタンス自体のコピーではなく、インスタンスのアドレスのコピーを受け取ることになります。</span><span class="sxs-lookup"><span data-stu-id="92067-111">That is, the method receives a copy of the address of the instance, not a copy of the instance itself.</span></span> <span data-ttu-id="92067-112">呼び出し側メソッドのクラス インスタンスにはアドレスがあり、呼び出されたメソッドのパラメータにはそのアドレスのコピーがあり、両方のアドレスが同じオブジェクトを参照します。</span><span class="sxs-lookup"><span data-stu-id="92067-112">The class instance in the calling method has an address, the parameter in the called method has a copy of the address, and both addresses refer to the same object.</span></span> <span data-ttu-id="92067-113">パラメーターにはアドレスのコピーのみが含まれるため、呼び出されたメソッドは呼び出し側メソッドのクラス インスタンスのアドレスを変更できません。</span><span class="sxs-lookup"><span data-stu-id="92067-113">Because the parameter contains only a copy of the address, the called method cannot change the address of the class instance in the calling method.</span></span> <span data-ttu-id="92067-114">ただし、呼び出されたメソッドはアドレスを使用して、元のアドレスとコピーの両方が参照するクラス メンバーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="92067-114">However, the called method can use the address to access the class members that both the original address and the copy reference.</span></span> <span data-ttu-id="92067-115">呼び出されたメソッドがクラス メンバーを変更すると、呼び出し側メソッドの元のクラス インスタンスも変更されます。</span><span class="sxs-lookup"><span data-stu-id="92067-115">If the called method changes a class member, the original class instance in the calling method also changes.</span></span>  
  
 <span data-ttu-id="92067-116">次の例の出力はこの違いを示しています。</span><span class="sxs-lookup"><span data-stu-id="92067-116">The output of the following example illustrates the difference.</span></span> <span data-ttu-id="92067-117">クラス インスタンスの `willIChange` フィールドの値はメソッド `ClassTaker` の呼び出しによって変更されます。これは、メソッドがパラメーターのアドレスを使用して、クラス インスタンスの指定されたフィールドを検索するためです。</span><span class="sxs-lookup"><span data-stu-id="92067-117">The value of the `willIChange` field of the class instance is changed by the call to method `ClassTaker` because the method uses the address in the parameter to find the specified field of the class instance.</span></span> <span data-ttu-id="92067-118">呼び出し側メソッドの構造体の `willIChange` フィールドはメソッド `StructTaker` の呼び出しによって変更されません。これは、引数の値が、そのアドレスのコピーではなく、構造体自体のコピーであるためです。</span><span class="sxs-lookup"><span data-stu-id="92067-118">The `willIChange` field of the struct in the calling method is not changed by the call to method `StructTaker` because the value of the argument is a copy of the struct itself, not a copy of its address.</span></span> <span data-ttu-id="92067-119">`StructTaker` はコピーを変更し、そのコピーは、`StructTaker` の呼び出しが完了したときに失われます。</span><span class="sxs-lookup"><span data-stu-id="92067-119">`StructTaker` changes the copy, and the copy is lost when the call to `StructTaker` is completed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92067-120">例</span><span class="sxs-lookup"><span data-stu-id="92067-120">Example</span></span>  
 <span data-ttu-id="92067-121">[!code-cs[csProgGuideObjects#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="92067-121">[!code-cs[csProgGuideObjects#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92067-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="92067-122">See Also</span></span>  
 <span data-ttu-id="92067-123">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="92067-123">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="92067-124">[クラス](../../../csharp/programming-guide/classes-and-structs/classes.md) </span><span class="sxs-lookup"><span data-stu-id="92067-124">[Classes](../../../csharp/programming-guide/classes-and-structs/classes.md) </span></span>  
 <span data-ttu-id="92067-125">[構造体](../../../csharp/programming-guide/classes-and-structs/structs.md) </span><span class="sxs-lookup"><span data-stu-id="92067-125">[Structs](../../../csharp/programming-guide/classes-and-structs/structs.md) </span></span>  
 [<span data-ttu-id="92067-126">パラメーターの引き渡し</span><span class="sxs-lookup"><span data-stu-id="92067-126">Passing Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)

