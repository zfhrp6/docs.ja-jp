---
title: Set は実行時にはサポートされません
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID382
ms.assetid: cb7285d3-778f-423d-a2be-88573be8ad48
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c10691abf13ea00cc4eaea961b5ca6fd59a2be8d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="set-not-supported-at-run-time"></a><span data-ttu-id="dd11b-102">Set は実行時にはサポートされません</span><span class="sxs-lookup"><span data-stu-id="dd11b-102">Set not supported at run time</span></span>
<span data-ttu-id="dd11b-103">デザイン時にのみ値を設定できるプロパティを設定または変更しようとしました。</span><span class="sxs-lookup"><span data-stu-id="dd11b-103">You tried to set or change a property whose value can only be set at design time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dd11b-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="dd11b-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="dd11b-105">コードからプロパティへの参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="dd11b-105">Remove the reference to the property from your code.</span></span>  
  
2.  <span data-ttu-id="dd11b-106">実行時に、プロパティの値のみを返す参照に変更します。</span><span class="sxs-lookup"><span data-stu-id="dd11b-106">Change the reference to only return the value of the property at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd11b-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd11b-107">See Also</span></span>  
 [<span data-ttu-id="dd11b-108">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="dd11b-108">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
