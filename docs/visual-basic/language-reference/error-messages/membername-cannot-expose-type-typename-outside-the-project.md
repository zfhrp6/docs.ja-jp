---
title: "&#39;&lt;membername&gt;&#39; cannot expose type &#39;&lt;typename&gt;&#39; outside the project through &lt;containertype&gt; &#39;&lt;containertypename&gt;&#39; | Microsoft Docs"
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
  - "bc30909"
  - "vbc30909"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30909"
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;membername&gt;&#39; cannot expose type &#39;&lt;typename&gt;&#39; outside the project through &lt;containertype&gt; &#39;&lt;containertypename&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

変数、プロシージャ パラメーター、または関数の戻り値がコンテナー外部に公開されていますが、これらの要素はコンテナー外部に公開してはならない型として宣言されています。  
  
 次のスケルトン コードは、このエラーが発生する状況の例を示しています。  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 型を `Protected`、`Friend`、`Protected Friend`、または `Private` として宣言したときは、その宣言コンテキストの外側でのアクセスを制限することを意図しています。  このような型を、それよりもアクセス レベルの緩い変数のデータ型として使用することは、この目的に反します。  上記のスケルトン コードでは、`exposedVar` を `Public` として宣言しており、`privateClass` をコンテキスト外のコードに公開しようとしています。  
  
 **Error ID:** BC30909  
  
### このエラーを解決するには  
  
-   変数、プロシージャ パラメーター、または関数の戻り値のアクセス レベルを変更して、少なくとも、そのデータ型のアクセス レベルと同じ厳しさにします。  
  
## 参照  
 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)