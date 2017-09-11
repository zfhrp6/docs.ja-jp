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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 69e9cab9dda1fefe8bee3dc46b541313d1d80e58
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-visual-basic"></a><span data-ttu-id="c608e-102">方法: を作成し、コマンドライン (Visual Basic) を使用してアセンブリを使用します。</span><span class="sxs-lookup"><span data-stu-id="c608e-102">How to: Create and Use Assemblies Using the Command Line (Visual Basic)</span></span>
<span data-ttu-id="c608e-103">アセンブリ、またはダイナミック リンク ライブラリ (DLL) は、実行時に、プログラムにリンクされます。</span><span class="sxs-lookup"><span data-stu-id="c608e-103">An assembly, or a dynamic linking library (DLL), is linked to your program at run time.</span></span> <span data-ttu-id="c608e-104">ビルドと DLL の使用例として、次のシナリオを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="c608e-104">To demonstrate building and using a DLL, consider the following scenario:</span></span>  
  
-   <span data-ttu-id="c608e-105">`MathLibrary.DLL`: 実行時に呼び出されるメソッドを含むライブラリ ファイル。</span><span class="sxs-lookup"><span data-stu-id="c608e-105">`MathLibrary.DLL`: The library file that contains the methods to be called at run time.</span></span> <span data-ttu-id="c608e-106">この例では、DLL は、2 つのメソッドを含まれています。`Add`と`Multiply`です。</span><span class="sxs-lookup"><span data-stu-id="c608e-106">In this example, the DLL contains two methods, `Add` and `Multiply`.</span></span>  
  
-   <span data-ttu-id="c608e-107">`Add`メソッドを含むソース ファイル:`Add`です。</span><span class="sxs-lookup"><span data-stu-id="c608e-107">`Add`: The source file that contains the method `Add`.</span></span> <span data-ttu-id="c608e-108">そのパラメーターの合計を返します。</span><span class="sxs-lookup"><span data-stu-id="c608e-108">It returns the sum of its parameters.</span></span> <span data-ttu-id="c608e-109">クラス`AddClass`メソッドが含まれている`Add`名前空間のメンバーである`UtilityMethods`です。</span><span class="sxs-lookup"><span data-stu-id="c608e-109">The class `AddClass` that contains the method `Add` is a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="c608e-110">`Mult`メソッドを含むソース コード:`Multiply`です。</span><span class="sxs-lookup"><span data-stu-id="c608e-110">`Mult`: The source code that contains the method `Multiply`.</span></span> <span data-ttu-id="c608e-111">これは、そのパラメーターの積を返します。</span><span class="sxs-lookup"><span data-stu-id="c608e-111">It returns the product of its parameters.</span></span> <span data-ttu-id="c608e-112">クラス`MultiplyClass`メソッドが含まれている`Multiply`名前空間のメンバーである`UtilityMethods`です。</span><span class="sxs-lookup"><span data-stu-id="c608e-112">The class `MultiplyClass` that contains the method `Multiply` is also a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="c608e-113">`TestCode`: 格納しているファイル、`Main`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="c608e-113">`TestCode`: The file that contains the `Main` method.</span></span> <span data-ttu-id="c608e-114">DLL ファイル内の合計と実行時引数の積を計算するのにメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="c608e-114">It uses the methods in the DLL file to calculate the sum and the product of the run-time arguments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c608e-115">例</span><span class="sxs-lookup"><span data-stu-id="c608e-115">Example</span></span>  
  
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
  
 <span data-ttu-id="c608e-116">このファイルには、DLL のメソッドを使用するアルゴリズムが含まれている`Add`と`Multiply`です。</span><span class="sxs-lookup"><span data-stu-id="c608e-116">This file contains the algorithm that uses the DLL methods, `Add` and `Multiply`.</span></span> <span data-ttu-id="c608e-117">コマンド プロンプトから入力した引数の解析で始まる`num1`と`num2`です。</span><span class="sxs-lookup"><span data-stu-id="c608e-117">It starts with parsing the arguments entered from the command line, `num1` and `num2`.</span></span> <span data-ttu-id="c608e-118">使用して合計を計算し、`Add`メソッドを`AddClass`クラス、および製品を使用して、`Multiply`メソッドを`MultiplyClass`クラスです。</span><span class="sxs-lookup"><span data-stu-id="c608e-118">Then it calculates the sum by using the `Add` method on the `AddClass` class, and the product by using the `Multiply` method on the `MultiplyClass` class.</span></span>  
  
 <span data-ttu-id="c608e-119">注意して、`Imports`ファイルの先頭にあるステートメントでは、次のように、コンパイル時に DLL のメソッドを参照する非修飾クラス名を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="c608e-119">Notice that the  `Imports` statement at the beginning of the file enables you to use the unqualified class names to reference the DLL methods at compile time, as follows:</span></span>  
  
```vb  
MultiplyClass.Multiply(num1, num2)  
```  
  
 <span data-ttu-id="c608e-120">それ以外の場合、次のように完全修飾名を使用しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="c608e-120">Otherwise, you have to use the fully qualified names, as follows:</span></span>  
  
```vb  
UtilityMethods.MultiplyClass.Multiply(num1, num2)  
```  
  
## <a name="execution"></a><span data-ttu-id="c608e-121">実行</span><span class="sxs-lookup"><span data-stu-id="c608e-121">Execution</span></span>  
 <span data-ttu-id="c608e-122">プログラムを実行するには、次のように&2; つの数値の後に、EXE ファイルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="c608e-122">To run the program, enter the name of the EXE file, followed by two numbers, as follows:</span></span>  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c608e-123">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="c608e-123">Compiling the Code</span></span>  
 <span data-ttu-id="c608e-124">ファイルをビルドする`MathLibrary.DLL`、2 つのファイルをコンパイル`Add`と`Mult`次のコマンドラインを使用しています。</span><span class="sxs-lookup"><span data-stu-id="c608e-124">To build the file `MathLibrary.DLL`, compile the two files `Add` and `Mult` by using the following command line.</span></span>  
  
```vb  
vbc /target:library /out:MathLibrary.DLL Add.vb Mult.vb  
```  
  
 <span data-ttu-id="c608e-125">[/Target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md)コンパイラ オプションを指定すると、EXE ファイルではなく、DLL を出力します。</span><span class="sxs-lookup"><span data-stu-id="c608e-125">The [/target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) compiler option tells the compiler to output a DLL instead of an EXE file.</span></span> <span data-ttu-id="c608e-126">[/Out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) DLL のファイル名を指定するファイル名を続けてコンパイラ オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="c608e-126">The [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) compiler option followed by a file name is used to specify the DLL file name.</span></span> <span data-ttu-id="c608e-127">それ以外の場合、コンパイラが最初のファイルを使用して (`Add.vb`) として、DLL の名前。</span><span class="sxs-lookup"><span data-stu-id="c608e-127">Otherwise, the compiler uses the first file (`Add.vb`) as the name of the DLL.</span></span>  
  
 <span data-ttu-id="c608e-128">実行可能ファイルをビルドする`TestCode.exe`、次のコマンドラインを使用します。</span><span class="sxs-lookup"><span data-stu-id="c608e-128">To build the executable file, `TestCode.exe`, use the following command line:</span></span>  
  
```vb  
vbc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.vb  
```  
  
 <span data-ttu-id="c608e-129">**/Out**コンパイラ オプションは、EXE ファイルを出力するようにコンパイラに指示し、出力ファイルの名前を指定 (`TestCode.exe`)。</span><span class="sxs-lookup"><span data-stu-id="c608e-129">The **/out** compiler option tells the compiler to output an EXE file and specifies the name of the output file (`TestCode.exe`).</span></span> <span data-ttu-id="c608e-130">このコンパイラ オプションは省略できます。</span><span class="sxs-lookup"><span data-stu-id="c608e-130">This compiler option is optional.</span></span> <span data-ttu-id="c608e-131">[/Reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md)コンパイラ オプションは、DLL ファイルをこのプログラムを使用してファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="c608e-131">The [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) compiler option specifies the DLL file or files that this program uses.</span></span>  
  
 <span data-ttu-id="c608e-132">コマンドラインからのビルドの詳細については、次を参照してください。 と[コマンドラインからのビルド](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)します。</span><span class="sxs-lookup"><span data-stu-id="c608e-132">For more information about building from the command line, see  and [Building from the Command Line](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c608e-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="c608e-133">See Also</span></span>  
 <span data-ttu-id="c608e-134">[プログラミングの概念](../../../../visual-basic/programming-guide/concepts/index.md) </span><span class="sxs-lookup"><span data-stu-id="c608e-134">[Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md) </span></span>  
<span data-ttu-id="c608e-135"> [アセンブリとグローバル アセンブリ キャッシュ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="c608e-135"> [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="c608e-136"> [DLL 関数を保持するクラスを作成します。](http://msdn.microsoft.com/library/e08e4c34-0223-45f7-aa55-a3d8dd979b0f)</span><span class="sxs-lookup"><span data-stu-id="c608e-136"> [Creating a Class to Hold DLL Functions](http://msdn.microsoft.com/library/e08e4c34-0223-45f7-aa55-a3d8dd979b0f)</span></span>
