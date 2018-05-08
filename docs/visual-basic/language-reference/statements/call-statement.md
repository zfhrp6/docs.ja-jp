---
title: Call ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
ms.openlocfilehash: 2074f44aedf59f1570e73c898a9bf64e57034923
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="call-statement-visual-basic"></a>Call ステートメント (Visual Basic)
転送コントロールを`Function`、 `Sub`、またはダイナミック リンク ライブラリ (DLL) プロシージャです。  
  
## <a name="syntax"></a>構文  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a>指定項目  
 `procedureName`  
 必須。 呼び出すプロシージャの名前。  
  
 `argumentList`  
 任意。 変数または呼び出された場合、プロシージャに渡される引数を表す式の一覧です。 複数の引数は、コンマで区切られます。 含める場合`argumentList`かっこで囲む必要があります。  
  
## <a name="remarks"></a>コメント  
 使用することができます、`Call`キーワード、プロシージャを呼び出すときにします。 ほとんどのプロシージャ呼び出しのためには、このキーワードを使用する必要はありません。  
  
 通常使用する、`Call`キーワードと呼ばれる式は、識別子で開始しない場合。 使用、`Call`キーワードの他の使用はお勧めしません。  
  
 プロシージャは、値を返す場合、`Call`ステートメントにそれを廃棄します。  
  
## <a name="example"></a>例  
 次のコードは、2 つの例を示しています。 ここで、`Call`キーワードは、プロシージャを呼び出す必要です。 どちらの例では、呼び出された式は識別子で開始しません。  
  
 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
