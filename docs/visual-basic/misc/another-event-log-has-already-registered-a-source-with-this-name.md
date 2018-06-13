---
title: 別のイベント ログが、既にこの名前のソースを登録しています
ms.date: 07/20/2015
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
ms.openlocfilehash: b12fd5dcdeaccb0dc294c44e4b8a898726978633
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598921"
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a>別のイベント ログが、既にこの名前のソースを登録しています
イベント ログにエントリを書き込もうとしましたが、指定のソースは別のイベント ログに登録されています。  
  
 <xref:System.Diagnostics.EventLog.Source%2A> コンポーネントのインスタンスの <xref:System.Diagnostics.EventLog> プロパティを設定しておかなければ、コンポーネントはログにエントリを書き込めません。 書き込み時、システムは、指定したソースがコンポーネントの書き込み先のイベント ログに登録されているかどうかを確認し、必要に応じて <xref:System.Diagnostics.EventLog.CreateEventSource%2A> を呼び出します。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> または <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> メソッドを使用して、最初のログに対するソースの関連付けを削除します。  
  
2.  ソースを新しいログに登録します。  
  
## <a name="see-also"></a>関連項目  
 [My.Application.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  

