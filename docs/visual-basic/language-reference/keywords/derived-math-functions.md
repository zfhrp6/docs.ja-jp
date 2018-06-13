---
title: 数値演算関数の導出 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operations, derived math functions
- cosecant function
- arcsecant function
- arccotangent function
- functions [Visual Basic], derived math functions
- inverse functions
- math functions, derived
- derived math functions
- cotangent function
- angles
- secant function
- trigonometric functions
- logarithms
- arccosecant function
- hyperbolic functions
- arcsine function
- degrees
- arccosine function
ms.assetid: 63e449d8-9444-44fb-8db1-6d9cf346e2aa
ms.openlocfilehash: 87faa623f5b145eec8b88e350fce4171125324dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33596809"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="09ea3-102">数値演算関数の導出 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09ea3-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="09ea3-103">次の表はの組み込みの数値演算関数から派生可能な非組み込みの数値演算関数、<xref:System.Math?displayProperty=nameWithType>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="09ea3-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="09ea3-104">組み込みの数値演算関数は追加することでアクセスできる`Imports System.Math`ファイルまたはプロジェクトにします。</span><span class="sxs-lookup"><span data-stu-id="09ea3-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="09ea3-105">関数</span><span class="sxs-lookup"><span data-stu-id="09ea3-105">Function</span></span>|<span data-ttu-id="09ea3-106">同等の派生</span><span class="sxs-lookup"><span data-stu-id="09ea3-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="09ea3-107">正割 (Sec(x))</span><span class="sxs-lookup"><span data-stu-id="09ea3-107">Secant (Sec(x))</span></span>|<span data-ttu-id="09ea3-108">1/Cos(x)</span><span class="sxs-lookup"><span data-stu-id="09ea3-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="09ea3-109">余割 (Csc(x))</span><span class="sxs-lookup"><span data-stu-id="09ea3-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="09ea3-110">1/Sin(x)</span><span class="sxs-lookup"><span data-stu-id="09ea3-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="09ea3-111">コタンジェント (Ctan(x))</span><span class="sxs-lookup"><span data-stu-id="09ea3-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="09ea3-112">1/Tan(x)</span><span class="sxs-lookup"><span data-stu-id="09ea3-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="09ea3-113">逆正弦 (Asin(x))</span><span class="sxs-lookup"><span data-stu-id="09ea3-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="09ea3-114">Atan (x/Sqrt (-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="09ea3-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="09ea3-115">逆余弦 (Acos(x))</span><span class="sxs-lookup"><span data-stu-id="09ea3-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="09ea3-116">Atan (-x/Sqrt (-x * x + 1)) + 2 \* Atan(1)</span><span class="sxs-lookup"><span data-stu-id="09ea3-116">Atan(-x / Sqrt(-x * x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="09ea3-117">逆正割 (Asec(x))</span><span class="sxs-lookup"><span data-stu-id="09ea3-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="09ea3-118">2 * Atan(1) – Atan(Sign(x)/Sqrt (x \* x 1))</span><span class="sxs-lookup"><span data-stu-id="09ea3-118">2 * Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="09ea3-119">逆余割 (Acsc(x))</span><span class="sxs-lookup"><span data-stu-id="09ea3-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="09ea3-120">Atan(Sign(x)/Sqrt (x \* x 1))</span><span class="sxs-lookup"><span data-stu-id="09ea3-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="09ea3-121">逆余接 (Acot(x))</span><span class="sxs-lookup"><span data-stu-id="09ea3-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="09ea3-122">2 \* Atan(1) - Atan(x)</span><span class="sxs-lookup"><span data-stu-id="09ea3-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="09ea3-123">双曲線正弦 (Sinh(x))</span><span class="sxs-lookup"><span data-stu-id="09ea3-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="09ea3-124">(関数: Exp(-x))/2</span><span class="sxs-lookup"><span data-stu-id="09ea3-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="09ea3-125">双曲線余弦 (Cosh(x))</span><span class="sxs-lookup"><span data-stu-id="09ea3-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="09ea3-126">(関数 + Exp(-x))/2</span><span class="sxs-lookup"><span data-stu-id="09ea3-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="09ea3-127">双曲線正接 (Tanh(x))</span><span class="sxs-lookup"><span data-stu-id="09ea3-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="09ea3-128">(関数: Exp(-x))/(関数 + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="09ea3-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="09ea3-129">双曲線正割 (Sech(x))</span><span class="sxs-lookup"><span data-stu-id="09ea3-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="09ea3-130">2/(関数 + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="09ea3-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="09ea3-131">双曲線余割 (Csch(x))</span><span class="sxs-lookup"><span data-stu-id="09ea3-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="09ea3-132">2/(関数: Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="09ea3-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="09ea3-133">双曲線余接 (Coth(x))</span><span class="sxs-lookup"><span data-stu-id="09ea3-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="09ea3-134">(関数 + Exp(-x))/(関数: Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="09ea3-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="09ea3-135">逆双曲線正弦 (Asinh(x))</span><span class="sxs-lookup"><span data-stu-id="09ea3-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="09ea3-136">ログ (x + Sqrt (x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="09ea3-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="09ea3-137">逆ハイパーボリック コサイン (Acosh(x))</span><span class="sxs-lookup"><span data-stu-id="09ea3-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="09ea3-138">ログ (x + Sqrt (x \* x 1))</span><span class="sxs-lookup"><span data-stu-id="09ea3-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="09ea3-139">逆双曲線正接 (Atanh(x))</span><span class="sxs-lookup"><span data-stu-id="09ea3-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="09ea3-140">ログ ((1 + x)/(1 – x))/2</span><span class="sxs-lookup"><span data-stu-id="09ea3-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="09ea3-141">逆双曲線正割 (AsecH(x))</span><span class="sxs-lookup"><span data-stu-id="09ea3-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="09ea3-142">ログ ((Sqrt (-x \* x + 1) + 1)/x)</span><span class="sxs-lookup"><span data-stu-id="09ea3-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="09ea3-143">逆双曲線余割 (Acsch(x))</span><span class="sxs-lookup"><span data-stu-id="09ea3-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="09ea3-144">Log((Sign(x) * Sqrt (x \* x + 1) + 1)/x)</span><span class="sxs-lookup"><span data-stu-id="09ea3-144">Log((Sign(x) * Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="09ea3-145">逆双曲線余接 (Acoth(x))</span><span class="sxs-lookup"><span data-stu-id="09ea3-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="09ea3-146">ログ ((x + 1)/(x – 1))/2</span><span class="sxs-lookup"><span data-stu-id="09ea3-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="09ea3-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="09ea3-147">See Also</span></span>  
 [<span data-ttu-id="09ea3-148">数値演算関数</span><span class="sxs-lookup"><span data-stu-id="09ea3-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
