---
title: "ファイルは既に開かれています。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3305831e840510e3f0b5bcb8bf847e39ea3ee4ba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="file-already-open"></a><span data-ttu-id="352d5-102">ファイルは既に開かれています。</span><span class="sxs-lookup"><span data-stu-id="352d5-102">File already open</span></span>
<span data-ttu-id="352d5-103">別の前に、ファイルを閉じる必要がある場合もあります`FileOpen`またはその他の操作が発生することができます。</span><span class="sxs-lookup"><span data-stu-id="352d5-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="352d5-104">このエラーでは以下の原因が考えられます。</span><span class="sxs-lookup"><span data-stu-id="352d5-104">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="352d5-105">連続した出力モード`FileOpen`操作が既に開いているファイルに対して実行されました。</span><span class="sxs-lookup"><span data-stu-id="352d5-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
-   <span data-ttu-id="352d5-106">ステートメントは、開いているファイルを参照します。</span><span class="sxs-lookup"><span data-stu-id="352d5-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="352d5-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="352d5-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="352d5-108">ステートメントを実行する前に、ファイルを閉じます。</span><span class="sxs-lookup"><span data-stu-id="352d5-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="352d5-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="352d5-109">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
