---
title: オーバーフローしました。(Visual Basic ランタイム エラー)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d1908ad576a499e79102aff23e3e2f11d7d99d52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="overflow-visual-basic-run-time-error"></a><span data-ttu-id="9d09c-102">オーバーフローしました。(Visual Basic ランタイム エラー)</span><span class="sxs-lookup"><span data-stu-id="9d09c-102">Overflow (Visual Basic Run-Time Error)</span></span>
<span data-ttu-id="9d09c-103">割り当てのターゲットの制限を超える値を代入しようとすると、オーバーフローが発生します。</span><span class="sxs-lookup"><span data-stu-id="9d09c-103">An overflow results when you attempt an assignment that exceeds the limits of the assignment's target.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9d09c-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="9d09c-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="9d09c-105">値の範囲が広いを割り当て、計算、およびデータ型変換が大きすぎるため、その値の型で使用できる変数の範囲内で表現されないし、型の変数に値を代入の結果が保持できることを確認してください。、必要な場合です。</span><span class="sxs-lookup"><span data-stu-id="9d09c-105">Make sure that results of assignments, calculations, and data type conversions are not too large to be represented within the range of variables allowed for that type of value, and assign the value to a variable of a type that can hold a larger range of values, if necessary.</span></span>  
  
2.  <span data-ttu-id="9d09c-106">プロパティへの割り当てに合わせて、によって行われたプロパティの範囲を確認します。</span><span class="sxs-lookup"><span data-stu-id="9d09c-106">Make sure assignments to properties fit the range of the property to which they are made.</span></span>  
  
3.  <span data-ttu-id="9d09c-107">整数に変換する計算で使用される数値の整数を超える結果がないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="9d09c-107">Make sure that numbers used in calculations that are coerced into integers do not have results larger than integers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d09c-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d09c-108">See Also</span></span>  
 <xref:System.Int32.MaxValue?displayProperty=nameWithType>  
 <xref:System.Double.MaxValue?displayProperty=nameWithType>  
 [<span data-ttu-id="9d09c-109">データの種類</span><span class="sxs-lookup"><span data-stu-id="9d09c-109">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="9d09c-110">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="9d09c-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
