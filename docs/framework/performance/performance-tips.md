---
title: .NET のパフォーマンスに関するヒント
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- C# language, performance
- performance [C#]
- Visual Basic, performance
- performance [Visual Basic]
ms.assetid: ae275793-857d-4102-9095-b4c2a02d57f4
caps.latest.revision: ''
author: BillWagner
ms.author: wiwagn
manager: wpickett
ms.workload:
- wiwagn
ms.openlocfilehash: ac1f5b9e0897650751320a7f5a9290c378d428b6
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2018
---
# <a name="net-performance-tips"></a><span data-ttu-id="e5457-102">.NET のパフォーマンスに関するヒント</span><span class="sxs-lookup"><span data-stu-id="e5457-102">.NET Performance Tips</span></span>
<span data-ttu-id="e5457-103">*パフォーマンス*という用語は、プログラムの実行速度を表す一般的な用語です。</span><span class="sxs-lookup"><span data-stu-id="e5457-103">The term *performance* generally refers to the execution speed of a program.</span></span> <span data-ttu-id="e5457-104">ソース コード内で特定の基本規則に従うことにより、実行速度を上げることができることもあります。</span><span class="sxs-lookup"><span data-stu-id="e5457-104">You can sometimes increase execution speed by following certain basic rules in your source code.</span></span> <span data-ttu-id="e5457-105">プログラムによっては、コードを綿密に調べることが重要で、プロファイラーを使用して、可能な限り速く実行しているかどうかを確認することが必要な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="e5457-105">In some programs, it is important to examine code closely and use profilers to make sure that it is running as fast as possible.</span></span> <span data-ttu-id="e5457-106">一方、記述どおりに許容可能な速度でコードが実行されているため、このような最適化が必要ないプログラムもあります。</span><span class="sxs-lookup"><span data-stu-id="e5457-106">In other programs, you do not have to perform such optimization because the code is running acceptably fast as it is written.</span></span> <span data-ttu-id="e5457-107">ここでは、パフォーマンスの低下が発生する一般的な状況と、パフォーマンスを向上させるためのヒント、およびパフォーマンスに関する追加のトピックについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e5457-107">This article lists some common areas where performance can suffer and tips for improving it as well as links to additional performance topics.</span></span> <span data-ttu-id="e5457-108">パフォーマンスの計画と計測の詳細については、「[Performance](../../../docs/framework/performance/index.md)」(パフォーマンス) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5457-108">For more information about planning and measuring for performance, see [Performance](../../../docs/framework/performance/index.md)</span></span>  
  
## <a name="boxing-and-unboxing"></a><span data-ttu-id="e5457-109">ボックス化とボックス化解除</span><span class="sxs-lookup"><span data-stu-id="e5457-109">Boxing and Unboxing</span></span>  
 <span data-ttu-id="e5457-110">たとえば、<xref:System.Collections.ArrayList?displayProperty=nameWithType> などの非ジェネリック コレクション クラスで、頻繁に値型をボックス化する必要がある状況では、値型の使用を回避するのが最も適しています。</span><span class="sxs-lookup"><span data-stu-id="e5457-110">It is best to avoid using value types in situations where they must be boxed a high number of times, for example in non-generic collections classes such as <xref:System.Collections.ArrayList?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e5457-111"><xref:System.Collections.Generic.List%601?displayProperty=nameWithType> などのジェネリック コレクションを使用することで、値型のボックス化を回避できます。</span><span class="sxs-lookup"><span data-stu-id="e5457-111">You can avoid boxing of value types by using generic collections such as <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e5457-112">ボックス化とボックス化解除は、負荷の大きい処理です。</span><span class="sxs-lookup"><span data-stu-id="e5457-112">Boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="e5457-113">値型をボックス化するときは、完全に新しいオブジェクトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5457-113">When a value type is boxed, an entirely new object must be created.</span></span> <span data-ttu-id="e5457-114">これには、単純な参照割り当てと比較して最大 20 倍もの時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="e5457-114">This can take up to 20 times longer than a simple reference assignment.</span></span> <span data-ttu-id="e5457-115">また、ボックス化を解除するときは、キャストのプロセスで代入の 4 倍の時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="e5457-115">When unboxing, the casting process can take four times as long as an assignment.</span></span> <span data-ttu-id="e5457-116">詳細については、「[ボックス化とボックス化解除](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5457-116">For more information, see [Boxing and Unboxing](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md).</span></span>  
  
## <a name="strings"></a><span data-ttu-id="e5457-117">文字列</span><span class="sxs-lookup"><span data-stu-id="e5457-117">Strings</span></span>  
 <span data-ttu-id="e5457-118">たとえば、短いループ内で多くの文字列変数を連結する場合は、C# の [+ 演算子](~/docs/csharp/language-reference/operators/addition-operator.md)または Visual Basic の[連結演算子](~/docs/visual-basic/language-reference/operators/concatenation-operators.md)ではなく、<xref:System.Text.StringBuilder?displayProperty=nameWithType> を使用します。</span><span class="sxs-lookup"><span data-stu-id="e5457-118">When you concatenate a large number of string variables, for example in a tight loop, use <xref:System.Text.StringBuilder?displayProperty=nameWithType> instead of the C# [+ operator](~/docs/csharp/language-reference/operators/addition-operator.md) or the Visual Basic [Concatenation Operators](~/docs/visual-basic/language-reference/operators/concatenation-operators.md).</span></span> <span data-ttu-id="e5457-119">詳細については、「[方法: 複数の文字列を連結する](../../csharp/how-to/concatenate-multiple-strings.md)」と「[Concatenation Operators in Visual Basic](~/docs/visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)」(Visual Basic の連結演算子) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5457-119">For more information, see [How to: Concatenate Multiple Strings](../../csharp/how-to/concatenate-multiple-strings.md) and [Concatenation Operators in Visual Basic](~/docs/visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md).</span></span>  
  
## <a name="destructors"></a><span data-ttu-id="e5457-120">デストラクター</span><span class="sxs-lookup"><span data-stu-id="e5457-120">Destructors</span></span>  
 <span data-ttu-id="e5457-121">空のデストラクターは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="e5457-121">Empty destructors should not be used.</span></span> <span data-ttu-id="e5457-122">デストラクターがクラスに存在するときは、エントリが終了キューで作成されます。</span><span class="sxs-lookup"><span data-stu-id="e5457-122">When a class contains a destructor, an entry is created in the Finalize queue.</span></span> <span data-ttu-id="e5457-123">デストラクターを呼び出すと、ガベージ コレクターが呼び出され、このキューを処理します。</span><span class="sxs-lookup"><span data-stu-id="e5457-123">When the destructor is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="e5457-124">デストラクターが空の場合は、これによってパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="e5457-124">If the destructor is empty, this simply results in a loss of performance.</span></span> <span data-ttu-id="e5457-125">詳細については、「[デストラクタ](~/docs/csharp/programming-guide/classes-and-structs/destructors.md)」と「[Object Lifetime: How Objects Are Created and Destroyed](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)」(オブジェクトの有効期間 : オブジェクトの作成と破棄) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5457-125">For more information, see [Destructors](~/docs/csharp/programming-guide/classes-and-structs/destructors.md) and [Object Lifetime: How Objects Are Created and Destroyed](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
## <a name="other-resources"></a><span data-ttu-id="e5457-126">その他の参照情報</span><span class="sxs-lookup"><span data-stu-id="e5457-126">Other Resources</span></span>  
  
-   [<span data-ttu-id="e5457-127">高速なマネージ コードを書く: 何にコストがかかるのかを知る</span><span class="sxs-lookup"><span data-stu-id="e5457-127">Writing Faster Managed Code: Know What Things Cost</span></span>](http://go.microsoft.com/fwlink/?LinkId=99294)  
  
-   [<span data-ttu-id="e5457-128">高パフォーマンスのマネージ アプリケーションを書く: 入門編</span><span class="sxs-lookup"><span data-stu-id="e5457-128">Writing High-Performance Managed Applications: A Primer</span></span>](http://go.microsoft.com/fwlink/?LinkId=99295)  
  
-   [<span data-ttu-id="e5457-129">ガベージ コレクターの基本とパフォーマンスのヒント</span><span class="sxs-lookup"><span data-stu-id="e5457-129">Garbage Collector Basics and Performance Hints</span></span>](http://go.microsoft.com/fwlink/?LinkId=99296)  
  
-   [<span data-ttu-id="e5457-130">.NET アプリケーションのパフォーマンス関連のヒントとトリック</span><span class="sxs-lookup"><span data-stu-id="e5457-130">Performance Tips and Tricks in .NET Applications</span></span>](http://go.microsoft.com/fwlink/?LinkId=99297)  

-   [<span data-ttu-id="e5457-131">Rico Mariani が紹介するパフォーマンスに関するニュース</span><span class="sxs-lookup"><span data-stu-id="e5457-131">Rico Mariani's Performance Tidbits</span></span>](http://go.microsoft.com/fwlink/?LinkId=115679)  

-   [<span data-ttu-id="e5457-132">Vance Morrison のブログ</span><span class="sxs-lookup"><span data-stu-id="e5457-132">Vance Morrison's Blog</span></span>](https://blogs.msdn.microsoft.com/vancem/)
  
## <a name="see-also"></a><span data-ttu-id="e5457-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="e5457-133">See Also</span></span>  
 [<span data-ttu-id="e5457-134">パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="e5457-134">Performance</span></span>](../../../docs/framework/performance/index.md)  
 [<span data-ttu-id="e5457-135">プログラミングの概念</span><span class="sxs-lookup"><span data-stu-id="e5457-135">Programming Concepts</span></span>](http://msdn.microsoft.com/library/65c12cca-af4f-4017-886e-2dbc00a189d6)  
 [<span data-ttu-id="e5457-136">Visual Basic プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="e5457-136">Visual Basic Programming Guide</span></span>](../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="e5457-137">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="e5457-137">C# Programming Guide</span></span>](http://msdn.microsoft.com/library/ac0f23a2-6bf3-4077-be99-538ae5fd3bc5)
