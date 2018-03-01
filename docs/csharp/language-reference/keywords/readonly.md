---
title: "readonly (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b499f9fc5121afe6c2e92bcf8c5d2ac593b4c06c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="readonly-c-reference"></a><span data-ttu-id="d373a-102">readonly (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="d373a-102">readonly (C# Reference)</span></span>
<span data-ttu-id="d373a-103">`readonly` キーワードは、フィールドで使用できる修飾子です。</span><span class="sxs-lookup"><span data-stu-id="d373a-103">The `readonly` keyword is a modifier that you can use on fields.</span></span> <span data-ttu-id="d373a-104">フィールド宣言に `readonly` 修飾子が含まれていると、その宣言によって導入されるフィールドへの割り当ては、宣言の一部分として、または同じクラスのコンストラクター内でのみ実行できます。</span><span class="sxs-lookup"><span data-stu-id="d373a-104">When a field declaration includes a `readonly` modifier, assignments to the fields introduced by the declaration can only occur as part of the declaration or in a constructor in the same class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d373a-105">例</span><span class="sxs-lookup"><span data-stu-id="d373a-105">Example</span></span>  
 <span data-ttu-id="d373a-106">この例では、`year` フィールドの値は、クラス コンストラクターで値が割り当てられていても `ChangeYear` メソッドでは変更できません。</span><span class="sxs-lookup"><span data-stu-id="d373a-106">In this example, the value of the field `year` cannot be changed in the method `ChangeYear`, even though it is assigned a value in the class constructor:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_1.cs)]  
  
 <span data-ttu-id="d373a-107">`readonly` のフィールドに値を割り当てることができるのは、次のコンテキスト内に限られます。</span><span class="sxs-lookup"><span data-stu-id="d373a-107">You can assign a value to a `readonly` field only in the following contexts:</span></span>  
  
-   <span data-ttu-id="d373a-108">値が宣言で初期化される場合。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d373a-108">When the variable is initialized in the declaration, for example:</span></span>  
  
    ```  
    public readonly int y = 5;  
    ```  
  
-   <span data-ttu-id="d373a-109">インスタンス フィールドの場合は、フィールド宣言が含まれるクラスのインスタンス コンストラクター内。静的フィールドの場合は、フィールド宣言が含まれるクラスの静的コンストラクター内。</span><span class="sxs-lookup"><span data-stu-id="d373a-109">For an instance field, in the instance constructors of the class that contains the field declaration, or for a static field, in the static constructor of the class that contains the field declaration.</span></span> <span data-ttu-id="d373a-110">また、こうしたコンテキスト内でのみ、`readonly` フィールドを [out](../../../csharp/language-reference/keywords/out.md) パラメーターまたは [ref](../../../csharp/language-reference/keywords/ref.md) パラメーターとして渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="d373a-110">These are also the only contexts in which it is valid to pass a `readonly` field as an [out](../../../csharp/language-reference/keywords/out.md) or [ref](../../../csharp/language-reference/keywords/ref.md) parameter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d373a-111">`readonly` キーワードは [const](../../../csharp/language-reference/keywords/const.md) キーワードとは異なります。</span><span class="sxs-lookup"><span data-stu-id="d373a-111">The `readonly` keyword is different from the [const](../../../csharp/language-reference/keywords/const.md) keyword.</span></span> <span data-ttu-id="d373a-112">`const` フィールドは、フィールドの宣言でしか初期化できません。</span><span class="sxs-lookup"><span data-stu-id="d373a-112">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="d373a-113">`readonly` フィールドは、宣言またはコンストラクターのどちらかで初期化できます。</span><span class="sxs-lookup"><span data-stu-id="d373a-113">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="d373a-114">このため、`readonly` フィールドは、使用するコンストラクターに応じて異なる値を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="d373a-114">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="d373a-115">また、次の例のように、`const` フィールドがコンパイル時定数であるのに対し、`readonly` フィールドは実行時定数として使用できます。</span><span class="sxs-lookup"><span data-stu-id="d373a-115">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for runtime constants as in the following example:</span></span>  
  
```  
public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;  
```  
  
## <a name="example"></a><span data-ttu-id="d373a-116">例</span><span class="sxs-lookup"><span data-stu-id="d373a-116">Example</span></span>  
 [!code-csharp[csrefKeywordsModifiers#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_2.cs)]  
  
 <span data-ttu-id="d373a-117">上の例で、次のようにステートメントを使用するとします。</span><span class="sxs-lookup"><span data-stu-id="d373a-117">In the preceding example, if you use a statement like this:</span></span>  
  
 `p2.y = 66;        // Error`  
  
 <span data-ttu-id="d373a-118">この場合、次のコンパイル エラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d373a-118">you will get the compiler error message:</span></span>  
  
 `The left-hand side of an assignment must be an l-value`  
  
 <span data-ttu-id="d373a-119">これは、定数に値を割り当てようとしたときのエラーと同じです。</span><span class="sxs-lookup"><span data-stu-id="d373a-119">which is the same error you get when you attempt to assign a value to a constant.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="d373a-120">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="d373a-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d373a-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="d373a-121">See Also</span></span>  
 [<span data-ttu-id="d373a-122">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="d373a-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d373a-123">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="d373a-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d373a-124">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="d373a-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="d373a-125">修飾子</span><span class="sxs-lookup"><span data-stu-id="d373a-125">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="d373a-126">const</span><span class="sxs-lookup"><span data-stu-id="d373a-126">const</span></span>](../../../csharp/language-reference/keywords/const.md)  
 [<span data-ttu-id="d373a-127">フィールド</span><span class="sxs-lookup"><span data-stu-id="d373a-127">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)
