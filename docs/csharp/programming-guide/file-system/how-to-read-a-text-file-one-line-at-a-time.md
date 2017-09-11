---
title: "方法: テキスト ファイルを一度に 1 行読み込む (Visual C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
caps.latest.revision: 11
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
ms.openlocfilehash: e9327181d82a97559c7be99bb76a2a93118d796b
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-read-a-text-file-one-line-at-a-time-visual-c"></a><span data-ttu-id="05211-102">方法: テキスト ファイルを一度に 1 行読み込む (Visual C#)</span><span class="sxs-lookup"><span data-stu-id="05211-102">How to: Read a Text File One Line at a Time (Visual C#)</span></span>
<span data-ttu-id="05211-103">次の例では、`StreamReader` クラスの `ReadLine` メソッドを使用して、テキスト ファイルの内容を一度に 1 行ずつ文字列に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="05211-103">This example reads the contents of a text file, one line at a time, into a string using the `ReadLine` method of the `StreamReader` class.</span></span> <span data-ttu-id="05211-104">各テキスト行は文字列 `line` に格納され、画面に表示されます。</span><span class="sxs-lookup"><span data-stu-id="05211-104">Each text line is stored into the string `line` and displayed on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05211-105">例</span><span class="sxs-lookup"><span data-stu-id="05211-105">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="05211-106">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="05211-106">Compiling the Code</span></span>  
 <span data-ttu-id="05211-107">コードをコピーし、コンソール アプリケーションの `Main` メソッドに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="05211-107">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
 <span data-ttu-id="05211-108">`"c:\test.txt"` を実際のファイル名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="05211-108">Replace `"c:\test.txt"` with the actual file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="05211-109">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="05211-109">Robust Programming</span></span>  
 <span data-ttu-id="05211-110">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="05211-110">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="05211-111">ファイルが存在しない。</span><span class="sxs-lookup"><span data-stu-id="05211-111">The file may not exist.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="05211-112">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="05211-112">.NET Framework Security</span></span>  
 <span data-ttu-id="05211-113">ファイル名からファイルの内容を判断しないでください。</span><span class="sxs-lookup"><span data-stu-id="05211-113">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="05211-114">たとえば、`myFile.cs` ファイルが C# ソース ファイルとは限りません。</span><span class="sxs-lookup"><span data-stu-id="05211-114">For example, the file `myFile.cs` may not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05211-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="05211-115">See Also</span></span>  
 <span data-ttu-id="05211-116"><xref:System.IO?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="05211-116"><xref:System.IO?displayProperty=fullName></span></span>   
 <span data-ttu-id="05211-117">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="05211-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="05211-118">ファイル システムとレジストリ (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="05211-118">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)

