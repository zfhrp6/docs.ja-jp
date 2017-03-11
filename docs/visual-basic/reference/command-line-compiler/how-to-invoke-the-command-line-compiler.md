---
title: "How to: Invoke the Command-Line Compiler (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "command-line arguments"
  - "vbc.exe"
  - "Visual Basic compiler, starting"
  - "command line, arguments"
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
caps.latest.revision: 28
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 28
---
# How to: Invoke the Command-Line Compiler (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

コマンド ライン コンパイラを起動するには、コマンド ライン \(MS\-DOS プロンプト\) で実行可能ファイルの名前を入力します。  既定の方法で、つまり Windows のコマンド プロンプトからコンパイルする場合は、実行可能ファイルの絶対パスを入力する必要があります。  この既定の動作をオーバーライドするには、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] のコマンド プロンプトを使うか、または PATH 環境変数を変更します。  どちらの方法でも、任意のディレクトリからコンパイラ名を入力するだけでコンパイルできます。  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### Visual Studio コマンド プロンプトを使ってコンパイラを起動するには  
  
1.  Microsoft Visual Studio のプログラム グループ内の、Visual Studio Tools プログラムのフォルダーを開きます。  
  
2.  Visual Studio がインストールされているコンピューターの任意のディレクトリからコンパイラにアクセスするために [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] のコマンド プロンプトを使用できます。  
  
3.  [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] のコマンド プロンプトを起動します。  
  
4.  コマンド ラインで `vbc.exe` *sourceFileName* と入力し、Enter キーを押します。  
  
     たとえば、ソース コードを `SourceFiles` ディレクトリに格納したとすると、コマンド プロンプトを開き、`cd SourceFiles` と入力してそのディレクトリに移動します。  ソース ファイルをディレクトリに `Source.vb` という名前で格納していれば、`vbc.exe Source.vb` と入力してコンパイルできます。  
  
### Windows のコマンド プロンプト用に、コンパイラへの PATH 環境変数を設定するには  
  
1.  Windows の検索機能を使用して、ローカル ディスクで Vbc.exe を検索します。  
  
     コンパイラが格納されているディレクトリの名前は、Windows ディレクトリの場所、およびインストールされている [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact-md.md)] のバージョンによって決まります。  複数のバージョンの [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact-md.md)] がインストールされている場合は、使用するバージョン \(通常は最新のバージョン\) を決定する必要があります。  
  
2.  **\[スタート\]** メニューの **\[マイ コンピューター\]** を右クリックし、ショートカット メニューの **\[プロパティ\]** をクリックします。  
  
3.  **\[詳細\]** タブをクリックし、**\[環境変数\]** をクリックします。  
  
4.  **\[システム環境変数\]** の一覧の **\[Path\]** を選択し、**\[編集\]** をクリックします。  
  
5.  **\[システム変数の編集\]** ダイアログ ボックスで、**\[変数値\]** ボックスの文字列の末尾にカーソルを移動し、セミコロン \(;\) に続けて手順 1 で検索されたディレクトリの完全パスを入力します。  
  
6.  **\[OK\]** をクリックして編集を完了し、ダイアログ ボックスを閉じます。  
  
     PATH 環境変数を変更したら、Windows のコマンド プロンプトを使用して、コンピューターの任意のディレクトリから [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コンパイラを実行できます。  
  
### Windows のコマンド プロンプトを使ってコンパイラを起動するには  
  
1.  **\[スタート\]** メニューの **\[アクセサリ\]** フォルダーをクリックし、**\[コマンド プロンプト\]** を開きます。  
  
2.  コマンド ラインで `vbc.exe` *sourceFileName* と入力し、Enter キーを押します。  
  
     たとえば、ソース コードを `SourceFiles` ディレクトリに格納したとすると、コマンド プロンプトを開き、`cd SourceFiles` と入力してそのディレクトリに移動します。  ソース ファイルをディレクトリに `Source.vb` という名前で格納していれば、`vbc.exe Source.vb` と入力してコンパイルできます。  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)