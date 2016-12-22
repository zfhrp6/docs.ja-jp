---
title: "Call Statement (Visual Basic) | Microsoft Docs"
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
  - "vb.Call"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "procedures, Call statement"
  - "Call statement"
  - "procedures, calling"
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Call Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`Function` 、`Sub`、またはダイナミック リンク ライブラリ \(DLL\) プロシージャに制御を渡すフロー制御ステートメントです。  
  
## 構文  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## 指定項目  
 `procedureName`  
 必ず指定します。  呼び出すプロシージャの名前を指定します。  
  
 `argumentList`  
 省略可能です。  プロシージャを呼び出すときにプロシージャに渡す引数を表す、変数または式のリストを指定します。  複数の引数を指定するときは、コンマ \(,\) で区切ります。  `argumentList` を指定する場合は、かっこで囲む必要があります。  
  
## 解説  
 プロシージャをダイヤルすると `Call` のキーワードを使用できます。  ほとんどのプロシージャ呼び出しでは、このキーワードを使用する必要はありません。  
  
 呼び出された式が ID で始まっていない場合に `Call` のキーワードを使用します。  他の `Call` のキーワードの使用は推奨されていません。  
  
 プロシージャが値を返す場合は、`Call` ステートメントを使用すると戻り値が破棄されます。  
  
## 使用例  
 次のコードは `Call` のキーワードがプロシージャをダイヤルする必要とする 2 例に示します。  どちらの例では、という式は ID から開始されません。  
  
 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## 参照  
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)