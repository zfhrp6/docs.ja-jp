---
title: Object Data Type
ms.date: 07/20/2015
f1_keywords:
- vb.Object
- vb.Variant
helpviewer_keywords:
- object variables [Visual Basic], Object type
- data types [Visual Basic], assigning
- Object data type
- Object data type [Visual Basic], reference
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
ms.openlocfilehash: e9b1da5a88c12e0d883c3afe63be98c3fa3e9173
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591627"
---
# <a name="object-data-type"></a>Object Data Type
オブジェクトを参照するアドレスを保持します。 任意の参照型 (文字列、配列、クラス、またはインターフェイス) を割り当てることができます、`Object`変数。 `Object`変数は、任意の値型のデータを指すことも (numeric、 `Boolean`、 `Char`、 `Date`、構造体、または列挙型)。  
  
## <a name="remarks"></a>コメント  
 `Object`データ型は、アプリケーションで認識済みのオブジェクト インスタンスを含む、任意のデータ型のデータを指すことができます。 使用して`Object`コンパイル時に不明な場合をポイントする変数がどのようなデータ型します。  
  
 既定値の`Object`は`Nothing`(null 参照)。  
  
## <a name="data-types"></a>データの種類  
 変数、定数、または任意のデータ型に式を割り当てることができます、`Object`変数。 データ型を決定する、`Object`変数を現在参照して、使用することができます、<xref:System.Type.GetTypeCode%2A>のメソッド、<xref:System.Type?displayProperty=nameWithType>クラスです。 次に例を示します。  
  
```  
Dim myObject As Object  
' Suppose myObject has now had something assigned to it.  
Dim datTyp As Integer  
datTyp = Type.GetTypeCode(myObject.GetType())  
```  
  
 `Object`データ型が参照型です。 ただし、Visual Basic の処理、`Object`値型のデータを参照するときに、値型として変数です。  
  
## <a name="storage"></a>記憶域  
 参照するすべてのデータ型、`Object`自体が、値へのポインターではなく、変数がデータ値を含んでいません。 コンピューター メモリ内で常に 4 バイトを使用しますが、これは、変数の値を表すデータの記憶域には含まれません。 ポインターを使用して、データを検索するコードのため`Object`値の型を保持する変数より明示的に型指定された変数にアクセスするのには、多少速度が低下します。  
  
## <a name="programming-tips"></a>プログラミングのヒント  
  
-   **相互運用の考慮事項。** オートメーション オブジェクトや COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントとやり取りする場合は、他の環境でのポインター型が、Visual Basic と互換性がないことに留意してください`Object`型です。  
  
-   **パフォーマンス。** 宣言した変数、`Object`型は任意のオブジェクトへの参照を格納するのに十分な柔軟性です。 ただし、メソッドまたはそのような変数のプロパティを呼び出すときに必ず*遅延バインディング*(実行時)。 強制的に*事前バインディング*(コンパイル時) とパフォーマンスの向上、特定のクラスの名前を持つ変数を宣言または特定のデータ型にキャストします。  
  
     オブジェクト変数を宣言するときに使用しようと特定のクラス型では、たとえば<xref:System.OperatingSystem>ではなく、汎用`Object`型です。 などに使用できる最も固有のクラスを使用することも必要があります。<xref:System.Windows.Forms.TextBox>の代わりに<xref:System.Windows.Forms.Control>、そのプロパティおよびメソッドにアクセスできるようにします。 通常使用することができます、**クラス**一覧に、**オブジェクト ブラウザー**利用可能なクラス名を検索します。  
  
-   **拡大します。** すべてのデータ型とすべての参照型に変換、`Object`データ型。 つまり、任意の種類を変換する`Object`遭遇することがなく、<xref:System.OverflowException?displayProperty=nameWithType>エラーです。  
  
     ただし、値型の間で変換する場合と`Object`、という操作を実行する Visual Basic*ボックス化*と*アンボックス*、により実行速度が低下します。  
  
-   **型宣言文字。** `Object` リテラルの型文字または識別子の型文字がありません。  
  
-   **Framework の型。** .NET Framework において対応する型は、<xref:System.Object?displayProperty=nameWithType>クラスです。  
  
## <a name="example"></a>例  
 次の例を示しています、`Object`変数オブジェクトのインスタンスをポイントします。  
  
```  
Dim objDb As Object  
Dim myCollection As New Collection()  
' Suppose myCollection has now been populated.  
objDb = myCollection.Item(1)  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Object>  
 [データの種類](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [方法: 2 つのオブジェクトが関連しているかどうかを決める](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [方法: 2 つのオブジェクトが同一であるかどうか判別する](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
