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
# <a name="how-to-determine-if-a-file-is-an-assembly-c"></a>方法: ファイルがアセンブリであるかどうかを確認する (C#)
ファイルが管理されていて、ファイルのメタデータにアセンブリ エントリが含まれている場合、そのファイルはアセンブリです。 アセンブリとメタデータの詳細については、「[アセンブリ マニフェスト](https://msdn.microsoft.com/library/1w45z383)」を参照してください。  
  
### <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>ファイルがアセンブリかどうかを手動で確認する方法  
  
1.  [Ildasm.exe (IL 逆アセンブラー)](https://msdn.microsoft.com/library/f7dy01k1) を起動します。  
  
2.  テストするファイルを読み込みます。  
  
3.  **ILDASM** で、そのファイルが移植可能な実行可能 (PE) ファイルではないと報告された場合、そのファイルはアセンブリでありません。 詳細については、「[方法: アセンブリの内容を表示する](../../../../framework/app-domains/how-to-view-assembly-contents.md)」を参照してください。  
  
### <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>ファイルがアセンブリかどうかをプログラムによって確認する方法  
  
1.  テストするファイルの完全パスと名前を渡して、<xref:System.Reflection.AssemblyName.GetAssemblyName%2A> メソッドを呼び出します。  
  
2.  <xref:System.BadImageFormatException> 例外がスローされた場合、ファイルはアセンブリでありません。  
  
## <a name="example"></a>例  
 次の例では、DLL がアセンブリかどうかをテストして確認します。  
  
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
  
 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> メソッドはテスト ファイルを読み込み、情報が読み取られた時点で解放します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Reflection.AssemblyName>   
 [C# プログラミング ガイド](../../../../csharp/programming-guide/index.md)   
 [アセンブリとグローバル アセンブリ キャッシュ (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)

