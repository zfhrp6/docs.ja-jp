---
title: "方法: ファイルがアセンブリ (Visual Basic) であるかを判断 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: de26f410-9bd1-4b55-a343-cc82f81684be
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4bd3404cbdc3b79ff92290a53574080bf197fe9d
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-determine-if-a-file-is-an-assembly-visual-basic"></a><span data-ttu-id="1e156-102">方法: ファイルがアセンブリ (Visual Basic) であるかを確認</span><span class="sxs-lookup"><span data-stu-id="1e156-102">How to: Determine If a File Is an Assembly (Visual Basic)</span></span>
<span data-ttu-id="1e156-103">ファイルはアセンブリのみ場合にそれが管理され、そのメタデータ内のアセンブリのエントリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1e156-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="1e156-104">アセンブリおよびメタデータの詳細については、トピックを参照してください。[アセンブリ マニフェスト](https://msdn.microsoft.com/library/1w45z383)します。</span><span class="sxs-lookup"><span data-stu-id="1e156-104">For more information on assemblies and metadata, see the topic [Assembly Manifest](https://msdn.microsoft.com/library/1w45z383).</span></span>  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="1e156-105">ファイルのアセンブリを手動で確認する方法</span><span class="sxs-lookup"><span data-stu-id="1e156-105">How to manually determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="1e156-106">開始、 [Ildasm.exe (IL 逆アセンブラー)](https://msdn.microsoft.com/library/f7dy01k1)します。</span><span class="sxs-lookup"><span data-stu-id="1e156-106">Start the [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1).</span></span>  
  
2.  <span data-ttu-id="1e156-107">テストするファイルを読み込めません。</span><span class="sxs-lookup"><span data-stu-id="1e156-107">Load the file you wish to test.</span></span>  
  
3.  <span data-ttu-id="1e156-108">場合**ILDASM**レポート ファイルは、ポータブル実行可能 (PE) ファイルではありませんし、アセンブリではないことです。</span><span class="sxs-lookup"><span data-stu-id="1e156-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="1e156-109">詳細については、トピックを参照してください。[方法: アセンブリの内容を表示](http://msdn.microsoft.com/library/fb7baaab-4c0d-47ad-8fd3-4591cf834709)します。</span><span class="sxs-lookup"><span data-stu-id="1e156-109">For more information, see the topic [How to: View Assembly Contents](http://msdn.microsoft.com/library/fb7baaab-4c0d-47ad-8fd3-4591cf834709).</span></span>  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="1e156-110">プログラムを使用して、ファイルがアセンブリであるかを確認する方法</span><span class="sxs-lookup"><span data-stu-id="1e156-110">How to programmatically determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="1e156-111">呼び出す、<xref:System.Reflection.AssemblyName.GetAssemblyName%2A>メソッドをテストしているファイルの名前とファイルの完全パスを渡します</xref:System.Reflection.AssemblyName.GetAssemblyName%2A>。</span><span class="sxs-lookup"><span data-stu-id="1e156-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method, passing the full file path and name of the file you are testing.</span></span>  
  
2.  <span data-ttu-id="1e156-112">場合、<xref:System.BadImageFormatException>例外がスローされた、ファイルがアセンブリではありません</xref:System.BadImageFormatException>。</span><span class="sxs-lookup"><span data-stu-id="1e156-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e156-113">例</span><span class="sxs-lookup"><span data-stu-id="1e156-113">Example</span></span>  
 <span data-ttu-id="1e156-114">この例では、アセンブリが DLL をテストします。</span><span class="sxs-lookup"><span data-stu-id="1e156-114">This example tests a DLL to see if it is an assembly.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        Try  
            Dim testAssembly As Reflection.AssemblyName =  
                                Reflection.AssemblyName.GetAssemblyName("C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll")  
            Console.WriteLine("Yes, the file is an Assembly.")  
        Catch ex As System.IO.FileNotFoundException  
            Console.WriteLine("The file cannot be found.")  
        Catch ex As System.BadImageFormatException  
            Console.WriteLine("The file is not an Assembly.")  
        Catch ex As System.IO.FileLoadException  
            Console.WriteLine("The Assembly has already been loaded.")  
        End Try  
        Console.ReadLine()  
    End Sub  
End Module  
' Output (with .NET Framework 3.5 installed):  
'        Yes, the file is an Assembly.  
```
  
 <span data-ttu-id="1e156-115"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A>メソッドがテスト ファイルを読み込むし、情報が読み取られた後に、解放します</xref:System.Reflection.AssemblyName.GetAssemblyName%2A>。</span><span class="sxs-lookup"><span data-stu-id="1e156-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e156-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="1e156-116">See Also</span></span>  
 <span data-ttu-id="1e156-117"><xref:System.Reflection.AssemblyName></xref:System.Reflection.AssemblyName></span><span class="sxs-lookup"><span data-stu-id="1e156-117"><xref:System.Reflection.AssemblyName></span></span>   
<span data-ttu-id="1e156-118"> [プログラミングの概念](../../../../visual-basic/programming-guide/concepts/index.md) </span><span class="sxs-lookup"><span data-stu-id="1e156-118"> [Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md) </span></span>  
<span data-ttu-id="1e156-119"> [アセンブリとグローバル アセンブリ キャッシュ (Visual Basic)](index.md)</span><span class="sxs-lookup"><span data-stu-id="1e156-119"> [Assemblies and the Global Assembly Cache (Visual Basic)](index.md)</span></span>
