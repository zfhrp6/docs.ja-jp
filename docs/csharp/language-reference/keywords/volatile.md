---
title: "volatile (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords: volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
caps.latest.revision: "29"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1cefa39313c3c551e8d05fbc31e528b86c6888d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="volatile-c-reference"></a><span data-ttu-id="19254-102">volatile (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="19254-102">volatile (C# Reference)</span></span>
<span data-ttu-id="19254-103">`volatile` キーワードは、同時に実行されている複数のスレッドによって、フィールドが変更される可能性があることを示します。</span><span class="sxs-lookup"><span data-stu-id="19254-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="19254-104">`volatile` と宣言されているフィールドは、シングル スレッドによるアクセスを前提とする、コンパイラの最適化の対象にはなりません。</span><span class="sxs-lookup"><span data-stu-id="19254-104">Fields that are declared `volatile` are not subject to compiler optimizations that assume access by a single thread.</span></span> <span data-ttu-id="19254-105">このため、フィールドには常に最新の値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="19254-105">This ensures that the most up-to-date value is present in the field at all times.</span></span>  
  
 <span data-ttu-id="19254-106">`volatile` 修飾子は、通常、アクセスをシリアル化する [lock](../../../csharp/language-reference/keywords/lock-statement.md) ステートメントが使用されない場合に、複数のスレッドからアクセスされるフィールドに対して使用します。</span><span class="sxs-lookup"><span data-stu-id="19254-106">The `volatile` modifier is usually used for a field that is accessed by multiple threads without using the [lock](../../../csharp/language-reference/keywords/lock-statement.md) statement to serialize access.</span></span>  
  
 <span data-ttu-id="19254-107">`volatile` キーワードは次の型のフィールドに使用できます。</span><span class="sxs-lookup"><span data-stu-id="19254-107">The `volatile` keyword can be applied to fields of these types:</span></span>  
  
-   <span data-ttu-id="19254-108">参照型。</span><span class="sxs-lookup"><span data-stu-id="19254-108">Reference types.</span></span>  
  
-   <span data-ttu-id="19254-109">ポインター型 (unsafe コンテキスト内)。</span><span class="sxs-lookup"><span data-stu-id="19254-109">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="19254-110">ポインター自体は volatile にできますが、ポインターが指しているオブジェクトは volatile にできません。</span><span class="sxs-lookup"><span data-stu-id="19254-110">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="19254-111">つまり、"volatile を指すポインター" は宣言できません。</span><span class="sxs-lookup"><span data-stu-id="19254-111">In other words, you cannot declare a "pointer to volatile."</span></span>  
  
-   <span data-ttu-id="19254-112">sbyte、byte、short、ushort、int、uint、char、float、bool などの型。</span><span class="sxs-lookup"><span data-stu-id="19254-112">Types such as sbyte, byte, short, ushort, int, uint, char, float, and bool.</span></span>  
  
-   <span data-ttu-id="19254-113">基本データ型 byte、sbyte、short、ushort、int、または uint のいずれかが含まれる列挙型。</span><span class="sxs-lookup"><span data-stu-id="19254-113">An enum type with one of the following base types: byte, sbyte, short, ushort, int, or uint.</span></span>  
  
-   <span data-ttu-id="19254-114">参照型であることが判明しているジェネリック型パラメーター。</span><span class="sxs-lookup"><span data-stu-id="19254-114">Generic type parameters known to be reference types.</span></span>  
  
-   <span data-ttu-id="19254-115"><xref:System.IntPtr> および <xref:System.UIntPtr>。</span><span class="sxs-lookup"><span data-stu-id="19254-115"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>  
  
 <span data-ttu-id="19254-116">volatile キーワードは、クラスまたは構造体のフィールドにのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="19254-116">The volatile keyword can only be applied to fields of a class or struct.</span></span> <span data-ttu-id="19254-117">ローカル変数を `volatile` として宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="19254-117">Local variables cannot be declared `volatile`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19254-118">例</span><span class="sxs-lookup"><span data-stu-id="19254-118">Example</span></span>  
 <span data-ttu-id="19254-119">次の例は、public のフィールド変数を `volatile` として宣言する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="19254-119">The following example shows how to declare a public field variable as `volatile`.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="19254-120">例</span><span class="sxs-lookup"><span data-stu-id="19254-120">Example</span></span>  
 <span data-ttu-id="19254-121">次の例は、補助スレッドつまりワーカー スレッドを作成および使用して、プライマリ スレッドとの並行処理を実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="19254-121">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="19254-122">マルチスレッドの背景情報については、[スレッド化](../../../standard/threading/index.md)に関するページと「[スレッド処理](../../programming-guide/concepts/threading/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19254-122">For background information about multithreading, see [Threading](../../../standard/threading/index.md) and [Threading](../../programming-guide/concepts/threading/index.md).</span></span>  
  
 [!code-csharp[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="19254-123">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="19254-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="19254-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="19254-124">See Also</span></span>  
 [<span data-ttu-id="19254-125">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="19254-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="19254-126">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="19254-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="19254-127">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="19254-127">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="19254-128">修飾子</span><span class="sxs-lookup"><span data-stu-id="19254-128">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
