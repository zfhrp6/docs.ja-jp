---
title: "診断トレース"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28e77a63-d20d-4b6a-9caf-ddad86550427
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2cb16bb2d492caca7957e6d58eadddf9bf1568b3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="diagnostic-traces"></a><span data-ttu-id="8c1d7-102">診断トレース</span><span class="sxs-lookup"><span data-stu-id="8c1d7-102">Diagnostic Traces</span></span>
<span data-ttu-id="8c1d7-103">トレースとは、アプリケーションの実行中に生成される特定のメッセージの発行です。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-103">Traces are the publishing of specific messages that are generated during application execution.</span></span> <span data-ttu-id="8c1d7-104">トレースを使用するときには、送信されたメッセージを収集して記録するための機構が必要です。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-104">When using tracing, you must have a mechanism for collecting and recording the messages that are sent.</span></span> <span data-ttu-id="8c1d7-105">トレース メッセージは "リスナー" によって受け取られます。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-105">Trace messages are received by listeners.</span></span> <span data-ttu-id="8c1d7-106">リスナーの目的は、トレース メッセージの収集、格納、およびルーティングを行うことです。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-106">The purpose of a listener is to collect, store, and route tracing messages.</span></span> <span data-ttu-id="8c1d7-107">リスナーにより、トレース出力が適切な場所 (ログ、ウィンドウ、またはテキスト ファイル) に送られます。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-107">Listeners direct the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="8c1d7-108">トレースを有効にすると、こうしたリスナーの 1 つである <xref:System.Diagnostics.DefaultTraceListener> が自動的に作成および初期化されます。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-108">One such listener, the <xref:System.Diagnostics.DefaultTraceListener>, is automatically created and initialized when tracing is enabled.</span></span> <span data-ttu-id="8c1d7-109">トレース出力を別のソースに送るには、別のトレース リスナーを作成して初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-109">If you want trace output to be directed to any additional sources, you must create and initialize additional trace listeners.</span></span> <span data-ttu-id="8c1d7-110">作成するリスナーには、個別の要求が反映されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-110">The listeners you create should reflect your individual needs.</span></span> <span data-ttu-id="8c1d7-111">たとえば、すべてのトレース出力のテキスト レコードが必要である場合は、</span><span class="sxs-lookup"><span data-stu-id="8c1d7-111">For example, you might want a text record of all trace output.</span></span> <span data-ttu-id="8c1d7-112">有効になったときにすべての出力を新しいテキスト ファイルに書き込むリスナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-112">In this case, you would create a listener that wrote all output to a new text file when enabled.</span></span> <span data-ttu-id="8c1d7-113">また、アプリケーションの実行時に出力を表示するだけでよい場合は、</span><span class="sxs-lookup"><span data-stu-id="8c1d7-113">On the other hand, you might only want to view output during application execution.</span></span> <span data-ttu-id="8c1d7-114">すべての出力をコンソール ウィンドウに送るリスナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-114">In that case, you might create a listener that directed all output to a console window.</span></span> <span data-ttu-id="8c1d7-115"><xref:System.Diagnostics.EventLogTraceListener> はイベント ログにトレース出力を転送し、<xref:System.Diagnostics.TextWriterTraceListener> はストリームにトレース出力を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-115">The <xref:System.Diagnostics.EventLogTraceListener> can direct trace output to an event log, and the <xref:System.Diagnostics.TextWriterTraceListener> can write trace output to a stream.</span></span>  
  
## <a name="enabling-tracing"></a><span data-ttu-id="8c1d7-116">トレースの有効化</span><span class="sxs-lookup"><span data-stu-id="8c1d7-116">Enabling Tracing</span></span>  
 <span data-ttu-id="8c1d7-117">トランザクション処理中にトレースを有効にするには、アプリケーションの構成ファイルを編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-117">To enable traces during transaction processing, you should edit your application’s configuration file.</span></span> <span data-ttu-id="8c1d7-118">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-118">The following is an example.</span></span>  
  
```xml  
<configuration>  
<system.diagnostics>  
     <sources>  
          <source name="System.Transactions" switchValue="Warning">  
               <listeners>  
                    <add name="tx"   
                     type="System.Diagnostics.XmlWriterTraceListener"   
                     initializeData= "tx.log" />  
               </listeners>  
          </source>  
     </sources>  
</system.diagnostics>  
</configuration>  
```  
  
 <span data-ttu-id="8c1d7-119"><xref:System.Transactions> トレースは、"System.Transactions" という名前のソースに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-119"><xref:System.Transactions> traces are written to the source named "System.Transactions".</span></span> <span data-ttu-id="8c1d7-120">`add` を使用して、使用するトレース リスナーの名前と種類を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-120">You can use `add` to specify the name and type of the trace listener you want to use.</span></span> <span data-ttu-id="8c1d7-121">この例の構成では、リスナーに "tx" という名前を付け、使用する種類として標準の .NET Framework トレース リスナー (<xref:System.Diagnostics.XmlWriterTraceListener>) を追加しています。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-121">In our example configuration, we named the Listener "tx" and added the standard .NET Framework trace listener (<xref:System.Diagnostics.XmlWriterTraceListener>) as the type we want to use.</span></span> <span data-ttu-id="8c1d7-122">`initializeData` を使用して、リスナーのログ ファイルの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-122">Use `initializeData` to set the name of the log file for that listener.</span></span> <span data-ttu-id="8c1d7-123">さらに、単純なファイル名と完全修飾パスを置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-123">In addition, you can substitute a fully qualified path for a simple file name.</span></span>  
  
 <span data-ttu-id="8c1d7-124">各トレース メッセージの種類は、その重大度を示すレベルに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-124">Each trace message type is assigned a level to indicate its degree of importance.</span></span> <span data-ttu-id="8c1d7-125">アプリケーション ドメインのトレース レベルがイベント タイプのレベル以下である場合、そのメッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-125">If the app-domain’s trace level is equal or lower than the level of an event type, then that message is generated.</span></span> <span data-ttu-id="8c1d7-126">トレース レベルは、構成ファイルの `switchValue` 設定で制御します。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-126">The tracing level is controlled by the `switchValue` setting in the configuration file.</span></span> <span data-ttu-id="8c1d7-127">次の表に、診断トレース メッセージに関連するレベルの定義を示します。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-127">The levels that are associated with diagnostic trace messages are defined in the following table.</span></span>  
  
|<span data-ttu-id="8c1d7-128">トレース レベル</span><span class="sxs-lookup"><span data-stu-id="8c1d7-128">Trace Level</span></span>|<span data-ttu-id="8c1d7-129">説明</span><span class="sxs-lookup"><span data-stu-id="8c1d7-129">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="8c1d7-130">Critical</span><span class="sxs-lookup"><span data-stu-id="8c1d7-130">Critical</span></span>|<span data-ttu-id="8c1d7-131">次のような重大な障害が発生しました。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-131">Serious failures, such as the following, have occurred:</span></span><br /><br /> <span data-ttu-id="8c1d7-132">-ユーザーの機能では直接的な損失を引き起こす可能性のあるエラー。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-132">-   An error that can cause an immediate loss in user functionality.</span></span><br /><span data-ttu-id="8c1d7-133">機能の損失を防止するアクションを実行する管理者を必要とするイベントです。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-133">-   An event that requires an administrator to take action to avoid loss of functionality.</span></span><br /><span data-ttu-id="8c1d7-134">コードがハングアップします。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-134">-   Code hangs.</span></span><br /><span data-ttu-id="8c1d7-135">-このトレース レベルは、他の重要なトレースを解釈する場合も十分なコンテキストを提供できます。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-135">-   This tracing level can also provide sufficient context for interpreting other critical traces.</span></span> <span data-ttu-id="8c1d7-136">これは、重大なエラーにつながる操作シーケンスの特定に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-136">This can help to identify the sequence of operations leading to a serious failure.</span></span>|  
|<span data-ttu-id="8c1d7-137">Error</span><span class="sxs-lookup"><span data-stu-id="8c1d7-137">Error</span></span>|<span data-ttu-id="8c1d7-138">ユーザー機能の損失につながるエラー (無効な設定、ネットワークの動作など) が発生しました。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-138">An error (for example, invalid configuration or network behavior) has occurred that can result in a loss of user functionality.</span></span>|  
|<span data-ttu-id="8c1d7-139">警告</span><span class="sxs-lookup"><span data-stu-id="8c1d7-139">Warning</span></span>|<span data-ttu-id="8c1d7-140">後続の処理でエラーまたは重大なエラーが起こる可能性のある状態が存在します (割り当ての失敗、制限への接近など)。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-140">A condition exists that can subsequently result in an error or critical failure (for example, allocation failing or approaching a limit).</span></span> <span data-ttu-id="8c1d7-141">ユーザー コードからのエラーの通常処理 (トランザクションの中止、タイムアウト、認証の失敗など) が警告を生成する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-141">Normal processing of errors from user code (for example, transaction aborted, timeouts, authentication failed) can also generate a warning.</span></span>|  
|<span data-ttu-id="8c1d7-142">情報</span><span class="sxs-lookup"><span data-stu-id="8c1d7-142">Information</span></span>|<span data-ttu-id="8c1d7-143">システム ステータスの監視と診断、パフォーマンスの計測、またはプロファイリングに有用なメッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-143">Messages helpful for monitoring and diagnosing system status, measuring performance, or profiling are generated.</span></span> <span data-ttu-id="8c1d7-144">これには、トランザクションの作成またはコミット、重要な境界の超過、重要なリソースの割り当てなど、トランザクションと参加の有効期間イベントが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-144">These can include transaction and enlistment lifetime events, such as a transaction being created or committed, the crossing of a significant boundary, or the allocation of significant resources.</span></span> <span data-ttu-id="8c1d7-145">このような情報は、後で開発者が容量設計やパフォーマンス管理に利用できます。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-145">A developer can then utilize such information for capacity planning and performance management.</span></span>|  
  
## <a name="trace-codes"></a><span data-ttu-id="8c1d7-146">トレース コード</span><span class="sxs-lookup"><span data-stu-id="8c1d7-146">Trace Codes</span></span>  
 <span data-ttu-id="8c1d7-147">次の表は、<xref:System.Transactions> インフラストラクチャで生成されるトレース コードの一覧です。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-147">The following table lists the trace codes that are generated by the <xref:System.Transactions> infrastructure.</span></span> <span data-ttu-id="8c1d7-148">トレース コードの識別子は、テーブルに含まれる、<xref:System.Diagnostics.EventTypeFilter.EventType%2A>列挙およびレベルをトレースに含まれている追加のデータ、 **TraceRecord**トレース。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-148">Included in the table are the trace code identifier, the <xref:System.Diagnostics.EventTypeFilter.EventType%2A> enumeration level for the trace, and the extra data contained in the **TraceRecord** for the trace.</span></span> <span data-ttu-id="8c1d7-149">さらに、トレースの対応するトレース レベルに保存も、 **TraceRecord**です。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-149">In addition, the corresponding trace level of the trace is also stored in the **TraceRecord**.</span></span>  
  
|<span data-ttu-id="8c1d7-150">TraceCode</span><span class="sxs-lookup"><span data-stu-id="8c1d7-150">TraceCode</span></span>|<span data-ttu-id="8c1d7-151">EventType</span><span class="sxs-lookup"><span data-stu-id="8c1d7-151">EventType</span></span>|<span data-ttu-id="8c1d7-152">TraceRecord の追加データ</span><span class="sxs-lookup"><span data-stu-id="8c1d7-152">Extra data in TraceRecord</span></span>|  
|---------------|---------------|-------------------------------|  
|<span data-ttu-id="8c1d7-153">TransactionCreated</span><span class="sxs-lookup"><span data-stu-id="8c1d7-153">TransactionCreated</span></span>|<span data-ttu-id="8c1d7-154">情報</span><span class="sxs-lookup"><span data-stu-id="8c1d7-154">Info</span></span>|<span data-ttu-id="8c1d7-155">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="8c1d7-155">TransactionTraceId</span></span>|  
|<span data-ttu-id="8c1d7-156">TransactionPromoted</span><span class="sxs-lookup"><span data-stu-id="8c1d7-156">TransactionPromoted</span></span>|<span data-ttu-id="8c1d7-157">情報</span><span class="sxs-lookup"><span data-stu-id="8c1d7-157">Info</span></span>|<span data-ttu-id="8c1d7-158">Local TransactionTraceId、Distributed TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="8c1d7-158">Local TransactionTraceId, Distributed TransactionTraceId</span></span>|  
|<span data-ttu-id="8c1d7-159">EnlistmentCreated</span><span class="sxs-lookup"><span data-stu-id="8c1d7-159">EnlistmentCreated</span></span>|<span data-ttu-id="8c1d7-160">情報</span><span class="sxs-lookup"><span data-stu-id="8c1d7-160">Info</span></span>|<span data-ttu-id="8c1d7-161">TransactionTraceId、EnlistmentTraceId、EnlistmentType (durable/volatile)、EnlistmentOptions</span><span class="sxs-lookup"><span data-stu-id="8c1d7-161">TransactionTraceId, EnlistmentTraceId, EnlistmentType (durable/volatile), EnlistmentOptions</span></span>|  
|<span data-ttu-id="8c1d7-162">EnlistmentCallbackNegative</span><span class="sxs-lookup"><span data-stu-id="8c1d7-162">EnlistmentCallbackNegative</span></span>|<span data-ttu-id="8c1d7-163">警告</span><span class="sxs-lookup"><span data-stu-id="8c1d7-163">Warning</span></span>|<span data-ttu-id="8c1d7-164">TransactionTraceId、EnlistmentTraceId、</span><span class="sxs-lookup"><span data-stu-id="8c1d7-164">TransactionTraceId, EnlistmentTraceId,</span></span><br /><br /> <span data-ttu-id="8c1d7-165">Callback (forcerollback/aborted/indoubt)</span><span class="sxs-lookup"><span data-stu-id="8c1d7-165">Callback (forcerollback/aborted/indoubt)</span></span>|  
|<span data-ttu-id="8c1d7-166">TransactionRollbackCalled</span><span class="sxs-lookup"><span data-stu-id="8c1d7-166">TransactionRollbackCalled</span></span>|<span data-ttu-id="8c1d7-167">警告</span><span class="sxs-lookup"><span data-stu-id="8c1d7-167">Warning</span></span>|<span data-ttu-id="8c1d7-168">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="8c1d7-168">TransactionTraceId</span></span>|  
|<span data-ttu-id="8c1d7-169">TransactionAborted</span><span class="sxs-lookup"><span data-stu-id="8c1d7-169">TransactionAborted</span></span>|<span data-ttu-id="8c1d7-170">警告</span><span class="sxs-lookup"><span data-stu-id="8c1d7-170">Warning</span></span>|<span data-ttu-id="8c1d7-171">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="8c1d7-171">TransactionTraceId</span></span>|  
|<span data-ttu-id="8c1d7-172">TransactionInDoubt</span><span class="sxs-lookup"><span data-stu-id="8c1d7-172">TransactionInDoubt</span></span>|<span data-ttu-id="8c1d7-173">警告</span><span class="sxs-lookup"><span data-stu-id="8c1d7-173">Warning</span></span>|<span data-ttu-id="8c1d7-174">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="8c1d7-174">TransactionTraceId</span></span>|  
|<span data-ttu-id="8c1d7-175">TransactionScopeCreated</span><span class="sxs-lookup"><span data-stu-id="8c1d7-175">TransactionScopeCreated</span></span>|<span data-ttu-id="8c1d7-176">情報</span><span class="sxs-lookup"><span data-stu-id="8c1d7-176">Info</span></span>|<span data-ttu-id="8c1d7-177">TransactionScopeResult (次のようになります)</span><span class="sxs-lookup"><span data-stu-id="8c1d7-177">TransactionScopeResult, which can be the following:</span></span><br /><br /> <span data-ttu-id="8c1d7-178">新しいトランザクションです。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-178">-   New transaction.</span></span><br /><span data-ttu-id="8c1d7-179">トランザクションが渡されます。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-179">-   Transaction passed.</span></span><br /><span data-ttu-id="8c1d7-180">に渡されたトランザクション依存します。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-180">-   Dependent transaction passed.</span></span><br /><span data-ttu-id="8c1d7-181">現在のトランザクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-181">-   Using current transaction.</span></span><br /><span data-ttu-id="8c1d7-182">-トランザクションです。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-182">-   No transaction.</span></span><br /><br /> <span data-ttu-id="8c1d7-183">新しい現在の TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="8c1d7-183">new current TransactionTraceId</span></span>|  
|<span data-ttu-id="8c1d7-184">TransactionScopeDisposed</span><span class="sxs-lookup"><span data-stu-id="8c1d7-184">TransactionScopeDisposed</span></span>|<span data-ttu-id="8c1d7-185">Info</span><span class="sxs-lookup"><span data-stu-id="8c1d7-185">Info</span></span>|<span data-ttu-id="8c1d7-186">スコープの TransactionTraceId は、現在のトランザクションを「必要」です。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-186">TransactionTraceId of the scope’s "expected" current transaction.</span></span>|  
|<span data-ttu-id="8c1d7-187">TransactionScopeIncomplete</span><span class="sxs-lookup"><span data-stu-id="8c1d7-187">TransactionScopeIncomplete</span></span>|<span data-ttu-id="8c1d7-188">警告</span><span class="sxs-lookup"><span data-stu-id="8c1d7-188">Warning</span></span>|<span data-ttu-id="8c1d7-189">スコープの TransactionTraceId は、現在のトランザクションを「必要」です。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-189">TransactionTraceId of the scope’s "expected" current transaction.</span></span>|  
|<span data-ttu-id="8c1d7-190">TransactionScopeNestedIncorrectly</span><span class="sxs-lookup"><span data-stu-id="8c1d7-190">TransactionScopeNestedIncorrectly</span></span>|<span data-ttu-id="8c1d7-191">警告</span><span class="sxs-lookup"><span data-stu-id="8c1d7-191">Warning</span></span>|<span data-ttu-id="8c1d7-192">スコープの TransactionTraceId は、現在のトランザクションを「必要」です。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-192">TransactionTraceId of the scope’s "expected" current transaction.</span></span>|  
|<span data-ttu-id="8c1d7-193">TransactionScopeCurrentTransactionChanged</span><span class="sxs-lookup"><span data-stu-id="8c1d7-193">TransactionScopeCurrentTransactionChanged</span></span>|<span data-ttu-id="8c1d7-194">警告</span><span class="sxs-lookup"><span data-stu-id="8c1d7-194">Warning</span></span>|<span data-ttu-id="8c1d7-195">古い (現在の) TransactionTraceId、他の TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="8c1d7-195">Old current TransactionTraceId, other TransactionTraceId</span></span>|  
|<span data-ttu-id="8c1d7-196">TransactionScopeTimeout</span><span class="sxs-lookup"><span data-stu-id="8c1d7-196">TransactionScopeTimeout</span></span>|<span data-ttu-id="8c1d7-197">警告</span><span class="sxs-lookup"><span data-stu-id="8c1d7-197">Warning</span></span>|<span data-ttu-id="8c1d7-198">スコープの TransactionTraceId は、現在のトランザクションを「必要」です。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-198">TransactionTraceId of the scope’s "expected" current transaction.</span></span>|  
|<span data-ttu-id="8c1d7-199">DependentCloneCreated</span><span class="sxs-lookup"><span data-stu-id="8c1d7-199">DependentCloneCreated</span></span>|<span data-ttu-id="8c1d7-200">情報</span><span class="sxs-lookup"><span data-stu-id="8c1d7-200">Info</span></span>|<span data-ttu-id="8c1d7-201">TransactionTraceId、作成される依存トランザクションの種類 (RollbackIfNotComplete/BlockCommitUntilComplete)</span><span class="sxs-lookup"><span data-stu-id="8c1d7-201">TransactionTraceId, type of dependent transaction created (RollbackIfNotComplete/BlockCommitUntilComplete)</span></span>|  
|<span data-ttu-id="8c1d7-202">DependentCloneComplete</span><span class="sxs-lookup"><span data-stu-id="8c1d7-202">DependentCloneComplete</span></span>|<span data-ttu-id="8c1d7-203">情報</span><span class="sxs-lookup"><span data-stu-id="8c1d7-203">Info</span></span>|<span data-ttu-id="8c1d7-204">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="8c1d7-204">TransactionTraceId</span></span>|  
|<span data-ttu-id="8c1d7-205">RecoveryComplete</span><span class="sxs-lookup"><span data-stu-id="8c1d7-205">RecoveryComplete</span></span>|<span data-ttu-id="8c1d7-206">情報</span><span class="sxs-lookup"><span data-stu-id="8c1d7-206">Info</span></span>|<span data-ttu-id="8c1d7-207">リソース マネージャー GUID (ベースから)</span><span class="sxs-lookup"><span data-stu-id="8c1d7-207">Resource Manager GUID (from base)</span></span>|  
|<span data-ttu-id="8c1d7-208">Reenlist</span><span class="sxs-lookup"><span data-stu-id="8c1d7-208">Reenlist</span></span>|<span data-ttu-id="8c1d7-209">情報</span><span class="sxs-lookup"><span data-stu-id="8c1d7-209">Info</span></span>|<span data-ttu-id="8c1d7-210">リソース マネージャー GUID (ベースから)</span><span class="sxs-lookup"><span data-stu-id="8c1d7-210">Resource Manager GUID (from base)</span></span>|  
|<span data-ttu-id="8c1d7-211">TransactionSerialized</span><span class="sxs-lookup"><span data-stu-id="8c1d7-211">TransactionSerialized</span></span>|<span data-ttu-id="8c1d7-212">情報</span><span class="sxs-lookup"><span data-stu-id="8c1d7-212">Info</span></span>|<span data-ttu-id="8c1d7-213">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="8c1d7-213">TransactionTraceId.</span></span>|  
|<span data-ttu-id="8c1d7-214">TransactionException</span><span class="sxs-lookup"><span data-stu-id="8c1d7-214">TransactionException</span></span>|<span data-ttu-id="8c1d7-215">Error</span><span class="sxs-lookup"><span data-stu-id="8c1d7-215">Error</span></span>|<span data-ttu-id="8c1d7-216">例外メッセージ</span><span class="sxs-lookup"><span data-stu-id="8c1d7-216">Exception message</span></span>|  
|<span data-ttu-id="8c1d7-217">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="8c1d7-217">InvalidOperationException</span></span>|<span data-ttu-id="8c1d7-218">Error</span><span class="sxs-lookup"><span data-stu-id="8c1d7-218">Error</span></span>|<span data-ttu-id="8c1d7-219">例外メッセージ</span><span class="sxs-lookup"><span data-stu-id="8c1d7-219">Exception message</span></span>|  
|<span data-ttu-id="8c1d7-220">InternalError</span><span class="sxs-lookup"><span data-stu-id="8c1d7-220">InternalError</span></span>|<span data-ttu-id="8c1d7-221">Critical</span><span class="sxs-lookup"><span data-stu-id="8c1d7-221">Critical</span></span>|<span data-ttu-id="8c1d7-222">例外メッセージ</span><span class="sxs-lookup"><span data-stu-id="8c1d7-222">Exception message</span></span>|  
|<span data-ttu-id="8c1d7-223">TransferEvent</span><span class="sxs-lookup"><span data-stu-id="8c1d7-223">TransferEvent</span></span>||<span data-ttu-id="8c1d7-224">トランザクションが逆シリアル化されるか、または <xref:System.Transactions> トランザクションから分散トランザクションに昇格される場合、ExecutionContext の現在の ActivityID および分散トランザクション ID が書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-224">When a transaction is deserialized, or promoted from a <xref:System.Transactions> transaction to a distributed one, the current ActivityID from the ExecutionContext and the distributed transaction ID are written.</span></span><br /><br /> <span data-ttu-id="8c1d7-225">DTC がマネージ コードにコールバックする場合、コールバックの間、分散トランザクション ID が ExecutionContext の ActivityID として設定されます。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-225">When the DTC calls back into managed code, the distributed transaction ID is set as the ActivityID in the ExecutionContext for the duration of the callback.</span></span>|  
|<span data-ttu-id="8c1d7-226">ConfiguredDefaultTimeoutAdjusted</span><span class="sxs-lookup"><span data-stu-id="8c1d7-226">ConfiguredDefaultTimeoutAdjusted</span></span>|<span data-ttu-id="8c1d7-227">警告</span><span class="sxs-lookup"><span data-stu-id="8c1d7-227">Warning</span></span>|<span data-ttu-id="8c1d7-228">追加データなし</span><span class="sxs-lookup"><span data-stu-id="8c1d7-228">No extra data</span></span>|  
|<span data-ttu-id="8c1d7-229">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="8c1d7-229">TransactionTimeout</span></span>|<span data-ttu-id="8c1d7-230">警告</span><span class="sxs-lookup"><span data-stu-id="8c1d7-230">Warning</span></span>|<span data-ttu-id="8c1d7-231">タイムアウトするトランザクションの TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="8c1d7-231">The TransactionTraceId of the transaction being timed out.</span></span>|  
  
 <span data-ttu-id="8c1d7-232">上の各追加データ項目に対する XML スキーマの形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-232">The XML schema for each of the preceding extra data items has the following format.</span></span>  
  
### <a name="transactiontraceidentifier"></a><span data-ttu-id="8c1d7-233">TransactionTraceIdentifier</span><span class="sxs-lookup"><span data-stu-id="8c1d7-233">TransactionTraceIdentifier</span></span>  
 `<TransactionTraceIdentifier>`  
  
 `<TransactionIdentifier >`  
  
 `string representation of transaction id`  
  
 `</TransactionIdentifier>`  
  
 `< CloneIdentifier >`  
  
 `the clone id number`  
  
 `</CloneIdentifier>`  
  
 `</TransactionTraceIdentifier>`  
  
### <a name="enlistmenttraceidentifier"></a><span data-ttu-id="8c1d7-234">EnlistmentTraceIdentifier</span><span class="sxs-lookup"><span data-stu-id="8c1d7-234">EnlistmentTraceIdentifier</span></span>  
 `<EnlistmentTraceIdentifier>`  
  
 `<ResourceManagerId>`  
  
 `string form of guid`  
  
 `</ResourceManagerId>`  
  
 `<TransactionTraceIdentifier>`  
  
 `<TransactionIdentifier >`  
  
 `string representation of transaction id`  
  
 `</TransactionIdentifier>`  
  
 `<CloneIdentifier >`  
  
 `the clone id number`  
  
 `</CloneIdentifier>`  
  
 `<TransactionTraceIdentifier>`  
  
 `<EnlistmentIdentifier>`  
  
 `the enlistment id number`  
  
 `</EnlistmentIdentifier>`  
  
 `</EnlistmentTraceIdentifier>`  
  
### <a name="resource-manager-identifier"></a><span data-ttu-id="8c1d7-235">リソース マネージャー識別子</span><span class="sxs-lookup"><span data-stu-id="8c1d7-235">Resource Manager Identifier</span></span>  
 `<ResourceManagerId>`  
  
 `string form of guid`  
  
 `</ResourceManagerId>`  
  
## <a name="security-issues-for-tracing"></a><span data-ttu-id="8c1d7-236">トレースのセキュリティに関する問題</span><span class="sxs-lookup"><span data-stu-id="8c1d7-236">Security Issues For Tracing</span></span>  
 <span data-ttu-id="8c1d7-237">トレースを管理者として有効にすると、ときに、既定で、機密情報をパブリックに表示されるトレース ログに書き込ま可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-237">When you as an administrator turn on tracing, sensitive information might be written to a trace log that is publicly viewable by default.</span></span> <span data-ttu-id="8c1d7-238">任意の潜在的なセキュリティの脅威を軽減するには、共有とファイル システム アクセス許可によって制御される安全な場所に、トレース ログを格納することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="8c1d7-238">To mitigate any possible security threat, you should consider storing the trace log in a secure location controlled by share and file system access permissions.</span></span>
