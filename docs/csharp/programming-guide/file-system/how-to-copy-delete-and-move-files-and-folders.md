---
title: "方法: ファイルおよびフォルダーのコピー、削除、および移動を行う (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a4cfec46e0af0056a0de20a1ed83a370cd010055
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="efa73-102">方法: ファイルおよびフォルダーのコピー、削除、および移動を行う (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="efa73-102">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>
<span data-ttu-id="efa73-103">次の例では、<xref:System.IO?displayProperty=fullName> 名前空間から <xref:System.IO.File?displayProperty=fullName>、<xref:System.IO.Directory?displayProperty=fullName>、<xref:System.IO.FileInfo?displayProperty=fullName>、および <xref:System.IO.DirectoryInfo?displayProperty=fullName> クラスを使用して、同期的な方法でファイルとフォルダーをコピー、移動および削除する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="efa73-103">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=fullName>, <xref:System.IO.Directory?displayProperty=fullName>, <xref:System.IO.FileInfo?displayProperty=fullName>, and <xref:System.IO.DirectoryInfo?displayProperty=fullName> classes from the <xref:System.IO?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="efa73-104">これらの例では、進行状況バーやその他のユーザー インターフェイスは表示されません。</span><span class="sxs-lookup"><span data-stu-id="efa73-104">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="efa73-105">標準の進行状況ダイアログ ボックスを表示する場合は、「[方法: ファイル操作の [進行状況] ダイアログ ボックスを表示する](how-to-provide-a-progress-dialog-box-for-file-operations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efa73-105">If you want to provide a standard progress dialog box, see [How to: Provide a Progress Dialog Box for File Operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="efa73-106">複数のファイルを操作するときに進行状況を計算できるイベントを提供するには、<xref:System.IO.FileSystemWatcher?displayProperty=fullName> を使用します。</span><span class="sxs-lookup"><span data-stu-id="efa73-106">Use <xref:System.IO.FileSystemWatcher?displayProperty=fullName> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="efa73-107">プラットフォーム呼び出しを使用して、Windows シェルで関連するファイル関連メソッドを呼び出す方法もあります。</span><span class="sxs-lookup"><span data-stu-id="efa73-107">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="efa73-108">これらのファイル操作を非同期に実行する方法については、「[非同期ファイル I/O](https://msdn.microsoft.com/library/kztecsys)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efa73-108">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](https://msdn.microsoft.com/library/kztecsys).</span></span>  
  
## <a name="example"></a><span data-ttu-id="efa73-109">例</span><span class="sxs-lookup"><span data-stu-id="efa73-109">Example</span></span>  
 <span data-ttu-id="efa73-110">次の例では、ファイルとディレクトリをコピーする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="efa73-110">The following example shows how to copy files and directories.</span></span>  
  
 <span data-ttu-id="efa73-111">[!code-cs[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="efa73-111">[!code-cs[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="efa73-112">例</span><span class="sxs-lookup"><span data-stu-id="efa73-112">Example</span></span>  
 <span data-ttu-id="efa73-113">次の例では、ファイルとディレクトリを移動する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="efa73-113">The following example shows how to move files and directories.</span></span>  
  
 <span data-ttu-id="efa73-114">[!code-cs[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="efa73-114">[!code-cs[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="efa73-115">例</span><span class="sxs-lookup"><span data-stu-id="efa73-115">Example</span></span>  
 <span data-ttu-id="efa73-116">次の例では、ファイルとディレクトリを削除する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="efa73-116">The following example shows how to delete files and directories.</span></span>  
  
 <span data-ttu-id="efa73-117">[!code-cs[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="efa73-117">[!code-cs[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efa73-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="efa73-118">See Also</span></span>  
 <span data-ttu-id="efa73-119"><xref:System.IO?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="efa73-119"><xref:System.IO?displayProperty=fullName></span></span>   
 <span data-ttu-id="efa73-120">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="efa73-120">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="efa73-121">[ファイル システムとレジストリ (C# プログラミング ガイド)](index.md) </span><span class="sxs-lookup"><span data-stu-id="efa73-121">[File System and the Registry (C# Programming Guide)](index.md) </span></span>  
 <span data-ttu-id="efa73-122">[方法: ファイル操作の [進行状況] ダイアログ ボックスを表示する](how-to-provide-a-progress-dialog-box-for-file-operations.md) </span><span class="sxs-lookup"><span data-stu-id="efa73-122">[How to: Provide a Progress Dialog Box for File Operations](how-to-provide-a-progress-dialog-box-for-file-operations.md) </span></span>  
 <span data-ttu-id="efa73-123">[ファイルおよびストリーム入出力](https://msdn.microsoft.com/library/k3352a4t) </span><span class="sxs-lookup"><span data-stu-id="efa73-123">[File and Stream I/O](https://msdn.microsoft.com/library/k3352a4t) </span></span>  
 [<span data-ttu-id="efa73-124">共通 I/O タスク</span><span class="sxs-lookup"><span data-stu-id="efa73-124">Common I/O Tasks</span></span>](https://msdn.microsoft.com/library/ms404278)

