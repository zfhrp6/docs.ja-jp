---
title: "Call ステートメント (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c72450fd6f931f36f640d3e384a6fd38d57a7a23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="call-statement-visual-basic"></a>Call ステートメント (Visual Basic)
転送コントロールを`Function`、 `Sub`、またはダイナミック リンク ライブラリ (DLL) プロシージャです。  
  
## <a name="syntax"></a>構文  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a>指定項目  
 `procedureName`  
 必須です。 呼び出すプロシージャの名前。  
  
 `argumentList`  
 省略可能です。 変数または呼び出された場合、プロシージャに渡される引数を表す式の一覧です。 複数の引数は、コンマで区切られます。 含める場合`argumentList`かっこで囲む必要があります。  
  
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
