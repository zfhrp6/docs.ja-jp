---
title: "方法: テキスト ファイルから読み込む (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- StreamReader.ReadToEnd
dev_langs:
- CSharp
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
caps.latest.revision: 17
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
ms.openlocfilehash: bd0ad3e062c4d4b32fb6140cacba9a4a32674759
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a><span data-ttu-id="07e0f-102">方法: テキスト ファイルから読み込む (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="07e0f-102">How to: Read From a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="07e0f-103">この例では、<xref:System.IO.File?displayProperty=fullName> クラスの静的メソッド <xref:System.IO.File.ReadAllText%2A> と <xref:System.IO.File.ReadAllLines%2A> を使用してテキスト ファイルの内容を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="07e0f-103">This example reads the contents of a text file by using the static methods <xref:System.IO.File.ReadAllText%2A> and <xref:System.IO.File.ReadAllLines%2A> from the <xref:System.IO.File?displayProperty=fullName> class.</span></span>  
  
 <span data-ttu-id="07e0f-104"><xref:System.IO.StreamReader> の使用例については、「[方法: テキスト ファイルを一度に 1 行読み込む](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07e0f-104">For an example that uses <xref:System.IO.StreamReader>, see [How to: Read a Text File One Line at a Time](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07e0f-105">この例では、「[方法: テキスト ファイルに書き込む](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md)」のトピックで作成したファイルを使用しています。</span><span class="sxs-lookup"><span data-stu-id="07e0f-105">The files that are used in this example are created in the topic [How to: Write to a Text File](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="07e0f-106">例</span><span class="sxs-lookup"><span data-stu-id="07e0f-106">Example</span></span>  
 <span data-ttu-id="07e0f-107">[!code-cs[csFilesandFolders#4](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-read-from-a-text-file_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="07e0f-107">[!code-cs[csFilesandFolders#4](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-read-from-a-text-file_1.cs)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="07e0f-108">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="07e0f-108">Compiling the Code</span></span>  
 <span data-ttu-id="07e0f-109">コードをコピーし、C# のコンソール アプリケーションに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="07e0f-109">Copy the code and paste it into a C# console application.</span></span>  
  
 <span data-ttu-id="07e0f-110">「[方法: テキスト ファイルに書き込む](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md)」のテキスト ファイルを使用せずに独自のテキスト ファイルを使用する場合は、`ReadAllText` と `ReadAllLines` の引数を、ご使用のコンピューター上の該当するパスおよびファイル名に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="07e0f-110">If you are not using the text files from [How to: Write to a Text File](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md), replace the argument to `ReadAllText` and `ReadAllLines` with the appropriate path and file name on your computer.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="07e0f-111">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="07e0f-111">Robust Programming</span></span>  
 <span data-ttu-id="07e0f-112">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="07e0f-112">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="07e0f-113">ファイルが存在しない、または指定した場所に存在しない。</span><span class="sxs-lookup"><span data-stu-id="07e0f-113">The file doesn't exist or doesn't exist at the specified location.</span></span> <span data-ttu-id="07e0f-114">ファイル名のパスとスペルを確認してください。</span><span class="sxs-lookup"><span data-stu-id="07e0f-114">Check the path and the spelling of the file name.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="07e0f-115">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="07e0f-115">.NET Framework Security</span></span>  
 <span data-ttu-id="07e0f-116">ファイル名に基づいてファイルの内容を判断しないでください。</span><span class="sxs-lookup"><span data-stu-id="07e0f-116">Do not rely on the name of a file to determine the contents of the file.</span></span> <span data-ttu-id="07e0f-117">たとえば、`myFile.cs` というファイルが C# のソース ファイルではない可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="07e0f-117">For example, the file `myFile.cs` might not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07e0f-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="07e0f-118">See Also</span></span>  
 <span data-ttu-id="07e0f-119"><xref:System.IO?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="07e0f-119"><xref:System.IO?displayProperty=fullName></span></span>   
 <span data-ttu-id="07e0f-120">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="07e0f-120">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="07e0f-121">ファイル システムとレジストリ (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="07e0f-121">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)

