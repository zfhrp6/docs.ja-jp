---
title: "&#39;&lt;methodname&gt;&#39; has multiple definitions with identical signatures | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30269"
  - "bc30269"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30269"
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# &#39;&lt;methodname&gt;&#39; has multiple definitions with identical signatures
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`Function` プロシージャ宣言または `Sub` プロシージャ宣言で、前の宣言と同じプロシージャ名と引数リストを使用しています。  元のプロシージャをオーバーロードしようとしたことが原因の 1 つとして考えられます。  オーバーロードされたプロシージャは、異なる引数リストを持つ必要があります。  
  
 **Error ID:** BC30269  
  
### このエラーを解決するには  
  
-   プロシージャ名か引数リストを変更するか、または重複している宣言を削除します。  
  
## 参照  
 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Considerations in Overloading Procedures](../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)