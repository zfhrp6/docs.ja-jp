---
title: "Derived Math Functions (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "arithmetic operations, derived math functions"
  - "cosecant function"
  - "arcsecant function"
  - "arccotangent function"
  - "functions [Visual Basic], derived math functions"
  - "inverse functions"
  - "math functions, derived"
  - "derived math functions"
  - "cotangent function"
  - "angles"
  - "secant function"
  - "trigonometric functions"
  - "logarithms"
  - "arccosecant function"
  - "hyperbolic functions"
  - "arcsine function"
  - "degrees"
  - "arccosine function"
ms.assetid: 63e449d8-9444-44fb-8db1-6d9cf346e2aa
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Derived Math Functions (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

次の表に、Visual Basic に組み込まれていない数値演算関数の導出式を示します。これらは、<xref:System.Math?displayProperty=fullName> オブジェクトの組み込みの数値演算関数から導くことができます。  ファイルまたはプロジェクトに `Imports System.Math` を追加すると、組み込みの数値演算関数にアクセスできます。  
  
|Function|組み込み関数を使った導出式|  
|--------------|-------------------|  
|セカント \(Sec\(x\)\)|1 \/ Cos\(x\)|  
|コセカント \(Csc\(x\)\)|1 \/ Sin\(x\)|  
|コタンジェント \(Ctan\(x\)\)|1 \/ Tan\(x\)|  
|アークサイン \(Asin\(x\)\)|Atan\(x \/ Sqrt\(\-x \* x \+ 1\)\)|  
|アークコサイン \(Acos\(x\)\)|Atan\(\-x \/ Sqrt\(\-x \* x \+ 1\)\) \+ 2 \* Atan\(1\)|  
|アークセカント \(Asec\(x\)\)|2 \* Atan\(1\) – Atan\(Sign\(x\) \/ Sqrt\(x \* x – 1\)\)|  
|アークコセカント \(Acsc\(x\)\)|Atan\(Sign\(x\) \/ Sqrt\(x \* x – 1\)\)|  
|アークコタンジェント \(Acot\(x\)\)|2 \* Atan\(1\) \- Atan\(x\)|  
|ハイパーボリック サイン \(Sinh\(x\)\)|\(Exp\(x\) – Exp\(\-x\)\) \/ 2|  
|ハイパーボリック コサイン \(Cosh\(x\)\)|\(Exp\(x\) \+ Exp\(\-x\)\) \/ 2|  
|ハイパーボリック タンジェント \(Tanh\(x\)\)|\(Exp\(x\) – Exp\(\-x\)\) \/ \(Exp\(x\) \+ Exp\(\-x\)\)|  
|ハイパーボリック セカント \(Sech\(x\)\)|2 \/ \(Exp\(x\) \+ Exp\(\-x\)\)|  
|ハイパーボリック コセカント \(Csch\(x\)\)|2 \/ \(Exp\(x\) – Exp\(\-x\)\)|  
|ハイパーボリック コタンジェント \(Coth\(x\)\)|\(Exp\(x\) \+ Exp\(\-x\)\) \/ \(Exp\(x\) – Exp\(\-x\)\)|  
|ハイパーボリック アークサイン \(Asinh\(x\)\)|Log\(x \+ Sqrt\(x \* x \+ 1\)\)|  
|ハイパーボリック アークコサイン \(Acosh\(x\)\)|Log\(x \+ Sqrt\(x \* x – 1\)\)|  
|ハイパーボリック アークタンジェント \(Atanh\(x\)\)|Log\(\(1 \+ x\) \/ \(1 – x\)\) \/ 2|  
|ハイパーボリック アークセカント \(AsecH\(x\)\)|Log\(\(Sqrt\(\-x \* x \+ 1\) \+ 1\) \/ x\)|  
|ハイパーボリック アークコセカント \(Acsch\(x\)\)|Log\(\(Sign\(x\) \* Sqrt\(x \* x \+ 1\) \+ 1\) \/ x\)|  
|ハイパーボリック アークコタンジェント \(Acoth\(x\)\)|Log\(\(x \+ 1\) \/ \(x – 1\)\) \/ 2|  
  
## 参照  
 [数値演算関数](../../../visual-basic/language-reference/functions/math-functions.md)