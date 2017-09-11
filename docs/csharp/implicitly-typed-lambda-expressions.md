---
title: "暗黙的に型指定されるラムダ式"
description: "暗黙的に型指定される変数宣言を使用してラムダ式を宣言することはできない理由を説明します。"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 663613af001f9727c48bd48553540305e47a6bab
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="implicitly-typed-lambda-expressions"></a><span data-ttu-id="ee305-104">暗黙的に型指定されるラムダ式</span><span class="sxs-lookup"><span data-stu-id="ee305-104">Implicitly typed lambda expressions</span></span>

<span data-ttu-id="ee305-105">私はこの式ツリーを宣言するのに `var` を使っていません。</span><span class="sxs-lookup"><span data-stu-id="ee305-105">I'm not using `var` to declare this expression tree.</span></span> <span data-ttu-id="ee305-106">暗黙的に型指定される変数宣言を使用してラムダ式を宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="ee305-106">You can't use an implicitly typed variable declaration to declare a lambda expression.</span></span>
<span data-ttu-id="ee305-107">そうした場合、コンパイラの循環論理問題が発生します。</span><span class="sxs-lookup"><span data-stu-id="ee305-107">It creates a circular logic problem for the compiler.</span></span> <span data-ttu-id="ee305-108">`var` 宣言は、代入演算子の右辺にある式の型から変数の型を推論するようにコンパイラに指示するものです。</span><span class="sxs-lookup"><span data-stu-id="ee305-108">The `var` declaration tells the compiler to figure out the type of the variable from the type of expression on the right hand side of the assignment operator.</span></span> <span data-ttu-id="ee305-109">ラムダ式はコンパイル時の型を持ちませんが、任意の一致するデリゲートまたは式の型に変換できます。</span><span class="sxs-lookup"><span data-stu-id="ee305-109">A lambda expression does not have a compile time type, but is convertible to any matching delegate or expression type.</span></span> <span data-ttu-id="ee305-110">デリゲートまたは式の型の変数にラムダ式を代入すると、"代入先の" 変数のシグネチャに一致する式またはデリゲートにラムダ式を変換するようコンパイラに指示することになります。</span><span class="sxs-lookup"><span data-stu-id="ee305-110">When you assign a lambda expression to a variable of a delegate or expression type, you tell the compiler to try and convert the lambda expression into an expression or delegate that matches the signature of the 'assigned to' variable.</span></span> <span data-ttu-id="ee305-111">コンパイラは、代入の右辺の値を代入の左辺の型に一致させることを試みる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee305-111">The compiler must try to make the thing on the right hand side of the assignment match the type on the left hand side of the assignment.</span></span> 

<span data-ttu-id="ee305-112">代入の左右どちらの側でも、代入演算子の反対側の辺のオブジェクトを調べて型が一致するかどうかを判断するようコンパイラに指示することはできません。</span><span class="sxs-lookup"><span data-stu-id="ee305-112">Both sides of the assignment can't be telling the compiler to look at the object on the other side of the assignment operator and see if my type matches.</span></span>

<span data-ttu-id="ee305-113">C# 言語でこの動作が指定されている理由については、[この記事](http://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf)を参照してください (PDF ダウンロード)。</span><span class="sxs-lookup"><span data-stu-id="ee305-113">You can get even more details on why the C# language specifies that behavior by reading [this article](http://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (PDF Download)</span></span>



