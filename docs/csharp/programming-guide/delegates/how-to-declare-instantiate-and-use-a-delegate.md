---
title: "方法 : デリゲートを宣言し、インスタンス化して使用する (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b5a5329b9e99fcd5830a57eb8f97b4edb67ad8a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="5248c-102">方法 : デリゲートを宣言し、インスタンス化して使用する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="5248c-102">How to: Declare, Instantiate, and Use a Delegate (C# Programming Guide)</span></span>
<span data-ttu-id="5248c-103">C# 1.0 以降では、次の例に示すようにデリゲートを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="5248c-103">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#13](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#14](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_2.cs)]  
  
 <span data-ttu-id="5248c-104">C# 2.0 では、次の例に示すように、上記の宣言をより簡単に記述できます。</span><span class="sxs-lookup"><span data-stu-id="5248c-104">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#32](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_3.cs)]  
  
 <span data-ttu-id="5248c-105">C# 2.0 以降では、次の例に示すように、匿名メソッドを使用して[デリゲート](../../../csharp/language-reference/keywords/delegate.md)の宣言と初期化を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="5248c-105">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../../csharp/language-reference/keywords/delegate.md), as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#15](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_4.cs)]  
  
 <span data-ttu-id="5248c-106">C# 3.0 以降では、次の例に示すように、ラムダ式を使用してデリゲートの宣言とインスタンス化を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="5248c-106">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#31](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_5.cs)]  
  
 <span data-ttu-id="5248c-107">詳しくは、「[ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5248c-107">For more information, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="5248c-108">次の例で、デリゲートの宣言、インスタンス化、および使用の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5248c-108">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="5248c-109">`BookDB` クラスにより、書籍のデータベースを保持する書店データベースをカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="5248c-109">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="5248c-110">これは、データベース内にあるすべてのペーパーバックを検索し、各ペーパーバックに対してデリゲートを呼び出す `ProcessPaperbackBooks` メソッドを公開します。</span><span class="sxs-lookup"><span data-stu-id="5248c-110">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="5248c-111">使用する `delegate` 型には `ProcessBookDelegate` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="5248c-111">The `delegate` type that is used is named `ProcessBookDelegate`.</span></span> <span data-ttu-id="5248c-112">`Test` クラスでは、このクラスを使用してペーパーバックのタイトルと平均価格を出力します。</span><span class="sxs-lookup"><span data-stu-id="5248c-112">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="5248c-113">デリゲートを使用することで、書店データベースとクライアント コードの機能を適切に分離しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="5248c-113">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="5248c-114">クライアント コードからは、書籍の格納方法や書店コードでのペーパーバックの検索方法はわかりません。</span><span class="sxs-lookup"><span data-stu-id="5248c-114">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="5248c-115">書店コードからは、検索後にペーパーバックに対して行われる処理はわかりません。</span><span class="sxs-lookup"><span data-stu-id="5248c-115">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5248c-116">例</span><span class="sxs-lookup"><span data-stu-id="5248c-116">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#12](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_6.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="5248c-117">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="5248c-117">Robust Programming</span></span>  
  
-   <span data-ttu-id="5248c-118">デリゲートを宣言する。</span><span class="sxs-lookup"><span data-stu-id="5248c-118">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="5248c-119">次のステートメントで、新しいデリゲート型を宣言します。</span><span class="sxs-lookup"><span data-stu-id="5248c-119">The following statement declares a new delegate type.</span></span>  
  
     [!code-csharp[csProgGuideDelegates#16](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_7.cs)]  
  
     <span data-ttu-id="5248c-120">各デリゲート型は、引数の数と型、およびデリゲートでカプセル化可能なメソッドの戻り値の型を示します。</span><span class="sxs-lookup"><span data-stu-id="5248c-120">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="5248c-121">引数型または戻り値型のセットが新しく必要になった場合は、常に新しいデリゲート型を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5248c-121">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
-   <span data-ttu-id="5248c-122">デリゲートをインスタンス化する。</span><span class="sxs-lookup"><span data-stu-id="5248c-122">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="5248c-123">デリゲート型の宣言後、デリゲート オブジェクトを作成して特定のメソッドに関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="5248c-123">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="5248c-124">先の例では、次の例に示すように `PrintTitle` メソッドを `ProcessPaperbackBooks` メソッドに渡すことでこの操作を行っています。</span><span class="sxs-lookup"><span data-stu-id="5248c-124">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#17](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_8.cs)]  
  
     <span data-ttu-id="5248c-125">これにより、[静的](../../../csharp/language-reference/keywords/static.md) メソッド `Test.PrintTitle` に関連付けられた新しいデリゲート オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="5248c-125">This creates a new delegate object associated with the [static](../../../csharp/language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="5248c-126">同様に、次の例で示すようにオブジェクト `totaller` の非静的メソッド `AddBookToTotal` も渡しています。</span><span class="sxs-lookup"><span data-stu-id="5248c-126">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#18](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_9.cs)]  
  
     <span data-ttu-id="5248c-127">どちらの場合でも、新しいデリゲート オブジェクトが `ProcessPaperbackBooks` メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="5248c-127">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="5248c-128">デリゲート オブジェクトは不変であるため、関連付けられているメソッドを、デリゲートの作成後に変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="5248c-128">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
-   <span data-ttu-id="5248c-129">デリゲートを呼び出す。</span><span class="sxs-lookup"><span data-stu-id="5248c-129">Calling a delegate.</span></span>  
  
     <span data-ttu-id="5248c-130">デリゲート オブジェクトを作成したら、通常は、そのデリゲートを呼び出す別のコードにデリゲート オブジェクトを渡します。</span><span class="sxs-lookup"><span data-stu-id="5248c-130">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="5248c-131">デリゲート オブジェクトを呼び出すときには、デリゲートに渡す引数を、デリゲート オブジェクト名の後ろにかっこで囲んで付けます。</span><span class="sxs-lookup"><span data-stu-id="5248c-131">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="5248c-132">デリゲートの呼び出しの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5248c-132">Following is an example of a delegate call:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#19](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_10.cs)]  
  
     <span data-ttu-id="5248c-133">デリゲートは、この例に示すように同期的に呼び出すことも、`BeginInvoke` メソッドおよび `EndInvoke` メソッドを使用して非同期的に呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="5248c-133">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5248c-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="5248c-134">See Also</span></span>  
 [<span data-ttu-id="5248c-135">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="5248c-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5248c-136">イベント</span><span class="sxs-lookup"><span data-stu-id="5248c-136">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="5248c-137">デリゲート</span><span class="sxs-lookup"><span data-stu-id="5248c-137">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
