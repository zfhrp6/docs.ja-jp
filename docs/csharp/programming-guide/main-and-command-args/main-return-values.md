---
title: "Main() の戻り値 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
caps.latest.revision: 20
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a24a0db126945d122db7a0c8d373d0c91e5da8a2
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="main-return-values-c-programming-guide"></a>Main() の戻り値 (C# プログラミング ガイド)
`Main` メソッドは `void` を返すことができます。  
  
 [!code-cs[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_1.cs)]  
  
 `int` を返すこともできます。  
  
 [!code-cs[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_2.cs)]  
  
 `Main` からの戻り値を使用しない場合は、`void` を返すと少し簡単なコードにすることができます。 ただし、整数値を返すことによって、プログラムが状態の情報を、実行可能ファイルを呼び出す他のプログラムまたはスクリプトに伝達することができます。 次の例では、`Main` からの戻り値にアクセスする方法を示します。  
  
## <a name="example"></a>例  
 この例では、バッチ ファイルは、プログラムを実行し、`Main` 関数の戻り値をテストするために使用されます。 プログラムを Windows で実行する場合、`Main` 関数からの戻り値はすべて `ERRORLEVEL` と呼ばれる環境変数に格納されます。 バッチ ファイルは、`ERRORLEVEL` 変数を調べて、実行の結果を決定することができます。 従来、ゼロの戻り値は、正常に実行されたことを示します。 `Main` 関数からゼロを返す単純なプログラムの例を次に示します。 ゼロは、プログラムが正常に実行されたことを示します。 プログラムを MainReturnValTest.cs として保存します。  
  
 [!code-cs[csProgGuideMain#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_3.cs)]  
  
## <a name="example"></a>例  
 この例では、バッチ ファイルを使用するため、コマンド プロンプトからコードをコンパイルすることをお勧めします。 「[How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)」 (方法: Visual Studio コマンド ラインに環境変数を設定する) の指示に従って、コマンド ライン ビルドを有効にするか、[**Visual Studio Tools**] の [**スタート**] メニューから Visual Studio コマンド プロンプトを使用します。 コマンド プロンプトから、プログラムを保存したフォルダーに移動します。 次のコマンドは、MainReturnValTest.cs をコンパイルし、実行可能ファイルの MainReturnValTest.exe を生成します。  
  
 `csc MainReturnValTest.cs`  
  
 次に、バッチ ファイルを作成して、MainReturnValTest.exe を実行し、結果を表示します。 次のコードをテキスト ファイルに貼り付けて、MainReturnValTest.cs と MainReturnValTest.exe を含むフォルダーに、`test.bat` として保存します。 コマンド プロンプトで「`test`」と入力して、バッチ ファイルを実行します。  
  
 コードがゼロを返すため、バッチ ファイルで成功が報告されます。 ただし、MainReturnValTest.cs が 0 以外の値を返すように変更して、プログラムを再コンパイルする場合、バッチ ファイルの後続の実行では失敗が報告されます。  
  
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
  
## <a name="sample-output"></a>出力例  
 `Execution succeeded`  
  
 `Return value = 0`  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [Main() とコマンド ライン引数](../../../csharp/programming-guide/main-and-command-args/index.md)   
 [方法: コマンド ライン引数を表示する](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)   
 [方法: foreach を使用してコマンド ライン引数にアクセスする](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)

