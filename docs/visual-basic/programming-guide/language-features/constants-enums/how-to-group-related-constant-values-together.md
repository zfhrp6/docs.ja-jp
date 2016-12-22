---
title: "How to: Group Related Constant Values Together (Visual Basic) | Microsoft Docs"
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
  - "enumerations [Visual Basic], constants"
  - "constants, grouping together"
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Group Related Constant Values Together (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

関連する定数値をまとめてグループ化するには、列挙型が最適です。  列挙型を作成するには、クラスまたはモジュールの宣言セクションで `Enum` ステートメントを使用します。  詳細については、「[How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)」を参照してください。  
  
### 関連する定数値をグループ化するには  
  
1.  コードのアクセス レベル、`Enum` キーワード、および有効な名前を含む宣言を作成します。  この例では、`Private` 列挙型、`temperatureValues` を作成します。  
  
     [!code-vb[VbEnumsTask#21](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_1.vb)]  
  
2.  列挙型で定数を定義します。  この例では `Public` 列挙型 `temperatureValues` を作成し、値を割り当てます。  
  
     [!code-vb[VbEnumsTask#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_2.vb)]  
  
## 参照  
 [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [How to: Refer to an Enumeration Member](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [When to Use an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)   
 [Constants Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)   
 [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)