---
title: "コンパイラにより生成された例外 (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d1417e42f588978d5fc1beca4ad55463502ee219
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a><span data-ttu-id="763ca-102">コンパイラにより生成された例外 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="763ca-102">Compiler-Generated Exceptions (C# Programming Guide)</span></span>
<span data-ttu-id="763ca-103">一部の例外は、基本操作が失敗した場合に .NET Framework の共通言語ランタイム (CLR) によって自動的にスローされます。</span><span class="sxs-lookup"><span data-stu-id="763ca-103">Some exceptions are thrown automatically by the .NET Framework's common language runtime (CLR) when basic operations fail.</span></span> <span data-ttu-id="763ca-104">次の表には、これらの例外とそのエラー条件が一覧で示されています。</span><span class="sxs-lookup"><span data-stu-id="763ca-104">These exceptions and their error conditions are listed in the following table.</span></span>  
  
|<span data-ttu-id="763ca-105">例外</span><span class="sxs-lookup"><span data-stu-id="763ca-105">Exception</span></span>|<span data-ttu-id="763ca-106">説明</span><span class="sxs-lookup"><span data-stu-id="763ca-106">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|<span data-ttu-id="763ca-107">算術演算中に発生する例外 (<xref:System.DivideByZeroException>、<xref:System.OverflowException> など) の基底クラスです。</span><span class="sxs-lookup"><span data-stu-id="763ca-107">A base class for exceptions that occur during arithmetic operations, such as <xref:System.DivideByZeroException> and <xref:System.OverflowException>.</span></span>|  
|<xref:System.ArrayTypeMismatchException>|<span data-ttu-id="763ca-108">要素の実際の型が配列の実際の型に適合していないことが原因で、指定された要素を配列に格納できない場合にスローされます。</span><span class="sxs-lookup"><span data-stu-id="763ca-108">Thrown when an array cannot store a given element because the actual type of the element is incompatible with the actual type of the array.</span></span>|  
|<xref:System.DivideByZeroException>|<span data-ttu-id="763ca-109">整数値のゼロ除算が試行されたときにスローされます。</span><span class="sxs-lookup"><span data-stu-id="763ca-109">Thrown when an attempt is made to divide an integral value by zero.</span></span>|  
|<xref:System.IndexOutOfRangeException>|<span data-ttu-id="763ca-110">インデックスがゼロよりも小さい場合またはインデックスが配列の境界外にある場合に、配列のインデックス作成が試行されたときにスローされます。</span><span class="sxs-lookup"><span data-stu-id="763ca-110">Thrown when an attempt is made to index an array when the index is less than zero or outside the bounds of the array.</span></span>|  
|<xref:System.InvalidCastException>|<span data-ttu-id="763ca-111">基本データ型からインターフェイスまたは派生型への明示的な変換が実行時に失敗したときにスローされます。</span><span class="sxs-lookup"><span data-stu-id="763ca-111">Thrown when an explicit conversion from a base type to an interface or to a derived type fails at runtime.</span></span>|  
|<xref:System.NullReferenceException>|<span data-ttu-id="763ca-112">値が [null](../../../csharp/language-reference/keywords/null.md) であるオブジェクトを参照しようとした場合にスローされます。</span><span class="sxs-lookup"><span data-stu-id="763ca-112">Thrown when you attempt to reference an object whose value is [null](../../../csharp/language-reference/keywords/null.md).</span></span>|  
|<xref:System.OutOfMemoryException>|<span data-ttu-id="763ca-113">[new](../../../csharp/language-reference/keywords/new-operator.md) 演算子を使用したメモリの割り当てに失敗するとスローされます。</span><span class="sxs-lookup"><span data-stu-id="763ca-113">Thrown when an attempt to allocate memory using the [new](../../../csharp/language-reference/keywords/new-operator.md) operator fails.</span></span> <span data-ttu-id="763ca-114">これは、共通言語ランタイムで使用できるメモリが足りなくなったことを示します。</span><span class="sxs-lookup"><span data-stu-id="763ca-114">This indicates that the memory available to the common language runtime has been exhausted.</span></span>|  
|<xref:System.OverflowException>|<span data-ttu-id="763ca-115">`checked` コンテキストで算術演算がオーバーフローしたときにスローされます。</span><span class="sxs-lookup"><span data-stu-id="763ca-115">Thrown when an arithmetic operation in a `checked` context overflows.</span></span>|  
|<xref:System.StackOverflowException>|<span data-ttu-id="763ca-116">保留中のメソッド呼び出しが多すぎることが原因で実行スタックが不足したときにスローされます。通常は、非常に深い再帰か無限再帰があることを示します。</span><span class="sxs-lookup"><span data-stu-id="763ca-116">Thrown when the execution stack is exhausted by having too many pending method calls; usually indicates a very deep or infinite recursion.</span></span>|  
|<xref:System.TypeInitializationException>|<span data-ttu-id="763ca-117">静的コンストラクターが例外をスローし、その例外をキャッチするための対応する `catch` 句がない場合にスローされます。</span><span class="sxs-lookup"><span data-stu-id="763ca-117">Thrown when a static constructor throws an exception and no compatible `catch` clause exists to catch it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="763ca-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="763ca-118">See Also</span></span>  
 [<span data-ttu-id="763ca-119">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="763ca-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="763ca-120">例外と例外処理</span><span class="sxs-lookup"><span data-stu-id="763ca-120">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)  
 [<span data-ttu-id="763ca-121">例外処理</span><span class="sxs-lookup"><span data-stu-id="763ca-121">Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/exception-handling.md)  
 [<span data-ttu-id="763ca-122">try-catch</span><span class="sxs-lookup"><span data-stu-id="763ca-122">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
 [<span data-ttu-id="763ca-123">try-finally</span><span class="sxs-lookup"><span data-stu-id="763ca-123">try-finally</span></span>](../../../csharp/language-reference/keywords/try-finally.md)  
 [<span data-ttu-id="763ca-124">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="763ca-124">try-catch-finally</span></span>](../../../csharp/language-reference/keywords/try-catch-finally.md)
