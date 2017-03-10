---
title: "Overrides (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "Overrides"
  - "vb.Overrides"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "properties [Visual Basic], redefining"
  - "procedures, overriding"
  - "procedures, redefining"
  - "overriding"
  - "Overrides keyword"
  - "overriding, Overrides keyword"
  - "properties [Visual Basic], overriding"
ms.assetid: 9f5e6144-ce10-465e-842b-1a8f8760af90
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Overrides (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プロパティまたはプロシージャが基本クラスから継承された同じ名前のプロパティまたはプロシージャをオーバーライドすることを示します。  
  
## 解説  
  
## 規則  
  
-   **宣言コンテキスト。** `Overrides` は、プロパティまたはプロシージャの宣言ステートメントでのみ使用できます。  
  
-   **結合された修飾子。** 同じ宣言内で `Overrides` を `Shadows` または `Shared` と共に指定することはできません。  オーバーライドする要素は暗黙的にオーバーライド可能であるため、`Overridable` と `Overrides` を結合することはできません。  
  
-   **シグネチャの一致。** この宣言のシグネチャは、オーバーライドされるプロパティまたはプロシージャの*シグネチャ*と完全に一致する必要があります。  つまり、パラメーター リストには、同じ数のパラメーターを、同じ順序、同じデータ型で指定する必要があります。  
  
     オーバーライドする宣言は、シグネチャに加え、次の点でも完全に一致している必要があります。  
  
    -   アクセス レベル  
  
    -   戻り値の型 \(戻り値がある場合\)  
  
-   **ジェネリック シグネチャ。** ジェネリック プロシージャでは、シグネチャに型パラメーターの数が含まれます。  したがって、オーバーライドする宣言は、その点でも基底クラスのバージョンに一致している必要があります。  
  
-   **その他の一致。** この宣言は、基底クラスのバージョンのシグネチャに一致していることに加え、次の点でも基底クラスと一致している必要があります。  
  
    -   アクセス レベル修飾子 \([Public](../../../visual-basic/language-reference/modifiers/public.md) など\)  
  
    -   各パラメーターの渡し方 \([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) または [ByRef](../../../visual-basic/language-reference/modifiers/byref.md)\)  
  
    -   ジェネリック プロシージャの型パラメーターごとの制約リスト  
  
-   **シャドウとオーバーライド。** シャドウとオーバーライドは、どちらも継承された要素を再定義しますが、その方法は大きく異なります。  詳細については、「[Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)」を参照してください。  
  
 `Overrides` を使用する場合は、ライブラリ API と C\# が連携しやすくなるように、コンパイラが暗黙的に `Overloads` を追加します。  
  
 `Overrides` 修飾子は、次のコンテキストで使用できます。  
  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## 参照  
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)   
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)   
 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)   
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)   
 [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Type List](../../../visual-basic/language-reference/statements/type-list.md)