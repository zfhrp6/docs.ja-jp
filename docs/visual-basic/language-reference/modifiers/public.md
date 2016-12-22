---
title: "Public (Visual Basic) | Microsoft Docs"
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
  - "vb.Public"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Public keyword"
  - "Public keyword, syntax"
  - "Public access modifier"
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Public (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

宣言された 1 つ以上のプログラミング要素に、アクセス制限がないことを指定します。  
  
## 解説  
 クラス ライブラリなど、1 つ以上のコンポーネントを発行する場合は、そのプログラミング要素へのアクセスを、自分のアセンブリとやり取りするすべてのコードに対して許可するのが普通です。  このような無制限のアクセス許可を与えるには、`Public` を使って要素を宣言します。  
  
 アクセスを制限する必要がないプログラミング要素に対しては、パブリック アクセスが通常のアクセス レベルになります。  特に宣言しなければ、インターフェイス、モジュール、クラス、または構造体の内部で宣言された要素のアクセス レベルは、既定で `Public` に設定されるので注意が必要です。  
  
## 規則  
  
-   **宣言コンテキスト。** `Public` は、モジュール レベル、インターフェイス レベル、または名前空間レベルでのみ使用できます。  つまり、`Public` 要素の宣言コンテキストは、ソース ファイル、名前空間、インターフェイス、モジュール、クラス、または構造体のいずれかである必要があり、プロシージャでは宣言できません。  
  
## \[動作\]  
  
-   **アクセス レベル。**モジュール、クラス、構造体にアクセスできるコードであれば、その `Public` 要素にアクセスできます。  
  
-   **既定のアクセス。**プロシージャ内のローカル変数のアクセス レベルは、既定で public になります。このような変数にはアクセス修飾子を指定できません。  
  
-   **アクセス修飾子。**アクセス レベルを指定するキーワードは、*アクセス修飾子*と呼ばれます。  アクセス修飾子の比較については、「[Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。  
  
 修飾子 `Public` は、次の構文で使用します。  
  
 [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Module ステートメント](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## 参照  
 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)   
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)   
 [Private](../../../visual-basic/language-reference/modifiers/private.md)   
 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)