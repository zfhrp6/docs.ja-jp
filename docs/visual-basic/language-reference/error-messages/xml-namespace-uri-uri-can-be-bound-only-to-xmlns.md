---
title: "XML namespace URI &#39;http://www.w3.org/XML/1998/namespace&#39; can be bound only to &#39;xmlns&#39; | Microsoft Docs"
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
  - "bc31183"
  - "vbc31183"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31183"
ms.assetid: 0ab1dbce-8397-4959-b2cd-f58798b051a0
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML namespace URI &#39;http://www.w3.org/XML/1998/namespace&#39; can be bound only to &#39;xmlns&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

XML 名前空間宣言の中で URI http:\/\/www.w3.org\/XML\/1998\/namespace が使用されています。  この URI は予約済みの名前空間であり、XML 名前空間の宣言に組み込むことはできません。  
  
 **エラー ID:** BC31183  
  
### このエラーを解決するには  
  
-   XML 名前空間宣言を削除するか、URI http:\/\/www.w3.org\/XML\/1998\/namespace を有効な名前空間の URI で置き換えます。  
  
## 参照  
 [Imports Statement \(XML Namespace\)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)