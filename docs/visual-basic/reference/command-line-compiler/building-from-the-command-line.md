---
title: "コマンド ラインからのビルド (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "ビルド [Visual Basic]、コマンド ライン"
  - "Visual Basic コンパイラ、Visual Basic コンパイラの概要"
  - "コマンド ライン [Visual Basic]、コンパイラ"
  - "コマンド ライン [Visual Basic]、ビルド (コマンド ラインからの)"
  - "コマンド ライン [Visual Basic]、ビルド"
  - "コンパイラ、起動 (コマンド ラインから)"
  - "コマンド ライン ビルド"
  - "コンパイル (ソース コードを)"
  - "コマンド ライン コンパイラ、Visual Basic"
  - "コマンド ライン [Visual Basic]、Visual Basic"
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# コマンド ラインからのビルド (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] プロジェクトは、1 つ以上の独立したソース ファイルで構成されています。  コンパイルと呼ばれるプロセスの間に、これらのファイルが 1 つのパッケージにまとめられて、アプリケーションとして実行できる実行可能ファイルになります。  
  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] 統合開発環境 \(IDE\) からプログラムをコンパイルする方法の他に、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] には、コマンド ライン コンパイラが用意されています。  コマンド ライン コンパイラは、IDE の機能のすべてが必要なわけではない場合に使用できます。たとえば、システム メモリや記憶領域が限られているコンピューターを使用している場合や、そうしたコンピューターを対象としてプログラムを作成している場合などに使用できます。  
  
 コマンド ラインからコンパイルする場合、`/reference` コンパイラ オプションを使用して [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ランタイム ライブラリを明示的に参照する必要があります。  
  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] IDE でソース ファイルをコンパイルするには、**\[ビルド\]** メニューの **\[ビルド\]** をクリックします。  
  
> [!TIP]
>  Visual Studio IDE を使用してプロジェクト ファイルをビルドすると、**vbc** の関連するコマンドについての情報を出力ウィンドウのスイッチを表示できます。  この情報を表示するには、[\[オプション\] ダイアログ ボックス、\[プロジェクトおよびソリューション\]、\[ビルド\/実行\]](/visual-studio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)を開き、**\[標準\]** に **\[MSBuild プロジェクト ビルドの出力の詳細\]** または詳細出力レベルを設定します。  詳細については、「[方法: ビルド ログ ファイルを表示、保存、および構成する](../Topic/How%20to:%20View,%20Save,%20and%20Configure%20Build%20Log%20Files.md)」を参照してください。  
  
 コマンド プロンプトで MSBuild を使用してプロジェクト \(.vbproj\) ファイルをコンパイルできます。  詳細については、「[Command\-Line Reference](/visual-studio/msbuild/msbuild-command-line-reference)」および「[チュートリアル: MSBuild の使用](../Topic/Walkthrough:%20Using%20MSBuild.md)」を参照してください。  
  
## このセクションの内容  
 [How to: Invoke the Command\-Line Compiler](../Topic/How%20to:%20Invoke%20the%20Command-Line%20Compiler%20\(Visual%20Basic\).md)  
 MS\-DOS プロンプトまたは特定のサブディレクトリからコマンド ライン コンパイラを起動する方法を説明します。  
  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 変更を加えて使用できるコマンド ラインのサンプルを紹介します。  
  
## 関連項目  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)  
 アルファベット順または用途別に整理されたコンパイラ オプションの一覧です。  
  
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 コードの特定のセクションをコンパイルする方法を説明します。  
  
 [Visual Studio でのプロジェクトとソリューションのビルドおよびクリーン](/visual-studio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 各ビルドに含める要素の整理、プロジェクト プロパティの選択、およびプロジェクトのビルド順序の設定の方法を説明します。