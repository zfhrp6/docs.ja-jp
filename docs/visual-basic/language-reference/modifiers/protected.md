---
title: "Protected (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Protected"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Protected Friend keyword combination"
  - "Protected keyword, and Friend"
  - "Protected keyword, syntax"
  - "Protected access modifier"
  - "Protected keyword"
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Protected (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

宣言された 1 つ以上のプログラミング要素が、要素と同じクラスまたは派生クラスからのみアクセス可能であることを指定します。  
  
## 解説  
 クラスに宣言されたプログラミング要素に重要情報や制限付きのコードが含まれるために、その要素へのアクセスを制限する場合があります。  しかし、それが継承可能なクラスで、派生クラスが階層的に構成されると予想される場合、これらの派生クラスから機密データや制限付きコードにアクセスすることも必要になります。  このような場合は、要素を基本クラスとすべての派生クラスからアクセス可能にしてください。  このような方法で要素へのアクセスを制限するには、要素を `Protected` で宣言します。  
  
## 規則  
  
-   **宣言コンテキスト。** `Protected` は、クラス レベルでのみ使用できます。  つまり、`Protected` 要素の宣言コンテキストはクラスであることが必要で、ソース ファイル、名前空間、インターフェイス、モジュール、構造体、またはプロシージャでは宣言できません。  
  
-   **結合された修飾子。** `Protected` 修飾子は、同じ宣言内で [Friend](../../../visual-basic/language-reference/modifiers/friend.md) 修飾子と組み合わせて使用できます。  この組み合わせで宣言すると、要素は同じアセンブリ内の任意の場所、要素と同じクラス、そして派生クラスからアクセス可能になります。  `Protected Friend` は、クラスのメンバーでのみ指定できます。  
  
## \[動作\]  
  
-   **アクセス レベル。**クラス内のすべてのコードがその要素にアクセスできます。  基本クラスから派生した任意のクラスのコードが、基本クラスのすべての `Protected` 要素にアクセスできます。  これは、派生のすべての世代で同じです、  つまり、クラスは、基本クラスのそのまた基本クラスなど、何世代も上の `Protected` 要素にアクセスできます。  
  
     プロテクト アクセスはフレンド アクセスのスーパーセットでもサブセットでもありません。  
  
-   **アクセス修飾子。**アクセス レベルを指定するキーワードは、*アクセス修飾子*と呼ばれます。  アクセス修飾子の比較については、「[Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。  
  
 修飾子 `Protected` は、次の構文で使用します。  
  
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
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)   
 [Private](../../../visual-basic/language-reference/modifiers/private.md)   
 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)