---
title: "/debug (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
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
  - "debug compiler switches"
  - "/debug compiler option [Visual Basic]"
  - "-debug compiler option [Visual Basic]"
  - "debug compiler option [Visual Basic]"
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /debug (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

コンパイラでデバッグ情報を生成し、出力ファイルを作成します。  
  
## 構文  
  
```  
/debug[+ | -]  
' -or-  
/debug:[full | pdbonly]  
```  
  
## 引数  
  
|||  
|-|-|  
|語句|定義|  
|`+`  &#124; `-`|省略可能です。  `+` または `/debug` を指定すると、コンパイラによってデバッグ情報が生成され、.pdb ファイルにその情報が出力されます。  `-` を指定するのは、`/debug` を指定しないのと同じです。|  
|`full`  &#124; `pdbonly`|省略可能です。  コンパイラによって生成されるデバッグ情報の種類を指定します。  `/debug:pdbonly` を指定しなかった場合、既定値は `full` となり、実行中のプログラムにデバッガーをアタッチできます。  `pdbonly` 引数を指定すると、プログラムがデバッガーで開始されたときにはソース コードをデバッグできますが、実行中のプログラムをデバッガーにアタッチしたときはアセンブリ言語のコードしか表示されません。|  
  
## 解説  
 このオプションを使用してデバッグ ビルドを作成します。  `/debug`、`/debug+`、または `/debug:full` を指定しないと、プログラムの出力ファイルをデバッグできません。  
  
 既定では、デバッグ情報は生成されません \(`/debug-`\)。  デバッグ情報を生成するには、`/debug` または `/debug+` を指定します。  
  
 アプリケーションのデバッグ パフォーマンスを設定する方法については、「[イメージのデバッグの簡略化](../Topic/Making%20an%20Image%20Easier%20to%20Debug.md)」を参照してください。  
  
||  
|-|  
|Visual Studio 統合開発環境で \/debug を設定するには|  
|1.  **ソリューション エクスプローラー**でプロジェクトが選択されている状態で、**\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  詳細については、「[Introduction to the Project Designer](http://msdn.microsoft.com/ja-jp/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。<br />2.  **\[コンパイル\]** タブをクリックします。<br />3.  **\[詳細コンパイル オプション\]** をクリックします。<br />4.  **\[デバッグ情報を作成\]** ボックスの値を変更します。|  
  
## 使用例  
 デバッグ情報をファイル `App.exe` に出力する場合のコード例です。  
  
```  
vbc /debug /out:app.exe test.vb  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)