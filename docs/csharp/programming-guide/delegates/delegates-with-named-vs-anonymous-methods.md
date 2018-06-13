---
title: 名前付きメソッドを使用したデリゲートと匿名メソッド (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: 93e140859e44aab860577feede40df6eab4c8e00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33330766"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a><span data-ttu-id="de336-102">名前付きメソッドを使用したデリゲートと匿名メソッド (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="de336-102">Delegates with Named vs. Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="de336-103">[デリゲート](../../../csharp/language-reference/keywords/delegate.md)は、名前付きメソッドに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="de336-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) can be associated with a named method.</span></span> <span data-ttu-id="de336-104">名前付きメソッドを使用してデリゲートをインスタンス化するときは、次のように、そのメソッドをパラメーターとして渡します。</span><span class="sxs-lookup"><span data-stu-id="de336-104">When you instantiate a delegate by using a named method, the method is passed as a parameter, for example:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#1](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_1.cs)]  
  
 <span data-ttu-id="de336-105">これを名前付きメソッドの使用といいます。</span><span class="sxs-lookup"><span data-stu-id="de336-105">This is called using a named method.</span></span> <span data-ttu-id="de336-106">名前付きメソッドで作成されたデリゲートは、[静的](../../../csharp/language-reference/keywords/static.md)メソッドまたはインスタンス メソッドのいずれかでカプセル化できます。</span><span class="sxs-lookup"><span data-stu-id="de336-106">Delegates constructed with a named method can encapsulate either a [static](../../../csharp/language-reference/keywords/static.md) method or an instance method.</span></span> <span data-ttu-id="de336-107">旧バージョンの C# では、デリゲートをインスタンス化するには、名前付きメソッドを使用するしかありませんが、</span><span class="sxs-lookup"><span data-stu-id="de336-107">Named methods are the only way to instantiate a delegate in earlier versions of C#.</span></span> <span data-ttu-id="de336-108">新しいメソッドを作成するのが、オーバーヘッドの点で望ましくない場合は、C# でデリゲートをインスタンス化し、そのデリゲートが呼び出されたときに処理するコード ブロックを直接指定できます。</span><span class="sxs-lookup"><span data-stu-id="de336-108">However, in a situation where creating a new method is unwanted overhead, C# enables you to instantiate a delegate and immediately specify a code block that the delegate will process when it is called.</span></span> <span data-ttu-id="de336-109">ブロックには、ラムダ式または匿名メソッドのいずれかを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="de336-109">The block can contain either a lambda expression or an anonymous method.</span></span> <span data-ttu-id="de336-110">詳細については、[匿名関数](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="de336-110">For more information, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de336-111">コメント</span><span class="sxs-lookup"><span data-stu-id="de336-111">Remarks</span></span>  
 <span data-ttu-id="de336-112">デリゲート パラメーターとして渡すメソッドには、デリゲート宣言と同じシグネチャが必要です。</span><span class="sxs-lookup"><span data-stu-id="de336-112">The method that you pass as a delegate parameter must have the same signature as the delegate declaration.</span></span>  
  
 <span data-ttu-id="de336-113">デリゲート インスタンスがカプセル化できるのは、静的メソッドまたはインスタンス メソッドのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="de336-113">A delegate instance may encapsulate either static or instance method.</span></span>  
  
 <span data-ttu-id="de336-114">デリゲートは [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) パラメーターを使用できますが、マルチキャスト イベント デリゲートでこのパラメーターを使用することはお勧めしません。どのデリゲートが呼び出されるかわからないためです。</span><span class="sxs-lookup"><span data-stu-id="de336-114">Although the delegate can use an [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter, we do not recommend its use with multicast event delegates because you cannot know which delegate will be called.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="de336-115">例 1</span><span class="sxs-lookup"><span data-stu-id="de336-115">Example 1</span></span>  
 <span data-ttu-id="de336-116">次のシンプルな例では、デリゲートを宣言して使用します。</span><span class="sxs-lookup"><span data-stu-id="de336-116">The following is a simple example of declaring and using a delegate.</span></span> <span data-ttu-id="de336-117">デリゲート `Del` とそれに関連付けられているメソッド `MultiplyNumbers` の両方に同じシグネチャが含まれることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="de336-117">Notice that both the delegate, `Del`, and the associated method, `MultiplyNumbers`, have the same signature</span></span>  
  
 [!code-csharp[csProgGuideDelegates#2](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_2.cs)]  
  
## <a name="example-2"></a><span data-ttu-id="de336-118">例 2</span><span class="sxs-lookup"><span data-stu-id="de336-118">Example 2</span></span>  
 <span data-ttu-id="de336-119">次の例では、1 つのデリゲートを静的メソッドとインスタンス メソッドの両方に割り当て、各メソッドから特定の情報を戻します。</span><span class="sxs-lookup"><span data-stu-id="de336-119">In the following example, one delegate is mapped to both static and instance methods and returns specific information from each.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#3](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="de336-120">参照</span><span class="sxs-lookup"><span data-stu-id="de336-120">See Also</span></span>  
 [<span data-ttu-id="de336-121">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="de336-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="de336-122">デリゲート</span><span class="sxs-lookup"><span data-stu-id="de336-122">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="de336-123">匿名メソッド</span><span class="sxs-lookup"><span data-stu-id="de336-123">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [<span data-ttu-id="de336-124">方法: デリゲートを結合する (マルチキャスト デリゲート)</span><span class="sxs-lookup"><span data-stu-id="de336-124">How to: Combine Delegates (Multicast Delegates)</span></span>](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
 [<span data-ttu-id="de336-125">イベント</span><span class="sxs-lookup"><span data-stu-id="de336-125">Events</span></span>](../../../csharp/programming-guide/events/index.md)
