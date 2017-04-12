---
title: "XML ファイル (Visual Basic) の処理 |Microsoft ドキュメント"
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
- XML comments, parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 72b2832d0131adf39a37ebd9297b43fb34ea49ba
ms.lasthandoff: 03/13/2017

---
# <a name="processing-the-xml-file-visual-basic"></a>XML ファイルの処理 (Visual Basic)
コンパイラでは、ドキュメントを生成するタグが付けられて、コードの中に各構成体の ID 文字列が生成されます。 (コードをタグ付けする方法については、次を参照してください[XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)。)。ID 文字列は、構成要素を一意に識別します。 XML ファイルを処理するプログラムは、対応するを識別する ID 文字列を使用して[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]メタデータ/リフレクション項目。  
  
 XML ファイルは、コードの階層的な表現ではありません。単純なリストの各要素に対して生成された ID を使用することをお勧めします。  
  
 コンパイラは、次の規則をに基づいて ID 文字列を生成します。  
  
-   文字列に空白文字は適用されません。  
  
-   ID 文字列の最初の部分では、一文字、コロンで識別されるメンバーの種類を識別します。 次のメンバーの型が使用されます。  
  
|文字|説明|  
|---|---|  
|N|namespace<br /><br /> ドキュメント コメントを名前空間に追加することはできませんが、CREF 参照を行うことができます、サポートされている場合。|  
|T|type: `Class`, `Module`, `Interface`, `Structure`, `Enum`,`Delegate`|  
|F|フィールド:`Dim`|  
|P|プロパティ: `Property` (既定のプロパティを含む)|  
|M|method: `Sub`, `Function`, `Declare`,`Operator`|  
|E|イベント:`Event`|  
|!|エラー文字列<br /><br /> 文字列の残りの部分では、エラーに関する情報を提供します。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラが解決できないリンクのエラー情報を生成します。|  
  
-   第&2; 部、 `String` 、名前空間のルートにある項目の完全修飾の名前を指定します。 アイテム、その外側の型、および名前空間の名前は、ピリオドで区切られます。 項目自体の名前にピリオドが含まれている場合、それらはシャープ記号で置き換えられます。 (#)。 項目の名前には、番号記号がないことが前提です。 たとえば、完全修飾名の`String`コンス トラクターになる`System.String.#ctor`します。  
  
-   プロパティとメソッドは、メソッドの引数がある場合、引数リストをかっこで囲まれたをたどります。 引数がない場合は、かっこは存在しません。 引数は、コンマで区切られます。 エンコード方法に直接依存各引数のエンコーディング、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]署名します。  
  
## <a name="example"></a>例  
 次のコードは、クラスの ID 文字列がどのようにあり、そのメンバーが生成されます。  
  
 [!code-vb[VbVbcnXmlDocComments&#10;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/processing-the-xml-file_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)   
 [方法: XML ドキュメントを作成する](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
