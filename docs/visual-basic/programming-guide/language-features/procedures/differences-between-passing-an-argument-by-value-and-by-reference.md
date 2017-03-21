---
title: "引数値渡しと参照渡し (Visual Basic) の相違点 |Microsoft ドキュメント"
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
- ByRef keyword, passing arguments by reference
- Visual Basic code, procedures
- procedures, passing arguments
- ByVal keyword, passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
caps.latest.revision: 14
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
ms.openlocfilehash: 93c515dd8524cde85555a27879baee00185f78e3
ms.lasthandoff: 03/13/2017

---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a>引数の値渡しと参照渡しの違い (Visual Basic)
プロシージャに&1; つまたは複数の引数を渡すときに、各引数は、呼び出し元のコード内の基になるプログラミング要素に対応します。 この基になる要素の値またはへの参照を渡すことができます。 これと呼ばれますが、*渡し*します。  
  
## <a name="passing-by-value"></a>値渡し  
 引数を渡す*値によって*を指定して、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)プロシージャ定義でパラメーターに対応するキーワードです。 これを使用するメカニズムを渡すときに[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]の手順でローカル変数に基になるプログラミング要素の値をコピーします。 プロシージャのコードには、呼び出し元のコード内の基になる要素へのアクセスがありません。  
  
## <a name="passing-by-reference"></a>参照による受け渡し  
 引数を渡す*参照によって*を指定して、 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)プロシージャ定義でパラメーターに対応するキーワードです。 これを使用するメカニズムを渡すときに[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]呼び出し元のコードで、手順、基になるプログラミング要素への直接参照を提供します。  
  
## <a name="passing-mechanism-and-element-type"></a>引数渡しの方法および要素の型  
 渡す機能の選択は、基になる要素の型の分類と同じではありません。 値渡しまたは参照渡しか参照何[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プロシージャ コードに提供します。 値型または参照型は、メモリ内プログラミング要素を格納する方法を参照します。  
  
 ただし、引き渡し方法および要素の型は相互にします。 参照型の値は、メモリ内の他の場所でのデータへのポインターです。 つまり、基になる要素自体にアクセスできない場合でも値が参照型を渡すときにプロシージャ コードが基になる要素のデータへのポインターを持っています。 など、要素が、配列変数の場合は、プロシージャのコードでは、変数自体にアクセスできないが、配列メンバーにアクセスできます。  
  
## <a name="ability-to-modify"></a>変更する権限  
 引数として、変更不可能な要素を渡すときに、手順変更できません呼び出し元のコードに渡されるかどうか`ByVal`または`ByRef`です。  
  
 変更可能な要素には、次の表は、要素の型と渡し間のやり取りを示します。  
  
|要素型|渡されました。`ByVal`|渡されました。`ByRef`|  
|------------------|--------------------|--------------------|  
|値型 (値のみを含む)|プロシージャには、変数、またはそのメンバーを変更できません。|プロシージャには、変数とそのメンバーを変更できます。|  
|参照型 (クラスまたは構造体のインスタンスへのポインターが含まれています)|プロシージャは、変数を変更できませんが、指すインスタンスのメンバーを変更できます。|プロシージャには、変数と、ポイントするインスタンスのメンバーを変更できます。|  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)   
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)   
 [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)   
 [値渡しと参照による引数渡し](./passing-arguments-by-value-and-by-reference.md)   
 [引数と変更できない引数の違い](./differences-between-modifiable-and-nonmodifiable-arguments.md)   
 [方法: プロシージャ引数の値を変更します。](./how-to-change-the-value-of-a-procedure-argument.md)   
 [方法: プロシージャ引数の値は変更しないように](./how-to-protect-a-procedure-argument-against-value-changes.md)   
 [方法: 引数値渡しを強制します。](./how-to-force-an-argument-to-be-passed-by-value.md)   
 [位置と名前による引数渡し](./passing-arguments-by-position-and-by-name.md)   
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
