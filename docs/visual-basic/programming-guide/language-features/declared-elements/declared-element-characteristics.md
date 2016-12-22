---
title: "Declared Element Characteristics (Visual Basic) | Microsoft Docs"
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
  - "declared elements, lifetime"
  - "access levels, declared elements"
  - "declared elements, scope"
  - "visibility, declared elements"
  - "elements, programming"
  - "scope, declared elements"
  - "lifetime, declared elements"
  - "declared elements, access level"
  - "data types [Visual Basic], declared elements"
  - "declared elements, visibility"
ms.assetid: 1bc40fb8-b67c-4428-90a4-76b630ae2583
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Declared Element Characteristics (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

宣言された要素の*特性*は、コードとその要素とのやり取りに影響します。  宣言された各要素には、次の特性の 1 つ以上が関連付けられています。  
  
-   *データ型* \- 要素が保持できる値およびその格納方法です。  詳細については、「[Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)」を参照してください。  
  
-   *有効期間* \- 実行時間のうち、その要素を使用できる期間です。  詳細については、「[Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)」を参照してください。  
  
-   *スコープ* \- 名前に修飾子を付けずに要素を参照できる全コードの範囲です。  詳細については、「[How to: Control the Scope of a Variable](../Topic/How%20to:%20Control%20the%20Scope%20of%20a%20Variable%20\(Visual%20Basic\).md)」を参照してください。  
  
-   *アクセス レベル* \- コードがこの要素を利用するためのアクセス許可です。  詳細については、「[How to: Control the Availability of a Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md)」を参照してください。  
  
## 要素の特性  
 宣言された要素、およびそれぞれの要素に適用される特性を次の表に示します。  
  
|要素|\[データ型\]|有効期間|スコープ <sup>1</sup>|アクセス レベル|  
|--------|--------------|----------|-----------------------|--------------|  
|変数|○|○|○|○|  
|定数|○|Ｘ|○|○|  
|列挙型|○|Ｘ|○|○|  
|Structure|Ｘ|Ｘ|○|○|  
|プロパティ|○|○|○|○|  
|メソッド|Ｘ|○|○|○|  
|プロシージャ \(`Sub` または `Function`\)|Ｘ|○|○|○|  
|プロシージャ パラメーター|○|○|○|Ｘ|  
|関数の戻り値|○|○|○|Ｘ|  
|\[演算子\]|○|Ｘ|○|○|  
|Interface|Ｘ|Ｘ|○|○|  
|Class|Ｘ|Ｘ|○|○|  
|Event|Ｘ|Ｘ|○|○|  
|Delegate|Ｘ|Ｘ|○|○|  
  
 <sup>1</sup> スコープは*参照範囲*と呼ばれる場合もあります。  
  
## 参照  
 [Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)   
 [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)