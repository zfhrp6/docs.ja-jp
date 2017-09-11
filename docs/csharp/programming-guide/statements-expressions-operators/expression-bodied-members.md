---
title: "式形式のメンバー (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d12f9f3af9a57e142311f6d1676b5f97e8b60d19
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="expression-bodied-members-c-programming-guide"></a><span data-ttu-id="1c940-102">式形式のメンバー (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="1c940-102">Expression-bodied members (C# programming guide)</span></span>
<span data-ttu-id="1c940-103">式本体の定義を使用すると、簡潔でわかりやすい形式でメンバーの実装を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1c940-103">Expression body definitions let you provide a member's implementation in a very concise, readable form.</span></span> <span data-ttu-id="1c940-104">サポートされる任意のメンバー (メソッドやプロパティなど) に関するロジックが単一の式で構成される場合は、常に式本体の定義を使用できます。</span><span class="sxs-lookup"><span data-stu-id="1c940-104">You can use an expression body definition whenever the logic for any supported member, such as a method or property, consists of a single expression.</span></span> <span data-ttu-id="1c940-105">式本体の定義には、次の一般的な構文があります。</span><span class="sxs-lookup"><span data-stu-id="1c940-105">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="1c940-106">この *expression* には有効な式を指定します。</span><span class="sxs-lookup"><span data-stu-id="1c940-106">where *expression* is a valid expression.</span></span> 

<span data-ttu-id="1c940-107">式本体の定義のサポートは、メソッドとプロパティの get アクセサーのために C# 6 で導入され、C# 7 で拡張されました。</span><span class="sxs-lookup"><span data-stu-id="1c940-107">Support for expression body definitions was introduced for methods and property get accessors in C# 6 and was expanded in C# 7.</span></span> <span data-ttu-id="1c940-108">式本体の定義は、次の表の方メンバーで使用できます。</span><span class="sxs-lookup"><span data-stu-id="1c940-108">Expression body definitions can be used with the type members listed in the following table:</span></span> 

|<span data-ttu-id="1c940-109">メンバー</span><span class="sxs-lookup"><span data-stu-id="1c940-109">Member</span></span>  |<span data-ttu-id="1c940-110">サポートが開始されたバージョン</span><span class="sxs-lookup"><span data-stu-id="1c940-110">Supported as of...</span></span> |
|---------|---------|
|[<span data-ttu-id="1c940-111">メソッド</span><span class="sxs-lookup"><span data-stu-id="1c940-111">Method</span></span>](#methods)  |<span data-ttu-id="1c940-112">C# 6</span><span class="sxs-lookup"><span data-stu-id="1c940-112">C# 6</span></span> |
|[<span data-ttu-id="1c940-113">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="1c940-113">Constructor</span></span>](#constructors)   |<span data-ttu-id="1c940-114">C# 7</span><span class="sxs-lookup"><span data-stu-id="1c940-114">C# 7</span></span> |
|[<span data-ttu-id="1c940-115">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="1c940-115">Finalizer</span></span>](#finalizers)     |<span data-ttu-id="1c940-116">C# 7</span><span class="sxs-lookup"><span data-stu-id="1c940-116">C# 7</span></span> |
|[<span data-ttu-id="1c940-117">プロパティの取得</span><span class="sxs-lookup"><span data-stu-id="1c940-117">Property Get</span></span>](#property-get-statements)  |<span data-ttu-id="1c940-118">C# 6</span><span class="sxs-lookup"><span data-stu-id="1c940-118">C# 6</span></span> |
|[<span data-ttu-id="1c940-119">プロパティの設定</span><span class="sxs-lookup"><span data-stu-id="1c940-119">Property Set</span></span>](#property-set-statements)  |<span data-ttu-id="1c940-120">C# 7</span><span class="sxs-lookup"><span data-stu-id="1c940-120">C# 7</span></span> |
|[<span data-ttu-id="1c940-121">インデクサー</span><span class="sxs-lookup"><span data-stu-id="1c940-121">Indexer</span></span>](#indexers)       |<span data-ttu-id="1c940-122">C# 7</span><span class="sxs-lookup"><span data-stu-id="1c940-122">C# 7</span></span> |

## <a name="methods"></a><span data-ttu-id="1c940-123">メソッド</span><span class="sxs-lookup"><span data-stu-id="1c940-123">Methods</span></span>

<span data-ttu-id="1c940-124">式形式のメソッドは、型がメソッドの戻り値の型と一致する値を返す単一の式、または、`void` を返すメソッドの場合は何らかの処理を実行する単一の式で構成されます。</span><span class="sxs-lookup"><span data-stu-id="1c940-124">An expression-bodied method consists of a single expression that returns a value whose type matches the method's return type, or, for methods that return `void`, that performs some operation.</span></span> <span data-ttu-id="1c940-125">たとえば、一般的に、<xref:System.Object.ToString%2A> メソッドをオーバーライドする型には、現在のオブジェクトの文字列形式を返す単一の式が含まれています。</span><span class="sxs-lookup"><span data-stu-id="1c940-125">For example, types that override the <xref:System.Object.ToString%2A> method typically include a single expression that returns the string representation of the current object.</span></span> 

<span data-ttu-id="1c940-126">次の例では、式本体の定義を使用して <xref:System.Object.ToString%2A> メソッドをオーバーライドする `Person` クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="1c940-126">The following example defines a `Person` class that overrides the <xref:System.Object.ToString%2A> method with an expression body definition.</span></span> <span data-ttu-id="1c940-127">また、名前をコンソールに表示する `Show` メソッドも定義します。</span><span class="sxs-lookup"><span data-stu-id="1c940-127">It also defines a `Show` method that displays a name to the console.</span></span> <span data-ttu-id="1c940-128">`ToString` 式本体の定義に `return` キーワードが使用されていない点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="1c940-128">Note that the `return` keyword is not used in the `ToString` expression body definition.</span></span>

<span data-ttu-id="1c940-129">[!code-cs[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]</span><span class="sxs-lookup"><span data-stu-id="1c940-129">[!code-cs[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]</span></span>  

<span data-ttu-id="1c940-130">詳細については、「[メソッド (C# プログラミング ガイド)](../classes-and-structs/methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c940-130">For more information, see [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span></span>
 
## <a name="constructors"></a><span data-ttu-id="1c940-131">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="1c940-131">Constructors</span></span>

<span data-ttu-id="1c940-132">一般的に、コンストラクターの式本体の定義は、コンストラクターの引数を処理したり、インスタンスの状態を初期化したりする単一の代入式またはメソッド呼び出しから構成されます。</span><span class="sxs-lookup"><span data-stu-id="1c940-132">An expression body definition for a constructor typically consists of a single assignment expression or a method call that handles the constructor's arguments or initializes instance state.</span></span> 

<span data-ttu-id="1c940-133">次の例では、コンストラクターに *name* という名前の文字列パラメーターが 1 つある `Location` クラスが定義されています。</span><span class="sxs-lookup"><span data-stu-id="1c940-133">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="1c940-134">式の本体の定義により `Name` プロパティに引数が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="1c940-134">The expression body definition assigns the argument to the `Name` property.</span></span>

<span data-ttu-id="1c940-135">[!code-cs[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="1c940-135">[!code-cs[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]</span></span>  

<span data-ttu-id="1c940-136">詳細については、「[コンストラクター (C# プログラミング ガイド)](../classes-and-structs/constructors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c940-136">For more information, see [Constructors (C# Programming Guide)](../classes-and-structs/constructors.md).</span></span>

## <a name="finalizers"></a><span data-ttu-id="1c940-137">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="1c940-137">Finalizers</span></span>

<span data-ttu-id="1c940-138">一般的に、ファイナライザーの式本体の定義には、アンマネージ リソースをリリースするステートメントなどのクリーンアップ ステートメントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1c940-138">An expression body definition for a finalizer typically contains cleanup statements, such as statements that release unmanaged resources.</span></span>

<span data-ttu-id="1c940-139">次の例では、式本体の定義を使用して、ファイナライザーが呼び出されたことを示すファイナライザーを定義します。</span><span class="sxs-lookup"><span data-stu-id="1c940-139">The following example defines a finalizer that uses an expression body definition to indicate that the finalizer has been called.</span></span>

<span data-ttu-id="1c940-140">[!code-cs[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="1c940-140">[!code-cs[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]</span></span>  

<span data-ttu-id="1c940-141">詳細については、「[ファイナライザー (C# プログラミング ガイド)](../classes-and-structs/destructors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c940-141">For more information, see [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span></span>

## <a name="property-get-statements"></a><span data-ttu-id="1c940-142">プロパティの get ステートメント</span><span class="sxs-lookup"><span data-stu-id="1c940-142">Property get statements</span></span>

<span data-ttu-id="1c940-143">プロパティの get アクセサーを自分で実装する場合、プロパティの値を返すだけの単一の式に式本体の定義を使用できます。</span><span class="sxs-lookup"><span data-stu-id="1c940-143">If you choose to implement a property get accessor yourself, you can use an expression body definition for single expressions that simply return the property value.</span></span> <span data-ttu-id="1c940-144">`return` ステートメントは使用されません。</span><span class="sxs-lookup"><span data-stu-id="1c940-144">Note that the `return` statement isn't used.</span></span>

<span data-ttu-id="1c940-145">次の例では、`Location.Name` プロパティを定義します。このプロパティの get アクセサーは、プロパティをバックするプライベート `locationName` フィールドの値を返します。</span><span class="sxs-lookup"><span data-stu-id="1c940-145">The following example defines a `Location.Name` property whose property get accessor returns the value of the private `locationName` field that backs the property.</span></span> 

<span data-ttu-id="1c940-146">[!code-cs[expression-bodied-property-getter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="1c940-146">[!code-cs[expression-bodied-property-getter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]</span></span>  

<span data-ttu-id="1c940-147">式本体の定義を使用する読み取り専用のプロパティは、明示的な `set` ステートメントなしで実装できます。</span><span class="sxs-lookup"><span data-stu-id="1c940-147">Read-only properties that use an expression body definition can be implemented without an explicit `set` statement.</span></span> <span data-ttu-id="1c940-148">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1c940-148">The syntax is:</span></span>

```csharp
PropertyName => returnValue;
```

<span data-ttu-id="1c940-149">次の例では、プライベート `locationName` フィールドの値を返す式本体の定義として読み取り専用の `Name` プロパティを実装する `Location` クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="1c940-149">The following example defines a `Location` class whose read-only `Name` property is implemented as an expression body definition that returns the value of the private `locationName` field.</span></span>

<span data-ttu-id="1c940-150">[!code-cs[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="1c940-150">[!code-cs[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]</span></span>  

<span data-ttu-id="1c940-151">詳細については、「[プロパティ (C# プログラミング ガイド)](../classes-and-structs/properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c940-151">For more information, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="property-set-statements"></a><span data-ttu-id="1c940-152">プロパティの set ステートメント</span><span class="sxs-lookup"><span data-stu-id="1c940-152">Property set statements</span></span>

<span data-ttu-id="1c940-153">プロパティの set アクセサーを自分で実装する場合、プロパティをバックするフィールドに値を代入する単一行の式に式本体の定義を使用できます。</span><span class="sxs-lookup"><span data-stu-id="1c940-153">If you choose to implement a property set accessor yourself, you can use an expression body definition for a single-line expression that assigns a value to the field that backs the property.</span></span>

<span data-ttu-id="1c940-154">次の例では、`Location.Name` プロパティを定義します。このプロパティの set ステートメントで、プロパティをバックするプライベート `locationName` フィールドにその入力引数を代入します。</span><span class="sxs-lookup"><span data-stu-id="1c940-154">The following example defines a `Location.Name` property whose property set statement assigns its input argument to the private `locationName` field that backs the property.</span></span>

<span data-ttu-id="1c940-155">[!code-cs[expression-bodied-property-setter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="1c940-155">[!code-cs[expression-bodied-property-setter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]</span></span>  

<span data-ttu-id="1c940-156">詳細については、「[プロパティ (C# プログラミング ガイド)](../classes-and-structs/properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c940-156">For more information, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="indexers"></a><span data-ttu-id="1c940-157">インデクサー</span><span class="sxs-lookup"><span data-stu-id="1c940-157">Indexers</span></span>

<span data-ttu-id="1c940-158">プロパティと同様に、get アクセサーが値を返す単一のステートメントで構成される場合、または set アクセサーが単純な代入を実行する場合、インデクサーの get と set アクセサーは、式本体の定義で構成されます。</span><span class="sxs-lookup"><span data-stu-id="1c940-158">Like properties, an indexer's get and set accessors consist of expression body definitions if the get accessor consists of a single statement that returns a value or the set accessor performs a simple assignment.</span></span>

<span data-ttu-id="1c940-159">次の例では、`Sports` というクラスを定義します。このクラスには、複数のスポーツ名を含む内部 <xref:System.String> 配列があります。</span><span class="sxs-lookup"><span data-stu-id="1c940-159">The following example defines a class named `Sports` that includes an internal <xref:System.String> array that contains the names of a number of sports.</span></span> <span data-ttu-id="1c940-160">インデクサーの get および set アクセサーはいずれも、式本体の定義として実装されます。</span><span class="sxs-lookup"><span data-stu-id="1c940-160">Both the indexer's get and set accessors are implemented as expression body definitions.</span></span>

<span data-ttu-id="1c940-161">[!code-cs[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="1c940-161">[!code-cs[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]</span></span> 

<span data-ttu-id="1c940-162">詳細については、「[インデクサー (C# プログラミング ガイド)](../indexers/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c940-162">For more information, see [Indexers (C# Programming Guide)](../indexers/index.md).</span></span>


