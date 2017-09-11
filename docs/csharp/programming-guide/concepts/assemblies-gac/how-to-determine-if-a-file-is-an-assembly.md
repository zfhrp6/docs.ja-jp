---
title: "方法: ファイルがアセンブリであるかどうかを確認する (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ee402e28374040ab22173788dce421345b2ef3b5
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-determine-if-a-file-is-an-assembly-c"></a><span data-ttu-id="a53b3-102">方法: ファイルがアセンブリであるかどうかを確認する (C#)</span><span class="sxs-lookup"><span data-stu-id="a53b3-102">How to: Determine If a File Is an Assembly (C#)</span></span>
<span data-ttu-id="a53b3-103">ファイルが管理されていて、ファイルのメタデータにアセンブリ エントリが含まれている場合、そのファイルはアセンブリです。</span><span class="sxs-lookup"><span data-stu-id="a53b3-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="a53b3-104">アセンブリとメタデータの詳細については、「[アセンブリ マニフェスト](https://msdn.microsoft.com/library/1w45z383)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a53b3-104">For more information on assemblies and metadata, see the topic [Assembly Manifest](https://msdn.microsoft.com/library/1w45z383).</span></span>  
  
### <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="a53b3-105">ファイルがアセンブリかどうかを手動で確認する方法</span><span class="sxs-lookup"><span data-stu-id="a53b3-105">How to manually determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="a53b3-106">[Ildasm.exe (IL 逆アセンブラー)](https://msdn.microsoft.com/library/f7dy01k1) を起動します。</span><span class="sxs-lookup"><span data-stu-id="a53b3-106">Start the [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1).</span></span>  
  
2.  <span data-ttu-id="a53b3-107">テストするファイルを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="a53b3-107">Load the file you wish to test.</span></span>  
  
3.  <span data-ttu-id="a53b3-108">**ILDASM** で、そのファイルが移植可能な実行可能 (PE) ファイルではないと報告された場合、そのファイルはアセンブリでありません。</span><span class="sxs-lookup"><span data-stu-id="a53b3-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="a53b3-109">詳細については、「[方法: アセンブリの内容を表示する](../../../../framework/app-domains/how-to-view-assembly-contents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a53b3-109">For more information, see the topic [How to: View Assembly Contents](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span></span>  
  
### <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="a53b3-110">ファイルがアセンブリかどうかをプログラムによって確認する方法</span><span class="sxs-lookup"><span data-stu-id="a53b3-110">How to programmatically determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="a53b3-111">テストするファイルの完全パスと名前を渡して、<xref:System.Reflection.AssemblyName.GetAssemblyName%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a53b3-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method, passing the full file path and name of the file you are testing.</span></span>  
  
2.  <span data-ttu-id="a53b3-112"><xref:System.BadImageFormatException> 例外がスローされた場合、ファイルはアセンブリでありません。</span><span class="sxs-lookup"><span data-stu-id="a53b3-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a53b3-113">例</span><span class="sxs-lookup"><span data-stu-id="a53b3-113">Example</span></span>  
 <span data-ttu-id="a53b3-114">次の例では、DLL がアセンブリかどうかをテストして確認します。</span><span class="sxs-lookup"><span data-stu-id="a53b3-114">This example tests a DLL to see if it is an assembly.</span></span>  
  
```  
class TestAssembly  
{  
    static void Main()  
    {  
  
        try  
        {  
            System.Reflection.AssemblyName testAssembly =  
                System.Reflection.AssemblyName.GetAssemblyName(@"C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll");  
  
            System.Console.WriteLine("Yes, the file is an assembly.");  
        }  
  
        catch (System.IO.FileNotFoundException)  
        {  
            System.Console.WriteLine("The file cannot be found.");  
        }  
  
        catch (System.BadImageFormatException)  
        {  
            System.Console.WriteLine("The file is not an assembly.");  
        }  
  
        catch (System.IO.FileLoadException)  
        {  
            System.Console.WriteLine("The assembly has already been loaded.");  
        }  
    }  
}  
/* Output (with .NET Framework 3.5 installed):  
    Yes, the file is an assembly.  
*/  
```  
  
 <span data-ttu-id="a53b3-115"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A> メソッドはテスト ファイルを読み込み、情報が読み取られた時点で解放します。</span><span class="sxs-lookup"><span data-stu-id="a53b3-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a53b3-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="a53b3-116">See Also</span></span>  
 <span data-ttu-id="a53b3-117"><xref:System.Reflection.AssemblyName></span><span class="sxs-lookup"><span data-stu-id="a53b3-117"><xref:System.Reflection.AssemblyName></span></span>   
 <span data-ttu-id="a53b3-118">[C# プログラミング ガイド](../../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="a53b3-118">[C# Programming Guide](../../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="a53b3-119">アセンブリとグローバル アセンブリ キャッシュ (C#)</span><span class="sxs-lookup"><span data-stu-id="a53b3-119">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)

