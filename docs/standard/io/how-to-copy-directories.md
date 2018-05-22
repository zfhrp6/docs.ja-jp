---
title: '方法 : ディレクトリをコピーする'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1cfe07af216da1c35b093a1ca23e4d48c60a7bfe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-copy-directories"></a><span data-ttu-id="d19ea-102">方法 : ディレクトリをコピーする</span><span class="sxs-lookup"><span data-stu-id="d19ea-102">How to: Copy Directories</span></span>
<span data-ttu-id="d19ea-103">この例では、I/O クラスを使用して、別の場所にディレクトリの内容を同期的にコピーする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d19ea-103">This example demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span> <span data-ttu-id="d19ea-104">ユーザーは、サブディレクトリもコピーするかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="d19ea-104">In this example, the user can specify whether to also copy the subdirectories.</span></span> <span data-ttu-id="d19ea-105">サブディレクトリをコピーする場合、この例で使用するメソッドは、コピーするディレクトリがなくなるまで、各サブディレクトリ上で自身を呼び出し、再帰的にコピーを行います。</span><span class="sxs-lookup"><span data-stu-id="d19ea-105">If the subdirectories are copied, the method in this example recursively copies them by calling itself on each subsequent subdirectory until there are no more to copy.</span></span>  
  
 <span data-ttu-id="d19ea-106">ファイルを非同期的にコピーする例については、「 [Asynchronous File I/O](../../../docs/standard/io/asynchronous-file-i-o.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d19ea-106">For an example of copying files asynchronously, see [Asynchronous File I/O](../../../docs/standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d19ea-107">例</span><span class="sxs-lookup"><span data-stu-id="d19ea-107">Example</span></span>  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d19ea-108">参照</span><span class="sxs-lookup"><span data-stu-id="d19ea-108">See Also</span></span>  
 <xref:System.IO.FileInfo>  
 <xref:System.IO.DirectoryInfo>  
 <xref:System.IO.FileStream>  
 [<span data-ttu-id="d19ea-109">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="d19ea-109">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="d19ea-110">共通 I/O タスク</span><span class="sxs-lookup"><span data-stu-id="d19ea-110">Common I/O Tasks</span></span>](../../../docs/standard/io/common-i-o-tasks.md)  
 [<span data-ttu-id="d19ea-111">非同期ファイル I/O</span><span class="sxs-lookup"><span data-stu-id="d19ea-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)
