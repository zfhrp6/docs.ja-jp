---
title: "using static ディレクティブ (C# リファレンス)"
ms.date: 03/10/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5838bede475cf2ad1b72518770241e86206a06bb
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="using-static-directive-c-reference"></a><span data-ttu-id="a77d4-102">using static ディレクティブ (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="a77d4-102">using static Directive (C# Reference)</span></span>

<span data-ttu-id="a77d4-103">`using static` ディレクティブは、型名を指定せずにアクセスできる静的メンバーの型を指定します。</span><span class="sxs-lookup"><span data-stu-id="a77d4-103">The `using static` directive designates a type whose static members you can access without specifying a type name.</span></span> <span data-ttu-id="a77d4-104">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a77d4-104">Its syntax is:</span></span>

```csharp
using static <fully-qualified-type-name>
```

<span data-ttu-id="a77d4-105">*fully-qualified-type-name* は、型名を指定せずに参照できる静的メンバーの型の名前です。</span><span class="sxs-lookup"><span data-stu-id="a77d4-105">where *fully-qualified-type-name* is the name of the type whose static members can be referenced without specifying a type name.</span></span> <span data-ttu-id="a77d4-106">完全修飾型名 (完全な名前空間名と型名) を指定しないと、C# によってコンパイラ エラー CS0246 "型または名前空間の名前 '<type-name>' が見つかりませんでした" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a77d4-106">If you do not provide a fully qualified type name (the full namespace name along with the type name), C# generates compiler error CS0246: "The type or namespace name '<type-name>' could not be found."</span></span>

<span data-ttu-id="a77d4-107">`using static` ディレクティブは、インスタンス メンバーがある場合でも、静的メンバーがあるすべての型に適用されます。</span><span class="sxs-lookup"><span data-stu-id="a77d4-107">The `using static` directive applies to any type that has static members, even if it also has instance members.</span></span> <span data-ttu-id="a77d4-108">ただし、インスタンス メンバーは、型のインスタンスを通してのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="a77d4-108">However, instance members can only be invoked through the type instance.</span></span>

<span data-ttu-id="a77d4-109">`using static` ディレクティブは、C# 6 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="a77d4-109">The `using static` directive was introduced in C# 6.</span></span>

## <a name="remarks"></a><span data-ttu-id="a77d4-110">コメント</span><span class="sxs-lookup"><span data-stu-id="a77d4-110">Remarks</span></span>
 
<span data-ttu-id="a77d4-111">通常は、静的メンバーを呼び出すときに、型名とメンバー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="a77d4-111">Ordinarily, when you call a static member, you provide the type name along with the member name.</span></span> <span data-ttu-id="a77d4-112">同じ型名を繰り返し入力してその型のメンバーを呼び出すと、コードが冗長でわかりにくくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a77d4-112">Repeatedly entering the same type name to invoke members of the type can result in verbose, obscure code.</span></span> <span data-ttu-id="a77d4-113">たとえば、次の `Circle` クラスの定義は、<xref:System.Math> クラスのメンバー数を参照します。</span><span class="sxs-lookup"><span data-stu-id="a77d4-113">For example, the following definition of a `Circle` class references a number of members of the <xref:System.Math> class.</span></span>
  
[!code-csharp[using-static#1](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

<span data-ttu-id="a77d4-114">メンバーが参照されるたびに <xref:System.Math> クラスを明示的に参照する必要がなくなれば、`using static` ディレクティブによって生成されるコードがより簡潔になります。</span><span class="sxs-lookup"><span data-stu-id="a77d4-114">By eliminating the need to explicitly reference the <xref:System.Math> class each time a member is referenced, the `using static` directive produces much cleaner code:</span></span>

[!code-csharp[using-static#2](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

<span data-ttu-id="a77d4-115">`using static` は、指定した型で宣言されているアクセス可能な静的メンバーおよび入れ子になった型のみをインポートします。</span><span class="sxs-lookup"><span data-stu-id="a77d4-115">`using static` imports only accessible static members and nested types declared in the specified type.</span></span>  <span data-ttu-id="a77d4-116">継承されたメンバーはインポートされません。</span><span class="sxs-lookup"><span data-stu-id="a77d4-116">Inherited members are not imported.</span></span>  <span data-ttu-id="a77d4-117">using static ディレクティブを使用して、Visual Basic モジュールを含む、名前付きの型からインポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="a77d4-117">You can import from any named type with a using static directive, including Visual Basic modules.</span></span>  <span data-ttu-id="a77d4-118">F# の最上位の関数が、有効な C# 識別子を名前に持つ名前付きの型の静的メンバーとしてメタデータに存在する場合は、その F# 関数をインポートできます。</span><span class="sxs-lookup"><span data-stu-id="a77d4-118">If F# top-level functions appear in metadata as static members of a named type whose name is a valid C# identifier, then the F# functions can be imported.</span></span>  
  
 <span data-ttu-id="a77d4-119">`using static` を使用すると、指定した型で宣言された拡張メソッドを拡張メソッドの参照で使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a77d4-119">`using static` makes extension methods declared in the specified type available for extension method lookup.</span></span>  <span data-ttu-id="a77d4-120">ただし、コード内で修飾なしで参照している場合は、拡張メソッドの名前はスコープにインポートされません。</span><span class="sxs-lookup"><span data-stu-id="a77d4-120">However, the names of the extension methods are not imported into scope for unqualified reference in code.</span></span>  
  
 <span data-ttu-id="a77d4-121">同じコンパイル単位または名前空間の多様な `using static` ディレクティブによってさまざまな型からインポートされた同じ名前を持つメソッドが、メソッド グループを形成します。</span><span class="sxs-lookup"><span data-stu-id="a77d4-121">Methods with the same name imported from different types by different `using static` directives in the same compilation unit or namespace form a method group.</span></span>  <span data-ttu-id="a77d4-122">これらのメソッド グループ内のオーバーロードの解決方法は、C# の通常の規則に従います。</span><span class="sxs-lookup"><span data-stu-id="a77d4-122">Overload resolution within these method groups follows normal C# rules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a77d4-123">例</span><span class="sxs-lookup"><span data-stu-id="a77d4-123">Example</span></span>

<span data-ttu-id="a77d4-124">次の例では、`using static` ディレクティブを使用して、<xref:System.Console> クラス、<xref:System.Math> クラス、および <xref:System.String> クラスの静的メンバーを、型名を指定せずに使用できるようにしています。</span><span class="sxs-lookup"><span data-stu-id="a77d4-124">The following example uses the `using static` directive to make the static members of the <xref:System.Console>, <xref:System.Math>, and <xref:System.String> classes available without having to specify their type name.</span></span>

[!code-csharp[using-static#3](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

<span data-ttu-id="a77d4-125">上の例では、`using static` ディレクティブを <xref:System.Double> 型に適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="a77d4-125">In the example, the `using static` directive could also have been applied to the <xref:System.Double> type.</span></span> <span data-ttu-id="a77d4-126">これは必要を呼び出すこと、<xref:System.Double.TryParse(System.String,System.Double@)>型名を指定せずメソッドです。</span><span class="sxs-lookup"><span data-stu-id="a77d4-126">This would have made it possible to call the <xref:System.Double.TryParse(System.String,System.Double@)> method without specifying a type name.</span></span> <span data-ttu-id="a77d4-127">ただし、どの数値型の `TryParse` メソッドが呼び出されたかを判断するために `using static` ステートメントを確認する必要が出てくるため、コードが読みにくくなります。</span><span class="sxs-lookup"><span data-stu-id="a77d4-127">However, this creates less readable code, since it becomes necessary to check the `using static` statements to determine which numeric type's `TryParse` method is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="a77d4-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="a77d4-128">See also</span></span>

<span data-ttu-id="a77d4-129">[using ディレクティブ](using-directive.md) </span><span class="sxs-lookup"><span data-stu-id="a77d4-129">[using directive](using-directive.md) </span></span>  
<span data-ttu-id="a77d4-130">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="a77d4-130">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="a77d4-131">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="a77d4-131">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="a77d4-132">[名前空間の使用](../../../csharp/programming-guide/namespaces/using-namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="a77d4-132">[Using Namespaces](../../../csharp/programming-guide/namespaces/using-namespaces.md) </span></span>  
<span data-ttu-id="a77d4-133">[名前空間キーワード](../../../csharp/language-reference/keywords/namespace-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="a77d4-133">[Namespace Keywords](../../../csharp/language-reference/keywords/namespace-keywords.md) </span></span>  
[<span data-ttu-id="a77d4-134">名前空間</span><span class="sxs-lookup"><span data-stu-id="a77d4-134">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)   
