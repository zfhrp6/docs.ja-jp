---
title: "方法: ファイルおよびフォルダーのコピー、削除、および移動を行う (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 56383873674998fc0d6417a2abf4fa72e498f08f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="f0f27-102">方法: ファイルおよびフォルダーのコピー、削除、および移動を行う (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="f0f27-102">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>
<span data-ttu-id="f0f27-103">次の例では、<xref:System.IO?displayProperty=nameWithType> 名前空間から <xref:System.IO.File?displayProperty=nameWithType>、<xref:System.IO.Directory?displayProperty=nameWithType>、<xref:System.IO.FileInfo?displayProperty=nameWithType>、および <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> クラスを使用して、同期的な方法でファイルとフォルダーをコピー、移動および削除する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f0f27-103">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, and <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> classes from the <xref:System.IO?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="f0f27-104">これらの例では、進行状況バーやその他のユーザー インターフェイスは表示されません。</span><span class="sxs-lookup"><span data-stu-id="f0f27-104">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="f0f27-105">標準の進行状況ダイアログ ボックスを表示する場合は、「[方法: ファイル操作の [進行状況] ダイアログ ボックスを表示する](how-to-provide-a-progress-dialog-box-for-file-operations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f27-105">If you want to provide a standard progress dialog box, see [How to: Provide a Progress Dialog Box for File Operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="f0f27-106">複数のファイルを操作するときに進行状況を計算できるイベントを提供するには、<xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> を使用します。</span><span class="sxs-lookup"><span data-stu-id="f0f27-106">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="f0f27-107">プラットフォーム呼び出しを使用して、Windows シェルで関連するファイル関連メソッドを呼び出す方法もあります。</span><span class="sxs-lookup"><span data-stu-id="f0f27-107">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="f0f27-108">これらのファイル操作を非同期に実行する方法については、「[非同期ファイル I/O](https://msdn.microsoft.com/library/kztecsys)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0f27-108">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](https://msdn.microsoft.com/library/kztecsys).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0f27-109">例</span><span class="sxs-lookup"><span data-stu-id="f0f27-109">Example</span></span>  
 <span data-ttu-id="f0f27-110">次の例では、ファイルとディレクトリをコピーする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f0f27-110">The following example shows how to copy files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="f0f27-111">例</span><span class="sxs-lookup"><span data-stu-id="f0f27-111">Example</span></span>  
 <span data-ttu-id="f0f27-112">次の例では、ファイルとディレクトリを移動する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f0f27-112">The following example shows how to move files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="f0f27-113">例</span><span class="sxs-lookup"><span data-stu-id="f0f27-113">Example</span></span>  
 <span data-ttu-id="f0f27-114">次の例では、ファイルとディレクトリを削除する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f0f27-114">The following example shows how to delete files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f0f27-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="f0f27-115">See Also</span></span>  
 <xref:System.IO?displayProperty=nameWithType>  
 [<span data-ttu-id="f0f27-116">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="f0f27-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f0f27-117">ファイル システムとレジストリ (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="f0f27-117">File System and the Registry (C# Programming Guide)</span></span>](index.md)  
 <span data-ttu-id="f0f27-118">[方法: ファイル操作の [進行状況] ダイアログ ボックスを表示する](how-to-provide-a-progress-dialog-box-for-file-operations.md)</span><span class="sxs-lookup"><span data-stu-id="f0f27-118">[How to: Provide a Progress Dialog Box for File Operations](how-to-provide-a-progress-dialog-box-for-file-operations.md)</span></span>  
 [<span data-ttu-id="f0f27-119">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="f0f27-119">File and Stream I/O</span></span>](https://msdn.microsoft.com/library/k3352a4t)  
 [<span data-ttu-id="f0f27-120">共通 I/O タスク</span><span class="sxs-lookup"><span data-stu-id="f0f27-120">Common I/O Tasks</span></span>](https://msdn.microsoft.com/library/ms404278)
