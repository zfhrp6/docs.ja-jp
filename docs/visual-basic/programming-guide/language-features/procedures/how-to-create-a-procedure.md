---
title: '方法: プロシージャを作成する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: da4cc299fbe35702990a62b5bf824e3ac71d5902
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649264"
---
# <a name="how-to-create-a-procedure-visual-basic"></a>方法: プロシージャを作成する (Visual Basic)
開始宣言ステートメントの間のプロシージャを囲みます (`Sub`または`Function`) と終了の宣言ステートメント (`End Sub`または`End Function`)。 これらのステートメント、プロシージャのすべてのコードの範囲です。  
  
 最初と最後のステートメントが、他のプロシージャの外側にある必要がありますので、プロシージャは別のプロシージャを含めることはできません。  
  
 別の場所で同じタスクを実行するコードがある場合は、プロシージャとして 1 回タスクを記述し、コード内の異なる場所から呼び出すできます。  
  
### <a name="to-create-a-procedure-that-does-not-return-a-value"></a>値を返さないプロシージャを作成するには  
  
1.  その他のすべてのプロシージャの外側を使用して、`Sub`ステートメントの後に、`End Sub`ステートメントです。  
  
2.  `Sub`ステートメントでは、以下の`Sub`パラメーター リストをかっこで、プロシージャの名前を持つキーワード。  
  
3.  間に、プロシージャのコード ステートメントを配置、`Sub`と`End Sub`ステートメントです。  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>値を返すプロシージャを作成するのには  
  
1.  その他のすべてのプロシージャの外側を使用して、`Function`ステートメントの後に、`End Function`ステートメントです。  
  
2.  `Function`ステートメントでは、以下の`Function`パラメーター リストをかっこで、プロシージャの名前を持つキーワードし、`As`戻り値のデータ型を指定する句。  
  
3.  間に、プロシージャのコード ステートメントを配置、`Function`と`End Function`ステートメントです。  
  
4.  使用して、`Return`ステートメントを呼び出し元のコードに値を返します。  
  
### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a>古い、反復的なコード ブロックで、新しいプロシージャを接続するには  
  
1.  古いコードがへのアクセス権を持つ場所に、新しいプロシージャを定義することを確認してください。  
  
2.  反復的な古いコード ブロックで、単一のステートメントを呼び出す反復的なタスクを実行しているステートメントを置き換える、`Sub`または`Function`プロシージャです。  
  
3.  プロシージャで置き換える場合、`Function`値を返す、ある呼び出し元のステートメントが変数に格納するなど、戻り値を使ってアクションを実行するか、値は失われますことを確認します。  
  
## <a name="example"></a>例  
 次`Function`最長側では、やの他の 2 つの辺の値を指定、直角三角形の斜辺を計算します。  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure_1.vb)]  
  
## <a name="see-also"></a>関連項目

 [手順](./index.md)  
 [Sub プロシージャ](./sub-procedures.md)  
 [Function プロシージャ](./function-procedures.md)  
 [Property プロシージャ](./property-procedures.md)  
 [演算子プロシージャ](./operator-procedures.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [再帰プロシージャ](./recursive-procedures.md)  
 [プロシージャのオーバーロード](./procedure-overloading.md)  
 [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [オブジェクト指向プログラミング (Visual Basic)](../../concepts/object-oriented-programming.md)  
