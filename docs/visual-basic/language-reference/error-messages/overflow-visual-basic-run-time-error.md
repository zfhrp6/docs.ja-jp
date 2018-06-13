---
title: オーバーフローしました。(Visual Basic ランタイム エラー)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: 9db79071c4895d49680352bde2d0824a3756d941
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594176"
---
# <a name="overflow-visual-basic-run-time-error"></a><span data-ttu-id="c3efc-102">オーバーフローしました。(Visual Basic ランタイム エラー)</span><span class="sxs-lookup"><span data-stu-id="c3efc-102">Overflow (Visual Basic Run-Time Error)</span></span>
<span data-ttu-id="c3efc-103">割り当てのターゲットの制限を超える値を代入しようとすると、オーバーフローが発生します。</span><span class="sxs-lookup"><span data-stu-id="c3efc-103">An overflow results when you attempt an assignment that exceeds the limits of the assignment's target.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c3efc-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="c3efc-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="c3efc-105">値の範囲が広いを割り当て、計算、およびデータ型変換が大きすぎるため、その値の型で使用できる変数の範囲内で表現されないし、型の変数に値を代入の結果が保持できることを確認してください。、必要な場合です。</span><span class="sxs-lookup"><span data-stu-id="c3efc-105">Make sure that results of assignments, calculations, and data type conversions are not too large to be represented within the range of variables allowed for that type of value, and assign the value to a variable of a type that can hold a larger range of values, if necessary.</span></span>  
  
2.  <span data-ttu-id="c3efc-106">プロパティへの割り当てに合わせて、によって行われたプロパティの範囲を確認します。</span><span class="sxs-lookup"><span data-stu-id="c3efc-106">Make sure assignments to properties fit the range of the property to which they are made.</span></span>  
  
3.  <span data-ttu-id="c3efc-107">整数に変換する計算で使用される数値の整数を超える結果がないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="c3efc-107">Make sure that numbers used in calculations that are coerced into integers do not have results larger than integers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3efc-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="c3efc-108">See Also</span></span>  
 <xref:System.Int32.MaxValue?displayProperty=nameWithType>  
 <xref:System.Double.MaxValue?displayProperty=nameWithType>  
 [<span data-ttu-id="c3efc-109">データの種類</span><span class="sxs-lookup"><span data-stu-id="c3efc-109">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="c3efc-110">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="c3efc-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
