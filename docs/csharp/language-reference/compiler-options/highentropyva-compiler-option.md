---
title: "/highentropyva (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/highentropyva"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/highentropyva compiler option [C#]"
  - "-highentropyva compiler option [C#]"
  - "highentropyva compiler option [C#]"
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /highentropyva (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

**\/highentropyva** のコンパイラ オプションは、Windows のカーネルに起因しているのかを特定の実行可能ファイル サポートの高いエントロピ ASLR \(ASLR\) を使用します。  
  
## 構文  
  
```  
/highentropyva[+ | -]  
```  
  
## Arguments  
 `+` &#124; `-`  
 高いエントロピの仮想アドレス空間をサポートする [\/platform: anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) コンパイラ オプションによって示されるこのオプションは 64 ビットの実行可能ファイルまたは実行可能ファイルことを指定します。  このオプションは既定で無効になります。  このオプションを有効にするために **\/highentropyva\+** または **\/highentropyva** を使用します。  
  
## 解説  
 **\/highentropyva** オプションは、プロセスのアドレス空間レイアウトを ASLR 機能の一部としてそれぞれ時に Windows のカーネル互換バージョンがエントロピの詳細を使用できるようになります。  エントロピの詳細を使用して、アドレスの数がスタックとヒープなどのメモリ領域に割り当てることができることを意味します。  したがって、特定のメモリ領域の場所を推測することは困難です。  
  
 **\/highentropyva** のコンパイラ オプションを指定すると、64 ビット プロセスとして実行されている場合に、実行可能ファイルと、ターゲットに依存するモジュールは 4 GB のより大きなポインター値を \(GB\) 処理必要があります。  
  
 ASLR 機能に関する詳細については、参照します [軽減のソフトウェアの脆弱性](http://go.microsoft.com/fwlink/?LinkId=226234)。