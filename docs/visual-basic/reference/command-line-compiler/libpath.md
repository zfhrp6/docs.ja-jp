---
title: "/libpath | Microsoft Docs"
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
  - "libpath compiler option [Visual Basic]"
  - "/libpath compiler option [Visual Basic]"
  - "-libpath compiler option [Visual Basic]"
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# /libpath
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

参照先アセンブリの場所を指定します。  
  
## 構文  
  
```  
/libpath:dirList  
```  
  
## 引数  
  
|||  
|-|-|  
|語句|定義|  
|`dirList`|必ず指定します。  参照先アセンブリが現在の作業ディレクトリ \(コンパイラを起動するディレクトリ\) または共通言語ランライムのシステム ディレクトリにない場合に、コンパイラが探すディレクトリのリストです。ディレクトリはセミコロンで区切って指定します。  ディレクトリ名に空白が含まれる場合は、二重引用符 \(" "\) で囲む必要があります。|  
  
## 解説  
 `/libpath` オプションでは、[\/reference](../../../visual-basic/reference/command-line-compiler/reference.md) オプションによって参照されるアセンブリの場所を指定します。  
  
 コンパイラは、完全には修飾されていないアセンブリ参照を次の順序で検索します。  
  
1.  現在の作業ディレクトリ。  これは、コンパイラが起動されるディレクトリです。  
  
2.  共通言語ランタイムのシステム ディレクトリ。  
  
3.  `/libpath` で指定したディレクトリ。  
  
4.  LIB 環境変数で指定したディレクトリ。  
  
 `/libpath` オプションは追加して指定できます。繰り返して指定すると前の値に追加されます。  
  
 アセンブリ参照を指定するには、`/reference` を使用します。  
  
||  
|-|  
|Visual Studio 統合開発環境で \/libpath を設定するには|  
|1.  **ソリューション エクスプローラー**でプロジェクトを選択します。  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  詳細については、「[Introduction to the Project Designer](http://msdn.microsoft.com/ja-jp/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。<br />2.  **\[参照設定\]** タブをクリックします。<br />3.  **\[参照パス...\]** ボタンをクリックします。<br />4.  **\[参照パス\]** ダイアログ ボックスで、**\[フォルダー:\]** ボックスにディレクトリ名を入力します。<br />5.  **\[フォルダーの追加\]** をクリックします。|  
  
## 使用例  
 `T2.vb` をコンパイルして .exe ファイルを作成する場合のコード例です。  コンパイラはアセンブリを参照するために、まず作業ディレクトリ \(C: ドライブのルートディレクトリ\) を探し、次に C: ドライブの New Assemblies ディレクトリを探します。  
  
```  
vbc /libpath:c:\;"c:\New Assemblies" /reference:t2.dll t2.vb  
```  
  
## 参照  
 [アセンブリとグローバル アセンブリ キャッシュ](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)