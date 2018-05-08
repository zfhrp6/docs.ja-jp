---
title: Imports ステートメント (.NET 名前空間および型)
ms.date: 07/20/2015
f1_keywords:
- vb.Imports
- imports
helpviewer_keywords:
- declared element names [Visual Basic], qualification
- imports [Visual Basic]
- Imports statement [Visual Basic]
- aliases [Visual Basic], Imports statement
- container elements [Visual Basic]
- namespaces [Visual Basic], importing
- Imports statement [Visual Basic], syntax
- import aliases [Visual Basic]
- aliases [Visual Basic], import
- declared elements [Visual Basic], container elements
ms.assetid: 7062f8aa-d890-4232-9eed-92836e13fb6e
ms.openlocfilehash: ef569b0ed6428d24d019e00c500e4d4b91c83d49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="imports-statement-net-namespace-and-type"></a>Imports ステートメント (.NET 名前空間および型)
有効では、名前空間修飾なしで参照されるように名前を入力します。  
  
## <a name="syntax"></a>構文  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`aliasname`|任意。 *インポート エイリアス*または名前ではコードを参照できます`namespace`完全修飾文字列の代わりにします。 参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。|  
|`namespace`|必須。 インポートされる名前空間の完全修飾名。 名前空間の文字列はネストできます任意のレベルに。|  
|`element`|任意。 プログラミング要素の名前は、名前空間で宣言されています。 任意のコンテナー要素を指定できます。|  
  
## <a name="remarks"></a>コメント  
 `Imports`ステートメントにより、直接参照されるように指定した名前空間に含まれている型。  
  
 1 つの名前空間の名前または入れ子になった名前空間の文字列を指定することができます。 入れ子になった各名前空間は、ピリオドで、[次へ] より高いレベルの名前空間から分離 (`.`)、次の例に示すようにします。  
  
 `Imports System.Collections.Generic`  
  
 各ソース ファイルは、任意の数を含めることができます`Imports`ステートメントです。 これらに従う必要ありますオプションの任意の宣言など、`Option Strict`ステートメント、および、必要がありますの前に任意のプログラミング要素宣言など`Module`または`Class`ステートメントです。  
  
 使用することができます`Imports`ファイル レベルでのみです。 つまり、宣言コンテキストのインポートはソース ファイルでは、名前空間、クラス、構造体、モジュール、インターフェイス、プロシージャ、またはブロックすることはできません。  
  
 なお、`Imports`ステートメントは行いません他のプロジェクトおよびアセンブリからの要素をプロジェクトに使用できます。 インポートは行われず、参照を設定します。 既にプロジェクトに使用できる名前を修飾する必要性のみを削除します。 詳細については、「を含む要素をインポートする」を参照してください[宣言された要素への参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)です。  
  
> [!NOTE]
>  暗黙の型を定義する`Imports`ステートメントを使用して、[参照設定 ページ、プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)です。 詳細については、次を参照してください。[する方法: 追加またはインポートされた名前空間 (Visual Basic) を削除する](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic)です。  
  
## <a name="import-aliases"></a>インポート エイリアス  
 *インポート エイリアス*名前空間または型のエイリアスを定義します。 インポート エイリアスは、1 つまたは複数の名前空間で宣言されている同じ名前の項目を使用する必要がある場合に便利です。 詳細と例を参照してください「の要素の名前を修飾」[宣言された要素への参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)です。  
  
 モジュール レベルと同じ名前のメンバーを宣言する必要がありますいない`aliasname`です。 Visual Basic コンパイラを使用する場合、`aliasname`宣言されたメンバーに対してのみとしません。 インポート エイリアスとして認識します。  
  
 インポート エイリアスの宣言に使用する構文はそのような XML 名前空間プレフィックスをインポートするため、使用、結果は異なります。 インポート エイリアスは、され、XML 名前空間プレフィックスでく XML リテラルまたは XML 軸のプロパティでのみ、プレフィックスとしてに使用で修飾された要素または属性の名前に、コード内の式として使用できます。  
  
### <a name="element-names"></a>要素の名前  
 指定した場合`element`、表されることにする必要があります、*コンテナー要素*、その他の要素を含めることができるプログラミング要素は、します。 コンテナー要素には、クラス、構造体、モジュール、インターフェイス、および列挙が含まれます。  
  
 使用できる要素のスコープ、`Imports`ステートメントは、指定するかどうかによって異なります`element`です。 のみを指定する場合`namespace`すべて一意にその名前空間のメンバーとその名前空間内のコンテナー要素のメンバーの名前は修飾なしで利用できます。 両方を指定する場合`namespace`と`element`、その要素のメンバーは、修飾しないで使用専用です。  
  
## <a name="example"></a>例  
 次の例では、C:\ ディレクトリ内のすべてのフォルダーを返しますを使用して、<xref:System.IO.DirectoryInfo>クラスです。  
  
 コードは いいえ`Imports`ファイルの上部にあるステートメントです。 したがって、 `DirectoryInfo`、 <xref:System.Text.StringBuilder>、および<xref:Microsoft.VisualBasic.ControlChars.CrLf>参照はすべて完全修飾名前空間にします。  
  
 [!code-vb[VbVbalrStatements#152](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_1.vb)]  
  
## <a name="example"></a>例  
 次の例が含まれます`Imports`参照先の名前空間のステートメント。 そのため、型は完全修飾名前空間にするのにはありません。  
  
 [!code-vb[VbVbalrStatements#153](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_2.vb)]  
  
 [!code-vb[VbVbalrStatements#154](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_3.vb)]  
  
## <a name="example"></a>例  
 次の例が含まれます`Imports`参照先の名前空間のエイリアスを作成するステートメント。 種類は、別名で修飾されます。  
  
 [!code-vb[VbVbalrStatements#155](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_4.vb)]  
  
 [!code-vb[VbVbalrStatements#156](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_5.vb)]  
  
## <a name="example"></a>例  
 次の例が含まれます`Imports`参照先の型のエイリアスを作成するステートメント。 エイリアスを使用して、種類を指定します。  
  
 [!code-vb[VbVbalrStatements#157](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_6.vb)]  
  
 [!code-vb[VbVbalrStatements#158](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_7.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Namespace ステートメント](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [参照と Imports ステートメント](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [Imports ステートメント (XML 名前空間)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)  
 [宣言された要素の参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
