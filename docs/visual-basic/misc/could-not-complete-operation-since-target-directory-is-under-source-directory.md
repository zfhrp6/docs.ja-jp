---
title: "ターゲット ディレクトリがソース ディレクトリ内にあるため、操作を完了できませんでした"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0a17877b2335ee010a97f0b522bd4c399867cd7d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="73832-102">ターゲット ディレクトリがソース ディレクトリ内にあるため、操作を完了できませんでした</span><span class="sxs-lookup"><span data-stu-id="73832-102">Could not complete operation since target directory is under source directory</span></span>
<span data-ttu-id="73832-103">循環操作が失敗しました。</span><span class="sxs-lookup"><span data-stu-id="73832-103">A cyclic operation has failed.</span></span> <span data-ttu-id="73832-104">循環操作は循環しているため、完了できません。</span><span class="sxs-lookup"><span data-stu-id="73832-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="73832-105">たとえば、オブジェクト A がオブジェクト B の継承を試行し、同様にオブジェクト B がオブジェクト A の継承を試行するような場合です。</span><span class="sxs-lookup"><span data-stu-id="73832-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="73832-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="73832-106">To correct this error</span></span>  
  
-   <span data-ttu-id="73832-107">継承を行うときには、参照の循環がないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="73832-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73832-108">参照</span><span class="sxs-lookup"><span data-stu-id="73832-108">See Also</span></span>  
 [<span data-ttu-id="73832-109">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="73832-109">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="73832-110">デバッグの基礎: ブレークポイント</span><span class="sxs-lookup"><span data-stu-id="73832-110">Debugging Basics: Breakpoints</span></span>](http://msdn.microsoft.com/library/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)
