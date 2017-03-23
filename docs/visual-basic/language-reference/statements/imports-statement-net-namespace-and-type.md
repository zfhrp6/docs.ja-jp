---
title: "Imports ステートメント (.NET Namespace よぶ型) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Imports
- imports
dev_langs:
- VB
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
caps.latest.revision: 40
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
ms.openlocfilehash: 393f3e9a264817d8658585267c954d973290530a
ms.lasthandoff: 03/13/2017

---
# <a name="imports-statement-net-namespace-and-type"></a>Imports ステートメント (.NET 名前空間および型)
有効では、名前空間の修飾せずに参照する名前を入力します。  
  
## <a name="syntax"></a>構文  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`aliasname`|省略可能です。 *インポート エイリアス*または名前ではコードから参照する`namespace`完全に修飾文字列の代わりにします。 参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)します。|  
|`namespace`|必須です。 インポートされる名前空間の完全修飾名。 名前空間の文字列はネストできます任意のレベルに。|  
|`element`|省略可能です。 プログラミングの要素の名前は、名前空間で宣言します。 任意のコンテナー要素を指定できます。|  
  
## <a name="remarks"></a>コメント  
 `Imports`ステートメントにより、型を直接参照できる特定の名前空間に含まれています。  
  
 単一の名前空間名または入れ子になった名前空間の文字列を指定することができます。 入れ子になった各名前空間がピリオドで区切った次のより高いレベルの名前空間から (`.`) 次の例に示すようにします。  
  
 `Imports System.Collections.Generic`  
  
 各ソース ファイルは、任意の数を含めることができます`Imports`ステートメントです。 これらをたどるに任意のオプションを宣言など、`Option Strict`ステートメント、およびそれらの前に指定任意のプログラミング要素宣言など`Module`または`Class`ステートメントです。  
  
 使用する`Imports`ファイル レベルでのみです。 つまり、宣言コンテキストのインポートでソース ファイルである名前空間、クラス、構造体、モジュール、インターフェイス、プロシージャ、またはブロックすることはできません。  
  
 `Imports`ステートメントは行いませんから他のプロジェクトおよびアセンブリの要素をプロジェクトで使用します。 インポートは行われず、参照を設定します。 既にプロジェクトに使用できる名前を修飾する必要性のみを削除します。 詳細については、「を含む要素のインポート」を参照してください[宣言された要素への参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)します。  
  
> [!NOTE]
>  暗黙の型を定義する`Imports`ステートメントを使用して、[参照設定 ページ、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)します。 詳細については、次を参照してください。[方法: 追加またはインポートされた名前空間 (Visual Basic) を削除する](http://msdn.microsoft.com/library/44cebec3-0ea0-47c2-8406-4edeab6a997e)です。  
  
## <a name="import-aliases"></a>インポート エイリアス  
 *インポート エイリアス*名前空間または型のエイリアスを定義します。 インポート エイリアスは、1 つ以上の名前空間で宣言されているのと同じ名前を持つ項目を使用する必要がある場合に役立ちます。 詳細および例に、「an 要素名を修飾する」を参照してください[宣言された要素への参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)します。  
  
 同じ名前のモジュール レベルでメンバーを宣言する必要があります`aliasname`します。 Visual Basic コンパイラを使用した場合、`aliasname`宣言されたメンバーに対してのみとしません。 インポート エイリアスとして認識します。  
  
 インポート エイリアスを宣言するために使用される構文は、XML 名前空間プレフィックスをインポートするため使用されることはそのようなが、結果は異なります。 インポート エイリアスは、XML 名前空間プレフィックスとして使用できます XML リテラルと XML 軸プロパティだけで、プレフィックスで修飾された要素または属性の名前には、コードでは、式として使用できます。  
  
### <a name="element-names"></a>要素の名前  
 指定した場合`element`、表している必要があります、*コンテナー要素*、その他の要素を含めることができるプログラミング要素は、です。 コンテナー要素には、クラス、構造体、モジュール、インターフェイス、および列挙が含まれます。  
  
 によって提供される要素のスコープ、`Imports`ステートメントは、指定するかどうかによって異なります`element`します。 だけを指定する場合は、 `namespace`、すべて一意にその名前空間のメンバーとその名前空間内のコンテナー要素のメンバーの名前、修飾なしで利用されます。 両方を指定する場合は、`namespace`と`element`、のみ、その要素のメンバーを修飾なしで使用します。  
  
## <a name="example"></a>例  
 次の例は、<xref:System.IO.DirectoryInfo>クラス</xref:System.IO.DirectoryInfo>を使用して、C:\ ディレクトリ内のすべてのフォルダーを返します  
  
 コードは いいえ`Imports`ステートメントをファイルの先頭にします。 したがって、 `DirectoryInfo`、 <xref:System.Text.StringBuilder>、および<xref:Microsoft.VisualBasic.ControlChars.CrLf>参照はすべて完全修飾名前空間にします</xref:Microsoft.VisualBasic.ControlChars.CrLf></xref:System.Text.StringBuilder>。  
  
 [!code-vb[VbVbalrStatements #&152;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_1.vb)]  
  
## <a name="example"></a>例  
 次の例が含まれます`Imports`参照先の名前空間ステートメントです。 そのため、型は、完全修飾名前空間にするのにはありません。  
  
 [!code-vb[VbVbalrStatements #&153;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_2.vb)]  
  
 [!code-vb[VbVbalrStatements #&154;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_3.vb)]  
  
## <a name="example"></a>例  
 次の例が含まれます`Imports`参照先の名前空間の別名を作成するステートメントです。 種類は、エイリアスを持つ修飾されます。  
  
 [!code-vb[VbVbalrStatements #&155;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_4.vb)]  
  
 [!code-vb[VbVbalrStatements #&156;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_5.vb)]  
  
## <a name="example"></a>例  
 次の例が含まれます`Imports`の参照先の型のエイリアスを作成するステートメントです。 エイリアスを使用して、種類を指定します。  
  
 [!code-vb[VbVbalrStatements #&157;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_6.vb)]  
  
 [!code-vb[VbVbalrStatements #&158;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_7.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Namespace ステートメント](../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [参照と Imports ステートメント](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [Imports ステートメント (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [宣言された要素の参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
