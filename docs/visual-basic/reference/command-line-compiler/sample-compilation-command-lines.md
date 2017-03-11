---
title: "コンパイル コマンド ラインのサンプル (Visual Basic) | Microsoft Docs"
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
  - "コマンド ライン、コンパイラ"
  - "コンパイル、コマンド ライン"
  - "コマンド ライン コンパイラ"
  - "コンパイル (ソース コードを)、コマンド ラインから"
  - "Visual Basic コンパイラ、コマンド ラインのサンプル"
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# コンパイル コマンド ラインのサンプル (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] プログラムを [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] からコンパイルする代わりに、コマンド ラインでコンパイルして、実行可能 \(.exe\) ファイルやダイナミック リンク ライブラリ \(.dll\) ファイルを作成できます。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] のコマンド ライン コンパイラは、ファイルの入出力、アセンブリ、およびデバッグを制御する一連のオプションとプリプロセッサ オプションをサポートしています。  各オプションには、それぞれ `-``option` と `/``option` という 2 つの形式があり、どちらの形式でも同じように使用できます。  ただし、ここでは `/``option` という形式だけを使用します。  
  
 以下のコマンド ラインのサンプルは、変更を加えてコード内で使用できます。  
  
|目的|使用|  
|--------|--------|  
|File.vb をコンパイルして File.exe を作成する|`vbc /reference:Microsoft.VisualBasic.dll File.vb`|  
|File.vb をコンパイルして File.dll を作成する|`vbc /target:library File.vb`|  
|File.vb をコンパイルして My.exe を作成する|`vbc /out:My.exe File.vb`|  
|最適化を有効にし、`DEBUG` シンボルを定義して、現在のディレクトリのすべての [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] ファイルをコンパイルして File2.exe を作成する|`vbc /define:DEBUG=1 /optimize /out:File2.exe *.vb`|  
|現在のディレクトリのすべての [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] ファイルをコンパイルし、ロゴも警告も表示せずに File2.dll のデバッグ バージョンを作成する|`vbc /target:library /out:File2.dll /nowarn /nologo /debug *.vb`|  
|現在のディレクトリのすべての [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] ファイルを Something.dll にコンパイルする|`vbc /target:library /out:Something.dll *.vb`|  
  
 コマンド ラインからコンパイルする場合、`/reference` コンパイラ オプションを使用して [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] ランタイム ライブラリを明示的に参照する必要があります。  
  
> [!TIP]
>  Visual Studio IDE を使用してプロジェクトをビルドすると、出力ウィンドウのコンパイラ オプションの **vbc** の関連するコマンドに関する情報を表示できます。  この情報を表示するには、[\[オプション\] ダイアログ ボックス、\[プロジェクトおよびソリューション\]、\[ビルド\/実行\]](/visual-studio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)を開き、**\[標準\]** に **\[MSBuild プロジェクト ビルドの出力の詳細\]** または詳細出力レベルを設定します。  詳細については、「[方法: ビルド ログ ファイルを表示、保存、および構成する](../Topic/How%20to:%20View,%20Save,%20and%20Configure%20Build%20Log%20Files.md)」を参照してください。  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)