---
title: "方法: オーバー ロードされたプロシージャ (Visual Basic) を呼び出す |Microsoft ドキュメント"
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
- Visual Basic code, procedures
- procedures, overloading
- procedures, calling
- procedures, multiple versions
- procedure calls, overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
caps.latest.revision: 12
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
ms.openlocfilehash: 0da83aa63bf013d841f2a01a535726f3b03497a1
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a>方法: オーバーロードされたプロシージャを呼び出す (Visual Basic)
プロシージャのオーバー ロードの利点は、呼び出しの柔軟性です。 呼び出し元のコードでは、プロシージャに渡すし、どの引数が渡される、単一のプロシージャ名を呼び出して必要な情報を取得できます。  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a>定義された&1; つ以上のバージョンを持つプロシージャを呼び出す  
  
1.  呼び出し元のコードでは、プロシージャに渡すデータを決定します。  
  
2.  通常の方法では、引数リストで、データを提供することで、プロシージャの呼び出しを記述します。 引数には、プロシージャに対して定義されたバージョンのいずれかのパラメーター リストが一致することをします。  
  
3.  呼び出すプロシージャのバージョンを決定する必要はありません。 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]引数リストに一致するバージョンに制御を渡す。  
  
     次の例では、`post`プロシージャ内で宣言[する方法: 複数のバージョンのプロシージャ定義](./how-to-define-multiple-versions-of-a-procedure.md)します。 顧客 id を取得して、ことがあるかどうかを判定する`String`または`Integer`、し、いずれの場合と同じ手順を呼び出します。  
  
     [!code-vb[VbVbcnProcedures #&56;](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]  
  
     [!code-vb[VbVbcnProcedures #&57;](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)   
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)   
 [プロシージャのオーバー ロード](./procedure-overloading.md)   
 [トラブルシューティングの手順](./troubleshooting-procedures.md)   
 [方法: プロシージャの複数のバージョンを定義します。](./how-to-define-multiple-versions-of-a-procedure.md)   
 [方法: 省略可能なパラメーターを受け取るプロシージャをオーバー ロード](./how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [方法: 不特定数のパラメーターを受け取るプロシージャをオーバー ロード](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [プロシージャのオーバー ロードに関する考慮事項](./considerations-in-overloading-procedures.md)   
 [オーバー ロードの解決](./overload-resolution.md)   
 [オーバーロード](../../../../visual-basic/language-reference/modifiers/overloads.md)
