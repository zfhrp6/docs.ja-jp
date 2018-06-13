---
title: パラメーターの一覧 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic
- parameters [Visual Basic], lists
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures [Visual Basic], parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
ms.openlocfilehash: 147a2501219db9f1f1c10f9cf1a81aa395b5ec2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605057"
---
# <a name="parameter-list-visual-basic"></a>パラメーターの一覧 (Visual Basic)
プロシージャが呼び出された場合を想定パラメーターを指定します。 複数のパラメーターは、コンマで区切られます。 1 つのパラメーターの構文を次に示します。  
  
## <a name="syntax"></a>構文  
  
```  
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]   
parametername[( )] [ As parametertype ] [ = defaultvalue ]  
```  
  
## <a name="parts"></a>指定項目  
 `attributelist`  
 任意。 このパラメーターに適用される属性の一覧です。 囲む必要があります、[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)山かっこ ("`<`「と」`>`") です。  
  
 `Optional`  
 任意。 プロシージャが呼び出されたときに、このパラメーターが必要ないことを指定します。  
  
 `ByVal`  
 任意。 プロシージャが置換または呼び出し元のコードに対応する引数の基になる変数の要素を再割り当てできませんを指定します。  
  
 `ByRef`  
 任意。 プロシージャ要素を変更できます、基になる変数呼び出し元のコードに呼び出し元コード自体と同じようを指定します。  
  
 `ParamArray`  
 任意。 パラメーター リストの最後のパラメーターが指定されたデータ型の要素の省略可能な配列であることを示します。 これにより、呼び出し元のコード、プロシージャに任意の数の引数を渡します。  
  
 `parametername`  
 必須。 パラメーターを表すローカル変数の名前です。  
  
 `parametertype`  
 場合は必須`Option Strict`は`On`します。 パラメーターを表すローカル変数のデータ型。  
  
 `defaultvalue`  
 必要な`Optional`パラメーター。 パラメーターのデータ型に評価される定数または定数式です。 型の場合`Object`、クラス、インターフェイス、配列、または構造体では、既定値は、必ずまたは`Nothing`です。  
  
## <a name="remarks"></a>コメント  
 パラメーターはかっこで囲まれているし、コンマで区切られました。 パラメーターは、任意のデータ型で宣言することができます。 指定しない場合`parametertype`、既定値は`Object`します。  
  
 呼び出し元のコードはプロシージャを呼び出すときに渡します、*引数*各必須パラメーターにします。 詳細については、次を参照してください。[の相違点の間でパラメーターと引数](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md)です。  
  
 呼び出し元のコードは、各パラメーターに渡す引数は、呼び出し元のコード内の基になる要素へのポインターです。 この要素は場合*不変*(定数、リテラル、列挙型、または式)、すべてのコードを変更することはできません。 ある場合、*変数*要素 (宣言された変数、フィールド、プロパティ、配列要素、または構造体の要素)、呼び出し元のコードで変更できます。 詳細については、次を参照してください。[の相違点の間で変更可能なと変更できない引数](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)です。  
  
 変数の要素が渡された場合`ByRef`プロシージャが同様に変更できます。 詳細については、次を参照してください。[の相違点の間で値と参照渡しによって引数の渡し](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)です。  
  
## <a name="rules"></a>ルール  
  
-   **かっこです。** パラメーター リストを指定する場合は、かっこで囲む必要があります。 パラメーターがない場合でも、空のリストを囲むかっこを使用することができます。 これにより、明確にすること、その要素は、プロシージャによって、コードの読みやすさが向上します。  
  
-   **省略可能なパラメーターです。** 使用する場合、`Optional`パラメーター修飾子は、リスト内のすべての後続のパラメーターはオプションもありを使用して宣言する、`Optional`修飾子です。  
  
     省略可能なパラメーターのすべての宣言を指定する必要があります、`defaultvalue`句。  
  
     詳細については、次を参照してください。[省略可能なパラメーター](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)です。  
  
-   **パラメーターの配列。** 指定する必要があります`ByVal`の`ParamArray`パラメーター。  
  
     両方を使用することはできません`Optional`と`ParamArray`同じパラメーター リストにします。  
  
     詳細については、次を参照してください。[パラメーター配列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)です。  
  
-   **値渡し。** すべての引数に対して既定のメカニズムは`ByVal`プロシージャは、基になる変数要素を変更ことはできません。 ただし、要素が参照型の場合は、プロシージャが変更できます内容や、基になるオブジェクトのメンバーでも置換や、オブジェクト自体を再割り当てはできません。  
  
-   **パラメーター名。** 次のパラメーターのデータ型が配列の場合は、`parametername`かっこの直後にします。 パラメーター名の詳細については、次を参照してください。[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。  
  
## <a name="example"></a>例  
 次の例は、 `Function` 2 つのパラメーターを定義するプロシージャ。  
  
 [!code-vb[VbVbalrStatements#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-list_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [属性の概要](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [方法 : コード内でステートメントを分割および連結する](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
