---
title: "別のイベント ログが、既にこの名前のソースを登録しています"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f04afd5d061a44f572d95abfb0173ad6fa2ac27
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a>別のイベント ログが、既にこの名前のソースを登録しています
イベント ログにエントリを書き込もうとしましたが、指定のソースは別のイベント ログに登録されています。  
  
 <xref:System.Diagnostics.EventLog.Source%2A> コンポーネントのインスタンスの <xref:System.Diagnostics.EventLog> プロパティを設定しておかなければ、コンポーネントはログにエントリを書き込めません。 書き込み時、システムは、指定したソースがコンポーネントの書き込み先のイベント ログに登録されているかどうかを確認し、必要に応じて <xref:System.Diagnostics.EventLog.CreateEventSource%2A> を呼び出します。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> または <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> メソッドを使用して、最初のログに対するソースの関連付けを削除します。  
  
2.  ソースを新しいログに登録します。  
  
## <a name="see-also"></a>参照  
 [My.Application.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  

