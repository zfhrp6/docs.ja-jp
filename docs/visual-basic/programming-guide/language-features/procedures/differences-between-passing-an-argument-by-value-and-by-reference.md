---
title: 引数の値渡しと参照渡しの違い (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- procedures [Visual Basic], passing arguments
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
ms.openlocfilehash: 4e846c59d3da01d4d9fe943795376c37db4fb397
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651656"
---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a>引数の値渡しと参照渡しの違い (Visual Basic)
プロシージャに 1 つまたは複数の引数を渡す際に、各引数は、基になる呼び出し元のコードでプログラミング要素に対応します。 この基になる要素の値かへの参照を渡すことができます。 これと呼ばれますが、*渡し*です。  
  
## <a name="passing-by-value"></a>値渡し  
 引数を渡す*値によって*を指定して、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)プロシージャの定義でパラメーターに対応するキーワードです。 渡しを使用するときに、Visual Basic はプロシージャ内のローカル変数に、基になるこのプログラミング要素の値をコピーします。 プロシージャのコードには、呼び出し元のコードで、基になる要素へのアクセスがありません。  
  
## <a name="passing-by-reference"></a>参照を渡し  
 引数を渡す*参照によって*を指定して、 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)プロシージャの定義でパラメーターに対応するキーワードです。 この渡すメカニズムを使用して、Visual Basic こと、プロシージャ、基になるこのプログラミング要素への直接参照での呼び出し元のコード。  
  
## <a name="passing-mechanism-and-element-type"></a>引き渡し方法および要素の型  
 引き渡し方法の選択は、基になる要素の型の分類と同じではありません。 値渡しまたは参照渡しで渡すことは、プロシージャのコードに提供する Visual Basic を指します。 値型または参照型は、プログラミング要素をメモリに格納する方法を指します。  
  
 ただし、引き渡し方法および要素の型は相互にします。 参照型の値は、メモリ内の他の場所のデータへのポインターです。 つまり、値によって、参照型を渡す際にプロシージャのコードは、基になる要素のデータへのポインター、基になる要素自体にアクセスできない場合でもです。 たとえば、要素が、配列変数の場合は、プロシージャ コード自体には、変数へのアクセスがありません配列メンバーにアクセスできます。  
  
## <a name="ability-to-modify"></a>変更する機能  
 変更不可能な要素は、引数として渡す、ときに、プロシージャことができますを変更したりしないで、呼び出し元のコードで渡されるかどうか`ByVal`または`ByRef`です。  
  
 変更可能な要素では、次の表は、引き渡し方法、要素の型間の相互作用をまとめたものです。  
  
|要素型|渡されました。 `ByVal`|渡されました。 `ByRef`|  
|------------------|--------------------|--------------------|  
|値の型 (値のみを含む)|プロシージャには、変数またはそのメンバーのいずれかを変更できません。|プロシージャには、変数とそのメンバーを変更できます。|  
|参照型 (クラスまたは構造体のインスタンスへのポインターを含む)|プロシージャは、変数を変更できませんが、ポイントするインスタンスのメンバーを変更できます。|プロシージャには、変数と、ポイントするインスタンスのメンバーを変更できます。|  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)  
 [引数の値渡しと参照渡し](./passing-arguments-by-value-and-by-reference.md)  
 [変更できる引数と変更できない引数の違い](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [方法: プロシージャ引数の値を変更する](./how-to-change-the-value-of-a-procedure-argument.md)  
 [方法: プロシージャ引数の値が変化しないようにする](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [方法: 引数の値渡しを強制する](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [位置と名前による引数渡し](./passing-arguments-by-position-and-by-name.md)  
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
