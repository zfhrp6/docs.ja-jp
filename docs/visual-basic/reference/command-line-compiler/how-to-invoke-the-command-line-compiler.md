---
title: '方法: コマンド ライン コンパイラを起動する (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f1ccf08ba58fa6af60bd8ffd7cba79b205dc0f3d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a>方法: コマンド ライン コンパイラを起動する (Visual Basic)
コマンド ラインで、MS-DOS のプロンプトとも呼ばれるにその実行可能ファイルの名前を入力して、コマンド ライン コンパイラを呼び出すことができます。 既定の Windows コマンド プロンプトからコンパイルする場合は、実行可能ファイルへの完全修飾パスを入力する必要があります。 この既定の動作をオーバーライドするを使用するか、[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]コマンド プロンプト、または、PATH 環境変数を変更します。 コンパイラの名前を入力するだけで任意のディレクトリからコンパイルを両方ができます。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-visual-studio-command-prompt"></a>Visual Studio コマンド プロンプトを使用してコンパイラを起動するには  
  
1.  Microsoft Visual Studio プログラム グループ内の Visual Studio Tools プログラム フォルダーを開きます。  
  
2.  使用することができます、[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]コマンド プロンプトを Visual Studio がインストールされている場合、コンピューター上の任意のディレクトリから、コンパイラにアクセスします。  
  
3.  呼び出す、[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]コマンド プロンプトです。  
  
4.  コマンドラインで「 `vbc.exe` *sourceFileName*し、ENTER キーを押します。  
  
     というディレクトリに、ソース コードを格納する場合など、 `SourceFiles`、するはプロンプトを開き、コマンド`cd SourceFiles`そのディレクトリに変更します。 ディレクトリには、という名前のソース ファイルが含まれている場合`Source.vb`、」と入力してコンパイルする`vbc.exe Source.vb`です。  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a>Windows コマンド プロンプトをコンパイラに PATH 環境変数を設定するには  
  
1.  ローカル ディスクに Vbc.exe を検索するのにには、Windows 検索機能を使用します。  
  
     コンパイラが配置されているディレクトリの正確な名前は、Windows ディレクトリの場所と、".NET Framework の"インストールされているバージョンに依存します。 1 つ以上の".NET Framework のバージョン"をインストールした場合 (通常は最新のバージョン) を使用するバージョンが判断する必要があります。  
  
2.  **開始**メニューを右クリックして**マイ コンピューター**、順にクリック**プロパティ**ショートカット メニューからです。  
  
3.  クリックして、**詳細** タブをクリックして**環境変数**です。  
  
4.  **システム**変数ウィンドウで、**パス**クリックしてリストから**編集**です。  
  
5.  **編集システム**変数 ダイアログ ボックス、内の文字列の末尾にカーソルを移動、**変数値**フィールドで、セミコロン (;) を入力し、続けて手順 1. で検出された完全なディレクトリ名。  
  
6.  をクリックして**OK**を編集内容を確認し、ダイアログ ボックスを閉じます。  
  
     PATH 環境変数を変更すると、後に実行できます Visual Basic コンパイラ、Windows コマンド プロンプトで任意のディレクトリから、コンピューター上。  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a>Windows コマンド プロンプトを使用するコンパイラを起動するには  
  
1.  **開始** メニューをクリックして、**アクセサリ**フォルダーを開き、 **Windows コマンド プロンプト**です。  
  
2.  コマンドラインで「 `vbc.exe` *sourceFileName*し、ENTER キーを押します。  
  
     というディレクトリに、ソース コードを格納する場合など、 `SourceFiles`、するはプロンプトを開き、コマンド`cd SourceFiles`そのディレクトリに変更します。 ディレクトリには、という名前のソース ファイルが含まれている場合`Source.vb`、」と入力してコンパイルする`vbc.exe Source.vb`です。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
