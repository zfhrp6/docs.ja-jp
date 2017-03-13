---
title: "Stop Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Stop"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "breakpoints, Stop statements"
  - "Stop statements, syntax"
  - "Stop statements"
  - "execution, suspending"
  - "processing, interrupting"
  - "processes, interrupting"
  - "execution, stopping"
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Stop Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

実行を中断するステートメントです。  
  
## 構文  
  
```  
Stop  
```  
  
## 解説  
 `Stop` ステートメントは、プロシージャ内の任意の場所に置いて、実行を中断できます。  `Stop` ステートメントは、プログラム コードのブレークポイントと同じ働きをします。  
  
 `Stop` ステートメントはプログラムの実行を中断しますが、`End` ステートメントと異なり、コンパイル済みの実行可能ファイル \(.EXE\) の内部でない限り、ファイルを閉じたり、変数をクリアすることはありません。  
  
> [!NOTE]
>  統合開発環境 \(IDE: Integrated Development Environment\) 外で実行されるコード内に `Stop` ステートメントが含まれている場合は、そこまで進むとデバッガーが呼び出されます。  そのコードがデバッグ モードとリテール モードのどちらでコンパイルされたかは関係ありません。  
  
## 使用例  
 `Stop` ステートメントを使って、`For...Next` ループを繰り返すごとに中断するコード例は、次のとおりです。  
  
 [!code-vb[VbVbalrStatements#56](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/stop-statement_1.vb)]  
  
## 参照  
 [End Statement](../../../visual-basic/language-reference/statements/end-statement.md)