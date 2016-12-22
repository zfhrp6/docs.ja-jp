---
title: "Variable &#39;&lt;variablename&gt;&#39; hides a variable in an enclosing block | Microsoft Docs"
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
  - "vbc30616"
  - "bc30616"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30616"
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Variable &#39;&lt;variablename&gt;&#39; hides a variable in an enclosing block
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

ブロック内の変数の名前が、別のローカル変数の名前と同じです。  
  
 **Error ID:** BC30616  
  
### このエラーを解決するには  
  
-   ブロック内の変数の名前を変更して、別のローカル変数の名前と重複しないようにします。  次に例を示します。  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   このエラーの一般的な原因は、イベント ハンドラー内で `Catch e As Exception` を使用することにあります。  その場合は、`Catch` ブロックの変数名を `e` ではなく `ex` とします。  
  
-   その他の一般的な原因としては、`Try` ブロック内で宣言されたローカル変数に個別の `Catch` ブロックでアクセスしようとしたことが考えられます。  これを修正するには、`Try...Catch...Finally` 構造体の外部で変数を宣言します。  
  
## 参照  
 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [変数宣言](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)