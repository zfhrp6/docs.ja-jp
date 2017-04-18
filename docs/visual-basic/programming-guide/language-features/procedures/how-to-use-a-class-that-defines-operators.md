---
title: "方法: 演算子 (Visual Basic) を定義するクラスを使用して |Microsoft ドキュメント"
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
- operator procedures, calling
- procedures, operator
- procedures, calling
- examples [Visual Basic], CType
- syntax, Operator procedures
- operators [Visual Basic], overloading
- return values, Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
caps.latest.revision: 21
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
ms.openlocfilehash: b1db7c0b2a6fd8160baa48892b5f2214df24674e
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>方法: 演算子を定義するクラスを使用する (Visual Basic)
クラスまたは独自の演算子を定義する構造体を使用している場合からこれらの演算子をアクセスすることができます[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。  
  
 クラスまたは構造体で、演算子を定義することと呼ばれる*オーバー ロード*演算子。  
  
## <a name="example"></a>例  
 次の例では、SQL 構造<xref:System.Data.SqlTypes.SqlString>、変換演算子を定義する ([CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md))、SQL 文字列の両方向で、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]文字列</xref:System.Data.SqlTypes.SqlString>。 使用`CType(` *SQL 文字列式*、`String)`への SQL 文字列に変換する、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]文字列、および`CType(` *Visual Basic の文字列式*、<xref:System.Data.SqlTypes.SqlString>`)`逆方向に変換する</xref:System.Data.SqlTypes.SqlString>。  
  
 [!code-vb[VbVbcnProcedures #&30;](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]  
  
 [!code-vb[VbVbcnProcedures #&31;](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]  
  
 <xref:System.Data.SqlTypes.SqlString>構造体定義の変換演算子 ([CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)) から`String`に<xref:System.Data.SqlTypes.SqlString>とから<xref:System.Data.SqlTypes.SqlString>に`String`</xref:System.Data.SqlTypes.SqlString></xref:System.Data.SqlTypes.SqlString></xref:System.Data.SqlTypes.SqlString>。 代入するステートメント`title`に`jobTitle`では、最初の演算子では、使用、および<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>関数の呼び出しは、もう&1; つを使用して</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 使用する演算子を定義、クラスまたは構造体を使用していることを確認します。 クラスまたは構造体と、オーバー ロード可能なすべてのオペレーターが定義されているとは限りません。 使用可能な演算子の一覧は、次を参照してください。 [Operator ステートメント](../../../../visual-basic/language-reference/statements/operator-statement.md)します。  
  
 含める、適切な`Imports`ソース ファイルの先頭に、SQL 文字列の文 (ここで<xref:System.Data.SqlTypes>).</xref:System.Data.SqlTypes>  
  
 プロジェクトは、System.Data および System.XML への参照が必要です。  
  
## <a name="see-also"></a>関連項目  
 [演算子プロシージャ](./operator-procedures.md)   
 [方法: 演算子を定義](./how-to-define-an-operator.md)   
 [方法: 変換演算子を定義します。](./how-to-define-a-conversion-operator.md)   
 [方法: 演算子プロシージャを呼び出す](./how-to-call-an-operator-procedure.md)   
 [拡大変換](../../../../visual-basic/language-reference/modifiers/widening.md)   
 [縮小変換](../../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Structure ステートメント](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [方法: 構造体を宣言](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [明示的および暗黙的な変換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
