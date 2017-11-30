---
title: MustInherit (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- MustInherit
- vb.MustInherit
helpviewer_keywords:
- classes [Visual Basic], abstract
- MustInherit classes [Visual Basic], MustInherit keyword
- abstract classes [Visual Basic], MustInherit class
- MustInherit keyword [Visual Basic]
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d384986e42ee69a0f425c1590599aa2c82bc856
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mustinherit-visual-basic"></a>MustInherit (Visual Basic)
クラスを基底クラスとしてのみ使用できます、また、オブジェクトを直接作成できないことを指定します。  
  
## <a name="remarks"></a>コメント  
 目的は、*基底クラス*(とも呼ばれる、*抽象クラス*) は、それから派生したすべてのクラスに共通する機能を定義します。 これにより、派生クラスが共通の要素を再定義する必要がなくなります。 場合によっては、この共通の機能が、使用可能なオブジェクトを作成するのに十分な不完全し、各派生クラスが不足している機能を定義します。 このような場合は、オブジェクトを作成する派生クラスからのみ利用側のコードが必要です。 使用する`MustInherit`を強制する、基本クラスです。  
  
 別の使用、`MustInherit`クラスは、関連するクラスのセットに変数を制限します。 基本クラスを定義し、そこからこれらのすべての関連するクラスを派生できます。 基本クラスは、すべての派生クラスに共通の機能を提供する必要はありませんが、その変数に値を割り当てるためのフィルターとして使用できます。 コンシューマー コードは、基底クラスとしての変数を宣言する場合 Visual Basic では、その変数に、派生クラスのいずれかのオブジェクトのみを割り当てることができます。  
  
 .NET Framework では、いくつかを定義します`MustInherit`クラスは、それらの間<xref:System.Array>、 <xref:System.Enum>、および<xref:System.ValueType>です。 <xref:System.ValueType>変数を制限する基本クラスの例を示します。 すべての値型から派生<xref:System.ValueType>です。 として変数を宣言する場合<xref:System.ValueType>、その変数に値型のみを割り当てることができます。  
  
## <a name="rules"></a>ルール  
  
-   **宣言コンテキスト。** 使用することができます`MustInherit`でのみ、`Class`ステートメントです。  
  
-   **結合された修飾子。** 指定することはできません`MustInherit`と共に`NotInheritable`同じ宣言内で。  
  
## <a name="example"></a>例  
 次の例は、強制的な継承と強制的なオーバーライドを示しています。 基本クラス`shape`変数を定義`acrossLine`です。 クラスは、`circle`と`square`から派生`shape`です。 定義を継承`acrossLine`、関数を定義する必要がありますが、`area`その計算方法は図形の種類ごとに異なるためです。  
  
 [!code-vb[VbVbalrKeywords#2](../../../visual-basic/language-reference/codesnippet/VisualBasic/mustinherit_1.vb)]  
  
 宣言することができます`shape1`と`shape2`型である`shape`です。 オブジェクトを作成することはできませんただし、`shape`関数の機能がないため`area`がマークされていると`MustInherit`です。  
  
 として宣言されているため`shape`、変数`shape1`と`shape2`派生クラスからオブジェクトに制限される`circle`と`square`です。 Visual Basic はできません、他のオブジェクトをこれらの変数に割り当てることにより、高レベルのタイプ セーフです。  
  
## <a name="usage"></a>使用方法  
 `MustInherit`修飾子は、このコンテキストで使用できます。  
  
 [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a>関連項目  
 [Inherits ステートメント](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)  
 [継承の基本](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
