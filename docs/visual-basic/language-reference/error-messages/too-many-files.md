---
title: "ファイルが多すぎます。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID67
ms.assetid: 2ff203e2-bba6-43ae-b72f-8e92a881c98f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 506f0735956267d51b575cd26b628605e9db38cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="too-many-files"></a><span data-ttu-id="f53ca-102">ファイルが多すぎます。</span><span class="sxs-lookup"><span data-stu-id="f53ca-102">Too many files</span></span>
<span data-ttu-id="f53ca-103">指定された数より多くのファイルが開かれているかよりオペレーティング システムの制限、ルート ディレクトリにファイルが作成されましたが、**ファイル =** CONFIG で設定します。SYS ファイルです。</span><span class="sxs-lookup"><span data-stu-id="f53ca-103">Either more files have been created in the root directory than the operating system permits, or more files have been opened than the number specified in the **files=** setting in your CONFIG.SYS file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f53ca-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="f53ca-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="f53ca-105">プログラムが開く、閉じるか、ルート ディレクトリでファイルを保存している場合、は、サブディレクトリを使用するようにプログラムを変更します。</span><span class="sxs-lookup"><span data-stu-id="f53ca-105">If your program is opening, closing, or saving files in the root directory, change your program so that it uses a subdirectory.</span></span>  
  
2.  <span data-ttu-id="f53ca-106">指定されたファイルの数を増やす、**ファイル =** CONFIG で設定します。SYS ファイルを開き、コンピューターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="f53ca-106">Increase the number of files specified in your **files=** setting in your CONFIG.SYS file, and restart your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f53ca-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="f53ca-107">See Also</span></span>  
 [<span data-ttu-id="f53ca-108">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="f53ca-108">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
