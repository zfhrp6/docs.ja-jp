---
title: "/verbose | Microsoft Docs"
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
  - "verbose compiler option [Visual Basic]"
  - "-verbose compiler option [Visual Basic]"
  - "/verbose compiler option [Visual Basic]"
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# /verbose
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

コンパイラで、詳細なステータスとエラー メッセージを生成します。  
  
## 構文  
  
```  
/verbose[+ | -]  
```  
  
## 引数  
 `+` &#124; `-`  
 省略可能です。  `/verbose` を指定すると `/verbose+` を指定した場合と同じになり、詳細なメッセージが生成されます。  このオプションの既定値は `/verbose-` です。  
  
## 解説  
 `/verbose` オプションを指定すると、コンパイラが生成したエラーの総数についての情報、モジュールが読み込んでいるアセンブリ、および現在コンパイルされているファイルが表示されます。  
  
> [!NOTE]
>  `/verbose` オプションは Visual Studio の開発環境内からは利用できません。このオプションを利用できるのは、コマンド ラインからコンパイルするときだけです。  
  
## 使用例  
 `In.vb` をコンパイルし、詳細なステータス情報を表示する場合のコード例を次に示します。  
  
```  
vbc /verbose in.vb  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)