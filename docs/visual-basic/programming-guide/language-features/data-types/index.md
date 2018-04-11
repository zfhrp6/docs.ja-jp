---
title: Visual Basic におけるデータ型
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data types [Visual Basic], declaring
- typing
- data types [Visual Basic]
- Visual Basic code, data types
- data types [Visual Basic], improving speed with
ms.assetid: 5e1b9aaf-c7ca-4b29-9b22-0e82ed8e85e2
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 20a24c8632e1f2193cfa86319a824dfcc038d9d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="data-types-in-visual-basic"></a>Visual Basic におけるデータ型
プログラミング要素の*データ型*は、保持できるデータの種類やデータの格納方法を示します。 データ型は、コンピューターのメモリに格納できるすべての値に適用され、式の評価にも関与します。 変数、リテラル、定数、列挙値、プロパティ、プロシージャのパラメーター、プロシージャの引数、およびプロシージャの戻り値にはすべてデータ型があります。  
  
## <a name="declared-data-types"></a>宣言済みデータ型  
 プログラミング要素は、宣言ステートメントで定義し、`As` 句を使用してデータ型を指定します。 次の表は、さまざまな要素の宣言に使用するステートメントを示しています。  
  
|プログラミング要素|データ型の宣言|  
|-------------------------|---------------------------|  
|変数|[Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)<br /><br /> `Dim`   `amount As Double`<br /><br /> `Static`   `yourName As String`<br /><br /> `Public`   `billsPaid As Decimal = 0`|  
|Literal|リテラルの型文字で指定する場合は、「[Type Characters (型文字)](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)」の「Literal Type Characters (リテラルの型文字)」を参照してください<br /><br /> `Dim searchChar As Char = "."`  `C`|  
|定数|[Const ステートメント](../../../../visual-basic/language-reference/statements/const-statement.md)<br /><br /> `Const`   `modulus As Single = 4.17825F`|  
|列挙|[Enum ステートメント](../../../../visual-basic/language-reference/statements/enum-statement.md)<br /><br /> `Public`   `Enum`   `colors`|  
|プロパティ|[Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)<br /><br /> `Property`   `region() As String`|  
|プロシージャ パラメーター|[Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)、[Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)、または[Operator ステートメント](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Sub addSale(ByVal`   `amount`   `As Double)`|  
|プロシージャ引数|呼び出しコードの各引数は、すでに宣言されているプログラミング要素、または宣言されている要素を含む式です<br /><br /> `subString = Left(`  `inputString`  `,`   `5`  `)`|  
|プロシージャの戻り値|[Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)、または[Operator ステートメント](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Function convert(ByVal b As Byte)`   `As String`|  
  
 Visual Basic のデータ型の一覧については、[データ型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)に関するページをご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [型文字](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [複合データ型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Visual Basic におけるジェネリック型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Visual Basic での型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [構造体](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [タプル](tuples.md)     
 [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [データの種類](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [データ型の有効な使用方法](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
