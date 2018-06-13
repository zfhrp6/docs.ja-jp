---
title: Inherits Statement
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: 43a8aa4e9e04ee035cb52e9f829de13e5c022217
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604342"
---
# <a name="inherits-statement"></a>Inherits Statement
現在のクラスまたはインターフェイスの属性、変数、プロパティ、プロシージャ、およびイベントを別のクラスまたはインターフェイスのセットから継承が発生します。  
  
## <a name="syntax"></a>構文  
  
```  
Inherits basetypenames  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`basetypenames`|必須。 このクラスの派生元となるクラスの名前。<br /><br /> - または -<br /><br /> このインターフェイスの派生元のインターフェイスの名前。 コンマを使用して、複数の名前を区切ります。|  
  
## <a name="remarks"></a>コメント  
 使用する場合、`Inherits`ステートメントはクラスまたはインターフェイスの定義では、最初の空白またはコメント以外の次の行である必要があります。 必要があります直後、`Class`または`Interface`ステートメントです。  
  
 使用することができます`Inherits`クラスまたはインターフェイスでのみです。 つまり、継承の宣言コンテキストはソース ファイル、名前空間、構造体、モジュール、プロシージャ、またはブロックすることはできません。  
  
## <a name="rules"></a>ルール  
  
-   **クラスの継承します。** クラスを使用している場合、`Inherits`ステートメントでは、1 つだけの基本クラスを指定することができます。  
  
     クラスは、内部に入れ子になったクラスから継承できません。  
  
-   **インターフェイスの継承します。** インターフェイスで使用する場合、`Inherits`ステートメントでは、1 つまたは複数の基底インターフェイスを指定することができます。 同じ名前のメンバーが定義されている場合でも、2 つのインターフェイスから継承することができます。 これを行う場合、実装コードは、実装するメンバーを指定する名前の修飾を使用する必要があります。  
  
     インターフェイスより制限の厳しいアクセス レベルを持つ別のインターフェイスから継承できません。 たとえば、`Public`インターフェイスを継承できません、`Friend`インターフェイスです。  
  
     インターフェイスは、内部に入れ子になったインターフェイスから継承できません。  
  
 .NET Framework におけるクラス継承の例は、<xref:System.ArgumentException>から継承されるクラスが、<xref:System.SystemException>クラスです。 これにより、<xref:System.ArgumentException>すべての定義済みプロパティとなどのシステム例外によって必要な手順、<xref:System.Exception.Message%2A>プロパティおよび<xref:System.Exception.ToString%2A>メソッドです。  
  
 .NET Framework のインターフェイスの継承の例は、<xref:System.Collections.ICollection>から継承されるインターフェイス、<xref:System.Collections.IEnumerable>インターフェイスです。 これにより、<xref:System.Collections.ICollection>コレクションを走査するために必要な列挙子の定義を継承します。  
  
## <a name="example"></a>例  
 次の例では、`Inherits`クラスの名前付け方法を表示するステートメント`thisClass`という名前の基本クラスのすべてのメンバーを継承できます`anotherClass`です。  
  
 [!code-vb[VbVbalrStatements#37](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_1.vb)]  
  
## <a name="example"></a>例  
 次の例では、複数のインターフェイスの継承を示します。  
  
 [!code-vb[VbVbalrStatements#38](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_2.vb)]  
  
 という名前のインターフェイス`thisInterface`内のすべての定義が含まれています、 <xref:System.IComparable>、 <xref:System.IDisposable>、および<xref:System.IFormattable>インターフェイスの継承されたメンバーでは、それぞれ 2 つのオブジェクトの種類に固有の比較を解放するには、リソースが割り当てられます、としてオブジェクトの値を表現して、`String`です。 実装するクラス`thisInterface`すべての基底インターフェイスのすべてのメンバーを実装する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
 [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [継承の基本](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
