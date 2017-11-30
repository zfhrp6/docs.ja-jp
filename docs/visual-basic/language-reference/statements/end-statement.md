---
title: "End ステートメント"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.End
- End
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- End keyword [Visual Basic], End statements
- programs [Visual Basic], quitting
- code, exiting
- program termination
- End statement [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b692409f2895f5e9b713c57fc35ff2def40bce75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="end-statement"></a>End ステートメント
すぐに実行を終了します。  
  
## <a name="syntax"></a>構文  
  
```  
End  
```  
  
## <a name="remarks"></a>コメント  
 配置することができます、`End`ステートメント、プロシージャを強制的に実行を停止するアプリケーション全体で任意の場所。 `End`使用して開いたファイルをすべて閉じます、`Open`ステートメントと、アプリケーションのすべての変数を消去します。 コードが実行されている、そのオブジェクトへの参照を保持している他のプログラムがないとすぐにアプリケーションを閉じます。  
  
> [!NOTE]
>  `End`ステートメントが突然、コードの実行を停止しは呼び出されません、`Dispose`または`Finalize`メソッド、またはその他の Visual Basic コードです。 その他のプログラムによって保持されているオブジェクトの参照が無効になります。 場合、`End`内でステートメントが検出された、`Try`または`Catch`ブロック、コントロールに対応する渡しません`Finally`ブロックします。  
  
 `Stop`ステートメントのとは異なりの実行が中断`End`、任意のファイルを閉じておよびコンパイル済み実行可能 (.exe) ファイルで検出された場合を除き、任意の変数をクリアされません。  
  
 `End`を推進せずアプリケーションを終了させるを閉じるためクリーンに使用する前に開いている可能性があるすべてのリソースを試してください。 たとえば、アプリケーションのすべてのフォームを開く場合を閉じる必要がありますにコントロールに到達する前に、`End`ステートメントです。  
  
 使用する必要があります`End`限り注意して、必要なときにすぐに停止します。 プロシージャを終了する通常の方法 ([Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)と[Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)) だけでなく、プロシージャを正常に終了しますが、も呼び出し元のコードに正常に閉じるための機会を提供します。 コンソール アプリケーションはたとえば、単にできます`Return`から、`Main`プロシージャです。  
  
> [!IMPORTANT]
>  `End`ステートメントの呼び出し、<xref:System.Environment.Exit%2A>のメソッド、<xref:System.Environment>クラス内で、<xref:System>名前空間。 <xref:System.Environment.Exit%2A>必要に`UnmanagedCode`権限です。 そうしない場合、<xref:System.Security.SecurityException>エラーが発生します。  
  
 追加のキーワードが続くと[終了\<キーワード > ステートメント](../../../visual-basic/language-reference/statements/end-keyword-statement.md)適切なプロシージャまたはブロックの定義の最後のようになります。 たとえば、`End Function`の定義を終了、`Function`プロシージャです。  
  
## <a name="example"></a>例  
 次の例では、`End`をユーザーが要求した場合、コードの実行を終了するステートメント。  
  
 [!code-vb[VbVersHelp60Controls#64](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/end-statement_1.vb)]  
  
## <a name="smart-device-developer-notes"></a>スマート デバイスの開発者向け注意事項  
 このステートメントはサポートされていません。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Security.Permissions.SecurityPermissionFlag>  
 [Stop ステートメント](../../../visual-basic/language-reference/statements/stop-statement.md)  
 [終了\<キーワード > ステートメント](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
