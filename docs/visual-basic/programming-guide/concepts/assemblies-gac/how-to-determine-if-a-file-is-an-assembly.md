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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2e58363369ae4420879310bf09ed89cdd4f5b5cc
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-determine-if-a-file-is-an-assembly-visual-basic"></a>方法: ファイルがアセンブリ (Visual Basic) であるかを確認
ファイルはアセンブリのみ場合にそれが管理され、そのメタデータ内のアセンブリのエントリが含まれています。 アセンブリおよびメタデータの詳細については、トピックを参照してください。[アセンブリ マニフェスト](https://msdn.microsoft.com/library/1w45z383)します。  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>ファイルのアセンブリを手動で確認する方法  
  
1.  開始、 [Ildasm.exe (IL 逆アセンブラー)](https://msdn.microsoft.com/library/f7dy01k1)します。  
  
2.  テストするファイルを読み込めません。  
  
3.  場合**ILDASM**レポート ファイルは、ポータブル実行可能 (PE) ファイルではありませんし、アセンブリではないことです。 詳細については、トピックを参照してください。[方法: アセンブリの内容を表示](http://msdn.microsoft.com/library/fb7baaab-4c0d-47ad-8fd3-4591cf834709)します。  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>プログラムを使用して、ファイルがアセンブリであるかを確認する方法  
  
1.  呼び出す、<xref:System.Reflection.AssemblyName.GetAssemblyName%2A>メソッドをテストしているファイルの名前とファイルの完全パスを渡します</xref:System.Reflection.AssemblyName.GetAssemblyName%2A>。  
  
2.  場合、<xref:System.BadImageFormatException>例外がスローされた、ファイルがアセンブリではありません</xref:System.BadImageFormatException>。  
  
## <a name="example"></a>例  
 この例では、アセンブリが DLL をテストします。  
  
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
  
 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A>メソッドがテスト ファイルを読み込むし、情報が読み取られた後に、解放します</xref:System.Reflection.AssemblyName.GetAssemblyName%2A>。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Reflection.AssemblyName></xref:System.Reflection.AssemblyName>   
 [プログラミングの概念](../../../../visual-basic/programming-guide/concepts/index.md)   
 [アセンブリとグローバル アセンブリ キャッシュ (Visual Basic)](index.md)
