---
title: "ターゲット ディレクトリがソース ディレクトリ内にあるため、操作を完了できませんでした"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 429d679157d25655ca73afef14ecd642f7cac37f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="f1902-102">ターゲット ディレクトリがソース ディレクトリ内にあるため、操作を完了できませんでした</span><span class="sxs-lookup"><span data-stu-id="f1902-102">Could not complete operation since target directory is under source directory</span></span>
<span data-ttu-id="f1902-103">循環操作が失敗しました。</span><span class="sxs-lookup"><span data-stu-id="f1902-103">A cyclic operation has failed.</span></span> <span data-ttu-id="f1902-104">循環操作は循環しているため、完了できません。</span><span class="sxs-lookup"><span data-stu-id="f1902-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="f1902-105">たとえば、オブジェクト A がオブジェクト B の継承を試行し、同様にオブジェクト B がオブジェクト A の継承を試行するような場合です。</span><span class="sxs-lookup"><span data-stu-id="f1902-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f1902-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="f1902-106">To correct this error</span></span>  
  
-   <span data-ttu-id="f1902-107">継承を行うときには、参照の循環がないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="f1902-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1902-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1902-108">See Also</span></span>  
 [<span data-ttu-id="f1902-109">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="f1902-109">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="f1902-110">デバッグの基礎: ブレークポイント</span><span class="sxs-lookup"><span data-stu-id="f1902-110">Debugging Basics: Breakpoints</span></span>](http://msdn.microsoft.com/en-us/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)
