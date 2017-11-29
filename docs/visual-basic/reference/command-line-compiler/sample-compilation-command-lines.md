---
title: "コンパイル コマンド ラインのサンプル (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e168d40a22ca3737bee18f966df95988a2736a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sample-compilation-command-lines-visual-basic"></a>コンパイル コマンド ラインのサンプル (Visual Basic)
コンパイルする代わりに[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]内からプログラム[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]、実行可能 (.exe) ファイルまたはダイナミック リンク ライブラリ (.dll) ファイルを生成するためにコマンドラインからコンパイルすることができます。  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]コマンド ライン コンパイラは、入力と出力ファイル、アセンブリ、およびデバッグを制御するオプションとプリプロセッサ オプションの完全なセットをサポートしています。 各オプションは、2 つの交換形式で利用可能:`-``option`と`/``option`です。 このドキュメントのみが表示されます、`/``option`フォーム。  
  
 次の表は、独自の用途を変更するサンプルのコマンドラインを一覧表示します。  
  
|目的|用途|  
|--------|---------|  
|File.vb をコンパイルして File.exe を作成します。|`vbc /reference:Microsoft.VisualBasic.dll File.vb`|  
|File.vb をコンパイルして File.dll を作成します。|`vbc /target:library File.vb`|  
|File.vb をコンパイルして My.exe を作成します。|`vbc /out:My.exe File.vb`|  
|すべてコンパイル[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]を最適化して、現在のディレクトリ内のファイルと`DEBUG`File2.exe を生成したシンボルを定義するには、|`vbc /define:DEBUG=1 /optimize /out:File2.exe *.vb`|  
|すべてコンパイル[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]ロゴや警告を表示することがなく、デバッグ バージョンの File2.dll を生成する、現在のディレクトリ内のファイル|`vbc /target:library /out:File2.dll /nowarn /nologo /debug *.vb`|  
|すべてコンパイル[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Something.dll を現在のディレクトリ内のファイル|`vbc /target:library /out:Something.dll *.vb`|  
  
 をコマンドラインからコンパイルするときは、Microsoft を明示的に参照する必要があります[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]経由のランタイム ライブラリ、`/reference`コンパイラ オプション。  
  
> [!TIP]
>  関連付けられているに関する情報を表示するには、Visual Studio IDE を使用してプロジェクトをビルドするときに**vbc**コマンドは、出力ウィンドウでコンパイラ オプションとします。 この情報を表示、開く、[オプション ダイアログ ボックス、プロジェクトとソリューションをビルドおよび実行](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)、し、設定、 **MSBuild プロジェクトのビルド出力の詳細度**に**標準**またはより高度な詳細度。 詳細については、「[方法: ビルド ログ ファイルを表示、保存、および構成する](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
