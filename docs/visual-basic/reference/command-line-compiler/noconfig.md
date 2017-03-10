---
title: "/noconfig | Microsoft Docs"
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
  - "noconfig compiler option [Visual Basic]"
  - "-noconfig compiler option [Visual Basic]"
  - "/noconfig compiler option [Visual Basic]"
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# /noconfig
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

よく使用される [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] アセンブリを自動的に参照したり、`System` および `Microsoft.VisualBasic` 名前空間をインポートしたりしないようコンパイラに指示します。  
  
## 構文  
  
```  
/noconfig  
```  
  
## 解説  
 `/noconfig` オプションは、コンパイルに Vbc.rsp ファイルを使用しないようにコンパイラに指示します。Vbc.rsp ファイルは、Vbc.exe ファイルと同じディレクトリにあります。  Vbc.rsp ファイルはよく使用される [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] アセンブリを参照し、`System` 名前空間と `Microsoft.VisualBasic` 名前空間をインポートします。  コンパイラは `/nostdlib` オプションが指定されている場合を除き、System.dll アセンブリを暗黙的に参照します。  `/nostdlib` オプションを指定すると、コンパイラは Vbc.rsp を使ってコンパイラしなくなるか、または System.dll アセンブリを自動的に参照しなくなります。  
  
> [!NOTE]
>  Mscorlib.dll アセンブリおよび Microsoft.VisualBasic.dll アセンブリは、常に参照されます。  
  
 Vbc.rsp ファイルを変更して、すべての Vbc.exe のコンパイルで使用する追加のコンパイラ オプションを指定できます \(`/noconfig` オプションが指定されている場合を除きます\)。  詳細については、「[@ \(Specify Response File\)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)」を参照してください。  
  
 コンパイラは、`vbc` コマンドに渡されるオプションを最後に処理します。  このため、コマンド ラインに指定したオプションは、Vbc.rsp ファイル内の同じオプションの設定をオーバーライドします。  
  
> [!NOTE]
>  `/noconfig` オプションは Visual Studio の開発環境内からは利用できません。このオプションを利用できるのは、コマンド ラインからコンパイルするときだけです。  
  
## 参照  
 [\/nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)   
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [@ \(Specify Response File\)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)   
 [\/reference](../../../visual-basic/reference/command-line-compiler/reference.md)