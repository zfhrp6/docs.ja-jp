---
title: "/highentropyva (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "highentropyva compiler option (Visual Basic)"
  - "/highentropyva compiler option (Visual Basic)"
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /highentropyva (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

64 ビットの実行可能ファイルまたは [\/platform: anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) のコンパイラ オプションによって示される実行可能ファイルが高いエントロピの ASLR （Address Space Layout Randomization） \(ASLR\) をサポートするかどうかを示します。  
  
## 構文  
  
```  
/highentropyva[+ | -]  
```  
  
## 引数  
 `+` &#124; `-`  
 省略可能です。  オプションは `/highentropyva-`を指定すると、は既定で無効になっています。  オプションは `/highentropyva` か `/highentropyva+`を指定した場合です。  
  
## 解説  
 このオプションを指定すると、ウィンドウのカーネル互換性のあるバージョンのは、カーネルが ASLR の一部として、プロセスのアドレス空間レイアウトをランダム化すると、エントロピの昇格を使用できます。  カーネルがエントロピの昇格を使用すると、アドレスの最大数はスタックおよびヒープなどのメモリ領域に割り当てることができます。  したがって、特定のメモリ領域の場所を推測することは困難です。  
  
 オプションがオンの場合、これらのモジュールに 64 ビット プロセスとして実行している場合、実行可能な依存するモジュールとターゲットは 4 GB の大きなポインター値を \(GB\) 対応できる必要があります。  
  
 ASLR に関する詳細については、 " " を参照 [軽減のソフトウェアの脆弱性](http://go.microsoft.com/fwlink/?LinkId=226234)してください。  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)