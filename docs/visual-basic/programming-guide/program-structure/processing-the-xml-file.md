---
title: XML ファイルの処理 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: 6be7597f1c03d8aa044eba70ef6287cfc07d9b84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="processing-the-xml-file-visual-basic"></a>XML ファイルの処理 (Visual Basic)
コンパイラは、ドキュメントを生成するためにタグ付けされたコードのコンストラクトごとに、ID 文字列を生成します。 (コードをタグ付けする方法については、次を参照してください[XML コメント タグ](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)。)。ID 文字列によって、コンストラクトは一意に識別されます。 XML ファイルを処理するプログラムが、対応するを識別する ID 文字列を使用して[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]メタデータ/リフレクション項目。  
  
 XML ファイルは、コードの階層的な表現ではありません。単純なリストの各要素に対して生成された ID を使用することをお勧めします。  
  
 コンパイラは、次の規則に基づいて ID 文字列を生成します。  
  
-   文字列内の空白文字は配置されません。  
  
-   ID 文字列の最初の部分では、その後にコロン、1 文字で識別されるメンバーの種類を識別します。 次のメンバーの種類が使用されます。  
  
|文字|説明|  
|---|---|  
|N|namespace<br /><br /> 名前空間にドキュメント コメントを追加することはできませんが、それらを CREF 参照を行うことができます、サポートされている場合。|  
|T|型: `Class`、 `Module`、 `Interface`、 `Structure`、 `Enum`、 `Delegate`|  
|F|フィールド: `Dim`|  
|P|プロパティ: `Property` (既定のプロパティを含む)|  
|M|方法: `Sub`、 `Function`、 `Declare`、 `Operator`|  
|E|イベント: `Event`|  
|!|エラー文字列<br /><br /> あとに続く文字列で、エラーの情報を示します。 Visual Basic コンパイラでは、解決できないリンクのエラー情報を生成します。|  
  
-   2 番目の部分、 `String` 、名前空間のルートにある項目の完全修飾の名前を指定します。 アイテム、その外側の型、および名前空間の名前は、ピリオドで区切られます。 項目自体の名前にピリオドが含まれている場合は、置き換えられるシャープ記号 (#)。 項目の名前には、番号記号がないことが前提です。 たとえば、完全修飾名の`String`コンス トラクターになる`System.String.#ctor`です。  
  
-   プロパティおよびメソッドについては、メソッドに引数がある場合は、引数のリストをかっこで囲み、メソッドに続けて指定します。 引数がない場合は、かっこはありません。 引数はコンマで区切られます。 エンコード方法に直接依存引数はそれぞれのエンコード、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]署名します。  
  
## <a name="example"></a>例  
 次のコードは、クラスの ID の文字列し、そのメンバーが生成されます。  
  
 [!code-vb[VbVbcnXmlDocComments#10](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/processing-the-xml-file_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [方法: XML ドキュメントを作成する](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
