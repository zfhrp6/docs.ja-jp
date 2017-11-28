---
title: "方法: コマンド ラインを使用してアセンブリを作成および使用する (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 408ddce3-89e3-4e12-8353-34a49beeb72b
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d59988ec4899b4115d8d0fd7172e0c8ff8802378
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-c"></a><span data-ttu-id="680af-102">方法: コマンド ラインを使用してアセンブリを作成および使用する (C#)</span><span class="sxs-lookup"><span data-stu-id="680af-102">How to: Create and Use Assemblies Using the Command Line (C#)</span></span>
<span data-ttu-id="680af-103">アセンブリとは、ダイナミック リンク ライブラリ (DLL) のことで、実行時にプログラムにリンクされます。</span><span class="sxs-lookup"><span data-stu-id="680af-103">An assembly, or a dynamic linking library (DLL), is linked to your program at run time.</span></span> <span data-ttu-id="680af-104">DLL のビルド例および使用例として、次に示すシナリオを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="680af-104">To demonstrate building and using a DLL, consider the following scenario:</span></span>  
  
-   <span data-ttu-id="680af-105">`MathLibrary.DLL`: 実行時に呼び出されるメソッドが格納されているライブラリ ファイル。</span><span class="sxs-lookup"><span data-stu-id="680af-105">`MathLibrary.DLL`: The library file that contains the methods to be called at run time.</span></span> <span data-ttu-id="680af-106">この例では、DLL には 2 つのメソッド `Add` と `Multiply` が含まれています。</span><span class="sxs-lookup"><span data-stu-id="680af-106">In this example, the DLL contains two methods, `Add` and `Multiply`.</span></span>  
  
-   <span data-ttu-id="680af-107">`Add`: `Add` メソッドが格納されているソース ファイル。</span><span class="sxs-lookup"><span data-stu-id="680af-107">`Add`: The source file that contains the method `Add`.</span></span> <span data-ttu-id="680af-108">パラメーターの和を返します。</span><span class="sxs-lookup"><span data-stu-id="680af-108">It returns the sum of its parameters.</span></span> <span data-ttu-id="680af-109">`Add` メソッドを含む `AddClass` クラスは `UtilityMethods` 名前空間のメンバーです。</span><span class="sxs-lookup"><span data-stu-id="680af-109">The class `AddClass` that contains the method `Add` is a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="680af-110">`Mult`: `Multiply` メソッドが格納されているソース コード。</span><span class="sxs-lookup"><span data-stu-id="680af-110">`Mult`: The source code that contains the method `Multiply`.</span></span> <span data-ttu-id="680af-111">パラメーターの積を返します。</span><span class="sxs-lookup"><span data-stu-id="680af-111">It returns the product of its parameters.</span></span> <span data-ttu-id="680af-112">`Multiply` メソッドを含む `MultiplyClass` クラスも `UtilityMethods` 名前空間のメンバーです。</span><span class="sxs-lookup"><span data-stu-id="680af-112">The class `MultiplyClass` that contains the method `Multiply` is also a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="680af-113">`TestCode`: `Main` メソッドが格納されているファイル。</span><span class="sxs-lookup"><span data-stu-id="680af-113">`TestCode`: The file that contains the `Main` method.</span></span> <span data-ttu-id="680af-114">DLL ファイルのメソッドを使用して、実行時引数の和と積を計算します。</span><span class="sxs-lookup"><span data-stu-id="680af-114">It uses the methods in the DLL file to calculate the sum and the product of the run-time arguments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="680af-115">例</span><span class="sxs-lookup"><span data-stu-id="680af-115">Example</span></span>  
  
```csharp  
// File: Add.cs   
namespace UtilityMethods  
{  
    public class AddClass   
    {  
        public static long Add(long i, long j)   
        {   
            return (i + j);  
        }  
    }  
}  
```  
  
```csharp  
// File: Mult.cs  
namespace UtilityMethods   
{  
    public class MultiplyClass  
    {  
        public static long Multiply(long x, long y)   
        {  
            return (x * y);   
        }  
    }  
}  
```  
  
```csharp  
// File: TestCode.cs  
  
using UtilityMethods;  
  
class TestCode  
{  
    static void Main(string[] args)   
    {  
        System.Console.WriteLine("Calling methods from MathLibrary.DLL:");  
  
        if (args.Length != 2)  
        {  
            System.Console.WriteLine("Usage: TestCode <num1> <num2>");  
            return;  
        }  
  
        long num1 = long.Parse(args[0]);  
        long num2 = long.Parse(args[1]);  
  
        long sum = AddClass.Add(num1, num2);  
        long product = MultiplyClass.Multiply(num1, num2);  
  
        System.Console.WriteLine("{0} + {1} = {2}", num1, num2, sum);  
        System.Console.WriteLine("{0} * {1} = {2}", num1, num2, product);  
    }  
}  
/* Output (assuming 1234 and 5678 are entered as command-line arguments):  
    Calling methods from MathLibrary.DLL:  
    1234 + 5678 = 6912  
    1234 * 5678 = 7006652          
*/  
```  
  
 <span data-ttu-id="680af-116">このファイルには、DLL のメソッド `Add` と `Multiply` を使用するアルゴリズムが格納されています。</span><span class="sxs-lookup"><span data-stu-id="680af-116">This file contains the algorithm that uses the DLL methods, `Add` and `Multiply`.</span></span> <span data-ttu-id="680af-117">最初に、コマンド ラインから入力された引数 `num1` と `num2` を解析します。</span><span class="sxs-lookup"><span data-stu-id="680af-117">It starts with parsing the arguments entered from the command line, `num1` and `num2`.</span></span> <span data-ttu-id="680af-118">次に、`AddClass` クラスの `Add` メソッドを使用して和を計算し、`MultiplyClass` クラスの `Multiply` メソッドを使って積を計算します。</span><span class="sxs-lookup"><span data-stu-id="680af-118">Then it calculates the sum by using the `Add` method on the `AddClass` class, and the product by using the `Multiply` method on the `MultiplyClass` class.</span></span>  
  
 <span data-ttu-id="680af-119">ファイルの先頭で `using` ディレクティブを指定すると、次のように、コンパイル時に非修飾クラス名を使用して、DLL メソッドを参照できます。</span><span class="sxs-lookup"><span data-stu-id="680af-119">Notice that the `using` directive at the beginning of the file enables you to use the unqualified class names to reference the DLL methods at compile time, as follows:</span></span>  
  
```csharp  
MultiplyClass.Multiply(num1, num2);  
```  
  
 <span data-ttu-id="680af-120">ディレクティブを指定しない場合は、次のように、完全修飾名を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="680af-120">Otherwise, you have to use the fully qualified names, as follows:</span></span>  
  
```csharp  
UtilityMethods.MultiplyClass.Multiply(num1, num2);  
```  
  
## <a name="execution"></a><span data-ttu-id="680af-121">実行</span><span class="sxs-lookup"><span data-stu-id="680af-121">Execution</span></span>  
 <span data-ttu-id="680af-122">プログラムを実行するには、次のように、EXE ファイルの名前と 2 つの数値を順に入力します。</span><span class="sxs-lookup"><span data-stu-id="680af-122">To run the program, enter the name of the EXE file, followed by two numbers, as follows:</span></span>  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a><span data-ttu-id="680af-123">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="680af-123">Compiling the Code</span></span>  
 <span data-ttu-id="680af-124">`MathLibrary.DLL` ファイルをビルドするには、次のコマンド ラインを使用して、`Add` ファイルと `Mult` ファイルをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="680af-124">To build the file `MathLibrary.DLL`, compile the two files `Add` and `Mult` by using the following command line.</span></span>  
  
```csharp  
csc /target:library /out:MathLibrary.DLL Add.cs Mult.cs  
```  
  
 <span data-ttu-id="680af-125">[/target:library](../../../../csharp/language-reference/compiler-options/target-library-compiler-option.md) コンパイラ オプションを指定すると、コンパイラは EXE ファイルではなく DLL ファイルを出力します。</span><span class="sxs-lookup"><span data-stu-id="680af-125">The [/target:library](../../../../csharp/language-reference/compiler-options/target-library-compiler-option.md) compiler option tells the compiler to output a DLL instead of an EXE file.</span></span> <span data-ttu-id="680af-126">[/out](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) コンパイラ オプションは、ファイル名の前で使用して DLL のファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="680af-126">The [/out](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) compiler option followed by a file name is used to specify the DLL file name.</span></span> <span data-ttu-id="680af-127">このオプションを指定しないと、コンパイラは最初のファイル (`Add.cs`) を DLL の名前として使用します。</span><span class="sxs-lookup"><span data-stu-id="680af-127">Otherwise, the compiler uses the first file (`Add.cs`) as the name of the DLL.</span></span>  
  
 <span data-ttu-id="680af-128">実行可能ファイル `TestCode.exe` をビルドするには、次のコマンド ラインを使用します。</span><span class="sxs-lookup"><span data-stu-id="680af-128">To build the executable file, `TestCode.exe`, use the following command line:</span></span>  
  
```csharp  
csc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.cs  
```  
  
 <span data-ttu-id="680af-129">**/out** コンパイラ オプションは、EXE ファイルを出力するようにコンパイラに指示し、出力ファイルの名前 (`TestCode.exe`) を指定します。</span><span class="sxs-lookup"><span data-stu-id="680af-129">The **/out** compiler option tells the compiler to output an EXE file and specifies the name of the output file (`TestCode.exe`).</span></span> <span data-ttu-id="680af-130">このコンパイラ オプションは省略できます。</span><span class="sxs-lookup"><span data-stu-id="680af-130">This compiler option is optional.</span></span> <span data-ttu-id="680af-131">[/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md) コンパイラ オプションは、このプログラムが使用する DLL ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="680af-131">The [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md) compiler option specifies the DLL file or files that this program uses.</span></span> <span data-ttu-id="680af-132">詳細については、「[/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="680af-132">For more information, see [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md).</span></span>  
  
 <span data-ttu-id="680af-133">コマンド ラインからのビルドの詳細については、「[csc.exe を使用したコマンド ラインからのビルド](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="680af-133">For more information about building from the command line, see [Command-line Building With csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="680af-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="680af-134">See Also</span></span>  
 [<span data-ttu-id="680af-135">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="680af-135">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="680af-136">アセンブリとグローバル アセンブリ キャッシュ (C#)</span><span class="sxs-lookup"><span data-stu-id="680af-136">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="680af-137">DLL 関数を保持するクラスの作成</span><span class="sxs-lookup"><span data-stu-id="680af-137">Creating a Class to Hold DLL Functions</span></span>](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
