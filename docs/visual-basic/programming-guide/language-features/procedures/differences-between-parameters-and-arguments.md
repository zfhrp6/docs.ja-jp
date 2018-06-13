---
title: パラメーターと引数の違い (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- parameters [Visual Basic], and arguments
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], and parameters
- procedure parameters
- parameters [Visual Basic], definition
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
ms.openlocfilehash: a5075c218371b754ac883b97475ab941811966b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650687"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a>パラメーターと引数の違い (Visual Basic)
ほとんどの場合、プロシージャが呼び出されたときの状況に関する情報が必要です。 繰り返しまたは共有のタスクを実行する手順は、呼び出しごとに異なる情報を使用します。 この情報は、変数、定数、およびメソッドを呼び出すときに、プロシージャに渡す式で構成されます。  
  
 プロシージャの定義、プロシージャにこの情報を通信するために、*パラメーター*、呼び出し元のコードに渡すと、*引数*そのパラメーターにします。 駐車場パラメーターと引数は、自動車を検討することができます。 な車は、異なる時刻で駐車場駐車できる、同様呼び出し元のコードは、するには、プロシージャが呼び出されるたびに同じパラメーターに別の引数を渡すことができます。  
  
## <a name="parameters"></a>パラメーター  
 A*パラメーター*プロシージャには、このメソッドを呼び出すときに渡すことが期待される値を表します。 プロシージャの宣言では、そのパラメーターを定義します。  
  
 定義するとき、`Function`または`Sub`プロシージャを指定する、*パラメーター リスト*プロシージャ名をすぐに続くかっこにします。 各パラメーターの名前、データ型、および引き渡し方法を指定 ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md))。 パラメーターが省略可能であることもあります。 これは、値を渡すことを呼び出し元のコードがないことを意味します。  
  
 各パラメーターの名前を果たす、*ローカル変数*の手順でします。 パラメーター名を使用すると、他の変数を使用するのと同様にします。  
  
## <a name="arguments"></a>引数  
 *引数*プロシージャを呼び出す場合、プロシージャのパラメーターに渡す値を表します。 呼び出し元のコードは、プロシージャを呼び出すときに、引数を指定します。  
  
 呼び出すと、`Function`または`Sub`が含まれて、プロシージャには、*引数リスト*プロシージャ名をすぐに続くかっこ内です。 各引数は、一覧内の同じ位置でのパラメーターに対応します。  
  
 パラメーターの定義とは対照的引数には名前がありません。 各引数は、ゼロまたは複数の変数、定数、およびリテラルに含めることができる式です。 式の評価結果のデータ型が、対応するパラメーターに対して定義されているデータ型に一致することは通常、パラメーターの型に変換可能ないずれの場合もあります。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)  
 [Sub プロシージャ](./sub-procedures.md)  
 [Function プロシージャ](./function-procedures.md)  
 [Property プロシージャ](./property-procedures.md)  
 [演算子プロシージャ](./operator-procedures.md)  
 [方法 : プロシージャにパラメーターを定義する](./how-to-define-a-parameter-for-a-procedure.md)  
 [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)  
 [引数の値渡しと参照渡し](./passing-arguments-by-value-and-by-reference.md)  
 [再帰プロシージャ](./recursive-procedures.md)  
 [プロシージャのオーバーロード](./procedure-overloading.md)
