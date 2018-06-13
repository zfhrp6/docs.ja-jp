---
title: volatile (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: 7f3aafc1255667f2a3917c6e171ce4ddf0343b41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272585"
---
# <a name="volatile-c-reference"></a><span data-ttu-id="2bdf0-102">volatile (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="2bdf0-102">volatile (C# Reference)</span></span>
<span data-ttu-id="2bdf0-103">`volatile` キーワードは、同時に実行されている複数のスレッドによって、フィールドが変更される可能性があることを示します。</span><span class="sxs-lookup"><span data-stu-id="2bdf0-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="2bdf0-104">`volatile` と宣言されているフィールドは、シングル スレッドによるアクセスを前提とする、コンパイラの最適化の対象にはなりません。</span><span class="sxs-lookup"><span data-stu-id="2bdf0-104">Fields that are declared `volatile` are not subject to compiler optimizations that assume access by a single thread.</span></span> <span data-ttu-id="2bdf0-105">このため、フィールドには常に最新の値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2bdf0-105">This ensures that the most up-to-date value is present in the field at all times.</span></span>  
  
 <span data-ttu-id="2bdf0-106">`volatile` 修飾子は、通常、アクセスをシリアル化する [lock](../../../csharp/language-reference/keywords/lock-statement.md) ステートメントが使用されない場合に、複数のスレッドからアクセスされるフィールドに対して使用します。</span><span class="sxs-lookup"><span data-stu-id="2bdf0-106">The `volatile` modifier is usually used for a field that is accessed by multiple threads without using the [lock](../../../csharp/language-reference/keywords/lock-statement.md) statement to serialize access.</span></span>  
  
 <span data-ttu-id="2bdf0-107">`volatile` キーワードは次の型のフィールドに使用できます。</span><span class="sxs-lookup"><span data-stu-id="2bdf0-107">The `volatile` keyword can be applied to fields of these types:</span></span>  
  
-   <span data-ttu-id="2bdf0-108">参照型。</span><span class="sxs-lookup"><span data-stu-id="2bdf0-108">Reference types.</span></span>  
  
-   <span data-ttu-id="2bdf0-109">ポインター型 (unsafe コンテキスト内)。</span><span class="sxs-lookup"><span data-stu-id="2bdf0-109">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="2bdf0-110">ポインター自体は volatile にできますが、ポインターが指しているオブジェクトは volatile にできません。</span><span class="sxs-lookup"><span data-stu-id="2bdf0-110">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="2bdf0-111">つまり、"volatile を指すポインター" は宣言できません。</span><span class="sxs-lookup"><span data-stu-id="2bdf0-111">In other words, you cannot declare a "pointer to volatile."</span></span>  
  
-   <span data-ttu-id="2bdf0-112">sbyte、byte、short、ushort、int、uint、char、float、bool などの型。</span><span class="sxs-lookup"><span data-stu-id="2bdf0-112">Types such as sbyte, byte, short, ushort, int, uint, char, float, and bool.</span></span>  
  
-   <span data-ttu-id="2bdf0-113">基本データ型 byte、sbyte、short、ushort、int、または uint のいずれかが含まれる列挙型。</span><span class="sxs-lookup"><span data-stu-id="2bdf0-113">An enum type with one of the following base types: byte, sbyte, short, ushort, int, or uint.</span></span>  
  
-   <span data-ttu-id="2bdf0-114">参照型であることが判明しているジェネリック型パラメーター。</span><span class="sxs-lookup"><span data-stu-id="2bdf0-114">Generic type parameters known to be reference types.</span></span>  
  
-   <span data-ttu-id="2bdf0-115"><xref:System.IntPtr> および <xref:System.UIntPtr>。</span><span class="sxs-lookup"><span data-stu-id="2bdf0-115"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>  
  
 <span data-ttu-id="2bdf0-116">volatile キーワードは、クラスまたは構造体のフィールドにのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="2bdf0-116">The volatile keyword can only be applied to fields of a class or struct.</span></span> <span data-ttu-id="2bdf0-117">ローカル変数を `volatile` として宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="2bdf0-117">Local variables cannot be declared `volatile`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bdf0-118">例</span><span class="sxs-lookup"><span data-stu-id="2bdf0-118">Example</span></span>  
 <span data-ttu-id="2bdf0-119">次の例は、public のフィールド変数を `volatile` として宣言する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="2bdf0-119">The following example shows how to declare a public field variable as `volatile`.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="2bdf0-120">例</span><span class="sxs-lookup"><span data-stu-id="2bdf0-120">Example</span></span>  
 <span data-ttu-id="2bdf0-121">次の例は、補助スレッドつまりワーカー スレッドを作成および使用して、プライマリ スレッドとの並行処理を実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="2bdf0-121">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="2bdf0-122">マルチスレッドの背景情報については、[スレッド化 (C#)](../../../standard/threading/index.md) と[マネージド スレッド処理](../../programming-guide/concepts/threading/index.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2bdf0-122">For background information about multithreading, see [Threading (C#)](../../../standard/threading/index.md) and [Managed Threading](../../programming-guide/concepts/threading/index.md).</span></span>  
  
 [!code-csharp[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="2bdf0-123">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="2bdf0-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2bdf0-124">参照</span><span class="sxs-lookup"><span data-stu-id="2bdf0-124">See Also</span></span>  
 [<span data-ttu-id="2bdf0-125">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="2bdf0-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2bdf0-126">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="2bdf0-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2bdf0-127">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="2bdf0-127">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="2bdf0-128">修飾子</span><span class="sxs-lookup"><span data-stu-id="2bdf0-128">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
