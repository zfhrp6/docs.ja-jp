---
title: "Main() の戻り値 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Main メソッド [C#], 戻り値"
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
caps.latest.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 20
---
# Main() の戻り値 (C# プログラミング ガイド)
`Main` メソッドは `void` を返すことができます。  
  
 [!code-cs[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_1.cs)]  
  
 `int` 型を返すこともできます。  
  
 [!code-cs[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_2.cs)]  
  
 `Main` の戻り値を使用しない場合は、`void` を返すと、コードを少し簡素化できます。  一方、整数を返すと、他のプログラムや、実行可能ファイルを呼び出すスクリプトに、ステータス情報を伝達できます。  `Main` からの戻り値にアクセスする方法を次の例に示します。  
  
## 使用例  
 この例では、バッチ ファイルを使用してプログラムを実行し、`Main` 関数の戻り値をテストします。  プログラムを Windows で実行すると、`Main` 関数から返された値が、`ERRORLEVEL` という環境変数に格納されます。  `ERRORLEVEL` 変数を検査することで、バッチ ファイルが実行結果を判断できます。  従来より、ゼロの戻り値は、実行が成功したことを示します。  次の例は、`Main` 関数からゼロを返す簡単なプログラムです。  ゼロは、プログラムが正常に実行されたことを示します。  プログラムを MainReturnValTest.cs として保存してください。  
  
 [!code-cs[csProgGuideMain#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_3.cs)]  
  
## 使用例  
 この例ではバッチ ファイルを使用するため、コマンド プロンプトからコードをコンパイルすることをお勧めします。  「[How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)」の手順に従ってコマンド ライン ビルドを有効にするか、**\[スタート\]** メニューの **\[Visual Studio ツール\]** から Visual Studio コマンド プロンプトを使用します。  コマンド プロンプトで、プログラムを保存したフォルダーに移動します。  次のコマンドにより、MainReturnValTest.cs がコンパイルされ、MainReturnValTest.exe という実行可能ファイルが生成されます。  
  
 `csc MainReturnValTest.cs`  
  
 次に、MainReturnValTest.exe を実行して結果を表示するバッチ ファイルを作成します。  次のコードをテキスト ファイルに貼り付け、MainReturnValTest.cs と MainReturnValTest.exe が含まれているフォルダーに、`test.bat` という名前で保存します。  コマンド プロンプトで「`test`」と入力して、バッチ ファイルを実行します。  
  
 コードからゼロが返されるため、バッチ ファイルは成功を報告します。  しかし、ゼロ以外の値を返すように MainReturnValTest.cs を変更し、プログラムを再コンパイルした後にバッチ ファイルを実行すると、失敗が報告されます。  
  
```  
rem test.bat  
@echo off  
MainReturnValTest  
@if "%ERRORLEVEL%" == "0" goto good  
  
:fail  
    echo Execution Failed  
    echo return value = %ERRORLEVEL%  
    goto end  
  
:good  
    echo Execution succeeded  
    echo Return value = %ERRORLEVEL%  
    goto end  
  
:end  
```  
  
## 出力例  
 `Execution succeeded`  
  
 `Return value = 0`  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [Main\(\) とコマンド ライン引数](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md)   
 [方法: コマンド ライン引数を表示する](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)   
 [方法: foreach を使用してコマンド ライン引数にアクセスする](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)