---
title: "サンプルのコンパイル コマンドライン (Visual Basic) |Microsoft ドキュメント"
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
- command line, compilers
- compilation, command-line
- command-line compilers
- compiling source code, from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 918787b3377f2e5a636a6b098046ac2f455efcdd
ms.lasthandoff: 03/13/2017

---
# <a name="sample-compilation-command-lines-visual-basic"></a>コンパイル コマンド ラインのサンプル (Visual Basic)
コンパイルする代わりに[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]内からプログラム[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]、実行可能 (.exe) ファイルまたはダイナミック リンク ライブラリ (.dll) ファイルを生成するためのコマンドラインからコンパイルすることができます。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コマンド ライン コンパイラは、入力呼び出し力ファイル、アセンブリ、およびデバッグを制御するオプションとプリプロセッサのオプションの完全なセットをサポートしています。 各オプションは、2 つの交換可能な形式で利用可能:`-``option`と`/``option`です。 このドキュメントの表示のみ、`/``option`フォームです。  
  
 次の表は、独自の変更できるサンプルのコマンドラインを示します。  
  
|目的|用途|  
|--------|---------|  
|.Vb というファイルをコンパイルして File.exe を作成します。|`vbc /reference:Microsoft.VisualBasic.dll File.vb`|  
|.Vb というファイルをコンパイルして作成します|`vbc /target:library File.vb`|  
|.Vb というファイルをコンパイルして My.exe を作成します。|`vbc /out:My.exe File.vb`|  
|すべてコンパイル[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]ファイルを現在のディレクトリに、最適化を有効にし、`DEBUG`シンボルを定義するには、File2.exe を生成します。|`vbc /define:DEBUG=1 /optimize /out:File2.exe *.vb`|  
|すべてコンパイル[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]ロゴや警告を表示することがなく File2.dll のデバッグ バージョンを作成して、現在のディレクトリ内のファイル|`vbc /target:library /out:File2.dll /nowarn /nologo /debug *.vb`|  
|すべてコンパイル[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Something.dll の現在のディレクトリ内のファイル|`vbc /target:library /out:Something.dll *.vb`|  
  
 コマンドラインからコンパイルするときは、Microsoft を明示的に参照する必要があります[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]のランタイム ライブラリ、`/reference`コンパイラ オプション。  
  
> [!TIP]
>  Visual Studio IDE を使用して、プロジェクトをビルドする場合は、関連付けられたに関する情報を表示できます**vbc**コマンド、出力ウィンドウには、そのコンパイラ オプションにします。 この情報を表示する、[のオプション ダイアログ ボックス、プロジェクトとソリューションをビルドおよび実行](https://docs.microsoft.com/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)、し、設定、 **MSBuild プロジェクトのビルド出力の詳細度**に**標準**または詳細度の高いレベルです。 詳細については、「[方法: ビルド ログ ファイルを表示、保存、および構成する](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
