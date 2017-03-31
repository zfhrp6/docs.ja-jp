---
title: "csc.exe を使用したコマンド ラインからのビルド | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
caps.latest.revision: 28
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: aa6dd9801a141ec430bc291302fe74c35057f117
ms.lasthandoff: 03/13/2017

---
# <a name="command-line-building-with-cscexe"></a>csc.exe を使用したコマンド ラインからのビルド
C# コンパイラは、その実行可能ファイルの名前 (csc.exe) をコマンド プロンプトに入力することによって呼び出します。  
  
 **Visual Studio コマンド プロンプト** ウィンドウを使用した場合、必要なすべての環境変数が設定されます。 Windows 7 では、**[スタート]** メニューから Microsoft Visual Studio "*バージョン*"\Visual Studio ツール フォルダーを開くことにより、このウィンドウを使用できます。 Windows 8 では、Visual Studio コマンド プロンプトは **VS2012 の開発者コマンド プロンプト**と呼ばれており、スタート画面から検索できます。  
  
 標準のコマンド プロンプト ウィンドウを使用する場合は、コンピューター上の任意のサブディレクトリから csc.exe を呼び出すことができるようにパスを修正する必要があります。 また、vsvars32.bat を実行して、コマンド ライン ビルドをサポートするための適切な環境変数を設定する必要があります。 検索して実行する方法の手順など、vsvars32.bat の詳細については、「[方法: Visual Studio のコマンド ラインのための環境変数を設定する](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)」を参照してください。  
  
 [!INCLUDE[winsdklong](../../../csharp/language-reference/compiler-options/includes/winsdklong_md.md)] のみがインストールされているコンピューターでは、**SDK コマンド プロンプト** (**[Microsoft .NET Framework SDK]** メニュー オプションから開くことができます) で C# コンパイラを使用できます。  
  
 MSBuild を使用して、プログラムによって C# プログラムをビルドすることもできます。 詳細については、「[MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild1)」を参照してください。  
  
 通常、実行可能ファイル csc.exe は、Windows ディレクトリの Microsoft.NET\Framework\\"*バージョン*" フォルダーに格納されています。 ただし、この格納場所は、特定のコンピューターの構成によって異なる場合があります。 複数のバージョンの .NET Framework がコンピューターにインストールされている場合、このファイルのバージョンが複数見つかります。 このようなインストールの詳細については、[インストールされている .NET Framework のバージョンの確認](http://msdn.microsoft.com/en-us/1a87cc6a-1c4b-4c38-b878-faa9b3beae3c)に関するページを参照してください。  
  
> [!TIP]
>  Visual Studio IDE を使用してプロジェクトをビルドすると、**csc** コマンドとその関連するコンパイラ オプションが**出力**ウィンドウに表示されます。 この情報を表示するには、「[方法: ビルド ログ ファイルを表示、保存、および構成する](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7)」の手順に従って、ログ データの詳細レベルを **[標準]** または **[詳細]** に変更します。 プロジェクトをリビルドした後、C# コンパイラの呼び出しを見つけるために**出力**ウィンドウで **csc** を検索します。  
  
 **このトピックの内容**  
  
-   [コマンド ライン構文の規則](#vcconcommand-linebuildinganchor1)  
  
-   [サンプル コマンド ライン](#vcconcommand-linebuildinganchor2)  
  
-   [C# コンパイラと C++ コンパイラの出力の相違点](#vcconcommand-linebuildinganchor3)  
  
##  <a name="vcconcommand-linebuildinganchor1"></a> C# コンパイラのコマンド ライン構文の規則  
 C# コンパイラは、オペレーティング システムのコマンド ラインで指定された引数を次の規則に従って解釈します。  
  
-   引数は、空白 (スペースまたはタブ) で区切ります。  
  
-   キャレット (^) は、エスケープ文字やデリミターとしては認識されません。 キャレットは、オペレーティング システムのコマンド ライン パーサーによって処理されてからプログラムの argv 配列に渡されます。  
  
-   二重引用符で囲まれた文字列 ("string") は、空白を含む場合でも、単一の引数と見なされます。 二重引用符で囲んだ文字列を引数に埋め込むこともできます。  
  
-   円記号を前に付けた二重引用符 (\\") は、リテラル二重引用符文字 (") として解釈されます。  
  
-   二重引用符の直前にある円記号以外は、円記号 (\) として解釈されます。  
  
-   二重引用符の直前に円記号が偶数個 (0 個は含まない) あると、円記号のペアごとに 1 個の円記号が argv 配列に格納されます。この場合、二重引用符は文字列のデリミターとして解釈されます。  
  
-   二重引用符の直前に円記号が奇数個 (3 個以上) あると、円記号のペアごとに 1 個の円記号が argv 配列に格納されます。この場合、二重引用符は残った円記号によりエスケープ シーケンスになります。 これにより、リテラル二重引用符 (") が argv に追加されます。  
  
##  <a name="vcconcommand-linebuildinganchor2"></a> C# コンパイラのコマンド ラインのサンプル  
  
-   File.cs をコンパイルして File.exe を作成します。  
  
    ```  
    csc File.cs   
    ```  
  
-   File.cs をコンパイルして File.dll を作成します。  
  
    ```  
    csc /target:library File.cs  
    ```  
  
-   File.cs をコンパイルして My.exe を作成します。  
  
    ```  
    csc /out:My.exe File.cs  
    ```  
  
-   最適化を有効にし、DEBUG シンボルを定義して、現在のディレクトリにあるすべての C# ファイルをコンパイルします。 File2.exe が出力されます。  
  
    ```  
    csc /define:DEBUG /optimize /out:File2.exe *.cs  
    ```  
  
-   現在のディレクトリにあるすべての C# ファイルをコンパイルして、デバッグ バージョンの File2.dll を作成します。 ロゴや警告は表示されません。  
  
    ```  
    csc /target:library /out:File2.dll /warn:0 /nologo /debug *.cs  
    ```  
  
-   現在のディレクトリにあるすべての C# ファイルをコンパイルして、Something.xyz (DLL) に出力します。  
  
    ```  
    csc /target:library /out:Something.xyz *.cs  
    ```  
  
##  <a name="vcconcommand-linebuildinganchor3"></a> C# コンパイラと C++ コンパイラの出力の相違点  
 C# コンパイラを起動してもオブジェクト (.obj) ファイルは作成されず、出力ファイルが直接作成されます。 このため、C# コンパイラにはリンカーが不要です。  
  
## <a name="see-also"></a>関連項目  
 [C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md)   
 [アルファベット順の C# コンパイラ オプションの一覧](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)   
 [カテゴリ別の C# コンパイラ オプションの一覧](../../../csharp/language-reference/compiler-options/listed-by-category.md)   
 [Main() とコマンド ライン引数](../../../csharp/programming-guide/main-and-command-args/index.md)   
 [コマンド ライン引数](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)   
 [方法: コマンド ライン引数を表示する](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)   
 [方法: foreach を使用してコマンド ライン引数にアクセスする](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)   
 [Main() の戻り値](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
