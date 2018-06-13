---
title: REM ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
helpviewer_keywords:
- REM statement [Visual Basic]
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
ms.openlocfilehash: 3bd526b08e1ba3be856e1e823cf8ef49ea9b6c97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604277"
---
# <a name="rem-statement-visual-basic"></a>REM ステートメント (Visual Basic)
プログラムのソース コードにコメントを記述するために使用します。  
  
## <a name="syntax"></a>構文  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a>指定項目  
 `comment`  
 任意。 含めるコメントのテキストです。 スペースは間で必要な`REM`キーワードと`comment`です。  
  
## <a name="remarks"></a>コメント  
 配置することができます、`REM`するか、行に単独でステートメントを使用すると別のステートメントを次の行に記述できます。 `REM`ステートメントは行の最後のステートメントである必要があります。 別のステートメントが続く場合、`REM`からそのステートメントをスペースで区切る必要があります。  
  
 単一引用符を使用することができます (`'`) の代わりに`REM`です。 これはコメントが同じ行の別のステートメントに依存してまたはを行に単独で上に存在するかどうかに当てはまります。  
  
> [!NOTE]
>  続行することはできません、`REM`行連結シーケンスを使用してステートメント (`_`)。 コメントが開始されると、コンパイラは特別な意味の文字を検査しません。 複数行にコメントを記述する場合は、別の操作を使用して`REM`ステートメントまたはコメント記号 (`'`) 行ごとにします。  
  
## <a name="example"></a>例  
 次の例を示しています、`REM`ステートメントでは、プログラムにコメントを記述するために使用します。 単一引用符文字を使用する方法も示しています (`'`) の代わりに`REM`です。  
  
 [!code-vb[VbVbalrStatements#6](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/rem-statement_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [コード内のコメント](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 [方法 : コード内でステートメントを分割および連結する](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
