---
title: '方法: テキスト ファイルを一度に 1 行読み込む (Visual C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: 2ed0069f9313955edc2cc46ecfd395a5f1ac2852
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339736"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-visual-c"></a><span data-ttu-id="af979-102">方法: テキスト ファイルを一度に 1 行読み込む (Visual C#)</span><span class="sxs-lookup"><span data-stu-id="af979-102">How to: Read a Text File One Line at a Time (Visual C#)</span></span>
<span data-ttu-id="af979-103">次の例では、`StreamReader` クラスの `ReadLine` メソッドを使用して、テキスト ファイルの内容を一度に 1 行ずつ文字列に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="af979-103">This example reads the contents of a text file, one line at a time, into a string using the `ReadLine` method of the `StreamReader` class.</span></span> <span data-ttu-id="af979-104">各テキスト行は文字列 `line` に格納され、画面に表示されます。</span><span class="sxs-lookup"><span data-stu-id="af979-104">Each text line is stored into the string `line` and displayed on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af979-105">例</span><span class="sxs-lookup"><span data-stu-id="af979-105">Example</span></span>  
  
```  
int counter = 0;  
string line;  
  
// Read the file and display it line by line.  
System.IO.StreamReader file =   
    new System.IO.StreamReader(@"c:\test.txt");  
while((line = file.ReadLine()) != null)  
{  
    System.Console.WriteLine (line);  
    counter++;  
}  
  
file.Close();  
System.Console.WriteLine("There were {0} lines.", counter);  
// Suspend the screen.  
System.Console.ReadLine();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="af979-106">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="af979-106">Compiling the Code</span></span>  
 <span data-ttu-id="af979-107">コードをコピーし、コンソール アプリケーションの `Main` メソッドに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="af979-107">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
 <span data-ttu-id="af979-108">`"c:\test.txt"` を実際のファイル名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="af979-108">Replace `"c:\test.txt"` with the actual file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="af979-109">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="af979-109">Robust Programming</span></span>  
 <span data-ttu-id="af979-110">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="af979-110">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="af979-111">ファイルが存在しない。</span><span class="sxs-lookup"><span data-stu-id="af979-111">The file may not exist.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="af979-112">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="af979-112">.NET Framework Security</span></span>  
 <span data-ttu-id="af979-113">ファイル名からファイルの内容を判断しないでください。</span><span class="sxs-lookup"><span data-stu-id="af979-113">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="af979-114">たとえば、`myFile.cs` ファイルが C# ソース ファイルとは限りません。</span><span class="sxs-lookup"><span data-stu-id="af979-114">For example, the file `myFile.cs` may not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af979-115">参照</span><span class="sxs-lookup"><span data-stu-id="af979-115">See Also</span></span>  
 <xref:System.IO?displayProperty=nameWithType>  
 [<span data-ttu-id="af979-116">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="af979-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="af979-117">ファイル システムとレジストリ (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="af979-117">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
