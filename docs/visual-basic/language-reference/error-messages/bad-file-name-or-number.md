---
title: ファイル名または番号が正しくありません。
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3d7c8bae3df0e75a1c4f9afacdff681a553503d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="008a3-102">ファイル名または番号が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="008a3-102">Bad file name or number</span></span>
<span data-ttu-id="008a3-103">指定したファイルにアクセスしようとしているときにエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="008a3-103">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="008a3-104">このエラーの考えられる原因には。</span><span class="sxs-lookup"><span data-stu-id="008a3-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="008a3-105">ステートメントで指定されていないファイルの名前または番号のファイルを参照して、`FileOpen`で指定されたステートメントまたはを`FileOpen`ステートメントが、後で終了します。</span><span class="sxs-lookup"><span data-stu-id="008a3-105">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
-   <span data-ttu-id="008a3-106">ステートメントは、ファイル番号の範囲外にある数値を持つファイルを参照します。</span><span class="sxs-lookup"><span data-stu-id="008a3-106">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
-   <span data-ttu-id="008a3-107">ステートメントは、ファイル名または無効な数を表します。</span><span class="sxs-lookup"><span data-stu-id="008a3-107">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="008a3-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="008a3-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="008a3-109">ファイル名がで指定されたことを確認してください、`FileOpen`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="008a3-109">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="008a3-110">呼び出した場合、`FileClose`ステートメント引数を指定せず可能性がありますが誤って閉じた開いているすべてのファイルです。</span><span class="sxs-lookup"><span data-stu-id="008a3-110">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2.  <span data-ttu-id="008a3-111">コードの生成は、ファイルの番号にアルゴリズムによっては場合、は、数値は有効なを確認します。</span><span class="sxs-lookup"><span data-stu-id="008a3-111">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3.  <span data-ttu-id="008a3-112">オペレーティング システムの規約に準拠しているかどうかを確認するファイルの名前を確認します。</span><span class="sxs-lookup"><span data-stu-id="008a3-112">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="008a3-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="008a3-113">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>  
 [<span data-ttu-id="008a3-114">Visual Basic の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="008a3-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
