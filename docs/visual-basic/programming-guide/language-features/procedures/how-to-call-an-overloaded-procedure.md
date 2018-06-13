---
title: '方法: オーバーロードされたプロシージャを呼び出す (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: 802a312d6ec6640594f3c6b662202d1ffcf2376d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649127"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a>方法: オーバーロードされたプロシージャを呼び出す (Visual Basic)
プロシージャのオーバー ロードの利点は、呼び出しの柔軟性にです。 呼び出し元のコードは、プロシージャに渡すし、どのような引数が渡されるに関係なく、1 つのプロシージャの名前を呼び出す必要がある情報を取得できます。  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a>1 つ以上のバージョンの定義を持つプロシージャを呼び出しています  
  
1.  呼び出し元のコードでは、プロシージャに渡すデータを決定します。  
  
2.  引数リスト内のデータの表示、通常の方法で、プロシージャの呼び出しを記述します。 必ず、引数、プロシージャに対して定義されているバージョンのいずれかのパラメーター リストに一致します。  
  
3.  呼び出すプロシージャのバージョンを決定する必要はありません。 Visual Basic では、引数リストに一致するバージョンに制御を渡します。  
  
     次の例では、`post`でプロシージャが宣言されて[する方法: 複数のバージョンのプロシージャ定義](./how-to-define-multiple-versions-of-a-procedure.md)です。 顧客 id を取得、かどうかが判断したこと、`String`または`Integer`、し、いずれの場合、同じプロシージャを呼び出します。  
  
     [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [プロシージャのオーバーロード](./procedure-overloading.md)  
 [プロシージャのトラブルシューティング](./troubleshooting-procedures.md)  
 [方法 : プロシージャの複数のバージョンを定義する](./how-to-define-multiple-versions-of-a-procedure.md)  
 [方法 : 省略可能なパラメーターを受け取るプロシージャをオーバーロードする](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [方法 : 不特定数のパラメーターを受け取るプロシージャをオーバーロードする](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [プロシージャのオーバーロードに関する注意事項](./considerations-in-overloading-procedures.md)  
 [オーバーロードの解決](./overload-resolution.md)  
 [オーバーロード](../../../../visual-basic/language-reference/modifiers/overloads.md)
