---
title: "インデクサーの使用 (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 17bbfabe8a53fc51e81434d0a2bd9fb2b29c4695
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2018
---
# <a name="using-indexers-c-programming-guide"></a><span data-ttu-id="01d80-102">インデクサーの使用 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="01d80-102">Using Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="01d80-103">インデクサーは構文を簡略化します。これを使用すると、[クラス](../../../csharp/language-reference/keywords/class.md)、[構造体](../../../csharp/language-reference/keywords/struct.md)、または[インターフェイス](../../../csharp/language-reference/keywords/interface.md)を作成でき、クライアント アプリケーションは配列と同じようにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="01d80-103">Indexers are a syntactic convenience that enable you to create a [class](../../../csharp/language-reference/keywords/class.md), [struct](../../../csharp/language-reference/keywords/struct.md), or [interface](../../../csharp/language-reference/keywords/interface.md) that client applications can access just as an array.</span></span> <span data-ttu-id="01d80-104">インデクサーは、内部コレクションまたは配列をカプセル化することが主な目的である型で最も多く実装されます。</span><span class="sxs-lookup"><span data-stu-id="01d80-104">Indexers are most frequently implemented in types whose primary purpose is to encapsulate an internal collection or array.</span></span> <span data-ttu-id="01d80-105">たとえば、TempRecord という名前のクラスがあるとします。これは温度を華氏で表し、24 時間のうちに 10 回、異なる時刻に温度を記録します。</span><span class="sxs-lookup"><span data-stu-id="01d80-105">For example, suppose you have a class named TempRecord that represents the temperature in Farenheit as recorded at 10 different times during a 24 hour period.</span></span> <span data-ttu-id="01d80-106">クラスには float 型の "temps" という名前の配列が含まれており、これは温度を表します。また、<xref:System.DateTime> も含まれており、これは温度が記録された日付を表します。</span><span class="sxs-lookup"><span data-stu-id="01d80-106">The class contains an array named "temps" of type float to represent the temperatures, and a <xref:System.DateTime> that represents the date the temperatures were recorded.</span></span> <span data-ttu-id="01d80-107">このクラスにインデクサーを実装することで、クライアントは、`float temp = tr.temps[4]` ではなく `float temp = tr[4]` として TempRecord インスタンスの温度にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="01d80-107">By implementing an indexer in this class, clients can access the temperatures in a TempRecord instance as `float temp = tr[4]` instead of as `float temp = tr.temps[4]`.</span></span> <span data-ttu-id="01d80-108">インデクサーはクライアント アプリケーションの構文を簡略化するだけでなく、クラスとその目的を、他の開発者たちにとってわかりやすい、より直感的なものにします。</span><span class="sxs-lookup"><span data-stu-id="01d80-108">The indexer notation not only simplifies the syntax for client applications; it also makes the class and its purpose more intuitive for other developers to understand.</span></span>  
  
 <span data-ttu-id="01d80-109">クラスまたは構造体でインデクサーを宣言するには、次の例のように [this](../../../csharp/language-reference/keywords/this.md) キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="01d80-109">To declare an indexer on a class or struct, use the [this](../../../csharp/language-reference/keywords/this.md) keyword, as in this example:</span></span>  
  
```  
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="01d80-110">コメント</span><span class="sxs-lookup"><span data-stu-id="01d80-110">Remarks</span></span>  
 <span data-ttu-id="01d80-111">インデクサーの型とそのパラメーターの型は、少なくとも、インデクサー自体と同程度にアクセス可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="01d80-111">The type of an indexer and the type of its parameters must be at least as accessible as the indexer itself.</span></span> <span data-ttu-id="01d80-112">アクセシビリティ レベルの詳細については、「[アクセス修飾子 (C# リファレンス)](../../../csharp/language-reference/keywords/access-modifiers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01d80-112">For more information about accessibility levels, see [Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="01d80-113">インターフェイスでインデクサーを使用する方法の詳細については、「[インターフェイスのインデクサー (C# プログラミング ガイド)](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01d80-113">For more information about how to use indexers with an interface, see [Interface Indexers](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md).</span></span>  
  
 <span data-ttu-id="01d80-114">インデクサーのシグネチャは、その仮パラメーターの数と型で構成されます。</span><span class="sxs-lookup"><span data-stu-id="01d80-114">The signature of an indexer consists of the number and types of its formal parameters.</span></span> <span data-ttu-id="01d80-115">これには、インデクサーの型や仮パラメーターの名前は含まれません。</span><span class="sxs-lookup"><span data-stu-id="01d80-115">It does not include the indexer type or the names of the formal parameters.</span></span> <span data-ttu-id="01d80-116">同じクラス内に複数のインデクサーを宣言する場合は、異なるシグネチャが必要です。</span><span class="sxs-lookup"><span data-stu-id="01d80-116">If you declare more than one indexer in the same class, they must have different signatures.</span></span>  
  
 <span data-ttu-id="01d80-117">インデクサーの値は変数として分類されないため、インデクサーの値を [ref](../../../csharp/language-reference/keywords/ref.md) や [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) パラメーターとして渡すことはできません。</span><span class="sxs-lookup"><span data-stu-id="01d80-117">An indexer value is not classified as a variable; therefore, you cannot pass an indexer value as a [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter.</span></span>  
  
 <span data-ttu-id="01d80-118">他の言語が使用できる名前をインデクサーに指定するには、宣言で `name` 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="01d80-118">To provide the indexer with a name that other languages can use, use a `name` attribute in the declaration.</span></span> <span data-ttu-id="01d80-119">例:</span><span class="sxs-lookup"><span data-stu-id="01d80-119">For example:</span></span>  
  
```  
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this [int index]   // Indexer declaration  
{  
}  
```  
  
 <span data-ttu-id="01d80-120">このインデクサーの名前は `TheItem` になります。</span><span class="sxs-lookup"><span data-stu-id="01d80-120">This indexer will have the name `TheItem`.</span></span> <span data-ttu-id="01d80-121">name 属性を指定しないと、`Item` が既定の名前になります。</span><span class="sxs-lookup"><span data-stu-id="01d80-121">Not providing the name attribute would make `Item` the default name.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="01d80-122">例 1</span><span class="sxs-lookup"><span data-stu-id="01d80-122">Example 1</span></span>  
  
### <a name="description"></a><span data-ttu-id="01d80-123">説明</span><span class="sxs-lookup"><span data-stu-id="01d80-123">Description</span></span>  
 <span data-ttu-id="01d80-124">次の例は、プライベートな配列フィールド `temps` とインデクサーの宣言方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="01d80-124">The following example shows how to declare a private array field, `temps`, and an indexer.</span></span> <span data-ttu-id="01d80-125">インデクサーを使用すれば、インスタンス `tempRecord[i]` に直接アクセスできます。</span><span class="sxs-lookup"><span data-stu-id="01d80-125">The indexer enables direct access to the instance `tempRecord[i]`.</span></span> <span data-ttu-id="01d80-126">インデクサーを使用しない場合は、配列を [public](../../../csharp/language-reference/keywords/public.md) メンバーとして宣言し、そのメンバー `tempRecord.temps[i]` に直接アクセスします。</span><span class="sxs-lookup"><span data-stu-id="01d80-126">The alternative to using the indexer is to declare the array as a [public](../../../csharp/language-reference/keywords/public.md) member and access its members, `tempRecord.temps[i]`, directly.</span></span>  
  
 <span data-ttu-id="01d80-127">`Console.Write` ステートメントなどでインデクサーのアクセスが評価されると、[get](../../../csharp/language-reference/keywords/get.md) アクセサーが呼び出されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="01d80-127">Notice that when an indexer's access is evaluated, for example, in a `Console.Write` statement, the [get](../../../csharp/language-reference/keywords/get.md) accessor is invoked.</span></span> <span data-ttu-id="01d80-128">したがって、`get` アクセサーが存在しない場合は、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="01d80-128">Therefore, if no `get` accessor exists, a compile-time error occurs.</span></span>  
  
### <a name="code"></a><span data-ttu-id="01d80-129">コード</span><span class="sxs-lookup"><span data-stu-id="01d80-129">Code</span></span>  
 [!code-csharp[csProgGuideIndexers#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_1.cs)]  
  
## <a name="indexing-using-other-values"></a><span data-ttu-id="01d80-130">他の値を使用したインデックス作成</span><span class="sxs-lookup"><span data-stu-id="01d80-130">Indexing Using Other Values</span></span>  
 <span data-ttu-id="01d80-131">C# では、インデックス型は整数に制限されません。</span><span class="sxs-lookup"><span data-stu-id="01d80-131">C# does not limit the index type to integer.</span></span> <span data-ttu-id="01d80-132">たとえば、文字列をインデクサーで使用すると有効な場合があります。</span><span class="sxs-lookup"><span data-stu-id="01d80-132">For example, it may be useful to use a string with an indexer.</span></span> <span data-ttu-id="01d80-133">このようなインデクサーは、コレクション内の文字列を検索し、適切な値を返すことによって実装される場合があります。</span><span class="sxs-lookup"><span data-stu-id="01d80-133">Such an indexer might be implemented by searching for the string in the collection, and returning the appropriate value.</span></span> <span data-ttu-id="01d80-134">アクセサーはオーバーロードできるため、文字列と整数のバージョンは共存できます。</span><span class="sxs-lookup"><span data-stu-id="01d80-134">As accessors can be overloaded, the string and integer versions can co-exist.</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="01d80-135">例 2</span><span class="sxs-lookup"><span data-stu-id="01d80-135">Example 2</span></span>  
  
### <a name="description"></a><span data-ttu-id="01d80-136">説明</span><span class="sxs-lookup"><span data-stu-id="01d80-136">Description</span></span>  
 <span data-ttu-id="01d80-137">この例では、曜日を格納するクラスが宣言されます。</span><span class="sxs-lookup"><span data-stu-id="01d80-137">In this example, a class is declared that stores the days of the week.</span></span> <span data-ttu-id="01d80-138">`get` アクセサーは、曜日を示す文字列を受け取り、対応する整数を返すように宣言されます。</span><span class="sxs-lookup"><span data-stu-id="01d80-138">A `get` accessor is declared that takes a string, the name of a day, and returns the corresponding integer.</span></span> <span data-ttu-id="01d80-139">たとえば、Sunday の場合は 0、Monday の場合は 1 などのように返します。</span><span class="sxs-lookup"><span data-stu-id="01d80-139">For example, Sunday will return 0, Monday will return 1, and so on.</span></span>  
  
### <a name="code"></a><span data-ttu-id="01d80-140">コード</span><span class="sxs-lookup"><span data-stu-id="01d80-140">Code</span></span>  
 [!code-csharp[csProgGuideIndexers#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_2.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="01d80-141">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="01d80-141">Robust Programming</span></span>  
 <span data-ttu-id="01d80-142">インデクサーのセキュリティと信頼性を改善するには、主に次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="01d80-142">There are two main ways in which the security and reliability of indexers can be improved:</span></span>  
  
-   <span data-ttu-id="01d80-143">クライアント コードが無効なインデックス値を渡しても、それを処理できるように必ずエラー処理戦略を組み込んでください。</span><span class="sxs-lookup"><span data-stu-id="01d80-143">Be sure to incorporate some type of error-handling strategy to handle the chance of client code passing in an invalid index value.</span></span> <span data-ttu-id="01d80-144">このトピックの最初の例の TempRecord クラスには Length プロパティが用意されており、入力がインデクサーに渡される前にクライアント コードで検証できるようになっています。</span><span class="sxs-lookup"><span data-stu-id="01d80-144">In the first example earlier in this topic, the TempRecord class provides a Length property that enables the client code to verify the input before passing it to the indexer.</span></span> <span data-ttu-id="01d80-145">インデクサー自体にエラー処理コードを配置することもできます。</span><span class="sxs-lookup"><span data-stu-id="01d80-145">You can also put the error handling code inside the indexer itself.</span></span> <span data-ttu-id="01d80-146">インデクサーのアクセサー内部でスローされる例外はすべて、ユーザーのために文書化してください。</span><span class="sxs-lookup"><span data-stu-id="01d80-146">Be sure to document for users any exceptions that you throw inside an indexer accessor.</span></span>  
  
-   <span data-ttu-id="01d80-147">`get` および [set](../../../csharp/language-reference/keywords/set.md) アクセサーのアクセシビリティを設定し、適切な制限を指定します。</span><span class="sxs-lookup"><span data-stu-id="01d80-147">Set the accessibility of the `get` and [set](../../../csharp/language-reference/keywords/set.md) accessors to be as restrictive as is reasonable.</span></span> <span data-ttu-id="01d80-148">これは、`set` アクセサーの場合、特に重要です。</span><span class="sxs-lookup"><span data-stu-id="01d80-148">This is important for the `set` accessor in particular.</span></span> <span data-ttu-id="01d80-149">詳細については、「[アクセサーのアクセシビリティの制限](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01d80-149">For more information, see [Restricting Accessor Accessibility](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01d80-150">参照</span><span class="sxs-lookup"><span data-stu-id="01d80-150">See Also</span></span>  
 [<span data-ttu-id="01d80-151">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="01d80-151">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="01d80-152">インデクサー</span><span class="sxs-lookup"><span data-stu-id="01d80-152">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="01d80-153">プロパティ</span><span class="sxs-lookup"><span data-stu-id="01d80-153">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
