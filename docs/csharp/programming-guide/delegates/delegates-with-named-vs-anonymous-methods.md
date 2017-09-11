---
title: "名前付きメソッドを使用したデリゲートと匿名メソッド (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
caps.latest.revision: 18
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
ms.openlocfilehash: f82519f42e75008fc78fe475b7e37040985a21a1
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a><span data-ttu-id="f63cb-102">名前付きメソッドを使用したデリゲートと匿名メソッド (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="f63cb-102">Delegates with Named vs. Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="f63cb-103">[デリゲート](../../../csharp/language-reference/keywords/delegate.md)は、名前付きメソッドに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="f63cb-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) can be associated with a named method.</span></span> <span data-ttu-id="f63cb-104">名前付きメソッドを使用してデリゲートをインスタンス化するときは、次のように、そのメソッドをパラメーターとして渡します。</span><span class="sxs-lookup"><span data-stu-id="f63cb-104">When you instantiate a delegate by using a named method, the method is passed as a parameter, for example:</span></span>  
  
 <span data-ttu-id="f63cb-105">[!code-cs[csProgGuideDelegates#1](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f63cb-105">[!code-cs[csProgGuideDelegates#1](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_1.cs)]</span></span>  
  
 <span data-ttu-id="f63cb-106">これを名前付きメソッドの使用といいます。</span><span class="sxs-lookup"><span data-stu-id="f63cb-106">This is called using a named method.</span></span> <span data-ttu-id="f63cb-107">名前付きメソッドで作成されたデリゲートは、[静的](../../../csharp/language-reference/keywords/static.md)メソッドまたはインスタンス メソッドのいずれかでカプセル化できます。</span><span class="sxs-lookup"><span data-stu-id="f63cb-107">Delegates constructed with a named method can encapsulate either a [static](../../../csharp/language-reference/keywords/static.md) method or an instance method.</span></span> <span data-ttu-id="f63cb-108">旧バージョンの C# では、デリゲートをインスタンス化するには、名前付きメソッドを使用するしかありませんが、</span><span class="sxs-lookup"><span data-stu-id="f63cb-108">Named methods are the only way to instantiate a delegate in earlier versions of C#.</span></span> <span data-ttu-id="f63cb-109">新しいメソッドを作成するのが、オーバーヘッドの点で望ましくない場合は、C# でデリゲートをインスタンス化し、そのデリゲートが呼び出されたときに処理するコード ブロックを直接指定できます。</span><span class="sxs-lookup"><span data-stu-id="f63cb-109">However, in a situation where creating a new method is unwanted overhead, C# enables you to instantiate a delegate and immediately specify a code block that the delegate will process when it is called.</span></span> <span data-ttu-id="f63cb-110">ブロックには、ラムダ式または匿名メソッドのいずれかを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="f63cb-110">The block can contain either a lambda expression or an anonymous method.</span></span> <span data-ttu-id="f63cb-111">詳細については、[匿名関数](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f63cb-111">For more information, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f63cb-112">コメント</span><span class="sxs-lookup"><span data-stu-id="f63cb-112">Remarks</span></span>  
 <span data-ttu-id="f63cb-113">デリゲート パラメーターとして渡すメソッドには、デリゲート宣言と同じシグネチャが必要です。</span><span class="sxs-lookup"><span data-stu-id="f63cb-113">The method that you pass as a delegate parameter must have the same signature as the delegate declaration.</span></span>  
  
 <span data-ttu-id="f63cb-114">デリゲート インスタンスがカプセル化できるのは、静的メソッドまたはインスタンス メソッドのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="f63cb-114">A delegate instance may encapsulate either static or instance method.</span></span>  
  
 <span data-ttu-id="f63cb-115">デリゲートは [out](../../../csharp/language-reference/keywords/out.md) パラメーターを使用できますが、マルチキャスト イベント デリゲートでこのパラメーターを使用することはお勧めしません。どのデリゲートが呼び出されるかわからないためです。</span><span class="sxs-lookup"><span data-stu-id="f63cb-115">Although the delegate can use an [out](../../../csharp/language-reference/keywords/out.md) parameter, we do not recommend its use with multicast event delegates because you cannot know which delegate will be called.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="f63cb-116">例 1</span><span class="sxs-lookup"><span data-stu-id="f63cb-116">Example 1</span></span>  
 <span data-ttu-id="f63cb-117">次のシンプルな例では、デリゲートを宣言して使用します。</span><span class="sxs-lookup"><span data-stu-id="f63cb-117">The following is a simple example of declaring and using a delegate.</span></span> <span data-ttu-id="f63cb-118">デリゲート `Del` とそれに関連付けられているメソッド `MultiplyNumbers` の両方に同じシグネチャが含まれることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f63cb-118">Notice that both the delegate, `Del`, and the associated method, `MultiplyNumbers`, have the same signature</span></span>  
  
 <span data-ttu-id="f63cb-119">[!code-cs[csProgGuideDelegates#2](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="f63cb-119">[!code-cs[csProgGuideDelegates#2](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_2.cs)]</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="f63cb-120">例 2</span><span class="sxs-lookup"><span data-stu-id="f63cb-120">Example 2</span></span>  
 <span data-ttu-id="f63cb-121">次の例では、1 つのデリゲートを静的メソッドとインスタンス メソッドの両方に割り当て、各メソッドから特定の情報を戻します。</span><span class="sxs-lookup"><span data-stu-id="f63cb-121">In the following example, one delegate is mapped to both static and instance methods and returns specific information from each.</span></span>  
  
 <span data-ttu-id="f63cb-122">[!code-cs[csProgGuideDelegates#3](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="f63cb-122">[!code-cs[csProgGuideDelegates#3](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_3.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f63cb-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="f63cb-123">See Also</span></span>  
 <span data-ttu-id="f63cb-124">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f63cb-124">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="f63cb-125">[デリゲート](../../../csharp/programming-guide/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="f63cb-125">[Delegates](../../../csharp/programming-guide/delegates/index.md) </span></span>  
 <span data-ttu-id="f63cb-126">[匿名メソッド](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) </span><span class="sxs-lookup"><span data-stu-id="f63cb-126">[Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) </span></span>  
 <span data-ttu-id="f63cb-127">[方法: デリゲートを結合する (マルチキャスト デリゲート)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md) </span><span class="sxs-lookup"><span data-stu-id="f63cb-127">[How to: Combine Delegates (Multicast Delegates)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md) </span></span>  
 [<span data-ttu-id="f63cb-128">イベント</span><span class="sxs-lookup"><span data-stu-id="f63cb-128">Events</span></span>](../../../csharp/programming-guide/events/index.md)

