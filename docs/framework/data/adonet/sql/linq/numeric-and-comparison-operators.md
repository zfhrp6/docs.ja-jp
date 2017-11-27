---
title: "数値演算子および比較演算子"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f77cb612468b401f6aa526e46cc7481d0b47d385
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="numeric-and-comparison-operators"></a><span data-ttu-id="8730d-102">数値演算子および比較演算子</span><span class="sxs-lookup"><span data-stu-id="8730d-102">Numeric and Comparison Operators</span></span>
<span data-ttu-id="8730d-103">算術演算子と比較演算子は、次の点を除いて、共通言語ランタイム (CLR) では期待どおりに動作します。</span><span class="sxs-lookup"><span data-stu-id="8730d-103">Arithmetic and comparison operators work as expected in the common language runtime (CLR) except as follows:</span></span>  
  
-   <span data-ttu-id="8730d-104">SQL では、浮動小数点数に対して剰余演算子がサポートされません。</span><span class="sxs-lookup"><span data-stu-id="8730d-104">SQL does not support the modulus operator on floating-point numbers.</span></span>  
  
-   <span data-ttu-id="8730d-105">SQL ではチェックされない算術はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="8730d-105">SQL does not support unchecked arithmetic.</span></span>  
  
-   <span data-ttu-id="8730d-106">インクリメント演算子とデクリメント演算子は、SQL に複製できない式で使用すると副作用があるため、SQL ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="8730d-106">Increment and decrement operators cause side-effects when you use them in expressions that cannot be replicated in SQL and are, therefore, not supported.</span></span>  
  
## <a name="supported-operators"></a><span data-ttu-id="8730d-107">サポートされる演算子</span><span class="sxs-lookup"><span data-stu-id="8730d-107">Supported Operators</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="8730d-108"> は、次の演算子をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="8730d-108"> supports the following operators.</span></span>  
  
-   <span data-ttu-id="8730d-109">基本算術演算子</span><span class="sxs-lookup"><span data-stu-id="8730d-109">Basic arithmetic operators:</span></span>  
  
    -   `+`  
  
    -   <span data-ttu-id="8730d-110">`-` (減算)</span><span class="sxs-lookup"><span data-stu-id="8730d-110">`-` (subtraction)</span></span>  
  
    -   `*`  
  
    -   `/`  
  
    -   <span data-ttu-id="8730d-111">Visual Basic 整数除算 (`\`)</span><span class="sxs-lookup"><span data-stu-id="8730d-111">Visual Basic integer division (`\`)</span></span>  
  
    -   <span data-ttu-id="8730d-112">`%` (Visual Basic `Mod`)</span><span class="sxs-lookup"><span data-stu-id="8730d-112">`%` (Visual Basic `Mod`)</span></span>  
  
    -   `<<`  
  
    -   `>>`  
  
    -   <span data-ttu-id="8730d-113">`-` (単項マイナス符号)</span><span class="sxs-lookup"><span data-stu-id="8730d-113">`-` (unary negation)</span></span>  
  
-   <span data-ttu-id="8730d-114">基本比較演算子</span><span class="sxs-lookup"><span data-stu-id="8730d-114">Basic comparison operators:</span></span>  
  
    -   <span data-ttu-id="8730d-115">Visual Basic `=` および C# `==`</span><span class="sxs-lookup"><span data-stu-id="8730d-115">Visual Basic `=` and C# `==`</span></span>  
  
    -   <span data-ttu-id="8730d-116">Visual Basic `<>` および C# `!=`</span><span class="sxs-lookup"><span data-stu-id="8730d-116">Visual Basic `<>` and C# `!=`</span></span>  
  
    -   <span data-ttu-id="8730d-117">Visual Basic `Is/IsNot`</span><span class="sxs-lookup"><span data-stu-id="8730d-117">Visual Basic `Is/IsNot`</span></span>  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a><span data-ttu-id="8730d-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="8730d-118">See Also</span></span>  
 [<span data-ttu-id="8730d-119">データ型および関数</span><span class="sxs-lookup"><span data-stu-id="8730d-119">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [<span data-ttu-id="8730d-120">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="8730d-120">C# Operators</span></span>](http://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43)  
 [<span data-ttu-id="8730d-121">演算子</span><span class="sxs-lookup"><span data-stu-id="8730d-121">Operators</span></span>](../../../../../visual-basic/language-reference/operators/index.md)
