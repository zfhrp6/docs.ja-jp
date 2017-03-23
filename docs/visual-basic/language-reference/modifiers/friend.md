---
title: "Friend (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Friend"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Friend キーワード"
  - "Friend アクセス修飾子"
  - "Friend キーワード、構文"
  - "Protected Friend キーワードの組み合わせ"
  - "Friend キーワード、Protected"
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
caps.latest.revision: 25
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 25
---
# Friend (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

1 つまたは複数の宣言されたプログラミング要素が、その宣言を含むアセンブリ内からのみアクセス可能であることを示します。  
  
## 解説  
 多くの場合、クラスや構造体のようなプログラミング要素は、それを宣言したコンポーネント内だけでなく、アセンブリ全体で使用できるようにします。  ただし、アプリケーションである場合\)、アセンブリ外部のコードからのアクセスを可能たくない場合もあります。たとえば。  要素へのアクセスをこのように制限する場合は `Friend` 修飾子を使用して宣言できます。  
  
 同じアセンブリにコンパイルされる他のクラス、構造体、モジュール内のコードは、そのアセンブリ内のすべての `Friend` 要素にアクセスできます。  
  
 `Friend` のアクセスは、アプリケーションのプログラミング要素に望ましいレベルで、`Friend` は、インターフェイス、モジュール、クラス、または構造体の既定のアクセス レベルです。  
  
 モジュール、インターフェイス、または名前空間レベルでのみ `Friend` を使用できます。  したがって、`Friend` の要素の申告コンテキストは、ソース ファイル、名前空間、インターフェイス、モジュール、クラス、または構造体である必要があります; これは、プロシージャにすることはできません。  
  
 `Friend` 修飾子は、同じ宣言内で [Protected](../../../visual-basic/language-reference/modifiers/protected.md) 修飾子と組み合わせて使用できます。  この組み合わせで宣言された要素の両方 `Friend` のアクセスおよびプロテクト アクセス参照します。これらはいずれも同じアセンブリ、独自のクラス、および派生クラスからアクセスできます。  `Protected Friend` は、クラスのメンバーでのみ指定できます。  
  
 `Friend` およびそのほかの比較にアクセス修飾子は、[Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)が表示されます。  
  
> [!NOTE]
>  もう一つのアセンブリが `Friend`としてマークされているすべての型およびメンバーにアクセスできるようにするフレンド アセンブリであることを指定できます。  詳細については、「[フレンド アセンブリ](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
## 使用例  
 次のクラスでは、`Friend` 修飾子を使用すると、同じアセンブリ内の他のプログラミング要素が特定のメンバーにアクセスできるようになります。  
  
 [!code-vb[VbVbalrAccessModifiers#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/friend_1.vb)]  
  
## 使用方法  
 これらのコンテキストで `Friend` 修飾子を使用して:  
  
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
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## 参照  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>   
 [Public](../../../visual-basic/language-reference/modifiers/public.md)   
 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)   
 [Private](../../../visual-basic/language-reference/modifiers/private.md)   
 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)