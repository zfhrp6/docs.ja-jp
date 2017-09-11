---
title: "方法 : デリゲートを宣言し、インスタンス化して使用する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
caps.latest.revision: 21
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
ms.openlocfilehash: 5a16fe4c627989f701ba523769cd87839d074849
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="51734-102">方法 : デリゲートを宣言し、インスタンス化して使用する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="51734-102">How to: Declare, Instantiate, and Use a Delegate (C# Programming Guide)</span></span>
<span data-ttu-id="51734-103">C# 1.0 以降では、次の例に示すようにデリゲートを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="51734-103">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 <span data-ttu-id="51734-104">[!code-cs[csProgGuideDelegates#13](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="51734-104">[!code-cs[csProgGuideDelegates#13](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_1.cs)]</span></span>  
  
 <span data-ttu-id="51734-105">[!code-cs[csProgGuideDelegates#14](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="51734-105">[!code-cs[csProgGuideDelegates#14](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_2.cs)]</span></span>  
  
 <span data-ttu-id="51734-106">C# 2.0 では、次の例に示すように、上記の宣言をより簡単に記述できます。</span><span class="sxs-lookup"><span data-stu-id="51734-106">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 <span data-ttu-id="51734-107">[!code-cs[csProgGuideDelegates#32](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="51734-107">[!code-cs[csProgGuideDelegates#32](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_3.cs)]</span></span>  
  
 <span data-ttu-id="51734-108">C# 2.0 以降では、次の例に示すように、匿名メソッドを使用して[デリゲート](../../../csharp/language-reference/keywords/delegate.md)の宣言と初期化を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="51734-108">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../../csharp/language-reference/keywords/delegate.md), as shown in the following example.</span></span>  
  
 <span data-ttu-id="51734-109">[!code-cs[csProgGuideDelegates#15](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="51734-109">[!code-cs[csProgGuideDelegates#15](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_4.cs)]</span></span>  
  
 <span data-ttu-id="51734-110">C# 3.0 以降では、次の例に示すように、ラムダ式を使用してデリゲートの宣言とインスタンス化を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="51734-110">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 <span data-ttu-id="51734-111">[!code-cs[csProgGuideDelegates#31](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="51734-111">[!code-cs[csProgGuideDelegates#31](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_5.cs)]</span></span>  
  
 <span data-ttu-id="51734-112">詳細については、「[ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51734-112">For more information, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="51734-113">次の例で、デリゲートの宣言、インスタンス化、および使用の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="51734-113">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="51734-114">`BookDB` クラスにより、書籍のデータベースを保持する書店データベースをカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="51734-114">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="51734-115">これは、データベース内にあるすべてのペーパーバックを検索し、各ペーパーバックに対してデリゲートを呼び出す `ProcessPaperbackBooks` メソッドを公開します。</span><span class="sxs-lookup"><span data-stu-id="51734-115">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="51734-116">使用する `delegate` 型には `ProcessBookDelegate` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="51734-116">The `delegate` type that is used is named `ProcessBookDelegate`.</span></span> <span data-ttu-id="51734-117">`Test` クラスでは、このクラスを使用してペーパーバックのタイトルと平均価格を出力します。</span><span class="sxs-lookup"><span data-stu-id="51734-117">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="51734-118">デリゲートを使用することで、書店データベースとクライアント コードの機能を適切に分離しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="51734-118">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="51734-119">クライアント コードからは、書籍の格納方法や書店コードでのペーパーバックの検索方法はわかりません。</span><span class="sxs-lookup"><span data-stu-id="51734-119">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="51734-120">書店コードからは、検索後にペーパーバックに対して行われる処理はわかりません。</span><span class="sxs-lookup"><span data-stu-id="51734-120">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51734-121">例</span><span class="sxs-lookup"><span data-stu-id="51734-121">Example</span></span>  
 <span data-ttu-id="51734-122">[!code-cs[csProgGuideDelegates#12](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="51734-122">[!code-cs[csProgGuideDelegates#12](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_6.cs)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="51734-123">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="51734-123">Robust Programming</span></span>  
  
-   <span data-ttu-id="51734-124">デリゲートを宣言する。</span><span class="sxs-lookup"><span data-stu-id="51734-124">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="51734-125">次のステートメントで、新しいデリゲート型を宣言します。</span><span class="sxs-lookup"><span data-stu-id="51734-125">The following statement declares a new delegate type.</span></span>  
  
     <span data-ttu-id="51734-126">[!code-cs[csProgGuideDelegates#16](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="51734-126">[!code-cs[csProgGuideDelegates#16](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_7.cs)]</span></span>  
  
     <span data-ttu-id="51734-127">各デリゲート型は、引数の数と型、およびデリゲートでカプセル化可能なメソッドの戻り値の型を示します。</span><span class="sxs-lookup"><span data-stu-id="51734-127">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="51734-128">引数型または戻り値型のセットが新しく必要になった場合は、常に新しいデリゲート型を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="51734-128">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
-   <span data-ttu-id="51734-129">デリゲートをインスタンス化する。</span><span class="sxs-lookup"><span data-stu-id="51734-129">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="51734-130">デリゲート型の宣言後、デリゲート オブジェクトを作成して特定のメソッドに関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="51734-130">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="51734-131">先の例では、次の例に示すように `PrintTitle` メソッドを `ProcessPaperbackBooks` メソッドに渡すことでこの操作を行っています。</span><span class="sxs-lookup"><span data-stu-id="51734-131">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     <span data-ttu-id="51734-132">[!code-cs[csProgGuideDelegates#17](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="51734-132">[!code-cs[csProgGuideDelegates#17](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_8.cs)]</span></span>  
  
     <span data-ttu-id="51734-133">これにより、[静的](../../../csharp/language-reference/keywords/static.md) メソッド `Test.PrintTitle` に関連付けられた新しいデリゲート オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="51734-133">This creates a new delegate object associated with the [static](../../../csharp/language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="51734-134">同様に、次の例で示すようにオブジェクト `totaller` の非静的メソッド `AddBookToTotal` も渡しています。</span><span class="sxs-lookup"><span data-stu-id="51734-134">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     <span data-ttu-id="51734-135">[!code-cs[csProgGuideDelegates#18](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="51734-135">[!code-cs[csProgGuideDelegates#18](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_9.cs)]</span></span>  
  
     <span data-ttu-id="51734-136">どちらの場合でも、新しいデリゲート オブジェクトが `ProcessPaperbackBooks` メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="51734-136">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="51734-137">デリゲート オブジェクトは不変であるため、関連付けられているメソッドを、デリゲートの作成後に変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="51734-137">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
-   <span data-ttu-id="51734-138">デリゲートを呼び出す。</span><span class="sxs-lookup"><span data-stu-id="51734-138">Calling a delegate.</span></span>  
  
     <span data-ttu-id="51734-139">デリゲート オブジェクトを作成したら、通常は、そのデリゲートを呼び出す別のコードにデリゲート オブジェクトを渡します。</span><span class="sxs-lookup"><span data-stu-id="51734-139">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="51734-140">デリゲート オブジェクトを呼び出すときには、デリゲートに渡す引数を、デリゲート オブジェクト名の後ろにかっこで囲んで付けます。</span><span class="sxs-lookup"><span data-stu-id="51734-140">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="51734-141">デリゲートの呼び出しの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="51734-141">Following is an example of a delegate call:</span></span>  
  
     <span data-ttu-id="51734-142">[!code-cs[csProgGuideDelegates#19](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_10.cs)]</span><span class="sxs-lookup"><span data-stu-id="51734-142">[!code-cs[csProgGuideDelegates#19](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_10.cs)]</span></span>  
  
     <span data-ttu-id="51734-143">デリゲートは、この例に示すように同期的に呼び出すことも、`BeginInvoke` メソッドおよび `EndInvoke` メソッドを使用して非同期的に呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="51734-143">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51734-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="51734-144">See Also</span></span>  
 <span data-ttu-id="51734-145">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="51734-145">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="51734-146">[イベント](../../../csharp/programming-guide/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="51734-146">[Events](../../../csharp/programming-guide/events/index.md) </span></span>  
 [<span data-ttu-id="51734-147">デリゲート</span><span class="sxs-lookup"><span data-stu-id="51734-147">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)

