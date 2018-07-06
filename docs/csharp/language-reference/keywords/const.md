---
title: const キーワード (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: 985ba9cfefce458fac73aa4b92de0b3d438405c6
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948343"
---
# <a name="const-c-reference"></a><span data-ttu-id="566bf-102">const (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="566bf-102">const (C# Reference)</span></span>

<span data-ttu-id="566bf-103">定数フィールドまたはローカル定数を宣言するには、`const` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="566bf-103">You use the `const` keyword to declare a constant field or a constant local.</span></span> <span data-ttu-id="566bf-104">定数フィールドとローカルは変数でないため、変更できません。</span><span class="sxs-lookup"><span data-stu-id="566bf-104">Constant fields and locals aren't variables and may not be modified.</span></span> <span data-ttu-id="566bf-105">定数には、数字、ブール値、文字列、または null 参照が含まれます。</span><span class="sxs-lookup"><span data-stu-id="566bf-105">Constants can be numbers, Boolean values, strings, or a null reference.</span></span> <span data-ttu-id="566bf-106">いずれかの時点で変わることが予想される情報を表すために定数を作成してはなりません。</span><span class="sxs-lookup"><span data-stu-id="566bf-106">Don’t create a constant to represent information that you expect to change at any time.</span></span> <span data-ttu-id="566bf-107">たとえば、サービスの価格、製品バージョン番号、会社のブランド名などを格納するためには定数フィールドを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="566bf-107">For example, don’t use a constant field to store the price of a service, a product version number, or the brand name of a company.</span></span> <span data-ttu-id="566bf-108">これらの値は時間の経過とともに変更される場合があります。コンパイラは定数を伝達するため、ライブラリでコンパイルされた他のコードを再コンパイルして、変更点を反映することが必要になってしまいます。</span><span class="sxs-lookup"><span data-stu-id="566bf-108">These values can change over time, and because compilers propagate constants, other code compiled with your libraries will have to be recompiled to see the changes.</span></span> <span data-ttu-id="566bf-109">[readonly](../../../csharp/language-reference/keywords/readonly.md) キーワードも参照してください。</span><span class="sxs-lookup"><span data-stu-id="566bf-109">See also the [readonly](../../../csharp/language-reference/keywords/readonly.md) keyword.</span></span> <span data-ttu-id="566bf-110">例:</span><span class="sxs-lookup"><span data-stu-id="566bf-110">For example:</span></span>

```csharp
const int x = 0;
public const double gravitationalConstant = 6.673e-11;
private const string productName = "Visual C#";
```

## <a name="remarks"></a><span data-ttu-id="566bf-111">コメント</span><span class="sxs-lookup"><span data-stu-id="566bf-111">Remarks</span></span>

<span data-ttu-id="566bf-112">定数宣言の型は、宣言で導入されるメンバーの型を指定します。</span><span class="sxs-lookup"><span data-stu-id="566bf-112">The type of a constant declaration specifies the type of the members that the declaration introduces.</span></span> <span data-ttu-id="566bf-113">ローカル定数または定数フィールドの初期化子は、ターゲット型に暗黙に変換できる定数式であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="566bf-113">The initializer of a constant local or a constant field must be a constant expression that can be implicitly converted to the target type.</span></span>

<span data-ttu-id="566bf-114">定数式は、コンパイル時にすべて評価されます。</span><span class="sxs-lookup"><span data-stu-id="566bf-114">A constant expression is an expression that can be fully evaluated at compile time.</span></span> <span data-ttu-id="566bf-115">このため、参照型の定数になりうる値は、`string` と null 参照に限られます。</span><span class="sxs-lookup"><span data-stu-id="566bf-115">Therefore, the only possible values for constants of reference types are `string` and a null reference.</span></span>

<span data-ttu-id="566bf-116">定数宣言は、複数の定数を宣言できます。たとえば、次のように宣言できます。</span><span class="sxs-lookup"><span data-stu-id="566bf-116">The constant declaration can declare multiple constants, such as:</span></span>

```csharp
public const double x = 1.0, y = 2.0, z = 3.0;
```

<span data-ttu-id="566bf-117">`static` 修飾子は、定数宣言では使用できません。</span><span class="sxs-lookup"><span data-stu-id="566bf-117">The `static` modifier is not allowed in a constant declaration.</span></span>

<span data-ttu-id="566bf-118">定数は、次に示すように、定数式の一部になることができます。</span><span class="sxs-lookup"><span data-stu-id="566bf-118">A constant can participate in a constant expression, as follows:</span></span>

```csharp
public const int c1 = 5;
public const int c2 = c1 + 100;
```

> [!NOTE]
> <span data-ttu-id="566bf-119">[readonly](../../../csharp/language-reference/keywords/readonly.md) キーワードは、`const` キーワードとは異なります。</span><span class="sxs-lookup"><span data-stu-id="566bf-119">The [readonly](../../../csharp/language-reference/keywords/readonly.md) keyword differs from the `const` keyword.</span></span> <span data-ttu-id="566bf-120">`const` フィールドは、フィールドの宣言でしか初期化できません。</span><span class="sxs-lookup"><span data-stu-id="566bf-120">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="566bf-121">`readonly` フィールドは、宣言またはコンストラクターのどちらかで初期化できます。</span><span class="sxs-lookup"><span data-stu-id="566bf-121">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="566bf-122">このため、`readonly` フィールドは、使用するコンストラクターに応じて異なる値を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="566bf-122">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="566bf-123">また、`const` フィールドがコンパイル時定数であるのに対し、`readonly` フィールドは実行時定数として使用できます。たとえば、`public static readonly uint l1 = (uint)DateTime.Now.Ticks;` のように使用します。</span><span class="sxs-lookup"><span data-stu-id="566bf-123">Also, although a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants, as in this line: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span></span>

## <a name="example"></a><span data-ttu-id="566bf-124">例</span><span class="sxs-lookup"><span data-stu-id="566bf-124">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#5)]

## <a name="example"></a><span data-ttu-id="566bf-125">例</span><span class="sxs-lookup"><span data-stu-id="566bf-125">Example</span></span>

<span data-ttu-id="566bf-126">この例では、定数をローカル変数として使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="566bf-126">This example demonstrates how to use constants as local variables.</span></span>

[!code-csharp[csrefKeywordsModifiers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="566bf-127">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="566bf-127">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="566bf-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="566bf-128">See also</span></span>

[<span data-ttu-id="566bf-129">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="566bf-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
[<span data-ttu-id="566bf-130">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="566bf-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="566bf-131">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="566bf-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
[<span data-ttu-id="566bf-132">修飾子</span><span class="sxs-lookup"><span data-stu-id="566bf-132">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
[<span data-ttu-id="566bf-133">readonly</span><span class="sxs-lookup"><span data-stu-id="566bf-133">readonly</span></span>](../../../csharp/language-reference/keywords/readonly.md)
