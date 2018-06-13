---
title: 型リスト (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- StructureConstraint
- vb.StructureConstraint
- ClassConstraint
- vb.ClassConstraint
helpviewer_keywords:
- class constraint
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- generics [Visual Basic], type list
- structure constraint
- constraints, in type parameters
- generics [Visual Basic], generic types
- parameters [Visual Basic], type
- constraints, Structure keyword
- type parameters [Visual Basic], constraints
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], type parameters
- type parameters
- constraints, Class keyword
ms.assetid: 56db947a-2ae8-40f2-a70a-960764e9d0db
ms.openlocfilehash: 5fbb07154fce27feb257b431c1726446b42fbfe0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605291"
---
# <a name="type-list-visual-basic"></a>型リスト (Visual Basic)
指定します、*パラメーター入力*の*ジェネリック*プログラミング要素です。 複数のパラメーターは、コンマで区切られます。 1 つの型パラメーターの構文を次に示します。  
  
## <a name="syntax"></a>構文  
  
```  
[genericmodifier] typename [ As constraintlist ]  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`genericmodifier`|任意。 ジェネリック インターフェイスとバリアント汎用デリゲートでのみ使用できます。 型を宣言する共変を使用して、[アウト](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)キーワードまたは反変を使用して、[で](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)キーワード。 「 [共変性と反変性](../../programming-guide/concepts/covariance-contravariance/index.md)を参照してください。|  
|`typename`|必須。 型パラメーターの名前です。 これは、対応する型引数で指定した定義済みの型によって置き換えられるプレース ホルダーです。|  
|`constraintlist`|任意。 指定できるデータ型を制約するための要件の一覧`typename`です。 複数の制約があれば、中かっこで囲む (`{ }`) をコンマで区切って指定します。 使用して、制約リストを導入する必要があります、[として](../../../visual-basic/language-reference/statements/as-clause.md)キーワード。 使用する`As`リストの先頭に一度だけです。|  
  
## <a name="remarks"></a>コメント  
 すべて汎用のプログラミング要素には、少なくとも 1 つの型パラメーターを受け取る必要があります。 型パラメーターは、特定の種類を表すプレース ホルダー (、*構築される要素*) クライアント コードは、ジェネリック型のインスタンスを作成するタイミングを指定します。 ジェネリック クラスを定義、構造体、インターフェイス、プロシージャ、したり、委任できます。  
  
 ジェネリック型を定義する場合の詳細については、次を参照してください。 [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)です。 型パラメーター名の詳細については、次を参照してください。[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。  
  
## <a name="rules"></a>ルール  
  
-   **かっこです。** 型パラメーター リストを指定する場合は、かっこで囲む必要がありますを使用してリストを導入する必要があります、[の](../../../visual-basic/language-reference/statements/of-clause.md)キーワード。 使用する`Of`リストの先頭に一度だけです。  
  
-   **制約。** 一連の*制約*型のパラメーターは、任意の組み合わせで、次の項目を含めることができます。  
  
    -   インターフェイスの数。 指定された型は、この一覧にすべてのインターフェイスを実装する必要があります。  
  
    -   1 つのクラスです。 指定された型は、そのクラスから継承する必要があります。  
  
    -   `New` キーワード。 指定された型は、ジェネリック型にアクセスできるパラメーターなしのコンス トラクターを公開する必要があります。 これは、1 つまたは複数のインターフェイスによって型パラメーターを制約する場合に便利です。 インターフェイスを実装する型は必ずしもは、コンス トラクターを公開しませんし、コンス トラクターのアクセス レベルに応じて、ジェネリック型内のコードできないことがありますへのアクセスします。  
  
    -   いずれか、`Class`キーワードまたは`Structure`キーワード。 `Class`キーワードは、すべての型引数が渡された文字列、配列、またはデリゲート、たとえば、参照型であること、またはクラスから作成されたオブジェクトを必要とするジェネリック型パラメーターを制約します。 `Structure`キーワードは、たとえば構造体、列挙型、または基本データ型をすべての型引数が渡された値型であることを必要とするジェネリック型パラメーターに制約します。 両方を含めることはできません`Class`と`Structure`同じ`constraintlist`です。  
  
     指定された型に含めるすべての要件を満たす必要があります`constraintlist`です。  
  
     それぞれの型パラメーターに対する制約は、その他の型パラメーターの制約の依存しません。  
  
## <a name="behavior"></a>動作  
  
-   **コンパイル時の代入。** 汎用のプログラミング要素から構築された型を作成する場合は、それぞれの型パラメーターの定義済みの型を指定します。 Visual Basic コンパイラごとに出現する位置を指定する型で置き換え`typename`内のジェネリックな要素です。  
  
-   **制約が存在しない場合。** コードは操作およびでサポートされているメンバーに限定型パラメーターに対する制約を指定しない場合、[オブジェクト データ型](../../../visual-basic/language-reference/data-types/object-data-type.md)その型パラメーターです。  
  
## <a name="example"></a>例  
 次の例では、ディクショナリに新しいエントリを追加する関数の骨組みをなどのジェネリック ディクショナリ クラスのスケルトン定義を示します。  
  
 [!code-vb[VbVbalrStatements#3](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_1.vb)]  
  
## <a name="example"></a>例  
 `dictionary`はジェネリックでそれを使用するコードから作成できますのさまざまなオブジェクト、同じ機能を持つが、別のデータ型で動作している各します。 次の例は、行のコードを作成する、`dictionary`オブジェクト`String`エントリと`Integer`キー。  
  
 [!code-vb[VbVbalrStatements#4](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_2.vb)]  
  
## <a name="example"></a>例  
 次の例では、前の例によって生成された同等のスケルトン定義を示します。  
  
 [!code-vb[VbVbalrStatements#5](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_3.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)  
 [New 演算子](../../../visual-basic/language-reference/operators/new-operator.md)  
 [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Object 型](../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [方法 : ジェネリック クラスを使用する](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [共変性と反変性](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
