---
title: "アプリケーションからの情報のログ記録 (Visual Basic) | Microsoft Docs"
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
- Log object
- My.Log object
- applications [Visual Basic], logging information from
- logging
- My.Application.Log object
- examples [Visual Basic], logging application information
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 25bf4e1d8b9b87c1545272c0d2746dc808d3fa4b
ms.contentlocale: ja-jp
ms.lasthandoff: 05/22/2017

---
# <a name="logging-information-from-the-application-visual-basic"></a>アプリケーションからの情報のログ記録 (Visual Basic)
このセクションには、`My.Application.Log` オブジェクトまたは `My.Log` オブジェクトを使ってアプリケーションの情報を記録する方法と、アプリケーションのログ機能を拡張する方法に関するトピックが含まれます。  
  
 `Log` オブジェクトはアプリケーションのログ リスナーに情報を書き込むためのメソッドを提供し、`Log` オブジェクトの高度な `TraceSource` プロパティは詳細な構成情報を提供します。 `Log` オブジェクトは、アプリケーションの構成ファイルによって構成されます。  
  
 `My.Log` オブジェクトは、ASP.NET アプリケーションでのみ使うことができます。 クライアント アプリケーションの場合は `My.Application.Log` を使います。 詳細については、「<xref:Microsoft.VisualBasic.Logging.Log>」を参照してください。  
  
## <a name="tasks"></a>タスク  
  
|目的|参照トピック|  
|--------|---------|  
|イベントの情報をアプリケーションのログに書き込みます。|[方法: ログ メッセージを書き込む](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)|  
|例外の情報をアプリケーションのログに書き込みます。|[方法 : 例外をログに記録する](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)|  
|アプリケーションの起動時または終了時に、トレース情報をアプリケーションのログに書き込みます。|[方法 : アプリケーションの起動時または終了時にメッセージをログに記録する](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|テキスト ファイルに情報を書き込むように `My.Application.Log` を構成します。|[方法 : イベント情報をテキスト ファイルに書き込む](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)|  
|イベント ログに情報を書き込むように `My.Application.Log` を構成します。|[方法 : アプリケーション イベント ログに書き込む](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)|  
|`My.Application.Log` が情報を書き込む場所を変更します。|[チュートリアル : My.Application.Log による情報の書き込み先の変更](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)|  
|`My.Application.Log` が情報を書き込む場所を取得します。|[チュートリアル : My.Application.Log による情報の書き込み先の確認](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)|  
|`My.Application.Log` のカスタム ログ リスナーを作成します。|[チュートリアル : カスタム ログ リスナーの作成](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)|  
|`My.Application.Log` ログの出力をフィルター処理します。|[チュートリアル : My.Application.Log の出力をフィルター処理する](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 [アプリケーション ログの使用](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [トラブルシューティング : ログ リスナー](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
