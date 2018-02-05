---
title: "方法 : ディレクトリをコピーする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directory copying
- I/O [.NET Framework], copying directories
- subdirectory copying
- copying directories
- directories [.NET Framework], copying
ms.assetid: 5a969765-e5f8-4b4e-977e-90e2b0a1fe3c
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 43e9027c1dbfc831f598991374c22434e01fe7ff
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-copy-directories"></a><span data-ttu-id="f6882-102">方法 : ディレクトリをコピーする</span><span class="sxs-lookup"><span data-stu-id="f6882-102">How to: Copy Directories</span></span>
<span data-ttu-id="f6882-103">この例では、I/O クラスを使用して、別の場所にディレクトリの内容を同期的にコピーする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f6882-103">This example demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span> <span data-ttu-id="f6882-104">ユーザーは、サブディレクトリもコピーするかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f6882-104">In this example, the user can specify whether to also copy the subdirectories.</span></span> <span data-ttu-id="f6882-105">サブディレクトリをコピーする場合、この例で使用するメソッドは、コピーするディレクトリがなくなるまで、各サブディレクトリ上で自身を呼び出し、再帰的にコピーを行います。</span><span class="sxs-lookup"><span data-stu-id="f6882-105">If the subdirectories are copied, the method in this example recursively copies them by calling itself on each subsequent subdirectory until there are no more to copy.</span></span>  
  
 <span data-ttu-id="f6882-106">ファイルを非同期的にコピーする例については、「 [Asynchronous File I/O](../../../docs/standard/io/asynchronous-file-i-o.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6882-106">For an example of copying files asynchronously, see [Asynchronous File I/O](../../../docs/standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6882-107">例</span><span class="sxs-lookup"><span data-stu-id="f6882-107">Example</span></span>  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f6882-108">参照</span><span class="sxs-lookup"><span data-stu-id="f6882-108">See Also</span></span>  
 <xref:System.IO.FileInfo>  
 <xref:System.IO.DirectoryInfo>  
 <xref:System.IO.FileStream>  
 [<span data-ttu-id="f6882-109">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="f6882-109">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="f6882-110">共通 I/O タスク</span><span class="sxs-lookup"><span data-stu-id="f6882-110">Common I/O Tasks</span></span>](../../../docs/standard/io/common-i-o-tasks.md)  
 [<span data-ttu-id="f6882-111">非同期ファイル I/O</span><span class="sxs-lookup"><span data-stu-id="f6882-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)
