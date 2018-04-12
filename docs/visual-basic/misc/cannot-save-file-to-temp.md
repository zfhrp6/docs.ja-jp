---
title: ファイルを TEMP に保存できません
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID735
ms.assetid: 1055fc15-9641-43b2-a40c-a0a9fbbb34b2
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3196f5f70405c6bf7ab8eda3d056c5a86eca57f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="cannot-save-file-to-temp"></a><span data-ttu-id="73696-102">ファイルを TEMP に保存できません</span><span class="sxs-lookup"><span data-stu-id="73696-102">Cannot save file to TEMP</span></span>
<span data-ttu-id="73696-103">コンポーネントが TEMP という名前のディレクトリを見つけられないか、または TEMP ディレクトリが含まれているドライブまたはパーティションには情報を保存するための十分な領域が不足しています。</span><span class="sxs-lookup"><span data-stu-id="73696-103">Either a component cannot find a directory named TEMP, or the drive or partition containing the TEMP directory lacks sufficient space to save information.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="73696-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="73696-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="73696-105">"TEMP" という名前のディレクトリを作成し、そのパスに等しい TEMP 環境変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="73696-105">Create a directory named "TEMP" and set the TEMP environment variable equal to its path.</span></span>  
  
2.  <span data-ttu-id="73696-106">不要なファイルを消去してドライブに領域を確保するか、または別のパーティションに TEMP ディレクトリを作成し、そのパスに等しい TEMP 環境変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="73696-106">Make space on the drive by erasing unnecessary files, or create a TEMP directory on another partition and set the TEMP environment variable equal to its path.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73696-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="73696-107">See Also</span></span>  
 [<span data-ttu-id="73696-108">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="73696-108">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)
