---
title: "/win32icon | Microsoft Docs"
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
  - "win32icon compiler option [Visual Basic]"
  - "-win32icon compiler option [Visual Basic]"
  - "/win32icon compiler option [Visual Basic]"
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /win32icon
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

.ico ファイルを出力ファイルに挿入します。  この .ico ファイルは **\[エクスプローラー\]**の出力ファイルを表します。  
  
## 構文  
  
```  
/win32icon:filename  
```  
  
## 引数  
  
|||  
|-|-|  
|語句|定義|  
|`filename`|出力ファイルに加える .ico ファイル。  ファイル名に空白が含まれている場合は、二重引用符 \(" "\) で囲みます。|  
  
## 解説  
 .ico ファイルは、Microsoft Windows リソース コンパイラ \(RC\) を使って作成できます。  リソース コンパイラは Visual C\+\+ プログラムをコンパイルするときに呼び出され、.ico ファイルは .rc ファイルから作成されます。  `/win32icon` オプションと `/win32resource` オプションは相互に排他的です。  
  
 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] リソース ファイルを参照するには「[\/linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)」、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] リソース ファイルを参照するには「[\/resource](../../../visual-basic/reference/command-line-compiler/resource.md)」を確認してください  .res ファイルのインポートについては、「[\/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)」を参照してください。  
  
||  
|-|  
|Visual Studio IDE で \/win32icon を設定するには|  
|1.  **ソリューション エクスプローラー**でプロジェクトを選択します。  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  詳細については、「[Introduction to the Project Designer](http://msdn.microsoft.com/ja-jp/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。<br />2.  **\[アプリケーション\]** タブをクリックします。<br />3.  **\[アイコン\]** ボックス内の値を変更します。|  
  
## 使用例  
 `In.vb` をコンパイルし、ico ファイル `Rf.ico` をアタッチする場合のコード例です。  
  
```  
vbc /win32icon:rf.ico in.vb  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)