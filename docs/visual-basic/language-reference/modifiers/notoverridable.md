---
title: "NotOverridable (Visual Basic) | Microsoft Docs"
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
  - "vb.NotOverridable"
  - "NotOverridable"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "sealed methods"
  - "NotOverridable keyword"
  - "properties [Visual Basic], redefining"
  - "elements, sealed"
  - "sealed elements"
  - "procedures, overriding"
  - "procedures, redefining"
  - "overriding"
  - "methods [Visual Basic], sealed"
  - "properties [Visual Basic], overriding"
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# NotOverridable (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

派生クラスでオーバーライドできないプロパティまたはプロシージャを示すキーワードです。  
  
## 解説  
 `NotOverridable` の修飾子はプロパティまたはメソッドが派生クラスでオーバーライドされることを防ぎます。  [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) の修飾子は派生クラスでオーバーライドされるクラスのプロパティまたはメソッドができます。  詳細については、「[Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)」を参照してください。  
  
 `Overridable` または `NotOverridable` の修飾子が指定されていない場合は既定の設定がプロパティまたはメソッドが基本クラスのプロパティやメソッドをオーバーライドするかどうかによって異なります。  プロパティまたはメソッドが基本クラスのプロパティやメソッドをオーバーライドすると既定の設定はです `Overridable`; それ以外の場合は `NotOverridable` です。  
  
 オーバーライドできない要素は、*シール*要素と呼ばれることもあります。  
  
 `NotOverridable` は、プロパティまたはプロシージャの宣言ステートメント内でだけ使用できます。  `NotOverridable` を指定できるのは、別のプロパティまたはプロシージャをオーバーライドしているプロパティやプロシージャだけです。つまり、`Overrides` と組み合わせた場合のみ使用できます。  
  
## 組み合わせて修飾子  
 `Private` メソッドに `Overridable` または `NotOverridable` を指定できません。  
  
 同じ変数宣言で `NotOverridable` を、`MustOverride`、`Overridable`、または `Shared` と同時に指定することはできません。  
  
## 使用方法  
 修飾子 `NotOverridable` は、次の構文で使用します。  
  
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## 参照  
 [Modifiers](../../../visual-basic/language-reference/modifiers/index.md)   
 [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)   
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)   
 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)   
 [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)   
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)   
 [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)