---
title: "Private (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Private"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Private keyword"
  - "Private keyword, syntax"
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# Private (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

1 つ以上のプログラミング要素が宣言のコンテキスト内 \(内包型など\) からのみアクセスできることを示します。  
  
## 解説  
 プログラミング要素が独自の機能を持つ場合や機密データを含む場合、その要素へのアクセスは可能な限り厳しく制限する必要があります。  その要素を定義したモジュール、クラス、または構造体のみがアクセスできるようにすることで、最大の制限が可能になります。  このような形で要素へのアクセスを制限するには、要素を `Private` で宣言します。  
  
## 規則  
  
-   **宣言コンテキスト。** `Private` は、モジュール レベルでのみ使用できます。  つまり、`Private` 要素の宣言コンテキストは、ソース ファイル、名前空間、インターフェイス、プロシージャではなく、モジュール、クラス、または構造体である必要があります。  
  
## \[動作\]  
  
-   **アクセス レベル。**宣言コンテキスト内のすべてのコードは、自らの `Private` 要素にアクセスできます。  これには、ネストされたクラスや、列挙体内の代入式など、内包型のコードも含まれます。  宣言コンテキスト外部のコードは、`Private` 要素にはアクセスできません。  
  
-   **アクセス修飾子。**アクセス レベルを指定するキーワードは、*アクセス修飾子*と呼ばれます。  アクセス修飾子の比較については、「[Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。  
  
 `Private` 修飾子は、次の場合に使用できます。  
  
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
 [Public](../../../visual-basic/language-reference/modifiers/public.md)   
 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)   
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)   
 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)