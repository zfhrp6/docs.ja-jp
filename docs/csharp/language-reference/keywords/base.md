---
title: base (C# リファレンス)
description: C# で派生クラス内から基底クラスのメンバーにアクセスするために使用する base キーワードについて説明します。
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: 69885ba0b2d05c79f2b7ba9458e7ba8c8b7aa0c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="base-c-reference"></a><span data-ttu-id="9e412-103">base (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="9e412-103">base (C# Reference)</span></span>

<span data-ttu-id="9e412-104">`base` キーワードは、派生クラス内から基底クラスのメンバーにアクセスするために使います。</span><span class="sxs-lookup"><span data-stu-id="9e412-104">The `base` keyword is used to access members of the base class from within a derived class:</span></span>

- <span data-ttu-id="9e412-105">別のメソッドによってオーバーライドされた基底クラスのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9e412-105">Call a method on the base class that has been overridden by another method.</span></span>

- <span data-ttu-id="9e412-106">派生クラスのインスタンスを作成するときに基底クラスのどのコンストラクターを呼び出す必要があるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="9e412-106">Specify which base-class constructor should be called when creating instances of the derived class.</span></span>

<span data-ttu-id="9e412-107">基底クラスへのアクセスは、コンストラクター、インスタンス メソッド、またはインスタンスのプロパティ アクセサーにおいてのみ許可されます。</span><span class="sxs-lookup"><span data-stu-id="9e412-107">A base class access is permitted only in a constructor, an instance method, or an instance property accessor.</span></span>

<span data-ttu-id="9e412-108">静的メソッド内から `base` キーワードを使うとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="9e412-108">It is an error to use the `base` keyword from within a static method.</span></span>

<span data-ttu-id="9e412-109">アクセスされる基底クラスは、クラス宣言で指定されている基底クラスです。</span><span class="sxs-lookup"><span data-stu-id="9e412-109">The base class that is accessed is the base class specified in the class declaration.</span></span> <span data-ttu-id="9e412-110">たとえば、`class ClassB : ClassA` と指定すると、ClassA の基底クラスに関係なく、ClassA のメンバーが ClassB からアクセスされます。</span><span class="sxs-lookup"><span data-stu-id="9e412-110">For example, if you specify `class ClassB : ClassA`, the members of ClassA are accessed from ClassB, regardless of the base class of ClassA.</span></span>

## <a name="example"></a><span data-ttu-id="9e412-111">例</span><span class="sxs-lookup"><span data-stu-id="9e412-111">Example</span></span>
<span data-ttu-id="9e412-112">この例では、基底クラス `Person` と派生クラス `Employee` の両方に、`Getinfo` という名前のメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="9e412-112">In this example, both the base class, `Person`, and the derived class, `Employee`, have a method named `Getinfo`.</span></span> <span data-ttu-id="9e412-113">`base` キーワードを使うことで、派生クラス内から基底クラスの `Getinfo` メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="9e412-113">By using the `base` keyword, it is possible to call the `Getinfo` method on the base class, from within the derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_1.cs)]

<span data-ttu-id="9e412-114">その他の例については、「[new](../../../csharp/language-reference/keywords/new.md)」、「[virtual](../../../csharp/language-reference/keywords/virtual.md)」、「[override](../../../csharp/language-reference/keywords/override.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9e412-114">For additional examples, see [new](../../../csharp/language-reference/keywords/new.md), [virtual](../../../csharp/language-reference/keywords/virtual.md), and [override](../../../csharp/language-reference/keywords/override.md).</span></span>

## <a name="example"></a><span data-ttu-id="9e412-115">例</span><span class="sxs-lookup"><span data-stu-id="9e412-115">Example</span></span>
<span data-ttu-id="9e412-116">この例では、派生クラスのインスタンスを作成するときに呼び出される基底クラスのコンストラクターを指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9e412-116">This example shows how to specify the base-class constructor called when creating instances of a derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_2.cs)]

## <a name="c-language-specification"></a><span data-ttu-id="9e412-117">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="9e412-117">C# language specification</span></span>
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="9e412-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e412-118">See also</span></span>
 [<span data-ttu-id="9e412-119">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="9e412-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9e412-120">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="9e412-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9e412-121">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="9e412-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="9e412-122">this</span><span class="sxs-lookup"><span data-stu-id="9e412-122">this</span></span>](../../../csharp/language-reference/keywords/this.md)