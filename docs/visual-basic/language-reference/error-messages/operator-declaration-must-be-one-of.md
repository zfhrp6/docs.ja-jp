---
title: '演算子の宣言は、のいずれかを指定する必要があります: +、-、*、-、-、^、 &amp;、Like、Mod、および、Or、Xor、Not、 &lt; &lt;、 &gt; &gt;、=、 &lt; &gt;、 &lt;、 &lt;=、 &gt;、 &gt;=、CType、IsTrue、または IsFalse'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 80c8358dd13105c18e73e94735a51b02d5bd22c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not-ltlt-gtgt"></a>演算子の宣言は、のいずれかを指定する必要があります: +、-、*、\,/、^、 &amp;、Like、Mod、および、Or、Xor、Not、 &lt; &lt;、 &gt;&gt;しています.
オーバー ロードできるは、演算子のみを宣言することができます。 次の表には、宣言できる演算子が一覧表示します。  
  
|型|演算子|  
|----------|---------------|  
|単項|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|2 項|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|変換 (単項)|`CType`|  
  
 なお、 `=` 2 項の一覧で演算子は、比較演算子、代入演算子ではありません。  
  
 **エラー ID:** BC33000  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  演算子をオーバーロード可能な演算子の中から選択します。  
  
2.  直接オーバーロードできない演算子をオーバーロードする機能が必要な場合は、適切なパラメーターを受け取り適切な値を返す `Function` プロシージャを作成します。  
  
## <a name="see-also"></a>関連項目  
 [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [方法 : 演算子を定義する](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [方法 : 変換演算子を定義する](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)
