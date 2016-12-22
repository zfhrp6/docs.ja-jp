---
title: "/out (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "/out compiler option [Visual Basic]"
  - "-out compiler option [Visual Basic]"
  - "out compiler option [Visual Basic]"
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /out (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

出力ファイルの名前を指定します。  
  
## 構文  
  
```  
/out:filename  
```  
  
## 引数  
  
|||  
|-|-|  
|語句|定義|  
|`filename`|必ず指定します。  コンパイラで作成される出力ファイルの名前。  ファイル名に空白が含まれる場合、ファイル名を引用符 \(" "\) で囲みます。|  
  
## 解説  
 作成するファイルのフルネームと拡張子を指定します。  ファイル名を指定しないと、.exe ファイルの場合は `Sub Main` プロシージャを含むソース コード ファイルの名前が使用され、.dll ファイルの場合は最初のソース コード ファイルの名前が使用されます。  
  
 .exe 拡張子または .dll 拡張子を含めずにファイル名を指定した場合、`/target` コンパイラ オプションに指定された値に応じて、コンパイラによって拡張子が自動的に追加されます。  
  
||  
|-|  
|Visual Studio 統合開発環境で \/out を設定するには|  
|1.  **ソリューション エクスプローラー**でプロジェクトを選択します。  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  詳細については、「[Introduction to the Project Designer](http://msdn.microsoft.com/ja-jp/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。<br />2.  **\[アプリケーション\]** タブをクリックします。<br />3.  **\[アセンブリ名\]** ボックス内の値を変更します。|  
  
## 使用例  
 `T2.vb` をコンパイルして出力ファイル `T2.exe` を作成する場合のコード例です。  
  
```  
vbc t2.vb /out:t3.exe  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)