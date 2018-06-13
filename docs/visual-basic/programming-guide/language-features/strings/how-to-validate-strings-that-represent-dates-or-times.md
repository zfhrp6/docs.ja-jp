---
title: '方法: 日付または時刻を表す文字列を検証する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 411c8517783421b2472c3e4aa77287f8252f179b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647863"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>方法: 日付または時刻を表す文字列を検証する (Visual Basic)
次のコード例のセット、`Boolean`文字列が有効な日付または時刻を表しているかどうかを示す値。  
  
## <a name="example"></a>例  
 [!code-vb[VbVbcnRegEx#2](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-strings-that-represent-dates-or-times_1.vb)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 置き換える`("01/01/03")`と`"9:30 PM"`日付と時刻を検証するとします。 ハード コードされた別の文字列、文字列を置き換えることができます、`String`など、文字列を返す変数、またはメソッドで`InputBox`です。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 変換する前に、文字列を検証するには、このメソッドを使用して、`String`を`DateTime`変数。 最初の日付または時刻をチェックする場合は、実行時に例外を生成を回避できます。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Information.IsDate%2A>  
 <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>  
 [Visual Basic における文字列の検証](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
