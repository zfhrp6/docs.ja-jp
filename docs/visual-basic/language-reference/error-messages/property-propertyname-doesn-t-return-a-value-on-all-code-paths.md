---
title: "Property &#39;&lt;propertyname&gt;&#39; doesn&#39;t return a value on all code paths | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc42107"
  - "vbc42107"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42107"
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# Property &#39;&lt;propertyname&gt;&#39; doesn&#39;t return a value on all code paths
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プロパティ '\<propertyname\>' は、すべてのコードのパスでは値を返しません。結果が使用されるときに、null 参照の例外が実行時に発生する可能性があります。  
  
 プロパティの `Get` プロシージャに、値を返さないコードへのパスが 1 つ以上含まれている可能性があります。  
  
 プロパティの `Get` プロシージャから値を返すには、次のいずれかの方法を使います。  
  
-   プロパティ名に値を割り当ててから、`Exit Property` ステートメントを実行します。  
  
-   プロパティ名に値を割り当ててから、`End Get` ステートメントを実行します。  
  
-   値を [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) に含めます。  
  
 制御が `Exit Property` または `End Get` に渡されたとき、プロパティ名に値が割り当てられていない場合、`Get` プロシージャはプロパティのデータ型の既定値を返します。  詳細については、「[Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)」の「動作」を参照してください。  
  
 既定では、このメッセージは警告です。  警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、[Visual Basic での警告の構成](/visual-studio/ide/configuring-warnings-in-visual-basic) を参照してください。  
  
 **Error ID:** BC42107  
  
### このエラーを解決するには  
  
-   制御フローのロジックを調べて、ステートメントが値を返す前に値が割り当てられていることをすべて確認してください。  
  
     常に `Return` ステートメントを使うと、値を返すプロシージャが確実に値を返すようにするのが簡単になります。  この場合は、`End Get` の直前のステートメントを `Return` ステートメントにする必要があります。  
  
## 参照  
 [Property プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md)