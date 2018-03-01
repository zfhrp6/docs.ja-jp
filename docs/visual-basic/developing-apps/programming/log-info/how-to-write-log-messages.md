---
title: "方法: ログ メッセージを書き込む (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Application.Log object, writing log messags
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ae4d875fd4f95ca51fff565551009e780b17d07a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-log-messages-visual-basic"></a>方法: ログ メッセージを書き込む (Visual Basic)
`My.Application.Log` オブジェクトおよび `My.Log` オブジェクトを使用すると、アプリケーションに関する情報をログに記録できます。 この例では、 `My.Application.Log.WriteEntry` メソッドを使用してトレース情報をログに記録する方法を示します。  
  
 例外情報をログに記録するには、`My.Application.Log.WriteException` メソッドを使います。方法については、「[方法 : 例外をログに記録する](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)」をご覧ください。  
  
## <a name="example"></a>例  
 この例では、 `My.Application.Log.WriteEntry` メソッドを使用してトレース情報を書き込みます。  
  
 [!code-vb[VbVbalrMyApplicationLog#11](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-write-log-messages_1.vb)]  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 ログに書き込むデータに、ユーザーのパスワードなどの機密情報が含まれないように注意してください。 詳しくは、「[アプリケーション ログの使用](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [アプリケーション ログの使用](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [方法 : 例外をログに記録する](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [チュートリアル : My.Application.Log による情報の書き込み先の確認](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
 [チュートリアル : My.Application.Log による情報の書き込み先の変更](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 [チュートリアル : My.Application.Log の出力をフィルター処理する](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)
