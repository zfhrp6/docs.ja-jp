---
title: "Overridable (Visual Basic) | Microsoft Docs"
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
  - "Overridable"
  - "vb.Overridable"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "elements, concrete"
  - "properties [Visual Basic], redefining"
  - "overriding, Overridable keyword"
  - "elements, virtual"
  - "virtual elements"
  - "procedures, overriding"
  - "concrete elements"
  - "procedures, redefining"
  - "Overridable keyword"
  - "properties [Visual Basic], overriding"
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Overridable (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

プロパティまたはプロシージャを、派生クラスで同じ名前のプロパティまたはプロシージャでオーバーライドできることを指定します。  
  
## 解説  
 `Overridable` の修飾子は派生クラスでオーバーライドされるクラスのプロパティまたはメソッドができます。  [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) の修飾子はプロパティまたはメソッドが派生クラスでオーバーライドされることを防ぎます。  詳細については、「[Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)」を参照してください。  
  
 `Overridable` または `NotOverridable` の修飾子が指定されていない場合は既定の設定がプロパティまたはメソッドが基本クラスのプロパティやメソッドをオーバーライドするかどうかによって異なります。  プロパティまたはメソッドが基本クラスのプロパティやメソッドをオーバーライドすると既定の設定はです `Overridable`; それ以外の場合は `NotOverridable` です。  
  
 シャドウまたはオーバーライドを行うと継承された要素を再定義できますが、この 2 つの方法には重大な違いがあります。  詳細については、「[Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)」を参照してください。  
  
 オーバーライド可能な要素は、*仮想*要素と呼ばれることもあります。  オーバーライド可能だが、オーバーライドする必要はないという場合は、*具象*要素とも呼ばれます。  
  
 `Overridable` は、プロパティまたはプロシージャの宣言ステートメント内でだけ使用できます。  
  
## 組み合わせて修飾子  
 `Private` メソッドに `Overridable` または `NotOverridable` を指定できません。  
  
 同じ変数宣言で `Overridable` を、`MustOverride`、`NotOverridable`、または `Shared` と同時に指定することはできません。  
  
 オーバーライドする要素は暗黙でオーバーライド可能なので、`Overridable` を `Overrides` と組み合わせることはできません。  
  
## 使用方法  
 修飾子 `Overridable` は、次の構文で使用します。  
  
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## 参照  
 [Modifiers](../../../visual-basic/language-reference/modifiers/index.md)   
 [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)   
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)   
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)   
 [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)   
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)   
 [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)