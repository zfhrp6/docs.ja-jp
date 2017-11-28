---
title: "&#39;です。いずれかの &#39; としてサポートされていません (& a) #39; Declare &#39;ステートメント"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords: BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 59120622688ee38d5b8f45c08dfc3ae40711fb8b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="39as-any39-is-not-supported-in-39declare39-statements"></a>&#39;です。いずれかの &#39; としてサポートされていません (& a) #39; Declare &#39;ステートメント
`Any`データ型と共に使用されました`Declare`任意のデータ型を含む可能性のある引数の使用を許可するには、Visual Basic 6.0 とそれ以前のバージョン内のステートメント。 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]ただし、オーバー ロードをサポートしは、`Any`旧式の型します。  
  
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
