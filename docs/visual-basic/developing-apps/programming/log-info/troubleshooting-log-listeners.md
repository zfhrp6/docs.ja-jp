---
title: "トラブルシューティング: ログ リスナー (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 14db7019415405af89e9f5e317da617debeb0a19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-log-listeners-visual-basic"></a>トラブルシューティング: ログ リスナー (Visual Basic)
`My.Application.Log` オブジェクトおよび `My.Log` オブジェクトを使用すると、アプリケーション内で発生したイベントに関する情報をログに記録できます。  
  
 これらのメッセージをどのログ リスナーが受け取るかを確認するには、「[チュートリアル : My.Application.Log による情報の書き込み先の確認](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)」をご覧ください。  
  
 `Log` オブジェクトでログ フィルターを使って、ログに記録される情報の量を制限できます。 フィルターが正しく構成されていない場合、ログに誤った情報が含まれる可能性があります。 フィルターについて詳しくは、「[チュートリアル: My.Application.Log の出力をフィルター処理する](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)」をご覧ください。  
  
 一方、ログが正しく構成されていない場合は、現在の構成についてさらに情報が必要な場合があります。 ログの高度な `TraceSource` プロパティを使って、この情報を取得できます。  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a>コードで Log オブジェクトのログ リスナーを特定するには  
  
1.  コード ファイルの先頭に <xref:System.Diagnostics> 名前空間をインポートします。 詳細については、「[Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。  
  
     [!code-vb[VbVbalrMyApplicationLog#13](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_1.vb)]  
  
2.  各ログ リスナーの情報で構成される文字列を返す関数を作成します。  
  
     [!code-vb[VbVbalrMyApplicationLog#14](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_2.vb)]  
  
3.  ログのトレース リスナーのコレクションを `GetListeners` 関数に渡し、戻り値を表示します。  
  
     [!code-vb[VbVbalrMyApplicationLog#19](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_3.vb)]  
  
     詳細については、「<xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [アプリケーション ログの使用](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [チュートリアル : My.Application.Log による情報の書き込み先の確認](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
