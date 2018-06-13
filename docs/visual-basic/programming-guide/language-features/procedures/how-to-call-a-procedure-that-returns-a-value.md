---
title: '方法: 値を返すプロシージャを呼び出す (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 35f757609b6d0b36652db3b14e62ecd299a063ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649413"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>方法: 値を返すプロシージャを呼び出す (Visual Basic)
A`Function`プロシージャが呼び出し元のコードに値を返します。 これを呼び出す、名前と引数を含む式、または代入ステートメントの右側にあるいずれか。  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>式の中で関数のプロシージャを呼び出しています  
  
1.  使用して、`Function`プロシージャ名の変数を使用すると同じ方法です。 使用することができます、`Function`プロシージャを呼び出す任意の場所の変数または定数を式で使用できます。  
  
2.  プロシージャ名を引数リストを囲むかっこに従ってください。 引数がない場合は、かっこを省略することができます。 ただし、かっこを使用して、コードを読みやすくします。  
  
3.  コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。 同じ順序で引数を指定する必要がありますする、`Function`プロシージャが、対応するパラメーターを定義します。  
  
     また、名前で 1 つまたは複数の引数を渡すことができます。 詳細については、次を参照してください。[位置と名前による引数を渡す](./passing-arguments-by-position-and-by-name.md)です。  
  
4.  プロシージャから返される値、変数の値と同様に、式または定数します。  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>プロシージャを呼び出す関数、代入ステートメントで  
  
1.  使用して、`Function`プロシージャ名の後に続く (`=`) 代入ステートメントにサインインします。  
  
2.  プロシージャ名を引数リストを囲むかっこに従ってください。 引数がない場合は、かっこを省略することができます。 ただし、かっこを使用して、コードを読みやすくします。  
  
3.  コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。 同じ順序で引数を指定する必要がありますする、`Function`名前で渡すことがない限り、プロシージャが、対応するパラメーターを定義します。  
  
4.  プロシージャから返される値は、変数または代入ステートメントの左側にあるプロパティに格納されます。  
  
## <a name="example"></a>例  
 次の例では、Visual Basic<xref:Microsoft.VisualBasic.Interaction.Environ%2A>オペレーティング システム環境変数の値を取得します。 最初の行呼び出し`Environ`代入ステートメントでその行の式、および 2 つ目の呼び出しです。 `Environ` その唯一の引数として変数名を使用します。 呼び出し元のコードに変数の値を返します。  
  
 [!code-vb[VbVbcnProcedures#7](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Function プロシージャ](./function-procedures.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [方法 : 値を返すプロシージャを作成する](./how-to-create-a-procedure-that-returns-a-value.md)  
 [方法 : プロシージャから値を返す](./how-to-return-a-value-from-a-procedure.md)  
 [方法 : 値を返さないプロシージャを呼び出す](./how-to-call-a-procedure-that-does-not-return-a-value.md)
