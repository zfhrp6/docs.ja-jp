---
title: "How to: Make an Object Variable Not Refer to Any Instance (Visual Basic) | Microsoft Docs"
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
  - "Nothing keyword, variable assignment"
  - "object variables, null reference"
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[Nothing](../../../../visual-basic/language-reference/nothing.md) に設定して、オブジェクト インスタンスから、オブジェクト変数の関連付けを解除できます。  
  
### オブジェクト インスタンスからオブジェクト変数の関連付けを解除するには  
  
-   代入ステートメントで、変数を `Nothing` に設定します。  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## 信頼性の高いプログラミング  
 `Nothing` に設定されたオブジェクト変数のメンバーに、コードがアクセスしようとしている場合、<xref:System.NullReferenceException> が発生します。  オブジェクト変数を頻繁に `Nothing` に設定する場合、または変数を初期化しないことが可能である場合、`Try...Catch...Finally` ブロックにメンバー アクセスを入れることをお勧めします。  
  
## .NET Framework セキュリティ  
 重要情報が含まれているオブジェクトのオブジェクト変数を使用する場合、これらのオブジェクトをアクティブに処理していないときに、変数を `Nothing` に設定できます。  これにより、悪意のあるコードがデータにアクセスできる機会を減らすことができます。  
  
## 参照  
 <xref:System.NullReferenceException>   
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Assignment](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [Nothing](../../../../visual-basic/language-reference/nothing.md)   
 [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [例外のトラブルシューティング : System.NullReferenceException](../Topic/Troubleshooting%20Exceptions:%20System.NullReferenceException.md)