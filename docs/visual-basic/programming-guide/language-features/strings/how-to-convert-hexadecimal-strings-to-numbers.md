---
title: "方法: 16 進文字列を数値に変換する (Visual Basic)"
ms.custom: 
ms.date: 01/31/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
author: petrusha
ms.author: ronpet
ms.manager: wpickett
ms.openlocfilehash: c35ac615e3f87710f934a1cf66e6546625298bd0
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a><span data-ttu-id="1ad74-102">方法: 16 進文字列を数値に変換する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ad74-102">How to: Convert Hexadecimal Strings to Numbers (Visual Basic)</span></span>
<span data-ttu-id="1ad74-103">この例では、16 進文字列に変換を使用して、整数、<xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="1ad74-103">This example converts a hexadecimal string to an integer using the <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="to-convert-a-hexadecimal-string-to-a-number"></a><span data-ttu-id="1ad74-104">16 進数文字列を数値に変換するには</span><span class="sxs-lookup"><span data-stu-id="1ad74-104">To convert a hexadecimal string to a number</span></span>  
  
-   <span data-ttu-id="1ad74-105">使用して、<xref:System.Convert.ToInt32(System.String,System.Int32)>ベース-16 を整数で表された数値に変換します。</span><span class="sxs-lookup"><span data-stu-id="1ad74-105">Use the <xref:System.Convert.ToInt32(System.String,System.Int32)> method to convert the number expressed in base-16 to an integer.</span></span>  
  
     <span data-ttu-id="1ad74-106">最初の引数、<xref:System.Convert.ToInt32(System.String,System.Int32)>メソッドは変換する文字列。</span><span class="sxs-lookup"><span data-stu-id="1ad74-106">The first argument of the <xref:System.Convert.ToInt32(System.String,System.Int32)> method is the string to convert.</span></span> <span data-ttu-id="1ad74-107">2 番目の引数で数を表現がどのベースを説明します。16 進数が 16 進です。</span><span class="sxs-lookup"><span data-stu-id="1ad74-107">The second argument describes what base the number is expressed in; hexadecimal is base 16.</span></span>  
  
     [!code-vb[HexConversion](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-hexadecimal-strings-to-numbers_1.vb)]  

- <span data-ttu-id="1ad74-108">16 進数文字列が、次の制限を持つことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1ad74-108">Note that the hexadecimal string has the following restrictions:</span></span>

   - <span data-ttu-id="1ad74-109">これを含めることはできません、`&h`プレフィックス。</span><span class="sxs-lookup"><span data-stu-id="1ad74-109">It cannot include the `&h` prefix.</span></span>
   - <span data-ttu-id="1ad74-110">これを含めることはできません、`_`桁区切り記号。</span><span class="sxs-lookup"><span data-stu-id="1ad74-110">It cannot include the `_` digit separator.</span></span>

   <span data-ttu-id="1ad74-111">プレフィックスまたは桁区切り記号が存在する場合への呼び出し、<xref:System.Convert.ToInt32(System.String,System.Int32)>メソッドがスローされます、<xref:System.FormatException>です。</span><span class="sxs-lookup"><span data-stu-id="1ad74-111">If the prefix or a digit separator is present, the call to the <xref:System.Convert.ToInt32(System.String,System.Int32)> method throws a <xref:System.FormatException>.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ad74-112">参照</span><span class="sxs-lookup"><span data-stu-id="1ad74-112">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>  
 <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
