---
title: "Inherits Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Inherits"
  - "Inherits"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Inherits statement"
  - "Inherits statement, syntax"
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Inherits Statement
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

現在のクラスまたはインターフェイスの属性、変数、プロパティ、プロシージャ、およびイベントを別のクラスまたは一連のインターフェイスから継承します。  
  
## 構文  
  
```  
Inherits basetypenames  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`basetypenames`|必ず指定します。  このクラスの派生元となるクラスの名前です。<br /><br /> または<br /><br /> このインターフェイスの派生元のインターフェイスの名前を指定します。  複数の名前を区切るには、コンマを使います。|  
  
## 解説  
 `Inherits` ステートメントを使用する場合は、クラス定義内またはインターフェイス定義内の空行やコメントではない 1 行目に配置する必要があります。  このステートメントは、`Class` ステートメントまたは `Interface` ステートメントの直後に追加します。  
  
 `Inherits` は、クラスまたはインターフェイスの中でのみ使用できます。  つまり、ソース ファイル、名前空間、構造体、モジュール、プロシージャ、またはブロックをコンテキストとして継承を宣言することはできません。  
  
## 規則  
  
-   **クラスの継承。**クラスで `Inherits` ステートメントを使用する場合は、1 つの基本クラスだけを指定できます。  
  
     中に入れ子になったクラスは継承できません。  
  
-   **インターフェイスの継承。**インターフェイスで `Inherits` ステートメントを使用する場合は、1 つ以上の基本インターフェイスを指定できます。  2 つのインターフェイスに同じ名前のメンバーが定義されている場合でも、その 2 つを継承できます。  その場合、実装コードでは、実装するメンバーを指すために名前の修飾を使う必要があります。  
  
     インターフェイスには、それ自身より厳しいアクセス レベルを持つ別のインターフェイスを継承することはできません。  たとえば、`Public` インターフェイスは `Friend` インターフェイスを継承できません。  
  
     インターフェイスは、自分の中に入れ子になっているインターフェイスを継承できません。  
  
 .NET Framework で使用されるクラス継承の例として、<xref:System.ArgumentException> クラスが挙げられます。このクラスは、<xref:System.SystemException> クラスを継承します。  この継承によって、<xref:System.ArgumentException> には、システム例外で必要とされる、<xref:System.Exception.Message%2A> プロパティや <xref:System.Exception.ToString%2A> メソッドなどのすべての定義済みのプロパティおよびプロシージャが提供されます。  
  
 .NET Framework で使用されるインターフェイス継承の例として、<xref:System.Collections.ICollection> インターフェイスが挙げられます。このインターフェイスは、<xref:System.Collections.IEnumerable> インターフェイスを継承します。  これにより、<xref:System.Collections.ICollection> はコレクションを走査するために必要な列挙子の定義を継承します。  
  
## 使用例  
 次の例は、`Inherits` ステートメントを使用して、`thisClass` というクラスに `anotherClass` という基本クラスのすべてのメンバーを継承する方法を示しています。  
  
 [!code-vb[VbVbalrStatements#37](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/inherits-statement_1.vb)]  
  
## 使用例  
 次の例は、複数のインターフェイスを継承する方法を示しています。  
  
 [!code-vb[VbVbalrStatements#38](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/inherits-statement_2.vb)]  
  
 これにより、`thisInterface` というインターフェイスには、<xref:System.IComparable>、<xref:System.IDisposable>、および <xref:System.IFormattable> の各インターフェイスにあるすべての定義が含まれるようになります。これらの継承されたメンバーは、2 つのオブジェクトを特定の型として比較する機能、割り当てられたリソースを解放する機能、およびオブジェクトの値を `String` で表現する機能を備えています。  `thisInterface` を実装するクラスは、すべての基本インターフェイスのすべてのメンバーを実装する必要があります。  
  
## 参照  
 [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)   
 [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)   
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)   
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)