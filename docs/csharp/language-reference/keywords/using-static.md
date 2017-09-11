---
title: "using static ディレクティブ (C# リファレンス)"
ms.date: 2017-03-10
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
author: rpetrusha
ms.author: ronpet
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
ms.openlocfilehash: b7d69d0262ba6f450e2cc0d5b30692bba181f9d9
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="using-static-directive-c-reference"></a><span data-ttu-id="1af30-102">using static ディレクティブ (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="1af30-102">using static Directive (C# Reference)</span></span>

<span data-ttu-id="1af30-103">`using static` ディレクティブは、型名を指定せずにアクセスできる静的メンバーの型を指定します。</span><span class="sxs-lookup"><span data-stu-id="1af30-103">The `using static` directive designates a type whose static members you can access without specifying a type name.</span></span> <span data-ttu-id="1af30-104">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1af30-104">Its syntax is:</span></span>

```csharp
using static <fully-qualified-type-name>
```

<span data-ttu-id="1af30-105">*fully-qualified-type-name* は、型名を指定せずに参照できる静的メンバーの型の名前です。</span><span class="sxs-lookup"><span data-stu-id="1af30-105">where *fully-qualified-type-name* is the name of the type whose static members can be referenced without specifying a type name.</span></span> <span data-ttu-id="1af30-106">完全修飾型名 (完全な名前空間名と型名) を指定しないと、C# によってコンパイラ エラー CS0246 "型または名前空間の名前 '<type-name>' が見つかりませんでした" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="1af30-106">If you do not provide a fully qualified type name (the full namespace name along with the type name), C# generates compiler error CS0246: "The type or namespace name '<type-name>' could not be found."</span></span>

<span data-ttu-id="1af30-107">`using static` ディレクティブは、インスタンス メンバーがある場合でも、静的メンバーがあるすべての型に適用されます。</span><span class="sxs-lookup"><span data-stu-id="1af30-107">The `using static` directive applies to any type that has static members, even if it also has instance members.</span></span> <span data-ttu-id="1af30-108">ただし、インスタンス メンバーは、型のインスタンスを通してのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="1af30-108">However, instance members can only be invoked through the type instance.</span></span>

<span data-ttu-id="1af30-109">`using static` ディレクティブは、C# 6 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="1af30-109">The `using static` directive was introduced in C# 6.</span></span>

## <a name="remarks"></a><span data-ttu-id="1af30-110">コメント</span><span class="sxs-lookup"><span data-stu-id="1af30-110">Remarks</span></span>
 
<span data-ttu-id="1af30-111">通常は、静的メンバーを呼び出すときに、型名とメンバー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="1af30-111">Ordinarily, when you call a static member, you provide the type name along with the member name.</span></span> <span data-ttu-id="1af30-112">同じ型名を繰り返し入力してその型のメンバーを呼び出すと、コードが冗長でわかりにくくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1af30-112">Repeatedly entering the same type name to invoke members of the type can result in verbose, obscure code.</span></span> <span data-ttu-id="1af30-113">たとえば、次の `Circle` クラスの定義は、@System.Math クラスのメンバー数を参照します。</span><span class="sxs-lookup"><span data-stu-id="1af30-113">For example, the following definition of a `Circle` class references a number of members of the @System.Math class.</span></span>
  
<span data-ttu-id="1af30-114">[!code-cs[using-static#1](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="1af30-114">[!code-cs[using-static#1](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]</span></span>

<span data-ttu-id="1af30-115">メンバーが参照されるたびに @System.Math クラスを明示的に参照する必要がなくなれば、`using static` ディレクティブによって生成されるコードがより簡潔になります。</span><span class="sxs-lookup"><span data-stu-id="1af30-115">By eliminating the need to explicitly reference the @System.Math class each time a member is referenced, the `using static` directive produces much cleaner code:</span></span>

<span data-ttu-id="1af30-116">[!code-cs[using-static#2](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="1af30-116">[!code-cs[using-static#2](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]</span></span>

<span data-ttu-id="1af30-117">`using static` は、指定した型で宣言されているアクセス可能な静的メンバーおよび入れ子になった型のみをインポートします。</span><span class="sxs-lookup"><span data-stu-id="1af30-117">`using static` imports only accessible static members and nested types declared in the specified type.</span></span>  <span data-ttu-id="1af30-118">継承されたメンバーはインポートされません。</span><span class="sxs-lookup"><span data-stu-id="1af30-118">Inherited members are not imported.</span></span>  <span data-ttu-id="1af30-119">using static ディレクティブを使用して、Visual Basic モジュールを含む、名前付きの型からインポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="1af30-119">You can import from any named type with a using static directive, including Visual Basic modules.</span></span>  <span data-ttu-id="1af30-120">F# の最上位の関数が、有効な C# 識別子を名前に持つ名前付きの型の静的メンバーとしてメタデータに存在する場合は、その F# 関数をインポートできます。</span><span class="sxs-lookup"><span data-stu-id="1af30-120">If F# top-level functions appear in metadata as static members of a named type whose name is a valid C# identifier, then the F# functions can be imported.</span></span>  
  
 <span data-ttu-id="1af30-121">`using static` を使用すると、指定した型で宣言された拡張メソッドを拡張メソッドの参照で使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1af30-121">`using static` makes extension methods declared in the specified type available for extension method lookup.</span></span>  <span data-ttu-id="1af30-122">ただし、コード内で修飾なしで参照している場合は、拡張メソッドの名前はスコープにインポートされません。</span><span class="sxs-lookup"><span data-stu-id="1af30-122">However, the names of the extension methods are not imported into scope for unqualified reference in code.</span></span>  
  
 <span data-ttu-id="1af30-123">同じコンパイル単位または名前空間の多様な `using static` ディレクティブによってさまざまな型からインポートされた同じ名前を持つメソッドが、メソッド グループを形成します。</span><span class="sxs-lookup"><span data-stu-id="1af30-123">Methods with the same name imported from different types by different `using static` directives in the same compilation unit or namespace form a method group.</span></span>  <span data-ttu-id="1af30-124">これらのメソッド グループ内のオーバーロードの解決方法は、C# の通常の規則に従います。</span><span class="sxs-lookup"><span data-stu-id="1af30-124">Overload resolution within these method groups follows normal C# rules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1af30-125">例</span><span class="sxs-lookup"><span data-stu-id="1af30-125">Example</span></span>

<span data-ttu-id="1af30-126">次の例では、`using static` ディレクティブを使用して、@System.Console クラス、@System.Math クラス、および @System.String クラスの静的メンバーを、型名を指定せずに使用できるようにしています。</span><span class="sxs-lookup"><span data-stu-id="1af30-126">The following example uses the `using static` directive to make the static members of the @System.Console, @System.Math, and @System.String classes available without having to specify their type name.</span></span>

<span data-ttu-id="1af30-127">[!code-cs[using-static#3](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]</span><span class="sxs-lookup"><span data-stu-id="1af30-127">[!code-cs[using-static#3](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]</span></span>

<span data-ttu-id="1af30-128">上の例では、`using static` ディレクティブを @System.Double 型に適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="1af30-128">In the example, the `using static` directive could also have been applied to the @System.Double type.</span></span> <span data-ttu-id="1af30-129">それにより、型名を指定せずに、@System.Double.TryParse 型 (System.String,System.Double@) メソッドを呼び出せるようになります。</span><span class="sxs-lookup"><span data-stu-id="1af30-129">This would have made it possible to call the @System.Double.TryParse(System.String,System.Double@) method without specifying a type name.</span></span> <span data-ttu-id="1af30-130">ただし、どの数値型の `TryParse` メソッドが呼び出されたかを判断するために `using static` ステートメントを確認する必要が出てくるため、コードが読みにくくなります。</span><span class="sxs-lookup"><span data-stu-id="1af30-130">However, this creates less readable code, since it becomes necessary to check the `using static` statements to determine which numeric type's `TryParse` method is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="1af30-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="1af30-131">See also</span></span>

<span data-ttu-id="1af30-132">[using ディレクティブ](using-directive.md) </span><span class="sxs-lookup"><span data-stu-id="1af30-132">[using directive](using-directive.md) </span></span>  
<span data-ttu-id="1af30-133">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="1af30-133">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="1af30-134">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="1af30-134">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="1af30-135">[名前空間の使用](../../../csharp/programming-guide/namespaces/using-namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="1af30-135">[Using Namespaces](../../../csharp/programming-guide/namespaces/using-namespaces.md) </span></span>  
<span data-ttu-id="1af30-136">[名前空間キーワード](../../../csharp/language-reference/keywords/namespace-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="1af30-136">[Namespace Keywords](../../../csharp/language-reference/keywords/namespace-keywords.md) </span></span>  
[<span data-ttu-id="1af30-137">名前空間</span><span class="sxs-lookup"><span data-stu-id="1af30-137">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)   

