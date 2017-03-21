---
title: "コマンド ライン (Visual Basic の場合) からのビルド |Microsoft ドキュメント"
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
- builds [Visual Basic], command-line
- Visual Basic compiler, about Visual Basic compiler
- command line [Visual Basic], compilers
- command line [Visual Basic], building from
- command line [Visual Basic], builds
- compilers, invoking from command line
- command-line builds
- compiling source code
- command-line compilers, Visual Basic
- command line [Visual Basic], Visual Basic
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
caps.latest.revision: 13
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
ms.openlocfilehash: 49f84c221e18457ab46534ca46da7c4764a8ee40
ms.lasthandoff: 03/13/2017

---
# <a name="building-from-the-command-line-visual-basic"></a>コマンド ラインからのビルド (Visual Basic)
A[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プロジェクトは&1; つ以上の別のソース ファイルの構成されています。 コンパイルと呼ばれるプロセス中にこれらのファイルが&1; つのパッケージにまとめられて — アプリケーションとして実行できる実行可能ファイルです。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]内からプログラムをコンパイルする別の方法として、コマンド ライン コンパイラを提供、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]統合開発環境 (IDE) です。 コマンド ライン コンパイラは、IDE の機能の完全なセットが不要になる状況向けに設計-などとまたはいる限られたシステムのメモリや記憶域の空き領域を持つコンピューターの記述。  
  
 コマンドラインからコンパイルするときは、Microsoft を明示的に参照する必要があります[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]のランタイム ライブラリ、`/reference`コンパイラ オプション。  
  
 内からソース ファイルをコンパイルする、 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] IDE、選択、**ビルド**コマンドを**ビルド**メニュー。  
  
> [!TIP]
>  Visual Studio IDE を使用してプロジェクト ファイルをビルドする場合は、関連付けられたに関する情報を表示できます**vbc**コマンドと出力 ウィンドウでスイッチにします。 この情報を表示する、[オプション ダイアログ ボックス、プロジェクトとソリューションをビルドおよび実行](https://docs.microsoft.com/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)、し、設定、 **MSBuild プロジェクトのビルド出力の詳細度**に**標準**または詳細度の高いレベルです。 詳細については、「[方法: ビルド ログ ファイルを表示、保存、および構成する](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7)」をご覧ください。  
  
 MSBuild を使用して、コマンド プロンプトで、プロジェクト (.vbproj) ファイルをコンパイルできます。 詳細については、次を参照してください。[コマンド ライン リファレンス](https://docs.microsoft.com/visualstudio/msbuild/msbuild-command-line-reference)と[チュートリアル: MSBuild を使用して](http://msdn.microsoft.com/library/b8a8b866-bb07-4abf-b9ec-0b40d281c310)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法 : コマンド ライン コンパイラを起動する](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)  
 MS-DOS プロンプトまたは固有のサブディレクトリからコマンド ライン コンパイラを起動する方法について説明します。  
  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 独自の変更できるコマンドラインのサンプルの一覧を示します。  
  
## <a name="related-sections"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 アルファベット順または目的別に整理コンパイラ オプションの一覧を提供します。  
  
 [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 コードの特定のセクションをコンパイルする方法について説明します。  
  
 [Visual Studio でのプロジェクトとソリューションのビルドおよびクリーン](https://docs.microsoft.com/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 どのようなさまざまなビルドに含まれる、プロジェクトのプロパティ を選択および適切な順序でプロジェクトをビルドすることを確認整理する方法について説明します。
