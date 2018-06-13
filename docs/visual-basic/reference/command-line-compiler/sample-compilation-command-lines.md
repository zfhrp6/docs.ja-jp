---
title: コンパイル コマンド ラインのサンプル (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b0f1fc1d269801efdbf2e89d10679dc8159851f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653664"
---
# <a name="sample-compilation-command-lines-visual-basic"></a>コンパイル コマンドラインのサンプル (Visual Basic)
Visual Studio 内から Visual Basic プログラムをコンパイルする代わりに、実行可能 (.exe) ファイルまたはダイナミック リンク ライブラリ (.dll) ファイルを生成するためにコマンドラインからコンパイルすることができます。  
  
 Visual Basic のコマンド ライン コンパイラは、出力ファイル、アセンブリ、およびデバッグおよびプリプロセッサ オプションおよび入力を制御するオプションの完全なセットをサポートします。 各オプションは、2 つの交換形式で利用可能:`-option`と`/option`です。 このドキュメントのみが表示されます、`-option`フォーム。  
  
 次の表は、独自の用途を変更するサンプルのコマンドラインを一覧表示します。  
  
|終了|使用|  
|--------|---------|  
|File.vb をコンパイルして File.exe を作成します。|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|File.vb をコンパイルして File.dll を作成します。|`vbc -target:library File.vb`|  
|File.vb をコンパイルして My.exe を作成します。|`vbc -out:My.exe File.vb`|  
|File.vb をコンパイルし、ライブラリと File.dll をという名前の参照アセンブリの両方を作成|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|最適化して、現在のディレクトリ内のすべての Visual Basic ファイルをコンパイルし、 `DEBUG` File2.exe を生成したシンボルを定義するには、|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|ロゴや警告を表示することがなく、デバッグ バージョンの File2.dll を生成する、現在のディレクトリ内のすべての Visual Basic ファイルをコンパイルします。|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|Something.dll を現在のディレクトリ内のすべての Visual Basic ファイルをコンパイルします。|`vbc -target:library -out:Something.dll *.vb`|  
  
> [!TIP]
>  関連付けられているに関する情報を表示するには、Visual Studio IDE を使用してプロジェクトをビルドするときに**vbc**コマンドは、出力ウィンドウでコンパイラ オプションとします。 この情報を表示、開く、[オプション ダイアログ ボックス、プロジェクトとソリューションをビルドおよび実行](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)、し、設定、 **MSBuild プロジェクトのビルド出力の詳細度**に**標準**またはより高度な詳細度。   
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
