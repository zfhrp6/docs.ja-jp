---
title: "アクセス許可は拒否されました。(Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID70
ms.assetid: 71f46756-f522-4814-aab4-492bf9924245
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c5d7965ebd42cb3e56d66966d035be9ba3d3957c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="permission-denied-visual-basic"></a><span data-ttu-id="d6cfa-102">アクセス許可は拒否されました。(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6cfa-102">Permission denied (Visual Basic)</span></span>
<span data-ttu-id="d6cfa-103">試みましたを書き込み可能ディスクに書き込む、またはロックされたファイルにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="d6cfa-103">An attempt was made to write to a write-protected disk or to access a locked file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d6cfa-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="d6cfa-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="d6cfa-105">読み取り専用のファイルを開くには、ファイルの書き込み禁止属性を変更します。</span><span class="sxs-lookup"><span data-stu-id="d6cfa-105">To open a write-protected file, change the write-protection attribute of the file.</span></span>  
  
2.  <span data-ttu-id="d6cfa-106">別のプロセスが、ファイルをロックしていないことを確認し、待ってから、他のプロセスが解放されるまで、ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="d6cfa-106">Make sure that another process has not locked the file, and wait to open the file until the other process releases it.</span></span>  
  
3.  <span data-ttu-id="d6cfa-107">レジストリにアクセスするには、ユーザーのアクセス許可がこの種類のレジストリへのアクセスを含めることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d6cfa-107">To access the registry, check that your user permissions include this type of registry access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6cfa-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6cfa-108">See Also</span></span>  
 [<span data-ttu-id="d6cfa-109">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="d6cfa-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
