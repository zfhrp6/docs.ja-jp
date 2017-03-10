---
title: "/nologo (Visual Basic) | Microsoft Docs"
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
  - "-nologo compiler option [Visual Basic]"
  - "banners, suppressing startup"
  - "nologo compiler option [Visual Basic]"
  - "/nologo compiler option [Visual Basic]"
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# /nologo (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

コンパイル時の著作権画面や情報メッセージの表示を中止します。  
  
## 構文  
  
```  
/nologo  
```  
  
## 解説  
 `/nologo` を指定すると、コンパイラは著作権画面を表示しません。  既定では、`/nologo` は無効です。  
  
> [!NOTE]
>  `/nologo` オプションは Visual Studio の開発環境内からは利用できません。このオプションを利用できるのは、コマンド ラインからコンパイルするときだけです。  
  
## 使用例  
 `T2.vb` を、著作権画面を表示しないように指定してコンパイルするコード例を次に示します。  
  
```  
vbc /nologo t2.vb  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)