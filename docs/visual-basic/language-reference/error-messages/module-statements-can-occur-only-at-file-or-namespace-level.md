---
title: "&#39;Module&#39; statements can occur only at file or namespace level | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30617"
  - "vbc30617"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30617"
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# &#39;Module&#39; statements can occur only at file or namespace level
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`Module` ステートメントは、ソース ファイルの先頭に記述する必要があります。つまり、`Option` ステートメント、`Imports` ステートメント、グローバル属性、および名前空間宣言の直後に、その他のすべての宣言より先に記述する必要があります。  
  
 **Error ID:** BC30617  
  
### このエラーを解決するには  
  
-   `Module` ステートメントを名前空間宣言またはソース ファイルの先頭に移動します。  
  
## 参照  
 [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)