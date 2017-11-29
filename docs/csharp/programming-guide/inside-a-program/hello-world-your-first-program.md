---
title: "Hello World -- 最初のプログラム (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: get-started-article
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
caps.latest.revision: "39"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c17dcce921f3a6ff1a9c547c5ff5d34c3dbbf28d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="hello-world----your-first-program-c-programming-guide"></a>Hello World -- 最初のプログラム (C# プログラミング ガイド)
次の手順では、従来の "Hello World!" プログラムの C# バージョンを 作成します。 このプログラムでは `Hello World!` という文字列を表示します。  
  
 基本概念の例については、「[Visual C# と Visual Basic の概要](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)」を参照してください。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-and-run-a-console-application"></a>コンソール アプリケーションを作成し、実行するには  
  
1.  Visual Studio を起動します。  
  
2.  メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]**の順にクリックします。  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
3.  **[インストール済み]**、**[テンプレート]**、**[Visual C#]** の順に展開し、**[コンソール アプリケーション]** を選択します。  
  
4.  **[名前]** ボックスにプロジェクト名を指定し、**[OK]** をクリックします。  
  
     **ソリューション エクスプローラー**に新しいプロジェクトが表示されます。  
  
5.  **コード エディター**で Program.cs が開いていない場合は、**ソリューション エクスプローラー**で **Program.cs** のショートカット メニューを開き、**[コードの表示]** をクリックします。  
  
6.  Program.cs の内容を次のコードで置き換えます。  
  
     [!code-csharp[csProgGuide#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_1.cs)]  
  
7.  F5 キーを押してプロジェクトを実行します。 `Hello World!` という行を含むコマンド プロンプト ウィンドウが表示されます。  
  
 次に、このプログラムの重要な部分を調べます。  
  
## <a name="comments"></a>コメント  
 最初の行はコメントになっています。 「`//`」という文字があると、これ以降その行はコメントになります。  
  
 [!code-csharp[csProgGuide#32](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_2.cs)]  
  
 テキスト ブロックを `/*` 文字と `*/` 文字で囲んでコメントにすることもできます。 これを次の例に示します。  
  
 [!code-csharp[csProgGuide#33](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_3.cs)]  
  
## <a name="main-method"></a>Main メソッド  
 C# コンソール アプリケーションには、`Main` メソッドが必要です。このメソッドの中で制御を開始して終了します。 `Main` メソッドでは、オブジェクトを作成し、ほかのメソッドを実行します。  
  
 `Main` メソッドはクラスまたは構造体の中に存在する [static](../../../csharp/language-reference/keywords/static.md) メソッドです。 前の "Hello World!" の 例では、`Hello` という名前のクラスに存在していました。 次の方法のいずれかで `Main` メソッドを宣言できます。  
  
-   `void` 型を返すことができます。  
  
     [!code-csharp[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_4.cs)]  
  
-   整数を返すこともできます。  
  
     [!code-csharp[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_5.cs)]  
  
-   どちらの戻り値の型でも、次のように引数を受け取ることができます。  
  
     [!code-csharp[csProgGuideMain#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_6.cs)]  
  
     または  
  
     [!code-csharp[csProgGuideMain#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_7.cs)]  
  
 `Main` メソッドのパラメーターである `args` は、`string` の配列で、プログラムの実行時に使用したコマンド ライン引数を含みます。 C++ とは異なり、この配列には実行可能 (exe) ファイルの名前は含まれていません。  
  
 コマンド ライン引数の使用方法の詳細については、「[Main() とコマンド ライン引数](../../../csharp/programming-guide/main-and-command-args/index.md)」および「[方法: コマンド ラインを使用してアセンブリを作成および使用する](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)」を参照してください。  
  
 <xref:System.Console.ReadKey%2A> メソッドの末尾で `Main` を呼び出すと、F5 キーを押してデバッグ モードでプログラムを実行するときに、出力を読み取る前にコンソール ウィンドウが終了することを回避できます。  
  
## <a name="input-and-output"></a>入出力  
 C# プログラムは、普通、.NET Framework のランタイム ライブラリが提供する入出力サービスを使用します。 ステートメント `System.Console.WriteLine("Hello World!");` では、<xref:System.Console.WriteLine%2A> メソッドを使用しています。 これは、ランタイム ライブラリの <xref:System.Console> クラスの出力メソッドの 1 つです。 文字列パラメーターを標準出力ストリームに出力し、最後に改行を付け加えます。 別の入出力操作には、他の <xref:System.Console> メソッドを使用できます。 `using System;` ディレクティブをプログラムの開始時にインクルードした場合は、完全に修飾せずに <xref:System> クラスおよびメソッドを直接使用できます。 たとえば、`Console.WriteLine` の代わりに `System.Console.WriteLine` を呼び出すことができます。  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_8.cs)]  
  
 [!code-csharp[csProgGuide#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_9.cs)]  
  
 入出力メソッドの詳細については、「<xref:System.IO>」を参照してください。  
  
## <a name="command-line-compilation-and-execution"></a>コマンド ライン コンパイルと実行  
 "Hello World!" プログラムは、 Visual Studio 統合開発環境 (IDE) の代わりに、コマンド ラインを使用してコンパイルできます。  
  
#### <a name="to-compile-and-run-from-a-command-prompt"></a>コマンド プロンプトからコンパイルおよび実行するには  
  
1.  前の手順のコードをテキスト エディターに貼り付け、テキスト ファイルとして保存します。 そのファイルに `Hello.cs` という名前を付けます。 C# のソース コード ファイルでは、`.cs` という拡張子を使います。  
  
2.  次のいずれかの手順を実行してコマンド プロンプト ウィンドウを開きます。  
  
    -   Windows 10 の場合、**[スタート]** メニューで `Developer Command Prompt` を検索し、**[開発者コマンド プロンプト for VS 2017]** をタップまたは選択します。  
  
         [開発者コマンド プロンプト] ウィンドウが表示されます。  
  
    -   Windows 7 の場合、**[スタート]** メニューを開き、Visual Studio の現在のバージョンのフォルダーを展開し、**[Visual Studio Tools]** のショートカット メニューを開いて、**[開発者コマンド プロンプト for VS 2017]** をクリックします。  
  
         [開発者コマンド プロンプト] ウィンドウが表示されます。  
  
    -   標準のコマンド プロンプト ウィンドウからコマンド ライン ビルドを有効にします。  
  
         「[方法: Visual Studio のコマンドラインのための環境変数を設定する](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)」を参照してください。  
  
3.  コマンド プロンプト ウィンドウで、`Hello.cs` ファイルが格納されているフォルダーに移動します。  
  
4.  `Hello.cs` をコンパイルするには、次のコマンドを入力します。  
  
     `csc Hello.cs`  
  
     プログラムにコンパイル エラーがない場合、`Hello.exe` という名前の実行可能ファイルが作成されます。  
  
5.  コマンド プロンプトで、次のコマンドを入力してプログラムを実行します。  
  
     `Hello`  
  
 C# コンパイラとそのオプションの詳細については、「[C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)」を参照してください。
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [インサイド C# プログラム](../../../csharp/programming-guide/inside-a-program/index.md)  
 [文字列](../../../csharp/programming-guide/strings/index.md)  
 [\<paveover>C# サンプル アプリケーション](http://msdn.microsoft.com/en-us/9a9d7aaa-51d3-4224-b564-95409b0f3e15)  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [Main() とコマンド ライン引数](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [Visual C# と Visual Basic の概要](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
