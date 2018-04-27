---
title: 値型と参照型
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- reference data types [Visual Basic]
- reference types [Visual Basic]
- value types [Visual Basic]
- value data types [Visual Basic]
- types [Visual Basic]
- data types [Visual Basic], value types
- data types [Visual Basic], reference types
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9cbab25e4af6b96ae22fe18d0b8a8fdbc7a7c7a7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="value-types-and-reference-types"></a>値型と参照型
Visual basic でのデータ型は、分類に基づいて実装します。 Visual Basic データ型は、特定の型の変数が、独自のデータまたはデータへのポインターを格納するかどうかに基づいて分類できます。 独自のデータを保管する場合は、*値の型*以外の場合は別の場所はメモリ内のデータへのポインターを保持、*型参照*です。  
  
## <a name="value-types"></a>値型  
 データ型は、*値の型*独自のメモリ割り当て内のデータが保持している場合。 値の型を以下に示します。  
  
-   すべての数値データ型  
  
-   `Boolean`、`Char`、および `Date`  
  
-   そのメンバーが参照型である場合でも、すべての構造  
  
-   列挙体、その基になる型は常にため`SByte`、 `Short`、 `Integer`、 `Long`、 `Byte`、 `UShort`、 `UInteger`、または `ULong`  
  
 すべての構造は、値型、参照型のメンバーが含まれている場合でもです。 このため、値などの型`Char`と`Integer`.NET Framework の構造体によって実装されます。  
  
 たとえば、予約済みキーワードを使用して値の型を宣言する`Decimal`です。 使用することも、`New`値型を初期化するキーワードです。 これは、型パラメーターを受け取るコンス トラクターがある場合に特に便利です。 この例は、<xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29>コンス トラクターは、新しいビルド`Decimal`指定した部分からの値。  
  
## <a name="reference-types"></a>参照型  
 A*型参照*データを保持する別のメモリ位置へのポインターが含まれています。 参照型を以下に示します。  
  
-   `String`  
  
-   その要素が値型である場合でも、すべての配列  
  
-   などのクラス型します。 <xref:System.Windows.Forms.Form>  
  
-   デリゲート  
  
 クラスは、*型参照*です。 このためなどの参照型`Object`と`String`でサポートされている[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]クラスです。 場合でも、そのメンバーは、値の型は、すべての配列が参照型である注意してください。  
  
 使用する必要がありますすべての参照型は、基になる .NET Framework クラスを表すため、 [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)キーワード初期化するときにします。 次のステートメントでは、配列を初期化します。  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a>型ではない要素  
 宣言された要素のデータ型としてそれらのいずれかを指定できないため、次のプログラミング要素は、型とは見なされません。  
  
-   名前空間  
  
-   モジュール  
  
-   イベント  
  
-   プロパティやプロシージャ  
  
-   変数、定数、およびフィールド  
  
## <a name="working-with-the-object-data-type"></a>オブジェクトのデータ型の使用  
 変数に参照型または値型のいずれかを割り当てることができます、`Object`データ型。 `Object`変数は常に、データをデータ自体では決してへのポインターを保持します。 ただし、値の型を割り当てる場合、`Object`変数、ように動作、独自のデータを保持します。 詳細については、次を参照してください。[オブジェクト データ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)です。  
  
 かどうか調べることができます、`Object`に渡すことによって変数が参照型または値の型として機能する、<xref:Microsoft.VisualBasic.Information.IsReference%2A>メソッドで、<xref:Microsoft.VisualBasic.Information>のクラス、<xref:Microsoft.VisualBasic?displayProperty=nameWithType>名前空間。 <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> 返します`True`場合のコンテンツ、`Object`変数が参照型を表します。  
  
## <a name="see-also"></a>関連項目  
 [null 許容値型](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [Visual Basic での型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Structure ステートメント](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [データ型の有効な使用方法](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Object 型](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
