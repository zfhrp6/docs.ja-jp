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
# <a name="derived-math-functions-visual-basic"></a>数値演算関数の導出 (Visual Basic)
次の表はの組み込みの数値演算関数から派生可能な非組み込みの数値演算関数、<xref:System.Math?displayProperty=nameWithType>オブジェクト。 組み込みの数値演算関数は追加することでアクセスできる`Imports System.Math`ファイルまたはプロジェクトにします。  
  
|関数|同等の派生|  
|--------------|-------------------------|  
|正割 (Sec(x))|1/Cos(x)|  
|余割 (Csc(x))|1/Sin(x)|  
|コタンジェント (Ctan(x))|1/Tan(x)|  
|逆正弦 (Asin(x))|Atan (x/Sqrt (-x * x + 1))|  
|逆余弦 (Acos(x))|Atan (-x/Sqrt (-x * x + 1)) + 2 \* Atan(1)|  
|逆正割 (Asec(x))|2 * Atan(1) – Atan(Sign(x)/Sqrt (x \* x 1))|  
|逆余割 (Acsc(x))|Atan(Sign(x)/Sqrt (x * x 1))|  
|逆余接 (Acot(x))|2 * Atan(1) - Atan(x)|  
|双曲線正弦 (Sinh(x))|(関数: Exp(-x))/2|  
|双曲線余弦 (Cosh(x))|(関数 + Exp(-x))/2|  
|双曲線正接 (Tanh(x))|(関数: Exp(-x))/(関数 + Exp(-x))|  
|双曲線正割 (Sech(x))|2/(関数 + Exp(-x))|  
|双曲線余割 (Csch(x))|2/(関数: Exp(-x))|  
|双曲線余接 (Coth(x))|(関数 + Exp(-x))/(関数: Exp(-x))|  
|逆双曲線正弦 (Asinh(x))|ログ (x + Sqrt (x * x + 1))|  
|逆ハイパーボリック コサイン (Acosh(x))|ログ (x + Sqrt (x * x 1))|  
|逆双曲線正接 (Atanh(x))|ログ ((1 + x)/(1 – x))/2|  
|逆双曲線正割 (AsecH(x))|ログ ((Sqrt (-x * x + 1) + 1)/x)|  
|逆双曲線余割 (Acsch(x))|Log((Sign(x) * Sqrt (x \* x + 1) + 1)/x)|  
|逆双曲線余接 (Acoth(x))|ログ ((x + 1)/(x – 1))/2|  
  
## <a name="see-also"></a>関連項目  
 [数値演算関数](../../../visual-basic/language-reference/functions/math-functions.md)
