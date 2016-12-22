---
title: "MustOverride (Visual Basic) | Microsoft Docs"
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
  - "vb.MustOverride"
  - "MustOverride"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "virtual elements, pure"
  - "elements, pure virtual"
  - "properties [Visual Basic], redefining"
  - "procedures, overriding"
  - "overriding, MustOverride keyword"
  - "procedures, redefining"
  - "pure virtual elements"
  - "MustOverride keyword"
  - "properties [Visual Basic], overriding"
ms.assetid: 6e9d9ad6-bb64-433f-b32b-3ef84293bf96
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# MustOverride (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

このクラスで実装されておらず、派生クラスでオーバーライドしないと使用できないプロパティやプロシージャであることを示します。  
  
## 解説  
 `MustOverride` は、プロパティまたはプロシージャの宣言ステートメント内でだけ使用できます。  `MustOverride` が指定されているプロパティまたはプロシージャは、クラスのメンバーであることが必要です。また、そのクラスには [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md) が指定されている必要があります。  
  
## 規則  
  
-   **不完全な宣言。** `MustOverride` を指定したプロパティまたはプロシージャには、コードを 1 行も追加しません。`End Function`、`End Property`、または `End Sub` のステートメントも追加しないでください。  
  
-   **結合された修飾子。**同じ変数宣言で `MustOverride` を、`NotOverridable`、`Overridable`、または `Shared` と同時に指定することはできません。  
  
-   **シャドウとオーバーライド。**シャドウとオーバーライドは、どちらも継承された要素を再定義しますが、そのアプローチは大きく異なります。  詳細については、「[Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)」を参照してください。  
  
-   **別の呼び名**オーバーライドしないと使用できない要素を、*純粋仮想*要素とも呼びます。  
  
 修飾子 `MustOverride` は、次の構文で使用します。  
  
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## 参照  
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)   
 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)   
 [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)   
 [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)   
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)   
 [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)