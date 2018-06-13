---
title: Error ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
ms.openlocfilehash: 3ecfe18392de15dc937d90565b49641415dd7e0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603887"
---
# <a name="error-statement"></a>Error ステートメント
エラーの発生をシミュレートします。  
  
## <a name="syntax"></a>構文  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a>指定項目  
 `errornumber`  
 必須。 任意の有効なエラー番号を指定できます。  
  
## <a name="remarks"></a>コメント  
 `Error`ステートメントは、旧バージョンとの互換性のためサポートされます。 オブジェクトを作成するときに特に新しいコードを使用して、`Err`オブジェクトの`Raise`実行時エラーを生成する方法です。  
  
 場合`errornumber`が定義されている、`Error`ステートメントでは、エラー ハンドラーを呼び出し、プロパティの後に、`Err`オブジェクトには、次の既定値が割り当てられます。  
  
|プロパティ|[値]|  
|--------------|-----------|  
|`Number`|引数として指定された値`Error`ステートメントです。 任意の有効なエラー番号を指定できます。|  
|`Source`|現在の Visual Basic プロジェクトの名前です。|  
|`Description`|文字列式の戻り値に対応する、 `Error` 、指定された関数`Number`、この文字列が存在する場合。 文字列が存在しない場合`Description`長さ 0 の文字列が含まれています ("") です。|  
|`HelpFile`|完全修飾のドライブ、パス、および適切な Visual Basic のヘルプ ファイルの名前。|  
|`HelpContext`|コンテキスト ID に対応するエラーを適切な Visual Basic のヘルプ ファイル、`Number`プロパティです。|  
|`LastDLLError`|0 を返します。|  
  
 エラー ハンドラーが存在しないか、エラー メッセージが作成されから表示される場合は、有効でない場合、`Err`オブジェクト プロパティです。  
  
> [!NOTE]
>  Visual Basic ホスト アプリケーションの一部では、オブジェクトを作成できません。 クラスとオブジェクトのどちらを作成できるかどうかを決定は、ホスト アプリケーションのドキュメントを参照してください。  
  
## <a name="example"></a>例  
 この例では、 `Error` 11 のエラー番号を生成するステートメント。  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>要件  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **アセンブリ:** Visual Basic Runtime Library (Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>  
 [On Error ステートメント](../../../visual-basic/language-reference/statements/on-error-statement.md)  
 [Resume ステートメント](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [エラー メッセージ](../../../visual-basic/language-reference/error-messages/index.md)
