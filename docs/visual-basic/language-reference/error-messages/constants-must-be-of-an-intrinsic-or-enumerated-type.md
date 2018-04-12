---
title: 定数は、class、structure、型パラメーター、または array 型ではなく、組み込み型または列挙型でなければなりません。
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 702472751810c2d2bd08ece944ef0ffafc2049b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a><span data-ttu-id="644b7-102">定数は、class、structure、型パラメーター、または array 型ではなく、組み込み型または列挙型でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="644b7-102">Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type</span></span>
<span data-ttu-id="644b7-103">クラス、構造体、または配列型、またはそれを含むジェネリック型によって定義された型パラメーターと定数を宣言しようとしました。</span><span class="sxs-lookup"><span data-stu-id="644b7-103">You have attempted to declare a constant as a class, structure, or array type, or as a type parameter defined by a containing generic type.</span></span>  
  
 <span data-ttu-id="644b7-104">定数は、組み込みの型でなければなりません (`Boolean`、 `Byte`、 `Date`、 `Decimal`、 `Double`、 `Integer`、 `Long`、 `Object`、 `SByte`、 `Short`、 `Single`、 `String`、 `UInteger`、 `ULong`、または`UShort`)、または`Enum`型が整数型のいずれかに基づいています。</span><span class="sxs-lookup"><span data-stu-id="644b7-104">Constants must be of an intrinsic type (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, or `UShort`), or an `Enum` type based on one of the integral types.</span></span>  
  
 <span data-ttu-id="644b7-105">**エラー ID:** BC30424</span><span class="sxs-lookup"><span data-stu-id="644b7-105">**Error ID:** BC30424</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="644b7-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="644b7-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="644b7-107">組み込み関数として定数を宣言または`Enum`型です。</span><span class="sxs-lookup"><span data-stu-id="644b7-107">Declare the constant as an intrinsic or `Enum` type.</span></span>  
  
2.  <span data-ttu-id="644b7-108">定数にはまた、特殊な値など`True`、 `False`、または`Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="644b7-108">A constant can also be a special value such as `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="644b7-109">コンパイラは、これら定義済みの値を適切な組み込み型であることを検討します。</span><span class="sxs-lookup"><span data-stu-id="644b7-109">The compiler considers these predefined values to be of the appropriate intrinsic type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="644b7-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="644b7-110">See Also</span></span>  
 [<span data-ttu-id="644b7-111">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="644b7-111">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [<span data-ttu-id="644b7-112">データの種類</span><span class="sxs-lookup"><span data-stu-id="644b7-112">Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="644b7-113">データの種類</span><span class="sxs-lookup"><span data-stu-id="644b7-113">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)
