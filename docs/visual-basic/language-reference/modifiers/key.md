---
title: "Key (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.AnonymousKey"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "anonymous types [Visual Basic], key"
  - "Key [Visual Basic]"
  - "Key keyword [Visual Basic]"
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Key (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`Key` キーワードを使用すると、匿名型のプロパティの動作を指定できます。  キー プロパティとして指定したプロパティのみが、匿名型のインスタンス間での等価テストやハッシュ コード値の計算に使用されます。  キー プロパティの値は変更できません。  
  
 匿名型のプロパティをキー プロパティとして指定するには、初期化リストでの宣言時に `Key` キーワードをプロパティの前に置きます。  次の例では、`Airline` と `FlightNo` はキー プロパティですが、`Gate` はキー プロパティではありません。  
  
 [!code-vb[VbVbalrAnonymousTypes#26](../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/key_1.vb)]  
  
 作成される新しい匿名型は、<xref:System.Object> から直接継承します。  コンパイラは、次の 3 つの継承されたメンバーをオーバーライドします。<xref:System.Object.Equals%2A>、<xref:System.Object.GetHashCode%2A>、および <xref:System.Object.ToString%2A>。  <xref:System.Object.Equals%2A> および <xref:System.Object.GetHashCode%2A> のために生成されるオーバーライド コードは、キー プロパティに基づいています。  型の中にキー プロパティがない場合、<xref:System.Object.GetHashCode%2A> と <xref:System.Object.Equals%2A> はオーバーライドされません。  
  
## 等価比較  
 2 つの匿名型のインスタンスは、型が同じであり、キープロパティの値が等しければ、等価のインスタンスです。  次の例では、`flight2` および前の例の `flight1` は、同じ匿名型のインスタンスであり、キー プロパティの値が一致するので等価です。  ただし、`flight3` と `flight1` は等価ではありません。キー プロパティの `FlightNo` の値が異なるためです。  `flight4` インスタンスの型は `flight1` と同じではありません。これらは、異なるプロパティをキー プロパティとして指定しています。  
  
 [!code-vb[VbVbalrAnonymousTypes#27](../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/key_2.vb)]  
  
 2 つのインスタンスが、キー プロパティ以外のプロパティで宣言されている場合は、名前、型、順序、および値が同一であっても、2 つのインスタンスは等価ではありません。  キー プロパティを持たないインスタンスは、自身に対してのみ等価です。  
  
 2 つの匿名型インスタンスが同じ匿名型のインスタンスである場合の条件については、「[Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)」を参照してください。  
  
## ハッシュ コードの計算  
 <xref:System.Object.Equals%2A> のように、匿名型に対して <xref:System.Object.GetHashCode%2A> で定義されたハッシュ関数は、型のキー プロパティに基づきます。  キー プロパティとハッシュ コード値の間のやり取りを次の例に示します。  
  
 すべてのキー プロパティに対して同じ値を持つ匿名型のインスタンスは、キー プロパティ以外のプロパティの値が一致していなくても、同じハッシュ コードを保持します。  次のステートメントは `True` を返します。  
  
 [!code-vb[VbVbalrAnonymousTypes#37](../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/key_3.vb)]  
  
 1 つ以上のキー プロパティの値が異なる匿名型のインスタンスは、異なるハッシュ コード値を保持します。  次のステートメントは `False` を返します。  
  
 [!code-vb[VbVbalrAnonymousTypes#38](../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/key_4.vb)]  
  
 異なるプロパティをキー プロパティとして指定する匿名型のインスタンスは、同じ型のインスタンスではありません。  これらは、すべてのプロパティの名前と値が同じであっても、ハッシュ コード値が異なります。  次のステートメントは `False` を返します。  
  
 [!code-vb[VbVbalrAnonymousTypes#39](../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/key_5.vb)]  
  
## 読み取り専用値  
 キー プロパティの値は変更できません。  たとえば、前の例の `flight1` では、`Airline` フィールドと `FlightNo` フィールドは読み取り専用ですが、`Gate` は変更可能です。  
  
 [!code-vb[VbVbalrAnonymousTypes#28](../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/key_6.vb)]  
  
## 参照  
 [Anonymous Type Definition](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)   
 [方法 : 匿名型の宣言におけるプロパティ名と型を推論する](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)   
 [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)