---
title: 数値演算子および比較演算子
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: a1ce13225d72b4286982434d52998a1913814abb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352182"
---
# <a name="numeric-and-comparison-operators"></a><span data-ttu-id="7388b-102">数値演算子および比較演算子</span><span class="sxs-lookup"><span data-stu-id="7388b-102">Numeric and Comparison Operators</span></span>
<span data-ttu-id="7388b-103">算術演算子と比較演算子は、次の点を除いて、共通言語ランタイム (CLR) では期待どおりに動作します。</span><span class="sxs-lookup"><span data-stu-id="7388b-103">Arithmetic and comparison operators work as expected in the common language runtime (CLR) except as follows:</span></span>  
  
-   <span data-ttu-id="7388b-104">SQL では、浮動小数点数に対して剰余演算子がサポートされません。</span><span class="sxs-lookup"><span data-stu-id="7388b-104">SQL does not support the modulus operator on floating-point numbers.</span></span>  
  
-   <span data-ttu-id="7388b-105">SQL ではチェックされない算術はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="7388b-105">SQL does not support unchecked arithmetic.</span></span>  
  
-   <span data-ttu-id="7388b-106">インクリメント演算子とデクリメント演算子は、SQL に複製できない式で使用すると副作用があるため、SQL ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="7388b-106">Increment and decrement operators cause side-effects when you use them in expressions that cannot be replicated in SQL and are, therefore, not supported.</span></span>  
  
## <a name="supported-operators"></a><span data-ttu-id="7388b-107">サポートされる演算子</span><span class="sxs-lookup"><span data-stu-id="7388b-107">Supported Operators</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="7388b-108"> は、次の演算子をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="7388b-108"> supports the following operators.</span></span>  
  
-   <span data-ttu-id="7388b-109">基本算術演算子</span><span class="sxs-lookup"><span data-stu-id="7388b-109">Basic arithmetic operators:</span></span>  
  
    -   `+`  
  
    -   <span data-ttu-id="7388b-110">`-` (減算)</span><span class="sxs-lookup"><span data-stu-id="7388b-110">`-` (subtraction)</span></span>  
  
    -   `*`  
  
    -   `/`  
  
    -   <span data-ttu-id="7388b-111">Visual Basic 整数除算 (`\`)</span><span class="sxs-lookup"><span data-stu-id="7388b-111">Visual Basic integer division (`\`)</span></span>  
  
    -   <span data-ttu-id="7388b-112">`%` (Visual Basic `Mod`)</span><span class="sxs-lookup"><span data-stu-id="7388b-112">`%` (Visual Basic `Mod`)</span></span>  
  
    -   `<<`  
  
    -   `>>`  
  
    -   <span data-ttu-id="7388b-113">`-` (単項マイナス符号)</span><span class="sxs-lookup"><span data-stu-id="7388b-113">`-` (unary negation)</span></span>  
  
-   <span data-ttu-id="7388b-114">基本比較演算子</span><span class="sxs-lookup"><span data-stu-id="7388b-114">Basic comparison operators:</span></span>  
  
    -   <span data-ttu-id="7388b-115">Visual Basic `=` および C# `==`</span><span class="sxs-lookup"><span data-stu-id="7388b-115">Visual Basic `=` and C# `==`</span></span>  
  
    -   <span data-ttu-id="7388b-116">Visual Basic `<>` および C# `!=`</span><span class="sxs-lookup"><span data-stu-id="7388b-116">Visual Basic `<>` and C# `!=`</span></span>  
  
    -   <span data-ttu-id="7388b-117">Visual Basic `Is/IsNot`</span><span class="sxs-lookup"><span data-stu-id="7388b-117">Visual Basic `Is/IsNot`</span></span>  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a><span data-ttu-id="7388b-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="7388b-118">See Also</span></span>  
 [<span data-ttu-id="7388b-119">データ型と関数</span><span class="sxs-lookup"><span data-stu-id="7388b-119">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [<span data-ttu-id="7388b-120">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="7388b-120">C# Operators</span></span>](http://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43)  
 [<span data-ttu-id="7388b-121">演算子</span><span class="sxs-lookup"><span data-stu-id="7388b-121">Operators</span></span>](../../../../../visual-basic/language-reference/operators/index.md)
