---
title: "方法: 値 (Visual Basic) を返すプロシージャを呼び出す |Microsoft ドキュメント"
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
- procedure calls, returning values
- Visual Basic code, procedures
- procedures, calling
- procedures, returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
caps.latest.revision: 15
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
ms.openlocfilehash: df6bb1ed8acf5f86a290d67fec9c053cfe5245d2
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>方法: 値を返すプロシージャを呼び出す (Visual Basic)
A`Function`プロシージャが呼び出し元のコードに値を返します。 名前に、名前と引数を含めることによって、代入ステートメントまたは式の右側にあるいずれかです。  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>式の中で関数のプロシージャを呼び出す  
  
1.  使用して、`Function`プロシージャ名の変数を使用すると同じ方法です。 使用することができます、`Function`プロシージャを呼び出す任意の場所が式の中で変数または定数を使用することができます。  
  
2.  次のプロシージャ名の引数リストを囲むかっこを使用します。 引数がない場合は、かっこを省略することができます。 ただし、かっこを使用して、コードを読みやすくします。  
  
3.  コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。 同じ順序で引数を指定する必要があります`Function`プロシージャは、対応するパラメーターを定義します。  
  
     または、名前によって&1; つまたは複数の引数を渡すことができます。 詳細については、次を参照してください。[位置と名前による引数を渡す](./passing-arguments-by-position-and-by-name.md)します。  
  
4.  プロシージャから返される値、変数の値と同じように式または定数します。  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>プロシージャを呼び出す関数、代入ステートメントで  
  
1.  使用して、`Function`プロシージャ名の後に続く (`=`) 代入ステートメントは、サインインします。  
  
2.  次のプロシージャ名の引数リストを囲むかっこを使用します。 引数がない場合は、かっこを省略することができます。 ただし、かっこを使用して、コードを読みやすくします。  
  
3.  コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。 同じ順序で引数を指定する必要があります`Function`名で渡すことがない限り、プロシージャが対応するパラメーターを定義します。  
  
4.  プロシージャから返される値は、変数または代入ステートメントの左側にあるプロパティに格納されます。  
  
## <a name="example"></a>例  
 次の例では、 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.Environ%2A>、オペレーティング システム環境変数の値を取得します</xref:Microsoft.VisualBasic.Interaction.Environ%2A>。 最初の行呼び出し`Environ`代入ステートメントでその行の式であり、2 番目の呼び出しです。 `Environ`単一の引数として変数名を取得します。 呼び出し元のコードに変数の値を返します。  
  
 [!code-vb[VbVbcnProcedures&#7;](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Function プロシージャ](./function-procedures.md)   
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)   
 [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [方法: 値を返すプロシージャを作成します。](./how-to-create-a-procedure-that-returns-a-value.md)   
 [方法: プロシージャから値を返す](./how-to-return-a-value-from-a-procedure.md)   
 [方法 : 値を返さないプロシージャを呼び出す](./how-to-call-a-procedure-that-does-not-return-a-value.md)
