---
title: "方法: を作成し、コマンドライン (Visual Basic) を使用してアセンブリを使用する |Microsoft ドキュメント"
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
ms.assetid: 229ff9fb-1bd1-403b-946b-526104864c60
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
ms.openlocfilehash: 363bca806736e5540165ea96e9b4fe60d0968098
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-visual-basic"></a>方法: を作成し、コマンドライン (Visual Basic) を使用してアセンブリを使用します。
アセンブリ、またはダイナミック リンク ライブラリ (DLL) は、実行時に、プログラムにリンクされます。 ビルドと DLL の使用例として、次のシナリオを考慮してください。  
  
-   `MathLibrary.DLL`: 実行時に呼び出されるメソッドを含むライブラリ ファイル。 この例では、DLL は、2 つのメソッドを含まれています。`Add`と`Multiply`です。  
  
-   `Add`メソッドを含むソース ファイル:`Add`です。 そのパラメーターの合計を返します。 クラス`AddClass`メソッドが含まれている`Add`名前空間のメンバーである`UtilityMethods`です。  
  
-   `Mult`メソッドを含むソース コード:`Multiply`です。 これは、そのパラメーターの積を返します。 クラス`MultiplyClass`メソッドが含まれている`Multiply`名前空間のメンバーである`UtilityMethods`です。  
  
-   `TestCode`: 格納しているファイル、`Main`メソッドです。 DLL ファイル内の合計と実行時引数の積を計算するのにメソッドを使用します。  
  
## <a name="example"></a>例  
  
```vb  
' File: Add.vb   
Namespace UtilityMethods  
    Public Class AddClass  
        Public Shared Function Add(ByVal i As Long, ByVal j As Long) As Long  
            Return i + j  
        End Function  
    End Class  
End Namespace  
```  
  
```vb  
' File: Mult.vb  
Namespace UtilityMethods  
    Public Class MultiplyClass  
        Public Shared Function Multiply(ByVal x As Long, ByVal y As Long) As Long  
            Return x * y  
        End Function  
    End Class  
End Namespace  
```  
  
```vb  
' File: TestCode.vb  
  
Imports UtilityMethods  
  
Module Test  
  
    Sub Main(ByVal args As String())  
  
        System.Console.WriteLine("Calling methods from MathLibrary.DLL:")  
  
        If args.Length <> 2 Then  
            System.Console.WriteLine("Usage: TestCode <num1> <num2>")  
            Return  
        End If  
  
        Dim num1 As Long = Long.Parse(args(0))  
        Dim num2 As Long = Long.Parse(args(1))  
  
        Dim sum As Long = AddClass.Add(num1, num2)  
        Dim product As Long = MultiplyClass.Multiply(num1, num2)  
  
        System.Console.WriteLine("{0} + {1} = {2}", num1, num2, sum)  
        System.Console.WriteLine("{0} * {1} = {2}", num1, num2, product)  
  
    End Sub  
  
End Module  
  
' Output (assuming 1234 and 5678 are entered as command-line arguments):  
' Calling methods from MathLibrary.DLL:  
' 1234 + 5678 = 6912  
' 1234 * 5678 = 7006652  
```  
  
 このファイルには、DLL のメソッドを使用するアルゴリズムが含まれている`Add`と`Multiply`です。 コマンド プロンプトから入力した引数の解析で始まる`num1`と`num2`です。 使用して合計を計算し、`Add`メソッドを`AddClass`クラス、および製品を使用して、`Multiply`メソッドを`MultiplyClass`クラスです。  
  
 注意して、`Imports`ファイルの先頭にあるステートメントでは、次のように、コンパイル時に DLL のメソッドを参照する非修飾クラス名を使用することができます。  
  
```vb  
MultiplyClass.Multiply(num1, num2)  
```  
  
 それ以外の場合、次のように完全修飾名を使用しなければなりません。  
  
```vb  
UtilityMethods.MultiplyClass.Multiply(num1, num2)  
```  
  
## <a name="execution"></a>実行  
 プログラムを実行するには、次のように&2; つの数値の後に、EXE ファイルの名前を入力します。  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 ファイルをビルドする`MathLibrary.DLL`、2 つのファイルをコンパイル`Add`と`Mult`次のコマンドラインを使用しています。  
  
```vb  
vbc /target:library /out:MathLibrary.DLL Add.vb Mult.vb  
```  
  
 [/Target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md)コンパイラ オプションを指定すると、EXE ファイルではなく、DLL を出力します。 [/Out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) DLL のファイル名を指定するファイル名を続けてコンパイラ オプションを使用します。 それ以外の場合、コンパイラが最初のファイルを使用して (`Add.vb`) として、DLL の名前。  
  
 実行可能ファイルをビルドする`TestCode.exe`、次のコマンドラインを使用します。  
  
```vb  
vbc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.vb  
```  
  
 **/Out**コンパイラ オプションは、EXE ファイルを出力するようにコンパイラに指示し、出力ファイルの名前を指定 (`TestCode.exe`)。 このコンパイラ オプションは省略できます。 [/Reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md)コンパイラ オプションは、DLL ファイルをこのプログラムを使用してファイルを指定します。  
  
 コマンドラインからのビルドの詳細については、次を参照してください。 と[コマンドラインからのビルド](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)します。  
  
## <a name="see-also"></a>関連項目  
 [プログラミングの概念](../../../../visual-basic/programming-guide/concepts/index.md)   
 [アセンブリとグローバル アセンブリ キャッシュ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [DLL 関数を保持するクラスを作成します。](http://msdn.microsoft.com/library/e08e4c34-0223-45f7-aa55-a3d8dd979b0f)
