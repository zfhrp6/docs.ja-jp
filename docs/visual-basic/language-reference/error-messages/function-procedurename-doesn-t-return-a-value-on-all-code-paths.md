---
title: "Function &#39;&lt;procedurename&gt;&#39; doesn&#39;t return a value on all code paths | Microsoft Docs"
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
  - "bc42105"
  - "vbc42105"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42105"
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Function &#39;&lt;procedurename&gt;&#39; doesn&#39;t return a value on all code paths
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

関数 '\<procedurename\>' すべてのコード パス上では値を返しません。'Return' ステートメントが不足していないかどうかを確認してください。  
  
 `Function` プロシージャには、値を返さない可能性があるコードへのパスが少なくとも 1 つあります。  
  
 `Function` プロシージャからは、以下の方法のいずれかで値を返すことができます。  
  
-   値を [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) に含めます。  
  
-   値を `Function` プロシージャ名に代入し、`Exit Function` ステートメントを実行します。  
  
-   値を `Function` プロシージャ名に代入し、`End Function` ステートメントを実行します。  
  
 値をプロシージャ名に代入しないで、制御を `Exit Function` または `End Function` に渡した場合、プロシージャは戻り値のデータ型の既定値を返します。  詳細については、「[Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)」の「動作」を参照してください。  
  
 既定では、このメッセージは警告です。  警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、[Visual Basic での警告の構成](/visual-studio/ide/configuring-warnings-in-visual-basic) を参照してください。  
  
 **Error ID:** BC42105  
  
### このエラーを解決するには  
  
-   制御フローのロジックを調べて、ステートメントが値を返す前に値が割り当てられていることをすべて確認してください。  
  
     常に `Return` ステートメントを使うと、値を返すプロシージャが確実に値を返すようにするのが簡単になります。  この場合は、`End Function` の直前のステートメントを `Return` ステートメントにする必要があります。  
  
## 参照  
 [Function プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [\[コンパイル\] ページ、プロジェクト デザイナー \(Visual Basic\)](../Topic/Compile%20Page,%20Project%20Designer%20\(Visual%20Basic\).md)