---
title: '&#39;いずれかとして&#39;でサポートされていない&#39;Declare&#39;ステートメント'
ms.date: 07/20/2015
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
ms.openlocfilehash: 34beaeb7178645d5a167d1b7b969bb3e4f500e1a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588227"
---
# <a name="39as-any39-is-not-supported-in-39declare39-statements"></a>&#39;いずれかとして&#39;でサポートされていない&#39;Declare&#39;ステートメント
`Any`データ型と共に使用されました`Declare`任意のデータ型を含む可能性のある引数の使用を許可するには、Visual Basic 6.0 とそれ以前のバージョン内のステートメント。 オーバー ロード、ただし、Visual Basic サポートされため、`Any`古いデータを入力します。  
  
 **エラー ID:** BC30828  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  を使用する特定の型のパラメーターを宣言します。例えば。  
  
     [!code-vb[VbVbalrStatements#95](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_1.vb)]  
  
2.  使用して、<xref:System.Runtime.InteropServices.MarshalAsAttribute>を指定する属性`As Any`とき`Void*`が呼び出されるプロシージャで想定されています。  
  
     [!code-vb[VbVbalrStatements#96](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [チュートリアル : Windows API の呼び出し](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [マネージ コードでのプロトタイプの作成](../../../framework/interop/creating-prototypes-in-managed-code.md)
