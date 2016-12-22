---
title: "XML comment exception must have a &#39;cref&#39; attribute | Microsoft Docs"
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
  - "bc42319"
  - "vbc42319"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42319"
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML comment exception must have a &#39;cref&#39; attribute
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

\<exception\> タグを使用すると、メソッドによってスローされる可能性のある例外をドキュメントに出力できます。  必須の `cref` 属性には、メンバーの名前を指定します。この名前はドキュメント生成機能によってチェックされます。  メンバーが存在する場合は、メンバーの名前がドキュメント ファイル内で標準の要素名に変換されます。  
  
 **Error ID:** BC42319  
  
### このエラーを解決するには  
  
-   `cref` 属性を、次のように例外に追加します。  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## 参照  
 [\<exception\>](../../../visual-basic/language-reference/xmldoc/exception.md)   
 [How to: Create XML Documentation](../Topic/How%20to:%20Create%20XML%20Documentation%20in%20Visual%20Basic.md)   
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)