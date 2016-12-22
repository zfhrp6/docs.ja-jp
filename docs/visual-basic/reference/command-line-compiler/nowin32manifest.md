---
title: "/nowin32manifest (Visual Basic) | Microsoft Docs"
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
  - "/nowin32manifest compiler option [Visual Basic]"
  - "nowin32manifest compiler option [Visual Basic]"
  - "-nowin32manifest compiler option [Visual Basic]"
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /nowin32manifest (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

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
 [\[アプリケーション\] ページ \(プロジェクト デザイナー\) \(Visual Basic\)](../Topic/Application%20Page,%20Project%20Designer%20\(Visual%20Basic\).md)