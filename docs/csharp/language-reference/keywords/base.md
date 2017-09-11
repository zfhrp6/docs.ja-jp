---
title: "base (C# リファレンス)"
description: "C# で派生クラス内から基底クラスのメンバーにアクセスするために使用する base キーワードについて説明します。"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
caps.latest.revision: 14
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
ms.sourcegitcommit: 867f9eb286fa7ff5ef3e9167c1ab944c81161216
ms.openlocfilehash: b3a389d92373b6ba5995a7644b0440f9d8fad9ac
ms.contentlocale: ja-jp
ms.lasthandoff: 08/17/2017

---
# <a name="base-c-reference"></a><span data-ttu-id="de413-103">base (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="de413-103">base (C# Reference)</span></span>

<span data-ttu-id="de413-104">`base` キーワードは、派生クラス内から基底クラスのメンバーにアクセスするために使います。</span><span class="sxs-lookup"><span data-stu-id="de413-104">The `base` keyword is used to access members of the base class from within a derived class:</span></span>

- <span data-ttu-id="de413-105">別のメソッドによってオーバーライドされた基底クラスのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="de413-105">Call a method on the base class that has been overridden by another method.</span></span>

- <span data-ttu-id="de413-106">派生クラスのインスタンスを作成するときに基底クラスのどのコンストラクターを呼び出す必要があるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="de413-106">Specify which base-class constructor should be called when creating instances of the derived class.</span></span>

<span data-ttu-id="de413-107">基底クラスへのアクセスは、コンストラクター、インスタンス メソッド、またはインスタンスのプロパティ アクセサーにおいてのみ許可されます。</span><span class="sxs-lookup"><span data-stu-id="de413-107">A base class access is permitted only in a constructor, an instance method, or an instance property accessor.</span></span>

<span data-ttu-id="de413-108">静的メソッド内から `base` キーワードを使うとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="de413-108">It is an error to use the `base` keyword from within a static method.</span></span>

<span data-ttu-id="de413-109">アクセスされる基底クラスは、クラス宣言で指定されている基底クラスです。</span><span class="sxs-lookup"><span data-stu-id="de413-109">The base class that is accessed is the base class specified in the class declaration.</span></span> <span data-ttu-id="de413-110">たとえば、`class ClassB : ClassA` と指定すると、ClassA の基底クラスに関係なく、ClassA のメンバーが ClassB からアクセスされます。</span><span class="sxs-lookup"><span data-stu-id="de413-110">For example, if you specify `class ClassB : ClassA`, the members of ClassA are accessed from ClassB, regardless of the base class of ClassA.</span></span>

## <a name="example"></a><span data-ttu-id="de413-111">例</span><span class="sxs-lookup"><span data-stu-id="de413-111">Example</span></span>
<span data-ttu-id="de413-112">この例では、基底クラス `Person` と派生クラス `Employee` の両方に、`Getinfo` という名前のメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="de413-112">In this example, both the base class, `Person`, and the derived class, `Employee`, have a method named `Getinfo`.</span></span> <span data-ttu-id="de413-113">`base` キーワードを使うことで、派生クラス内から基底クラスの `Getinfo` メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="de413-113">By using the `base` keyword, it is possible to call the `Getinfo` method on the base class, from within the derived class.</span></span>

<span data-ttu-id="de413-114">[!code-cs[csrefKeywordsAccess#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="de413-114">[!code-cs[csrefKeywordsAccess#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_1.cs)]</span></span>

<span data-ttu-id="de413-115">その他の例については、「[new](../../../csharp/language-reference/keywords/new.md)」、「[virtual](../../../csharp/language-reference/keywords/virtual.md)」、「[override](../../../csharp/language-reference/keywords/override.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="de413-115">For additional examples, see [new](../../../csharp/language-reference/keywords/new.md), [virtual](../../../csharp/language-reference/keywords/virtual.md), and [override](../../../csharp/language-reference/keywords/override.md).</span></span>

## <a name="example"></a><span data-ttu-id="de413-116">例</span><span class="sxs-lookup"><span data-stu-id="de413-116">Example</span></span>
<span data-ttu-id="de413-117">この例では、派生クラスのインスタンスを作成するときに呼び出される基底クラスのコンストラクターを指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="de413-117">This example shows how to specify the base-class constructor called when creating instances of a derived class.</span></span>

<span data-ttu-id="de413-118">[!code-cs[csrefKeywordsAccess#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="de413-118">[!code-cs[csrefKeywordsAccess#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_2.cs)]</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="de413-119">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="de413-119">C# language specification</span></span>
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="de413-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="de413-120">See also</span></span>
 <span data-ttu-id="de413-121">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="de413-121">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="de413-122">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="de413-122">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="de413-123">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="de413-123">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 [<span data-ttu-id="de413-124">this</span><span class="sxs-lookup"><span data-stu-id="de413-124">this</span></span>](../../../csharp/language-reference/keywords/this.md)
