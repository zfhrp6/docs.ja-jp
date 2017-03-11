---
title: "/nowin32manifest (Visual Basic) | Microsoft Docs"
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
  - "/nowin32manifest compiler option [Visual Basic]"
  - "nowin32manifest compiler option [Visual Basic]"
  - "-nowin32manifest compiler option [Visual Basic]"
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# /nowin32manifest (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

コンパイラがアプリケーション マニフェストを実行可能ファイルに埋め込まないよう指定します。  
  
## 構文  
  
```  
/nowin32manifest  
```  
  
## 解説  
 このオプションを使用すると、アプリケーションは Windows Vista の仮想化に従います。ただし、Win32 リソース ファイルで、または後のビルド手順で、アプリケーション マニフェストを指定した場合を除きます。  仮想化の詳細については、「[Windows Vista の ClickOnce 配置](/visual-studio/deployment/clickonce-deployment-on-windows-vista)」を参照してください。  
  
 マニフェストの作成の詳細については、「[\/win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)」を参照してください。  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\[アプリケーション\] ページ \(プロジェクト デザイナー\) \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic)