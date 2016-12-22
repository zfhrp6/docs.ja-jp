---
title: "Logging Information from the Application (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Log object"
  - "My.Log object"
  - "applications [Visual Basic], logging information from"
  - "logging"
  - "My.Application.Log object"
  - "examples [Visual Basic], logging application information"
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Logging Information from the Application (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

このセクションのトピックでは、`My.Application.Log` オブジェクトまたは `My.Log` オブジェクトを使用してアプリケーションから情報をログに記録する方法と、アプリケーションのログ機能を拡張する方法について取り上げます。  
  
 `Log` オブジェクトには、アプリケーションのログ リスナーに情報を書き込むためのメソッドが用意されています。また、`Log` オブジェクトの高度な `TraceSource` プロパティでは、詳細な構成情報にアクセスできます。  `Log` オブジェクトは、アプリケーションの構成ファイルにより構成されます。  
  
 `My.Log` オブジェクトは ASP.NET アプリケーションでのみ利用できます。  クライアント アプリケーションでは、`My.Application.Log` を使用します。  詳細については、「<xref:Microsoft.VisualBasic.Logging.Log>」を参照してください。  
  
## タスク  
  
|目的|参照項目|  
|--------|----------|  
|イベント情報をアプリケーションのログに書き込む。|[方法: ログ メッセージを書き込む](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)|  
|例外情報をアプリケーションのログに書き込む。|[How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)|  
|アプリケーションが起動および終了するときに、アプリケーションのログにトレース情報を書き込む。|[方法 : アプリケーションの起動時または終了時にメッセージをログに記録する](../Topic/How%20to:%20Log%20Messages%20When%20the%20Application%20Starts%20or%20Shuts%20Down%20\(Visual%20Basic\).md)|  
|テキスト ファイルへ情報を書き込むように `My.Application.Log` を構成する。|[How to: Write Event Information to a Text File](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)|  
|イベント ログへ情報を書き込むように `My.Application.Log` を構成する。|[方法 : アプリケーション イベント ログに書き込む](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)|  
|`My.Application.Log` が情報を書き込む先を変更する。|[チュートリアル : My.Application.Log による情報の書き込み先の変更](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)|  
|`My.Application.Log` が情報を書き込む先を判断する。|[チュートリアル : My.Application.Log による情報の書き込み先の確認](../Topic/Walkthrough:%20Determining%20Where%20My.Application.Log%20Writes%20Information%20\(Visual%20Basic\).md)|  
|`My.Application.Log` 用のカスタム ログ リスナーを作成する。|[Walkthrough: Creating Custom Log Listeners](../Topic/Walkthrough:%20Creating%20Custom%20Log%20Listeners%20\(Visual%20Basic\).md)|  
|`My.Application.Log` ログの出力をフィルター処理する。|[Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)|  
  
## 参照  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 [アプリケーション ログの使用](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [Troubleshooting: Log Listeners](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)