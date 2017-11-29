---
title: "書き込みを行うと MaximumSize 値を超えてしまうため、ログ ファイルに書き込めません"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrApplicationLog_FileExceedsMaximumSize
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b4d284f9e1a79e409a41aed57ec880fc371b8332
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-cause-it-to-exceed-maximumsize-value"></a>書き込みを行うと MaximumSize 値を超えてしまうため、ログ ファイルに書き込めません
次の理由により、 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> クラスは、ログ ファイルに書き込むことができませんでした。  
  
-   ログ ファイルのサイズ (バイト単位) が <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> プロパティの値より大きい  
  
     —および—  
  
-   <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> プロパティの値が <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>でした。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  既存のログをアーカイブし、それらをコンピューターから削除して、 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> オブジェクトが新しいログを作成できるようにします。  
  
2.  <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> プロパティの値を変更して、より大きなログを作成できるようにします。  
  
3.  <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> プロパティを <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> に設定し、ログが大きすぎる場合は、警告のないメッセージを破棄します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
 [My.Application.Log オブジェクト](../../visual-basic/language-reference/objects/my-application-log-object.md)  
 [My.Log オブジェクト](../../visual-basic/language-reference/objects/my-log-object.md)
