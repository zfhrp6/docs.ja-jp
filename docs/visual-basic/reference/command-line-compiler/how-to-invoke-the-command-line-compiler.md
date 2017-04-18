---
title: "方法: コマンド ライン コンパイラ (Visual Basic) を起動 |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line, arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 69c95289f91f712bd3fda03a7f582d879141591a
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a>方法: コマンド ライン コンパイラを起動する (Visual Basic)
コマンド ラインで、MS-DOS プロンプトとも呼ばれますにその実行可能ファイルの名前を入力して、コマンド ライン コンパイラを呼び出すことができます。 既定の Windows コマンド プロンプトからコンパイルする場合は、実行可能ファイルへの完全修飾パスを入力する必要があります。 この既定の動作をオーバーライドする使用するか、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]コマンド プロンプト、または PATH 環境変数を変更します。 コンパイラの名前を入力するだけで任意のディレクトリからコンパイルをどちらもができます。  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-visual-studio-command-prompt"></a>Visual Studio コマンド プロンプトを使用するコンパイラを起動するには  
  
1.  Microsoft Visual Studio のプログラム グループ内の Visual Studio Tools プログラム フォルダーを開きます。  
  
2.  使用することができます、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]コマンド プロンプトは、Visual Studio がインストールされている場合、コンピューター上の任意のディレクトリから、コンパイラにアクセスします。  
  
3.  呼び出す、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]コマンド プロンプト。  
  
4.  コマンドラインで「 `vbc.exe` *sourceFileName* ENTER キーを押します。  
  
     という名前のディレクトリにソース コードを格納する場合など`SourceFiles`、コマンド プロンプトと型が開きます`cd SourceFiles`そのディレクトリに変更します。 ディレクトリには、という名前のソース ファイルが含まれている場合`Source.vb`、」と入力してコンパイルすることが`vbc.exe Source.vb`です。  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a>Windows コマンド プロンプトをコンパイラに PATH 環境変数を設定するには  
  
1.  Windows Search の機能を使用して、ローカル ハード_ディスク上の Vbc.exe を検索します。  
  
     コンパイラがあるディレクトリの正確な名前の Windows ディレクトリの場所とのバージョンによって異なる、[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)]をインストールします。 複数のバージョンがインストールされている場合、[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)]インストールされている、(通常は最新のバージョン) を使用するバージョンを決定する必要があります。  
  
2.  **開始** メニューの を右クリックして**マイ コンピューター**、 をクリックし、**プロパティ**のショートカット メニュー。  
  
3.  クリックして、**詳細**タブをクリックし、をクリックして**環境変数**します。  
  
4.  **システム**変数ウィンドウで、**パス**、リストをクリックしてから**編集**します。  
  
5.  **編集システム**変数 ダイアログ ボックス内の文字列の末尾にカーソルを移動、**変数値**フィールドで、セミコロン (;) を入力し、続けて手順 1. で検出された完全なディレクトリ名です。  
  
6.  クリックして**OK**を編集内容を確認し、ダイアログ ボックスを閉じます。  
  
     実行することができます、PATH 環境変数を変更した後、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラ、Windows コマンド プロンプトで、コンピューター上の任意のディレクトリからです。  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a>Windows コマンド プロンプトを使用してコンパイラを起動するには  
  
1.  **開始**メニューをクリックして、**アクセサリ**フォルダー、およびを開きます、 **Windows コマンド プロンプト**します。  
  
2.  コマンドラインで「 `vbc.exe` *sourceFileName* ENTER キーを押します。  
  
     という名前のディレクトリにソース コードを格納する場合など`SourceFiles`、コマンド プロンプトと型が開きます`cd SourceFiles`そのディレクトリに変更します。 ディレクトリには、という名前のソース ファイルが含まれている場合`Source.vb`、」と入力してコンパイルすることが`vbc.exe Source.vb`です。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
