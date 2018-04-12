---
title: '&#39; 必要な一時ファイルを作成できません。'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID322
ms.assetid: 53617b5b-eb06-4188-b4c2-8607cb9fbc79
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dbb1c65318f954249da097b026583b09ad340e20
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="can39t-create-necessary-temporary-file"></a><span data-ttu-id="59cdd-102">&#39; 必要な一時ファイルを作成できません。</span><span class="sxs-lookup"><span data-stu-id="59cdd-102">Can&#39;t create necessary temporary file</span></span>
<span data-ttu-id="59cdd-103">いずれかのドライブがいっぱい、TEMP 環境変数で指定されたディレクトリを格納しているか、TEMP 環境変数が無効であるか読み取り専用のドライブまたはディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="59cdd-103">Either the drive is full that contains the directory specified by the TEMP environment variable, or the TEMP environment variable specifies an invalid or read-only drive or directory.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="59cdd-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="59cdd-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="59cdd-105">いっぱいの場合は、ドライブからファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="59cdd-105">Delete files from the drive, if full.</span></span>  
  
2.  <span data-ttu-id="59cdd-106">TEMP 環境変数では、別のドライブを指定します。</span><span class="sxs-lookup"><span data-stu-id="59cdd-106">Specify a different drive in the TEMP environment variable.</span></span>  
  
3.  <span data-ttu-id="59cdd-107">TEMP 環境変数の有効なドライブを指定します。</span><span class="sxs-lookup"><span data-stu-id="59cdd-107">Specify a valid drive for the TEMP environment variable.</span></span>  
  
4.  <span data-ttu-id="59cdd-108">現在指定されているドライブまたはディレクトリから読み取り専用の制限を削除します。</span><span class="sxs-lookup"><span data-stu-id="59cdd-108">Remove the read-only restriction from the currently specified drive or directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59cdd-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="59cdd-109">See Also</span></span>  
 [<span data-ttu-id="59cdd-110">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="59cdd-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
