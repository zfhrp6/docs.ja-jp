---
title: "volatile (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- volatile_CSharpKeyword
- volatile
dev_langs:
- CSharp
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
caps.latest.revision: 29
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
ms.openlocfilehash: c8f9fba15991197be885a973435089098a57db87
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="volatile-c-reference"></a><span data-ttu-id="c764f-102">volatile (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="c764f-102">volatile (C# Reference)</span></span>
<span data-ttu-id="c764f-103">`volatile` キーワードは、同時に実行されている複数のスレッドによって、フィールドが変更される可能性があることを示します。</span><span class="sxs-lookup"><span data-stu-id="c764f-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="c764f-104">`volatile` と宣言されているフィールドは、シングル スレッドによるアクセスを前提とする、コンパイラの最適化の対象にはなりません。</span><span class="sxs-lookup"><span data-stu-id="c764f-104">Fields that are declared `volatile` are not subject to compiler optimizations that assume access by a single thread.</span></span> <span data-ttu-id="c764f-105">このため、フィールドには常に最新の値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c764f-105">This ensures that the most up-to-date value is present in the field at all times.</span></span>  
  
 <span data-ttu-id="c764f-106">`volatile` 修飾子は、通常、アクセスをシリアル化する [lock](../../../csharp/language-reference/keywords/lock-statement.md) ステートメントが使用されない場合に、複数のスレッドからアクセスされるフィールドに対して使用します。</span><span class="sxs-lookup"><span data-stu-id="c764f-106">The `volatile` modifier is usually used for a field that is accessed by multiple threads without using the [lock](../../../csharp/language-reference/keywords/lock-statement.md) statement to serialize access.</span></span>  
  
 <span data-ttu-id="c764f-107">`volatile` キーワードは次の型のフィールドに使用できます。</span><span class="sxs-lookup"><span data-stu-id="c764f-107">The `volatile` keyword can be applied to fields of these types:</span></span>  
  
-   <span data-ttu-id="c764f-108">参照型。</span><span class="sxs-lookup"><span data-stu-id="c764f-108">Reference types.</span></span>  
  
-   <span data-ttu-id="c764f-109">ポインター型 (unsafe コンテキスト内)。</span><span class="sxs-lookup"><span data-stu-id="c764f-109">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="c764f-110">ポインター自体は volatile にできますが、ポインターが指しているオブジェクトは volatile にできません。</span><span class="sxs-lookup"><span data-stu-id="c764f-110">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="c764f-111">つまり、"volatile を指すポインター" は宣言できません。</span><span class="sxs-lookup"><span data-stu-id="c764f-111">In other words, you cannot declare a "pointer to volatile."</span></span>  
  
-   <span data-ttu-id="c764f-112">sbyte、byte、short、ushort、int、uint、char、float、bool などの型。</span><span class="sxs-lookup"><span data-stu-id="c764f-112">Types such as sbyte, byte, short, ushort, int, uint, char, float, and bool.</span></span>  
  
-   <span data-ttu-id="c764f-113">基本データ型 byte、sbyte、short、ushort、int、または uint のいずれかが含まれる列挙型。</span><span class="sxs-lookup"><span data-stu-id="c764f-113">An enum type with one of the following base types: byte, sbyte, short, ushort, int, or uint.</span></span>  
  
-   <span data-ttu-id="c764f-114">参照型であることが判明しているジェネリック型パラメーター。</span><span class="sxs-lookup"><span data-stu-id="c764f-114">Generic type parameters known to be reference types.</span></span>  
  
-   <span data-ttu-id="c764f-115"><xref:System.IntPtr> および <xref:System.UIntPtr>。</span><span class="sxs-lookup"><span data-stu-id="c764f-115"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>  
  
 <span data-ttu-id="c764f-116">volatile キーワードは、クラスまたは構造体のフィールドにのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="c764f-116">The volatile keyword can only be applied to fields of a class or struct.</span></span> <span data-ttu-id="c764f-117">ローカル変数を `volatile` として宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="c764f-117">Local variables cannot be declared `volatile`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c764f-118">例</span><span class="sxs-lookup"><span data-stu-id="c764f-118">Example</span></span>  
 <span data-ttu-id="c764f-119">次の例は、public のフィールド変数を `volatile` として宣言する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c764f-119">The following example shows how to declare a public field variable as `volatile`.</span></span>  
  
 <span data-ttu-id="c764f-120">[!code-cs[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c764f-120">[!code-cs[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="c764f-121">例</span><span class="sxs-lookup"><span data-stu-id="c764f-121">Example</span></span>  
 <span data-ttu-id="c764f-122">次の例は、補助スレッドつまりワーカー スレッドを作成および使用して、プライマリ スレッドとの並行処理を実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c764f-122">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="c764f-123">マルチスレッドの背景情報については、[スレッド化](../../../standard/threading/index.md)に関するページと「[スレッド処理](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c764f-123">For background information about multithreading, see [Threading](../../../standard/threading/index.md) and [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span></span>  
  
 <span data-ttu-id="c764f-124">[!code-cs[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="c764f-124">[!code-cs[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c764f-125">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="c764f-125">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c764f-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="c764f-126">See Also</span></span>  
 <span data-ttu-id="c764f-127">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="c764f-127">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="c764f-128">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c764f-128">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="c764f-129">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="c764f-129">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 [<span data-ttu-id="c764f-130">修飾子</span><span class="sxs-lookup"><span data-stu-id="c764f-130">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)

