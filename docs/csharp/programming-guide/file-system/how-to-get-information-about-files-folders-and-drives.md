---
title: "方法 : ファイル、フォルダー、およびドライブに関する情報を取得する (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d5652dda53a0192ce39be497b6e8ad3c97bef042
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a><span data-ttu-id="af052-102">方法 : ファイル、フォルダー、およびドライブに関する情報を取得する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="af052-102">How to: Get Information About Files, Folders, and Drives  (C# Programming Guide)</span></span>
<span data-ttu-id="af052-103">.NET Framework では、次のクラスを使用して、ファイル システム情報にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="af052-103">In the .NET Framework, you can access file system information by using the following classes:</span></span>  
  
-   <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.Directory?displayProperty=nameWithType>  
  
-   <xref:System.IO.File?displayProperty=nameWithType>  
  
 <span data-ttu-id="af052-104"><xref:System.IO.FileInfo> クラスと <xref:System.IO.DirectoryInfo> クラスはファイルまたはディレクトリを表し、NTFS ファイル システムでサポートされるファイル属性の多くを公開するプロパティを含みます。</span><span class="sxs-lookup"><span data-stu-id="af052-104">The <xref:System.IO.FileInfo> and <xref:System.IO.DirectoryInfo> classes represent a file or directory and contain properties that expose many of the file attributes that are supported by the NTFS file system.</span></span> <span data-ttu-id="af052-105">また、ファイルとフォルダーを開く、閉じる、移動する、および削除するためのメソッドも含まれます。</span><span class="sxs-lookup"><span data-stu-id="af052-105">They also contain methods for opening, closing, moving, and deleting files and folders.</span></span> <span data-ttu-id="af052-106">コンストラクターに、ファイル、フォルダー、またはドライブの名前を表す文字列を渡すことで、クラスのインスタンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="af052-106">You can create instances of these classes by passing a string that represents the name of the file, folder, or drive in to the constructor:</span></span>  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 <span data-ttu-id="af052-107">また、<xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>、<xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>、および <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType> の呼び出しを使用して、ファイル、フォルダー、またはドライブの名前を取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="af052-107">You can also obtain the names of files, folders, or drives by using calls to <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>, and <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="af052-108"><xref:System.IO.Directory?displayProperty=nameWithType> クラスと <xref:System.IO.File?displayProperty=nameWithType> クラスは、ディレクトリとファイルに関する情報を取得するための静的メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="af052-108">The <xref:System.IO.Directory?displayProperty=nameWithType> and <xref:System.IO.File?displayProperty=nameWithType> classes provide static methods for retrieving information about directories and files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af052-109">例</span><span class="sxs-lookup"><span data-stu-id="af052-109">Example</span></span>  
 <span data-ttu-id="af052-110">次の例では、ファイルとフォルダーに関する情報にアクセスするさまざまな方法を示します。</span><span class="sxs-lookup"><span data-stu-id="af052-110">The following example shows various ways to access information about files and folders.</span></span>  
  
 [!code-csharp[csFilesandFolders#6](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-get-information-about-files-folders-and-drives_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="af052-111">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="af052-111">Robust Programming</span></span>  
 <span data-ttu-id="af052-112">ユーザー指定のパス文字列を処理する場合、次の条件の例外も処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="af052-112">When you process user-specified path strings, you should also handle exceptions for the following conditions:</span></span>  
  
-   <span data-ttu-id="af052-113">ファイル名が不適切である。</span><span class="sxs-lookup"><span data-stu-id="af052-113">The file name is malformed.</span></span> <span data-ttu-id="af052-114">たとえば、無効な文字が含まれている場合や、空白のみの場合です。</span><span class="sxs-lookup"><span data-stu-id="af052-114">For example, it contains invalid characters or only white space.</span></span>  
  
-   <span data-ttu-id="af052-115">ファイル名が NULL である。</span><span class="sxs-lookup"><span data-stu-id="af052-115">The file name is null.</span></span>  
  
-   <span data-ttu-id="af052-116">ファイル名の長さがシステムで定義された最大長を超えている。</span><span class="sxs-lookup"><span data-stu-id="af052-116">The file name is longer than the system-defined maximum length.</span></span>  
  
-   <span data-ttu-id="af052-117">ファイル名にコロン (:) が含まれている。</span><span class="sxs-lookup"><span data-stu-id="af052-117">The file name contains a colon (:).</span></span>  
  
 <span data-ttu-id="af052-118">指定したファイルの読み取りに必要なアクセス許可がアプリケーションに与えられていない場合、`Exists` メソッドは目的のパスが存在するかどうかに関係なく `false` を返します。ただし、例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="af052-118">If the application does not have sufficient permissions to read the specified file, the `Exists` method returns `false` regardless of whether a path exists; the method does not throw an exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af052-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="af052-119">See Also</span></span>  
 <xref:System.IO?displayProperty=nameWithType>  
 [<span data-ttu-id="af052-120">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="af052-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="af052-121">ファイル システムとレジストリ (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="af052-121">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
