---
title: 変更できる引数と変更できない引数の違い (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: 2b60d732b260ad0477946e41ece4cd182de541ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649764"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a>変更できる引数と変更できない引数の違い (Visual Basic)
プロシージャを呼び出すときに通常を 1 つまたは複数の引数を渡します。 各引数は、基になるプログラミング要素に対応しています。 基になる要素と引数の両方には、変更可能または変更不可能なのかを指定できます。  
  
## <a name="modifiable-and-nonmodifiable-elements"></a>変更可能なと変更できない要素  
 プログラミング要素には、いずれかを指定できます、*変更可能な要素*、変更されると、その値であることができます、または*変更不可能*、固定値が作成されています。  
  
 次の表には、変更可能なと変更できないのプログラミング要素が一覧表示します。  
  
|変更可能な要素|変更できない要素|  
|-------------------------|----------------------------|  
|(プロシージャ内で宣言)、ローカル変数が読み取り専用以外のオブジェクト変数を含む|読み取り専用の変数、フィールド、およびプロパティ|  
|読み取り専用以外のフィールド (モジュール、クラス、および構造体のメンバー変数)|定数とリテラル|  
|読み取り専用以外のプロパティ|列挙体メンバー|  
|配列の要素|式 (その要素が変更可能な場合でも)|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a>変更可能なと変更できない引数  
 A*変更可能な引数*は変更可能な基になる要素を持つ 1 つです。 呼び出し元のコードは、いつでも新しい値を格納することができます、引数を渡した場合と[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)プロシージャ内のコードでは、呼び出し元のコード内の基になる要素を変更することもできます。  
  
 A*変更できない引数*変更不可能な基になる要素があるか、渡される[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)です。 プロシージャは、変更可能な要素がある場合でも、呼び出し元のコードでは、基になる要素を変更できません。 変更不可能である場合、呼び出し元コード自体によって変更できません。  
  
 変更では呼び出し元のコード内の基になる要素には影響しませんが、呼び出されたプロシージャ変更できない引数のローカル コピーが変更される可能性があります。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)  
 [引数の値渡しと参照渡し](./passing-arguments-by-value-and-by-reference.md)  
 [引数の値渡しと参照渡しの違い](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [方法: プロシージャ引数の値を変更する](./how-to-change-the-value-of-a-procedure-argument.md)  
 [方法: プロシージャ引数の値が変化しないようにする](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [方法: 引数の値渡しを強制する](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [位置と名前による引数渡し](./passing-arguments-by-position-and-by-name.md)  
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
