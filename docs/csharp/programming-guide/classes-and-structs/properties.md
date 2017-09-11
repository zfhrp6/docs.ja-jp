---
title: "プロパティ (C# プログラミング ガイド)"
ms.date: 2017-03-10
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.properties
dev_langs:
- CSharp
helpviewer_keywords:
- properties [C#]
- C# language, properties
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
caps.latest.revision: 38
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
ms.openlocfilehash: 127299a617cacee15f87964a12bb3877a2586204
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="properties-c-programming-guide"></a><span data-ttu-id="3990c-102">プロパティ (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="3990c-102">Properties (C# Programming Guide)</span></span>

<span data-ttu-id="3990c-103">プロパティは、プライベート フィールドの値の読み取り、書き込み、または計算を行う、柔軟な機構が用意されたメンバーです。</span><span class="sxs-lookup"><span data-stu-id="3990c-103">A property is a member that provides a flexible mechanism to read, write, or compute the value of a private field.</span></span> <span data-ttu-id="3990c-104">プロパティは、パブリック データのメンバーと同様に使用できますが、実際は*アクセサー*という特殊なメソッドです。</span><span class="sxs-lookup"><span data-stu-id="3990c-104">Properties can be used as if they are public data members, but they are actually special methods called *accessors*.</span></span> <span data-ttu-id="3990c-105">メソッドの安全性と柔軟性を高めながら、簡単にデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="3990c-105">This enables data to be accessed easily and still helps promote the safety and flexibility of methods.</span></span>  

## <a name="properties-overview"></a><span data-ttu-id="3990c-106">プロパティの概要</span><span class="sxs-lookup"><span data-stu-id="3990c-106">Properties overview</span></span>  
  
- <span data-ttu-id="3990c-107">プロパティを使えば、実装や検査コードを隠したままで、値の取得と設定についてパブリックな方法をクラスが公開できます。</span><span class="sxs-lookup"><span data-stu-id="3990c-107">Properties enable a class to expose a public way of getting and setting values, while hiding implementation or verification code.</span></span>  
  
- <span data-ttu-id="3990c-108">[get](../../../csharp/language-reference/keywords/get.md) プロパティ アクセサーはプロパティ値を取得するために使用し、[set](../../../csharp/language-reference/keywords/set.md) プロパティ アクセサーは新しい値を割り当てるために使用します。</span><span class="sxs-lookup"><span data-stu-id="3990c-108">A [get](../../../csharp/language-reference/keywords/get.md) property accessor is used to return the property value, and a [set](../../../csharp/language-reference/keywords/set.md) property accessor is used to assign a new value.</span></span> <span data-ttu-id="3990c-109">これらのアクセサーには異なるアクセス レベルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="3990c-109">These accessors can have different access levels.</span></span> <span data-ttu-id="3990c-110">詳細については、「[アクセサーのアクセシビリティの制限](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3990c-110">For more information, see [Restricting Accessor Accessibility](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span></span>  
  
- <span data-ttu-id="3990c-111">`set` アクセサーで割り当てる値は [value](../../../csharp/language-reference/keywords/value.md) キーワードを使用して定義します。</span><span class="sxs-lookup"><span data-stu-id="3990c-111">The [value](../../../csharp/language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` accessor.</span></span>  
- <span data-ttu-id="3990c-112">プロパティの種類には、*読み取り/書き込み* (`get` アクセサーと `set` アクセサーの両方を備える)、*読み取り専用* (`get` アクセサーのみで `set` アクセサーはない)、*書き込み専用* (`set` アクセサーのみで `get` アクセサーはない) があります。</span><span class="sxs-lookup"><span data-stu-id="3990c-112">Properties can be *read-write* (they have both a `get` and a `set` accessor), *read-only* (they have a `get` accessor but no `set` accessor), or *write-only* (they have a `set` accessor, but no `get` accessor).</span></span> <span data-ttu-id="3990c-113">書き込み専用のプロパティの使用頻度は低く、ほとんどの場合、機密データへのアクセスを制限するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="3990c-113">Write-only properties are rare and are most commonly used to restrict access to sensitive data.</span></span>

- <span data-ttu-id="3990c-114">カスタムのアクセサー コードを必要としない単純なプロパティは、式本体の定義として、または[自動実装プロパティ](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)として実装できます。</span><span class="sxs-lookup"><span data-stu-id="3990c-114">Simple properties that require no custom accessor code can be implemented either as expression body definitions or as [auto-implemented properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>
 
## <a name="properties-with-backing-fields"></a><span data-ttu-id="3990c-115">バッキング フィールドを持つプロパティ</span><span class="sxs-lookup"><span data-stu-id="3990c-115">Properties with backing fields</span></span>

<span data-ttu-id="3990c-116">プロパティを実装する基本的な手法の 1 つとして、プロパティ値の設定と取得にプライベート バッキング フィールドを使用する方法があります。</span><span class="sxs-lookup"><span data-stu-id="3990c-116">One basic pattern for implementing a property involves using a private backing field for setting and retrieving the property value.</span></span> <span data-ttu-id="3990c-117">この方法では、`get` アクセサーはプライベート フィールドの値を返します。`set` アクセサーはプライベート フィールドに値を割り当てる前にデータ検証を実行できます。</span><span class="sxs-lookup"><span data-stu-id="3990c-117">The `get` accessor returns the value of the private field, and the `set` accessor may perform some data validation before assigning a value to the private field.</span></span> <span data-ttu-id="3990c-118">また、どちらのアクセサーも、データの変換や計算を行ってから、データを格納したり返したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="3990c-118">Both accessors may also perform some conversion or computation on the data before it is stored or returned.</span></span>

<span data-ttu-id="3990c-119">このパターンを説明する例を下に示します。</span><span class="sxs-lookup"><span data-stu-id="3990c-119">The following example illustrates this pattern.</span></span> <span data-ttu-id="3990c-120">この例では、`TimePeriod` クラスは時間間隔を表しています。</span><span class="sxs-lookup"><span data-stu-id="3990c-120">In this example, the `TimePeriod` class represents an interval of time.</span></span> <span data-ttu-id="3990c-121">クラスの内部では、`seconds` という名前のプライベート フィールドに時間間隔が秒単位で格納されます。</span><span class="sxs-lookup"><span data-stu-id="3990c-121">Internally, the class stores the time interval in seconds in a private field named `seconds`.</span></span> <span data-ttu-id="3990c-122">`Hours` という読み取り/書き込みプロパティでは、ユーザーが時間間隔を時間単位で指定できます。</span><span class="sxs-lookup"><span data-stu-id="3990c-122">A read-write property named `Hours` allows the customer to specify the time interval in hours.</span></span> <span data-ttu-id="3990c-123">`get` アクセサーと `set` アクセサーの両方で、必要に応じて時間と秒の変換が実行されます。</span><span class="sxs-lookup"><span data-stu-id="3990c-123">Both the `get` and the `set` accessors perform the necessary conversion between hours and seconds.</span></span> <span data-ttu-id="3990c-124">また、`set` アクセサーは、データを検証し、時間数が無効である場合に @System.ArgumentOutOfRangeException をスローします。</span><span class="sxs-lookup"><span data-stu-id="3990c-124">In addition, the `set` accessor validates the data and throws an @System.ArgumentOutOfRangeException if the number of hours is invalid.</span></span> 
   
 <span data-ttu-id="3990c-125">[!code-cs[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]</span><span class="sxs-lookup"><span data-stu-id="3990c-125">[!code-cs[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="3990c-126">式本体の定義</span><span class="sxs-lookup"><span data-stu-id="3990c-126">Expression body definitions</span></span>  

 <span data-ttu-id="3990c-127">プロパティ アクセサーは、通常、式の結果を割り当てるか返すだけの 1 行のステートメントで構成されます。</span><span class="sxs-lookup"><span data-stu-id="3990c-127">Property accessors often consist of single-line statements that just assign or return the result of an expression.</span></span> <span data-ttu-id="3990c-128">プロパティは、本体が式形式のメンバーとして実装できます。</span><span class="sxs-lookup"><span data-stu-id="3990c-128">You can implement these properties as expression-bodied members.</span></span> <span data-ttu-id="3990c-129">式本体の定義は、`=>` 記号の後に、プロパティに割り当てるかプロパティから取得するための式を続けて構成します。</span><span class="sxs-lookup"><span data-stu-id="3990c-129">Expression body definitions consist of the `=>` symbol followed by the expression to assign to or retrieve from the property.</span></span>

 <span data-ttu-id="3990c-130">C# 6 以降では、読み取り専用プロパティに `get` アクセサーを式形式のメンバーとして実装できます。</span><span class="sxs-lookup"><span data-stu-id="3990c-130">Starting with C# 6, read-only properties can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="3990c-131">この場合、`get` アクセサー キーワードと `return` キーワードはどちらも使用しません。</span><span class="sxs-lookup"><span data-stu-id="3990c-131">In this case, neither the `get` accessor keyword nor the `return` keyword is used.</span></span> <span data-ttu-id="3990c-132">次の例では、読み取り専用 `Name` プロパティを式形式のメンバーとして実装しています。</span><span class="sxs-lookup"><span data-stu-id="3990c-132">The following example implements the read-only `Name` property as an expression-bodied member.</span></span>

 <span data-ttu-id="3990c-133">[!code-cs[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]</span><span class="sxs-lookup"><span data-stu-id="3990c-133">[!code-cs[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]</span></span>  

 <span data-ttu-id="3990c-134">C# 7 以降では、`get` アクセサーと `set` アクセサーのどちらも、式形式のメンバーとして実装できます。</span><span class="sxs-lookup"><span data-stu-id="3990c-134">Starting with C# 7, both the `get` and the `set` accessor can be implemented as expression-bodied members.</span></span> <span data-ttu-id="3990c-135">この場合、`get` キーワードと `set` キーワードを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3990c-135">In this case, the `get` and `set` keywords must be present.</span></span> <span data-ttu-id="3990c-136">両方のアクセサーに式本体の定義を使用する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3990c-136">The following example illustrates the use of expression body definitions for both accessors.</span></span> <span data-ttu-id="3990c-137">`get` アクセサーで `return` キーワードが使用されていない点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="3990c-137">Note that the `return` keyword is not used with the `get` accessor.</span></span>
 
  <span data-ttu-id="3990c-138">[!code-cs[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]</span><span class="sxs-lookup"><span data-stu-id="3990c-138">[!code-cs[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]</span></span>  

## <a name="auto-implemented-properties"></a><span data-ttu-id="3990c-139">自動実装プロパティ</span><span class="sxs-lookup"><span data-stu-id="3990c-139">Auto-implemented properties</span></span>

<span data-ttu-id="3990c-140">ロジックを追加しなくても、プロパティの `get` アクセサーと `set` アクセサーはバッキング フィールドに値を割り当てたりバッキング フィールドから取得したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="3990c-140">In some cases, property `get` and `set` accessors just assign a value to or retrieve a value from a backing field without including any additional logic.</span></span> <span data-ttu-id="3990c-141">この自動実装プロパティを使用すると、C# コンパイラによってバッキング フィールドが透過的に提供されるため、コードを簡略化できます。</span><span class="sxs-lookup"><span data-stu-id="3990c-141">By using auto-implemented properties, you can simplify your code while having the C# compiler transparently provide the backing field for you.</span></span> 

<span data-ttu-id="3990c-142">プロパティが `get` アクセサーと `set` アクセサーの両方を備えている場合は、両方を自動実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3990c-142">If a property has both a `get` and a `set` accessor, both must be auto-implemented.</span></span> <span data-ttu-id="3990c-143">自動実装プロパティを定義するには、実装を省略して `get` キーワードと `set` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="3990c-143">You define an auto-implemented property by using the `get` and `set` keywords without providing any implementation.</span></span> <span data-ttu-id="3990c-144">次の例は前の例と似ていますが、`Name` と `Price` が自動実装プロパティである点が異なります。</span><span class="sxs-lookup"><span data-stu-id="3990c-144">The following example repeats the previous one, except that `Name` and `Price` are auto-implemented properties.</span></span> <span data-ttu-id="3990c-145">この例では、パラメーター化されたコンストラクターも削除されているため、`SaleItem` オブジェクトが既定のコンストラクターの呼び出しと[オブジェクト初期化子](object-and-collection-initializers.md)を使用して初期化されています。</span><span class="sxs-lookup"><span data-stu-id="3990c-145">Note that the example also removes the parameterized constructor, so that `SaleItem` objects are now initialized with a call to the default constructor and an [object initializer](object-and-collection-initializers.md).</span></span>

  <span data-ttu-id="3990c-146">[!code-cs[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]</span><span class="sxs-lookup"><span data-stu-id="3990c-146">[!code-cs[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]</span></span>  

## <a name="related-sections"></a><span data-ttu-id="3990c-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="3990c-147">Related sections</span></span>  
  
-   [<span data-ttu-id="3990c-148">プロパティの使用</span><span class="sxs-lookup"><span data-stu-id="3990c-148">Using Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [<span data-ttu-id="3990c-149">インターフェイスのプロパティ</span><span class="sxs-lookup"><span data-stu-id="3990c-149">Interface Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
  
-   [<span data-ttu-id="3990c-150">プロパティとインデクサーの比較</span><span class="sxs-lookup"><span data-stu-id="3990c-150">Comparison Between Properties and Indexers</span></span>](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [<span data-ttu-id="3990c-151">アクセサーのアクセシビリティの制限</span><span class="sxs-lookup"><span data-stu-id="3990c-151">Restricting Accessor Accessibility</span></span>](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
-   [<span data-ttu-id="3990c-152">自動実装プロパティ</span><span class="sxs-lookup"><span data-stu-id="3990c-152">Auto-Implemented Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="3990c-153">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="3990c-153">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3990c-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="3990c-154">See also</span></span>
 <span data-ttu-id="3990c-155">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="3990c-155">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="3990c-156">[プロパティの使用](../../../csharp/programming-guide/classes-and-structs/using-properties.md) </span><span class="sxs-lookup"><span data-stu-id="3990c-156">[Using Properties](../../../csharp/programming-guide/classes-and-structs/using-properties.md) </span></span>  
 <span data-ttu-id="3990c-157">[インデクサー](../../../csharp/programming-guide/indexers/index.md) </span><span class="sxs-lookup"><span data-stu-id="3990c-157">[Indexers](../../../csharp/programming-guide/indexers/index.md) </span></span>  
 <span data-ttu-id="3990c-158">[et キーワード](../../../csharp/language-reference/keywords/get.md)  </span><span class="sxs-lookup"><span data-stu-id="3990c-158">[get keyword](../../../csharp/language-reference/keywords/get.md)  </span></span>  
 [<span data-ttu-id="3990c-159">set キーワード</span><span class="sxs-lookup"><span data-stu-id="3990c-159">set keyword</span></span>](../../../csharp/language-reference/keywords/set.md)    

