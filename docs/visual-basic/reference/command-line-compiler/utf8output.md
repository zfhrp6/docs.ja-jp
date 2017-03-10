---
title: "/utf8output (Visual Basic) | Microsoft Docs"
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
  - "-utf8output compiler option [Visual Basic]"
  - "utf8output compiler option [Visual Basic]"
  - "/utf8output compiler option [Visual Basic]"
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# /utf8output (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

UTF\-8 エンコーディングを使用してコンパイラ出力を表示します。  
  
## 構文  
  
```  
/utf8output[+ | -]  
```  
  
## 引数  
 `+` &#124; `-`  
 省略可能です。  このオプションの既定値は `/utf8output-` で、コンパイラの出力では UTF\-8 エンコーディングは使用されません。  `/utf8output` の指定は、`/utf8output+` の指定と同じです。  
  
## 解説  
 いくつかの国際対応の設定では、コンパイラの出力をコンソールに正しく表示できません。  そのような場合は、`/utf8output` を使用してコンパイラの出力をファイルにリダイレクトできます。  
  
> [!NOTE]
>  `/utf8output` オプションは Visual Studio の開発環境内からは利用できません。このオプションを利用できるのは、コマンド ラインからコンパイルするときだけです。  
  
## 使用例  
 `In.vb` をコンパイルし、コンパイラの出力を UTF\-8 エンコードで表示する場合のコード例です。  
  
```  
vbc /utf8output in.vb  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)