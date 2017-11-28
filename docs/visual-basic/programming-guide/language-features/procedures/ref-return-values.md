---
title: "Ref 戻り値 (Visual Basic)"
ms.custom: 
ms.date: 04/28/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 560607f7aa304b25314daabeef3952e6bbef7426
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="support-for-reference-return-values-visual-basic"></a><span data-ttu-id="3b751-102">参照戻り値 (Visual Basic) のサポート</span><span class="sxs-lookup"><span data-stu-id="3b751-102">Support for reference return values (Visual Basic)</span></span>

<span data-ttu-id="3b751-103">C# 言語をサポートしています (C#) 7 以降、*戻り値の参照*です。</span><span class="sxs-lookup"><span data-stu-id="3b751-103">Starting with C# 7, the C# language supports *reference return values*.</span></span> <span data-ttu-id="3b751-104">戻り値の参照を理解する方法の 1 つは、メソッドへの参照によって渡される引数の逆であることです。</span><span class="sxs-lookup"><span data-stu-id="3b751-104">One way to understand reference return values is that they are the opposite of arguments that are passed by reference to a method.</span></span> <span data-ttu-id="3b751-105">参照によって渡された引数が変更されると、変更が、呼び出し元に対して、変数の値に反映されます。</span><span class="sxs-lookup"><span data-stu-id="3b751-105">When an argument passed by reference is modified, the changes are reflected in value of the variable on the caller.</span></span> <span data-ttu-id="3b751-106">提供する場合、メソッドの参照の戻り値を呼び出し元に、呼び出し元の参照の戻り値に加えた変更が、呼び出されたメソッドのデータに反映されます。</span><span class="sxs-lookup"><span data-stu-id="3b751-106">When an method provides a reference return value to a caller, modifications made to the reference return value by the caller are reflected in the called method's data.</span></span>

<span data-ttu-id="3b751-107">Visual Basic では、参照を持つメソッドを作成すると、戻り値が、参照戻り値を使用することは許可されません。</span><span class="sxs-lookup"><span data-stu-id="3b751-107">Visual Basic does not allow you to author methods with reference return values, but it does allow you to consume reference return values.</span></span> <span data-ttu-id="3b751-108">つまり、参照戻り値を持つメソッドを呼び出すし、その戻り値を変更し、参照の戻り値の変更は、呼び出されたメソッドのデータに反映されます。</span><span class="sxs-lookup"><span data-stu-id="3b751-108">In other words, you can call a method with a reference return value and modify that return value, and changes to the reference return value are reflected in the called method's data.</span></span>

## <a name="modifying-the-ref-return-value-directly"></a><span data-ttu-id="3b751-109">Ref の戻り値を直接変更します。</span><span class="sxs-lookup"><span data-stu-id="3b751-109">Modifying the ref return value directly</span></span>

<span data-ttu-id="3b751-110">常に成功して、されていないメソッドは`ByRef`パラメーター参照の戻り値を直接変更することができます。</span><span class="sxs-lookup"><span data-stu-id="3b751-110">For methods that always succeed and have no `ByRef` parameters, you can modify the reference return value directly.</span></span> <span data-ttu-id="3b751-111">これを行う参照戻り値を返す式を割り当てると、新しい値。</span><span class="sxs-lookup"><span data-stu-id="3b751-111">You do this by assigning the new value to the expressions that returns the reference return value.</span></span> 

<span data-ttu-id="3b751-112">次の c# の例では定義、`NumericValue.IncrementValue`を内部値をインクリメントし、参照として返すメソッドの戻り値。</span><span class="sxs-lookup"><span data-stu-id="3b751-112">The following C# example defines a `NumericValue.IncrementValue` method that increments an internal value and returns it as a reference return value.</span></span> 

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

<span data-ttu-id="3b751-113">参照は、値は、Visual Basic の例を次に、呼び出し元によって変更を返します。</span><span class="sxs-lookup"><span data-stu-id="3b751-113">The reference return value is then modified by the caller in the following Visual Basic example.</span></span> <span data-ttu-id="3b751-114">なおでは、行、`NumericValue.IncrementValue`メソッドの呼び出しが、メソッドに値を割り当てられません。</span><span class="sxs-lookup"><span data-stu-id="3b751-114">Note that the line with the `NumericValue.IncrementValue` method call does not assign a value to the method.</span></span> <span data-ttu-id="3b751-115">代わりに、メソッドによって返される参照の戻り値に値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="3b751-115">Instead, it assigns a value to the reference return value returned by the method.</span></span>

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a><span data-ttu-id="3b751-116">ヘルパー メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="3b751-116">Using a helper method</span></span>

<span data-ttu-id="3b751-117">その他の場合、メソッド呼び出しの参照の戻り値を直接変更できない可能性があります常にことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3b751-117">In other cases, modifying the reference return value of a method call directly may not always be desirable.</span></span> <span data-ttu-id="3b751-118">たとえば、文字列を返す検索メソッド可能性があります常に一致が見つかりません。</span><span class="sxs-lookup"><span data-stu-id="3b751-118">For example, a search method that returns a string may not always find a match.</span></span> <span data-ttu-id="3b751-119">その場合は、検索が成功した場合にのみ、参照の戻り値を変更します。</span><span class="sxs-lookup"><span data-stu-id="3b751-119">In that case, you want to modify the reference return value only if the search is successful.</span></span>

<span data-ttu-id="3b751-120">次の c# の例では、このシナリオを示します。</span><span class="sxs-lookup"><span data-stu-id="3b751-120">The following C# example illustrates this scenario.</span></span> <span data-ttu-id="3b751-121">定義する、 `Sentence` c# で記述されたクラスが含まれています、`FindNext`メソッドを指定した部分文字列で始まる文章内の次の単語を検索します。</span><span class="sxs-lookup"><span data-stu-id="3b751-121">It defines a `Sentence` class written in C# includes a `FindNext` method that finds the next word in a sentence that begins with a specified substring.</span></span> <span data-ttu-id="3b751-122">文字列は参照戻り値として返され、参照によりメソッドに渡される `Boolean` 変数は検索が成功したかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="3b751-122">The string is returned as a reference return value, and a `Boolean` variable passed by reference to the method indicates whether the search was successful.</span></span> <span data-ttu-id="3b751-123">参照の戻り値読み取りことを示します、呼び出し元できましていないのみ返される値です。そのユーザーも変更できますとで内部に含まれるデータにその変更が反映されます、`Sentence`クラスです。</span><span class="sxs-lookup"><span data-stu-id="3b751-123">The reference return value indicates that the caller can not only read the returned value; he or she can also modify it, and that modification is reflected in the data contained internally in the `Sentence` class.</span></span>

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

<span data-ttu-id="3b751-124">参照を直接変更する値ここではなく、信頼性の高いためを一致するものを検索し、センテンス内の最初の単語を返すメソッドの呼び出しが失敗するを返します。</span><span class="sxs-lookup"><span data-stu-id="3b751-124">Directly modifying the reference return value in this case is not reliable, since the method call may fail to find a match and return the first word in the sentence.</span></span> <span data-ttu-id="3b751-125">その場合は、呼び出し元は誤って文の最初の単語を変更します。</span><span class="sxs-lookup"><span data-stu-id="3b751-125">In that case, the caller will inadvertently modify the first word of the sentence.</span></span> <span data-ttu-id="3b751-126">返す、呼び出し元で、これを防止でした、 `null` (または`Nothing`Visual Basic で)。</span><span class="sxs-lookup"><span data-stu-id="3b751-126">This could be prevented by the caller returning a `null` (or `Nothing` in Visual Basic).</span></span> <span data-ttu-id="3b751-127">その場合は、値がある文字列を変更しようとしていますが、`Nothing`スロー、<xref:System.NullReferenceException>です。</span><span class="sxs-lookup"><span data-stu-id="3b751-127">But in that case, attempting to modify a string whose value is `Nothing` throws a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="3b751-128">返す、呼び出し元によっても禁止することが場合<xref:System.String.Empty?displayProperty=nameWithType>、呼び出し元は、値が文字列変数を定義することが必要ですが、<xref:System.String.Empty?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="3b751-128">If could also be prevented by the caller returning <xref:System.String.Empty?displayProperty=nameWithType>, but this requires that the caller define a string variable whose value is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3b751-129">呼び出し元は、その文字列を変更できます、自体を変更の目的なし、変更後の文字列によって格納される、センテンス内の単語にリレーションシップがあるないので、`Sentence`クラスです。</span><span class="sxs-lookup"><span data-stu-id="3b751-129">While the caller can modify that string, the modification itself serves no purpose, since the modified string has no relationship to the words in the sentence stored by the `Sentence` class.</span></span>

<span data-ttu-id="3b751-130">このシナリオを処理する最善の方法では、ヘルパー メソッドへの参照によって参照戻り値を渡すです。</span><span class="sxs-lookup"><span data-stu-id="3b751-130">The best way to handle this scenario is to pass the reference return value by reference to a helper method.</span></span> <span data-ttu-id="3b751-131">ヘルパー メソッドには、メソッド呼び出しが成功したし、変わった場合は、変更、参照値を返すかどうかを判断するロジックが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3b751-131">The helper method then contains the logic to determine whether the method call succeeded and, if it did, to modify the reference return value.</span></span> <span data-ttu-id="3b751-132">次の例では、可能な実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="3b751-132">The following example provides a possible implementation.</span></span>

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a><span data-ttu-id="3b751-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="3b751-133">See also</span></span>

<span data-ttu-id="3b751-134">[引数値渡しと参照渡し](passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="3b751-134">[Passing arguments by value and by reference](passing-arguments-by-value-and-by-reference.md) </span></span>  
[<span data-ttu-id="3b751-135">Visual Basic におけるプロシージャ</span><span class="sxs-lookup"><span data-stu-id="3b751-135">Procedures in Visual Basic</span></span>](index.md)   


