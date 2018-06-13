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
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a><span data-ttu-id="8559e-102">別のイベント ログが、既にこの名前のソースを登録しています</span><span class="sxs-lookup"><span data-stu-id="8559e-102">Another event log has already registered a source with this name</span></span>
<span data-ttu-id="8559e-103">イベント ログにエントリを書き込もうとしましたが、指定のソースは別のイベント ログに登録されています。</span><span class="sxs-lookup"><span data-stu-id="8559e-103">An attempt was made to write an entry to an event log where the specified source is registered with another event log.</span></span>  
  
 <span data-ttu-id="8559e-104"><xref:System.Diagnostics.EventLog.Source%2A> コンポーネントのインスタンスの <xref:System.Diagnostics.EventLog> プロパティを設定しておかなければ、コンポーネントはログにエントリを書き込めません。</span><span class="sxs-lookup"><span data-stu-id="8559e-104">You must set the <xref:System.Diagnostics.EventLog.Source%2A> property of your <xref:System.Diagnostics.EventLog> component instance before your component writes an entry to a log.</span></span> <span data-ttu-id="8559e-105">書き込み時、システムは、指定したソースがコンポーネントの書き込み先のイベント ログに登録されているかどうかを確認し、必要に応じて <xref:System.Diagnostics.EventLog.CreateEventSource%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8559e-105">When this happens, the system checks that the source you specified is registered with the event log to which the component is writing, and calls <xref:System.Diagnostics.EventLog.CreateEventSource%2A> if needed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8559e-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="8559e-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="8559e-107"><xref:System.Diagnostics.EventLog.DeleteEventSource%2A> または <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> メソッドを使用して、最初のログに対するソースの関連付けを削除します。</span><span class="sxs-lookup"><span data-stu-id="8559e-107">Remove the association of the source with the first log using the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> or the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> method.</span></span>  
  
2.  <span data-ttu-id="8559e-108">ソースを新しいログに登録します。</span><span class="sxs-lookup"><span data-stu-id="8559e-108">Register the source with the new log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8559e-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="8559e-109">See Also</span></span>  
 [<span data-ttu-id="8559e-110">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="8559e-110">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  

