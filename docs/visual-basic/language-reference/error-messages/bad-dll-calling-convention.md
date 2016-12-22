---
title: "Bad DLL calling convention | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrID49"
dev_langs: 
  - "VB"
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Bad DLL calling convention
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

ダイナミック リンク ライブラリ \(DLL: dynamic\-link library\) に渡される引数は、ルーチンが受け取る引数と一致している必要があります。  呼び出し規約は、引数の数、型、および順序に関係があります。  プログラムが、型または数の間違った引数を渡された DLL 内のルーチンを呼び出している可能性があります。  
  
### このエラーを解決するには  
  
1.  すべての引数の型が、呼び出しているルーチンの宣言で指定されている引数の型と一致していることを確認します。  
  
2.  呼び出しているルーチンの宣言で指定されている引数の数と同じ数の引数を渡していることを確認します。  
  
3.  DLL 内のルーチンが引数を値渡しで受け取る場合は、そのルーチンの宣言で引数に `ByVal` が指定されていることを確認します。  
  
## 参照  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)   
 [Call Statement](../../../visual-basic/language-reference/statements/call-statement.md)   
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)