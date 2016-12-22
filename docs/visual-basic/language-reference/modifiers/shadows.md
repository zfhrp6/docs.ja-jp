---
title: "Shadows (Visual Basic) | Microsoft Docs"
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
  - "vb.Shadows"
  - "shadows"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "shadowing"
  - "duplicate names"
  - "scope, shadowing"
  - "Shadows keyword"
  - "names, shadowing"
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Shadows (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

宣言されたプログラミング要素が、基本クラスにある、同じ名前を持つ要素またはオーバーロードされる要素を宣言し直すことを示します。  
  
## 解説  
 シャドウ \(*名前による隠ぺい*とも呼ばれます\) の主な目的は、クラス メンバーの定義を保持することにあります。  基本クラスは、既に定義されている要素と同じ名前の要素を作成するように変更される可能性もあります。  このような場合、`Shadows` 修飾子を指定してあると、派生クラスを通じた参照は新しい基本クラスの要素に解決されず、派生クラスで定義したメンバーに解決されます。  
  
 シャドウとオーバーライドは、どちらも継承された要素を再定義しますが、そのアプローチは大きく異なります。  詳細については、「[Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)」を参照してください。  
  
## 規則  
  
-   **宣言コンテキスト。** `Shadows` は、クラス レベルでのみ使用できます。  つまり、`Shadows` 要素の宣言コンテキストはクラスであることが必要で、ソース ファイル、名前空間、インターフェイス、モジュール、構造体、またはプロシージャでは宣言できません。  
  
     1 つの宣言ステートメントに宣言できるシャドウ要素は 1 つだけです。  
  
-   **結合された修飾子。**同じ変数宣言で `Shadows` を、`Overloads`、`Overrides`、または `Static` と同時に指定することはできません。  
  
-   **要素の型。**宣言された要素は、他の任意の種類の要素でシャドウできます。  プロパティまたはプロシージャを別のプロパティまたはプロシージャでシャドウする場合、パラメーターおよび戻り値の型は、基本クラスのプロパティまたはプロシージャのパラメーターおよび戻り値の型と一致しなくてもかまいません。  
  
-   **アクセス。**通常、シャドウされた基本クラスの要素は、その要素をシャドウする派生クラスからは使用できません。  ただし、次の点に注意してください。  
  
    -   シャドウする要素が、その要素を参照するコードからアクセス不可能である場合、参照はシャドウされる要素に解決されます。  たとえば、`Private` 要素が基本クラスの要素をシャドウした場合、その `Private` 要素へのアクセス許可を持たないコードは、基本クラスの要素へ代わりにアクセスします。  
  
    -   要素をシャドウした場合でも、基本クラスの型で宣言されたオブジェクトを使用すると、シャドウされた要素にアクセスできます。  `MyBase` を使用してアクセスすることもできます。  
  
 修飾子 `Shadows` は、次の構文で使用します。  
  
 [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## 参照  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)   
 [Static](../../../visual-basic/language-reference/modifiers/static.md)   
 [Private](../../../visual-basic/language-reference/modifiers/private.md)   
 [Me, My, MyBase, and MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)   
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)   
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)   
 [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)   
 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)   
 [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)