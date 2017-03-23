---
title: "値型と参照型 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- reference data types
- reference types
- value types
- value data types
- types [Visual Basic]
- data types [Visual Basic], value types
- data types [Visual Basic], reference types
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: de8016b4b2a5550b32373a41c89a484fa996c596
ms.lasthandoff: 03/13/2017

---
# <a name="value-types-and-reference-types"></a>Value Types and Reference Types
Visual basic でのデータ型は、分類に基づいて実装されます。 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]データ型は、特定の型の変数が、独自のデータまたはデータへのポインターを格納するかどうかによって分類できます。 独自のデータを格納する場合、*値の型*別の場所ではメモリ内のデータへのポインターを保持している場合、*型を参照*します。  
  
## <a name="value-types"></a>値型  
 データ型は、*値の型*独自のメモリ内のデータが保持している場合。 値型を以下に示します。  
  
-   すべての数値データ型  
  
-   `Boolean`、`Char`、および `Date`  
  
-   そのメンバーが参照型である場合でも、すべての構造  
  
-   列挙型、その基になる型は常にため`SByte`、 `Short`、 `Integer`、 `Long`、 `Byte`、 `UShort`、 `UInteger`、または`ULong`  
  
 参照型のメンバーが含まれている場合でも、すべての構造体は値の型です。 このため、値などの型`Char`と`Integer`.NET Framework の構造体によって実装されます。  
  
 予約済みキーワードを使用して、値型を宣言できます`Decimal`します。 使用することも、`New`値型を初期化するキーワードです。 これは、型のパラメーターを受け取るコンス トラクターがある場合に特に便利です。 この例は、<xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29>コンス トラクターは、新しい`Decimal`指定した部分からの値</xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29>。  
  
## <a name="reference-types"></a>参照型  
 A*型参照*データを保持する別のメモリ位置へのポインターが含まれています。 参照型を以下に示します。  
  
-   `String`  
  
-   その要素が値型の場合でも、すべての配列  
  
-   などのクラス型します。<xref:System.Windows.Forms.Form></xref:System.Windows.Forms.Form>  
  
-   デリゲート  
  
 クラスは、*型参照*します。 参照型など、このため、`Object`と`String`でサポートされている[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]クラスです。 場合でも、そのメンバーが値型は、すべての配列が参照型である注意してください。  
  
 使用する必要がありますので、すべての参照型は、基になる .NET Framework クラスを表す、 [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)初期化するときのキーワードです。 次のステートメントでは、配列を初期化します。  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a>型ではない要素  
 これらはいずれも、宣言された要素のデータ型として指定できないため、次のプログラミング要素は型とは見なされません。  
  
-   名前空間  
  
-   モジュール  
  
-   イベント  
  
-   プロパティとプロシージャ  
  
-   変数、定数、およびフィールド  
  
## <a name="working-with-the-object-data-type"></a>オブジェクトのデータ型の操作  
 変数に参照型または値型を割り当てることができます、`Object`データ型。 `Object`変数は常に、データそのものでは決してでデータへのポインターを保持します。 ただし、値の型を割り当てる場合、`Object`変数、動作、独自のデータが保持している場合にします。 詳細については、次を参照してください。 [Object データ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)します。  
  
 かどうか調べることができます、`Object`に渡すことによって変数が参照型または値の型として機能する、<xref:Microsoft.VisualBasic.Information.IsReference%2A>メソッドで、<xref:Microsoft.VisualBasic.Information>のクラス、<xref:Microsoft.VisualBasic?displayProperty=fullName>名前空間</xref:Microsoft.VisualBasic?displayProperty=fullName></xref:Microsoft.VisualBasic.Information></xref:Microsoft.VisualBasic.Information.IsReference%2A>。 <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=fullName>返します`True`場合の内容、`Object`変数が参照型を表します。</xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=fullName>  
  
## <a name="see-also"></a>関連項目  
 [Null 許容値型](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)   
 [Visual Basic における型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Structure ステートメント](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [データ型の効率的な使用](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)   
 [オブジェクトのデータ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
