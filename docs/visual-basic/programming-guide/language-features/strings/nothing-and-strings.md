---
title: Visual Basic の Nothing と文字列
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: d03781209f0f9b021d540bd251c6c6025ad21422
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="8094f-102">Visual Basic の Nothing と文字列</span><span class="sxs-lookup"><span data-stu-id="8094f-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="8094f-103">Visual Basic ランタイムと[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]評価`Nothing`が異なるとなる文字列。</span><span class="sxs-lookup"><span data-stu-id="8094f-103">The Visual Basic runtime and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="8094f-104">Visual Basic ランタイムおよび .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8094f-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="8094f-105">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="8094f-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/nothing-and-strings_1.vb)]  
  
 <span data-ttu-id="8094f-106">Visual Basic ランタイムは通常評価`Nothing`として空の文字列 ("") です。</span><span class="sxs-lookup"><span data-stu-id="8094f-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="8094f-107">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]しない、ただし、および文字列操作を実行する試みが行われたときに例外がスロー`Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="8094f-107">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8094f-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="8094f-108">See Also</span></span>  
 [<span data-ttu-id="8094f-109">Visual Basic の文字列の概要</span><span class="sxs-lookup"><span data-stu-id="8094f-109">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
