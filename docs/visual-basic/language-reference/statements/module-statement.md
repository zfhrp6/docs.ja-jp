---
title: "Module Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "Module"
  - "vb.Module"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "modules, classes"
  - "modules"
  - "Module statement"
  - "modules, declaring"
  - "standard modules"
  - "classes [Visual Basic], vs. modules"
  - "declarations, modules"
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 24
---
# Module Statement
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

モジュールの名前を宣言し、モジュールを構成する変数、プロパティ、イベント、およびプロシージャの定義を提供します。  
  
## 構文  
  
```  
[ <attributelist> ] [ accessmodifier ]  Module name  
    [ statements ]  
End Module  
```  
  
## 指定項目  
 `attributelist`  
 省略可能です。  「[Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md)」を参照してください。  
  
 `accessmodifier`  
 省略可能です。  次のいずれかになります。  
  
-   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
 「[Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。  
  
 `name`  
 必ず指定します。  このモジュールの名前です。  「[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。  
  
 `statements`  
 省略可能です。  モジュールの変数、プロパティ、イベント、プロシージャ、および入れ子にされた型を定義するステートメントを指定します。  
  
 `End Module`  
 `Module` 定義を終了します。  
  
## 解説  
 `Module` ステートメントは、名前空間全体で使用可能な参照型を定義します。  *モジュール* \(*標準モジュール*とも呼ばれる\) は、クラスと似ていますが、重要な違いがいくつかあります。  モジュールのインスタンスは厳密に 1 つだけであり、作成する必要や変数に代入する必要はありません。  モジュールは、継承をサポートすることもインターフェイスを実装することもありません。  モジュールは、クラスや構造体が型であるという意味での*型*ではないことに注意してください。モジュールのデータ型を持つプログラミング要素を宣言することはできません。  
  
 `Module` は、名前空間レベルでのみ使用できます。  つまり、モジュールの*宣言コンテキスト*は、ソース ファイルまたは名前空間のどちらかである必要があり、クラス、構造体、モジュール、インターフェイス、プロシージャ、およびブロックでは宣言できません。  モジュールは、別のモジュールまたは型に入れ子にできません。  詳細については、「[Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 モジュールの有効期間は、プログラムと同じです。  すべてのメンバーは `Shared` であるため、メンバーの有効期間もプログラムと同じです。  
  
 既定で、モジュールのアクセス レベルは [Friend](../../../visual-basic/language-reference/modifiers/friend.md) です。  アクセス修飾子を使用してこれらのアクセス レベルを調整できます。  詳細については、「[Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。  
  
 モジュールのすべてのメンバーは、暗黙的に `Shared` になります。  
  
## クラスとモジュール  
 これらの要素はよく似ていますが、重要な相違点がいくつかあります。  
  
-   **用語。**以前のバージョンの Visual Basic には、*クラス モジュール* \(.cls ファイル\) と*標準モジュール* \(.bas ファイル\) という 2 種類のモジュールがありました。  現在のバージョンでは、これらをそれぞれ*クラス*と*モジュール*と呼びます。  
  
-   **共有メンバー。**クラスのメンバーを共有メンバーにするかインスタンス メンバーにするかを制御できます。  
  
-   **オブジェクト指向。**クラスはオブジェクト指向ですが、モジュールはオブジェクト指向ではありません。  したがって、クラスだけがオブジェクトとしてインスタンス化できます。  詳細については、「[Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)」を参照してください。  
  
## 規則  
  
-   **修飾子。**すべてのモジュール メンバーは、暗黙的に [Shared](../../../visual-basic/language-reference/modifiers/shared.md) になります。  メンバーを宣言するときに `Shared` キーワードは使用できません。また、メンバーの共有の状態は変更できません。  
  
-   **継承。**モジュールは、<xref:System.Object> 以外の型を継承できません。すべてのモジュールが、この型を継承します。  特に、モジュールは別のモジュールを継承できません。  
  
     たとえ <xref:System.Object> を指定するためであっても、[Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md) をモジュールの定義で使用することはできません。  
  
-   **既定のプロパティ。**既定のプロパティをモジュール内に定義することはできません。  詳細については、「[Default](../../../visual-basic/language-reference/modifiers/default.md)」を参照してください。  
  
## \[動作\]  
  
-   **アクセス レベル。**モジュールの内部では、各メンバーを独自のアクセス レベルで宣言できます。  モジュール メンバーのアクセス レベルは、既定で [Public](../../../visual-basic/language-reference/modifiers/public.md) になりますが、変数と定数だけは [Private](../../../visual-basic/language-reference/modifiers/private.md) が既定のアクセス レベルです。  モジュールのアクセス レベルがメンバーのレベルより厳しい場合、指定したモジュール アクセス レベルが優先されます。  
  
-   **スコープ。**モジュールのスコープは、名前空間全体です。  
  
     モジュール メンバーのスコープは、モジュール全体です。  すべてのメンバーに*型の上位変換*が行われ、メンバーのスコープがモジュールのある名前空間に上位変換されることに注意してください。  詳細については、「[Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)」を参照してください。  
  
-   **修飾。**1 つのプロジェクトが複数のモジュールを持つことができます。また、名前の同じメンバーを複数のモジュールに宣言できます。  ただし、モジュールの外部にあるメンバーを参照する場合は、適切なモジュール名を使ってメンバーへの参照を修飾する必要があります。  詳細については、「[References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)」を参照してください。  
  
## 使用例  
 [!code-vb[VbVbalrStatements#69](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/module-statement_1.vb)]  
  
## 参照  
 [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)