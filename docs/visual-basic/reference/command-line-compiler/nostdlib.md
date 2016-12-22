---
title: "/nostdlib (Visual Basic) | Microsoft Docs"
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
  - "nostdlib compiler option [Visual Basic]"
  - "-nostdlib compiler option [Visual Basic]"
  - "/nostdlib compiler option [Visual Basic]"
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /nostdlib (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

コンパイラが標準のライブラリを自動的に参照しないよう指定します。  
  
## 構文  
  
```  
/nostdlib  
```  
  
## 解説  
 `/nostdlib` オプションは、System.dll アセンブリへの自動参照を削除して、コンパイラが Vbc.rsp ファイルを読み取らないようにします。  Vbc.exe ファイルと同じディレクトリにある Vbc.rsp ファイルは、一般に使用される [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] アセンブリを参照し、`System` 名前空間および `Microsoft.VisualBasic` 名前空間をインポートします。  
  
> [!NOTE]
>  Mscorlib.dll アセンブリおよび Microsoft.VisualBasic.dll アセンブリは、常に参照されます。  
  
> [!NOTE]
>  `/nostdlib` オプションは Visual Studio の開発環境内からは利用できません。このオプションを利用できるのは、コマンド ラインからコンパイルするときだけです。  
  
## 使用例  
 次のコードは、標準ライブラリを参照しないで `T2.vb` をコンパイルします。  `_MYTYPE` 条件付きコンパイル定数を文字列 "Empty" に設定して、`My` オブジェクトを削除する必要があります。  
  
```  
vbc /nostdlib /define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## 参照  
 [\/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Customizing Which Objects are Available in My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)