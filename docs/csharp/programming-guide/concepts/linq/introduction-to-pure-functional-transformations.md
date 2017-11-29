---
title: "純粋関数型変換の概要 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 8495c9d9-2d02-4aa0-8a10-9e8794b985fe
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 535d022b68fd4d08f04648fb98f5a7a7c53ed6e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="introduction-to-pure-functional-transformations-c"></a><span data-ttu-id="6bc3b-102">純粋関数型変換の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="6bc3b-102">Introduction to Pure Functional Transformations (C#)</span></span>
<span data-ttu-id="6bc3b-103">ここでは、関数型変換の概要について、その基になる概念や、それをサポートする言語構成要素も含めて説明します。</span><span class="sxs-lookup"><span data-stu-id="6bc3b-103">This section introduces functional transformations, including the underlying concepts and supporting language constructs.</span></span> <span data-ttu-id="6bc3b-104">また、オブジェクト指向変換と関数型変換という 2 つのプログラミング方法を対比させて、関数型変換に移行するためのアドバイスを紹介します。</span><span class="sxs-lookup"><span data-stu-id="6bc3b-104">It contrasts the object-oriented and functional transformation approaches to programming, including advice on how to transition to the latter.</span></span> <span data-ttu-id="6bc3b-105">関数型変換はさまざまなプログラミング シナリオで使用できますが、ここでは XML 変換を具体例として取り上げます。</span><span class="sxs-lookup"><span data-stu-id="6bc3b-105">Although functional transformations can be used in many programming scenarios, XML transformation is used here as a concrete example.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6bc3b-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="6bc3b-106">In This Section</span></span>  
  
|<span data-ttu-id="6bc3b-107">トピック</span><span class="sxs-lookup"><span data-stu-id="6bc3b-107">Topic</span></span>|<span data-ttu-id="6bc3b-108">説明</span><span class="sxs-lookup"><span data-stu-id="6bc3b-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="6bc3b-109">概念と用語 (関数型変換) (C#)</span><span class="sxs-lookup"><span data-stu-id="6bc3b-109">Concepts and Terminology (Functional Transformation) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)|<span data-ttu-id="6bc3b-110">純粋関数型変換の概念と用語について説明します。</span><span class="sxs-lookup"><span data-stu-id="6bc3b-110">Introduces the concepts and terminology of pure functional transformations.</span></span>|  
|[<span data-ttu-id="6bc3b-111">関数型プログラミングと命令型プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="6bc3b-111">Functional Programming vs. Imperative Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)|<span data-ttu-id="6bc3b-112">関数型プログラミングを従来の命令型 (手続き型) プログラミングと比較対照します。</span><span class="sxs-lookup"><span data-stu-id="6bc3b-112">Compares and contrasts functional programming to more traditional imperative (procedural) programming.</span></span>|  
|[<span data-ttu-id="6bc3b-113">純粋関数へのリファクタリング (C#)</span><span class="sxs-lookup"><span data-stu-id="6bc3b-113">Refactoring Into Pure Functions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)|<span data-ttu-id="6bc3b-114">純粋関数について説明し、純粋関数と純粋でない関数の例を示します。</span><span class="sxs-lookup"><span data-stu-id="6bc3b-114">Introduces pure functions, and shows examples of and pure and impure functions.</span></span>|  
|[<span data-ttu-id="6bc3b-115">関数型変換の適用範囲 (C#)</span><span class="sxs-lookup"><span data-stu-id="6bc3b-115">Applicability of Functional Transformation (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/applicability-of-functional-transformation.md)|<span data-ttu-id="6bc3b-116">関数型変換の一般的なシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="6bc3b-116">Describes typical scenarios for functional transformations.</span></span>|  
|[<span data-ttu-id="6bc3b-117">XML の関数型変換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6bc3b-117">Functional Transformation of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md)|<span data-ttu-id="6bc3b-118">XML ツリーの変換のコンテキストにおける関数型変換について説明します。</span><span class="sxs-lookup"><span data-stu-id="6bc3b-118">Describes functional transformations in the context of transforming XML trees.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6bc3b-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="6bc3b-119">See Also</span></span>  
 [<span data-ttu-id="6bc3b-120">XML の純粋関数型変換 (C#)</span><span class="sxs-lookup"><span data-stu-id="6bc3b-120">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)
