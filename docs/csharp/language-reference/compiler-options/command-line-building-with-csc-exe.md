---
title: "csc.exe を使用したコマンド ラインからのビルド | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ビルド [C#]"
  - "コマンド ライン [C#]"
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
caps.latest.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 28
---
# csc.exe を使用したコマンド ラインからのビルド
C# コンパイラは、その実行可能ファイルの名前 (csc.exe) をコマンド プロンプトに入力することによって呼び出します。  
  
 使用する場合、 **Visual Studio コマンド プロンプト** ウィンドウで、すべての必要な環境変数は、自動的に設定されます。 Windows 7 ではそのウィンドウからアクセスできます、 **開始** ] メニューの [Microsoft Visual Studio を開いて *バージョン*\Visual Studio Tools フォルダーです。 Windows 8 で、Visual Studio コマンド プロンプトと呼ばれる、 **VS2012 の開発者コマンド プロンプト**, 、スタート画面から検索して参照できます。  
  
 標準のコマンド プロンプト ウィンドウを使用する場合は、コンピューター上の任意のサブディレクトリから csc.exe を呼び出すことができるようにパスを修正する必要があります。 また、vsvars32.bat を実行して、コマンド ライン ビルドをサポートするための適切な環境変数を設定する必要があります。 見つけて、それを実行する方法の手順を含む vsvars32.bat の詳細については、次を参照してください。 [方法: 環境変数の設定を、Visual Studio のコマンドライン](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)します。  
  
 のみを持つコンピューターで作業しているかどうか、 [!INCLUDE[winsdklong](../../../csharp/language-reference/compiler-options/includes/winsdklong-md.md)], 、c# コンパイラを使用することができます、 **SDK コマンド プロンプト**, から開くことが、 **Microsoft .NET Framework SDK** メニュー オプション。  
  
 MSBuild を使用して、プログラムによって C# プログラムをビルドすることもできます。 詳細については、次を参照してください。 [MSBuild](/visual-studio/msbuild/msbuild1)します。  
  
 実行可能ファイル csc.exe 通常にある、\framework\\*バージョン* Windows ディレクトリの下のフォルダーです。 ただし、この格納場所は、特定のコンピューターの構成によって異なる場合があります。 複数のバージョンの .NET Framework がコンピューターにインストールされている場合、このファイルのバージョンが複数見つかります。 このようなインストールの詳細については、次を参照してください。 [、.NET Framework がインストールされているのバージョンの決定](http://msdn.microsoft.com/ja-jp/1a87cc6a-1c4b-4c38-b878-faa9b3beae3c)します。  
  
> [!TIP]
>  Visual Studio IDE を使用してプロジェクトをビルドするときに表示できます、 **csc** コマンドとその関連するコンパイラ オプションで、 **出力** ウィンドウです。 この情報を表示するには、以下の指示 [方法: ビュー、保存、およびビルドのログ ファイルの構成](../Topic/How%20to:%20View,%20Save,%20and%20Configure%20Build%20Log%20Files.md) にログ データの詳細レベルを変更する **標準** または **Detailed**します。 プロジェクトをリビルドした後、検索、 **出力** ウィンドウ **csc** を c# コンパイラの呼び出しを検索します。  
  
 **このトピックの内容**  
  
-   [コマンドライン構文の規則](#vcconcommand-linebuildinganchor1)  
  
-   [コマンドラインのサンプル](#vcconcommand-linebuildinganchor2)  
  
-   [C# コンパイラと C++ コンパイラの出力の相違点](#vcconcommand-linebuildinganchor3)  
  
##  <a name="a-namevcconcommand-linebuildinganchor1a-rules-for-command-line-syntax-for-the-c-compiler"></a><a name="vcconcommand-linebuildinganchor1"></a> C# コンパイラのコマンドライン構文の規則  
 C# コンパイラは、オペレーティング システムのコマンド ラインで指定された引数を次の規則に従って解釈します。  
  
-   引数は、空白 (スペースまたはタブ) で区切ります。  
  
-   キャレット (^) は、エスケープ文字やデリミターとしては認識されません。 キャレットは、オペレーティング システムのコマンド ライン パーサーによって処理されてからプログラムの argv 配列に渡されます。  
  
-   二重引用符で囲まれた文字列 ("string") は、空白を含む場合でも、単一の引数と見なされます。 二重引用符で囲んだ文字列を引数に埋め込むこともできます。  
  
-   二重引用符の前に円記号 (\\") は、リテラル二重引用符文字 (") として解釈されます。  
  
-   二重引用符の直前にある円記号以外は、円記号 (\) として解釈されます。  
  
-   二重引用符の直前に円記号が偶数個 (0 個は含まない) あると、円記号のペアごとに 1 個の円記号が argv 配列に格納されます。この場合、二重引用符は文字列のデリミターとして解釈されます。  
  
-   二重引用符の直前に円記号が奇数個 (3 個以上) あると、円記号のペアごとに 1 個の円記号が argv 配列に格納されます。この場合、二重引用符は残った円記号によりエスケープ シーケンスになります。 これにより、リテラル二重引用符 (") が argv に追加されます。  
  
##  <a name="a-namevcconcommand-linebuildinganchor2a-sample-command-lines-for-the-c-compiler"></a><a name="vcconcommand-linebuildinganchor2"></a> C# コンパイラのコマンドラインのサンプル  
  
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
  
##  <a name="a-namevcconcommand-linebuildinganchor3a-differences-between-c-compiler-and-c-compiler-output"></a><a name="vcconcommand-linebuildinganchor3"></a> C# コンパイラと C++ コンパイラの出力の相違点  
 C# コンパイラを起動してもオブジェクト (.obj) ファイルは作成されず、出力ファイルが直接作成されます。 このため、C# コンパイラにはリンカーが不要です。  
  
## <a name="see-also"></a>「  
 [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)   
 [C# コンパイラ オプションの一覧 (アルファベット順)](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)   
 [C# コンパイラ オプションのカテゴリ別一覧](../../../csharp/language-reference/compiler-options/listed-by-category.md)   
 [Main() とコマンドライン引数](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md)   
 [コマンドライン引数](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)   
 [方法: コマンドライン引数を表示](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)   
 [方法: foreach を使用してコマンドライン引数にアクセス](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)   
 [Main() の戻り値](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)