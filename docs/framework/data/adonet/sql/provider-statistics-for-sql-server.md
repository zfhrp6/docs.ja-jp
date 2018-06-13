---
title: SQL Server のプロバイダー統計情報
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: f32b1c9f800a1ec2d80511cbbf46aba9840075d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365991"
---
# <a name="provider-statistics-for-sql-server"></a><span data-ttu-id="514e1-102">SQL Server のプロバイダー統計情報</span><span class="sxs-lookup"><span data-stu-id="514e1-102">Provider Statistics for SQL Server</span></span>
<span data-ttu-id="514e1-103">.NET Framework version 2.0 以降では、.NET Framework Data Provider for SQL Server によって実行時の統計がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="514e1-103">Starting with the .NET Framework version 2.0, the .NET Framework Data Provider for SQL Server supports run-time statistics.</span></span> <span data-ttu-id="514e1-104">統計情報を有効にするには、有効な接続オブジェクトを作成した後で、<xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> オブジェクトの <xref:System.Data.SqlClient.SqlConnection> プロパティを `True` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="514e1-104">You must enable statistics by setting the <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object to `True` after you have a valid connection object created.</span></span> <span data-ttu-id="514e1-105">統計情報が有効にされると、<xref:System.Collections.IDictionary> オブジェクトの <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> メソッドを通じて <xref:System.Data.SqlClient.SqlConnection> 参照を取得することにより、"時間単位のスナップショット" として統計情報を確認できます。</span><span class="sxs-lookup"><span data-stu-id="514e1-105">After statistics are enabled, you can review them as a "snapshot in time" by retrieving an <xref:System.Collections.IDictionary> reference via the <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="514e1-106">名前と値がペアになったディクショナリ エントリのセットとして、一覧を列挙します。</span><span class="sxs-lookup"><span data-stu-id="514e1-106">You enumerate through the list as a set of name/value pair dictionary entries.</span></span> <span data-ttu-id="514e1-107">これらの名前と値のペアは順序付けられていません。</span><span class="sxs-lookup"><span data-stu-id="514e1-107">These name/value pairs are unordered.</span></span> <span data-ttu-id="514e1-108">いつでも <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> オブジェクトの <xref:System.Data.SqlClient.SqlConnection> メソッドを呼び出して、カウンターをリセットすることができます。</span><span class="sxs-lookup"><span data-stu-id="514e1-108">At any time, you can call the <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object to reset the counters.</span></span> <span data-ttu-id="514e1-109">統計情報収集が有効になっていない場合、例外は生成されません。</span><span class="sxs-lookup"><span data-stu-id="514e1-109">If statistic gathering has not been enabled, an exception is not generated.</span></span> <span data-ttu-id="514e1-110">また、<xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> が最初に呼び出されるずに <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> が呼び出されると、取得される値は各エントリの初期値になります。</span><span class="sxs-lookup"><span data-stu-id="514e1-110">In addition, if <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> is called without <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> having been called first, the values retrieved are the initial values for each entry.</span></span> <span data-ttu-id="514e1-111">統計情報を有効にしてからアプリケーションをしばらく実行した後で統計情報を無効にした場合、取得される値には、統計情報が無効にされた時点までに収集された値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="514e1-111">If you enable statistics, run your application for a while, and then disable statistics, the values retrieved will reflect the values collected up to the point where statistics were disabled.</span></span> <span data-ttu-id="514e1-112">すべての統計情報の値は、接続ごとに収集されます。</span><span class="sxs-lookup"><span data-stu-id="514e1-112">All statistical values gathered are on a per-connection basis.</span></span>  
  
## <a name="statistical-values-available"></a><span data-ttu-id="514e1-113">使用できる統計情報の値</span><span class="sxs-lookup"><span data-stu-id="514e1-113">Statistical Values Available</span></span>  
 <span data-ttu-id="514e1-114">現在、Microsoft SQL Server プロバイダーから使用できる項目は 18 種類あります。</span><span class="sxs-lookup"><span data-stu-id="514e1-114">Currently there are 18 different items available from the Microsoft SQL Server provider.</span></span> <span data-ttu-id="514e1-115">利用可能なアイテムの数は、経由でアクセスできる、**カウント**のプロパティ、<xref:System.Collections.IDictionary>インターフェイスによって返されるリファレンス<xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>です。</span><span class="sxs-lookup"><span data-stu-id="514e1-115">The number of items available can be accessed via the **Count** property of the <xref:System.Collections.IDictionary> interface reference returned by <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span></span> <span data-ttu-id="514e1-116">共通言語ランタイムを使用してすべてのプロバイダー統計カウンター<xref:System.Int64>型 (**長い**c# および Visual Basic で)、64 ビット幅であります。</span><span class="sxs-lookup"><span data-stu-id="514e1-116">All of the counters for provider statistics use the common language runtime <xref:System.Int64> type (**long** in C# and Visual Basic), which is 64 bits wide.</span></span> <span data-ttu-id="514e1-117">最大値、 **int64**データ型で定義されている、 **int64 です。MaxValue**フィールド、((2^63)-1))。</span><span class="sxs-lookup"><span data-stu-id="514e1-117">The maximum value of the **int64** data type, as defined by the **int64.MaxValue** field, is ((2^63)-1)).</span></span> <span data-ttu-id="514e1-118">カウンターの値がこの最大値に達すると、これ以降カウンターは正確ではないと見なされます。</span><span class="sxs-lookup"><span data-stu-id="514e1-118">When the values for the counters reach this maximum value, they should no longer be considered accurate.</span></span> <span data-ttu-id="514e1-119">つまり、 **int64 です。MaxValue**-1((2^63)-2) はすべての統計の最大有効値は実質的にします。</span><span class="sxs-lookup"><span data-stu-id="514e1-119">This means that **int64.MaxValue**-1((2^63)-2) is effectively the greatest valid value for any statistic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="514e1-120">プロバイダーの統計情報を返すためにディクショナリが使用されているのは、返される統計情報の数値、名前、および順序が今後変更される可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="514e1-120">A dictionary is used for returning provider statistics because the number, names and order of the returned statistics may change in the future.</span></span> <span data-ttu-id="514e1-121">アプリケーションでは、ディクショナリ内で見つかった特定の値に依存する必要はありませんが、値が存在するかどうかや、この値に応じて分岐させるかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="514e1-121">Applications should not rely on a specific value being found in the dictionary, but should instead check whether the value is there and branch accordingly.</span></span>  
  
 <span data-ttu-id="514e1-122">次の表では、使用可能な現在の統計情報の値が説明されています。</span><span class="sxs-lookup"><span data-stu-id="514e1-122">The following table describes the current statistical values available.</span></span> <span data-ttu-id="514e1-123">個々の値のキー名は、Microsoft .NET Framework の地域別バージョン全体でローカライズされているわけではないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="514e1-123">Note that the key names for the individual values are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="514e1-124">キー名</span><span class="sxs-lookup"><span data-stu-id="514e1-124">Key Name</span></span>|<span data-ttu-id="514e1-125">説明</span><span class="sxs-lookup"><span data-stu-id="514e1-125">Description</span></span>|  
|--------------|-----------------|  
|`BuffersReceived`|<span data-ttu-id="514e1-126">アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後にプロバイダーが SQL Server から受け取る、表形式のデータ ストリーム (TDS) パケットの数を返します。</span><span class="sxs-lookup"><span data-stu-id="514e1-126">Returns the number of tabular data stream (TDS) packets received by the provider from SQL Server after the application has started using the provider and has enabled statistics.</span></span>|  
|`BuffersSent`|<span data-ttu-id="514e1-127">統計情報が有効になった後に、プロバイダーにより SQL Server に送信された TDS パケットの数を返します。</span><span class="sxs-lookup"><span data-stu-id="514e1-127">Returns the number of TDS packets sent to SQL Server by the provider after statistics have been enabled.</span></span> <span data-ttu-id="514e1-128">大量の処理を伴うコマンドでは、複数のバッファーが必要になります。</span><span class="sxs-lookup"><span data-stu-id="514e1-128">Large commands can require multiple buffers.</span></span> <span data-ttu-id="514e1-129">たとえば、大きなコマンドがサーバーに送信され、6 つのパケットが必要になる場合は、`ServerRoundtrips` は 1 だけインクリメントされ、`BuffersSent` は 6 だけインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="514e1-129">For example, if a large command is sent to the server and it requires six packets, `ServerRoundtrips` is incremented by one and `BuffersSent` is incremented by six.</span></span>|  
|`BytesReceived`|<span data-ttu-id="514e1-130">アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後にプロバイダーが SQL Server から受け取る、TDS パケット内のデータのバイト数を返します。</span><span class="sxs-lookup"><span data-stu-id="514e1-130">Returns the number of bytes of data in the TDS packets received by the provider from SQL Server once the application has started using the provider and has enabled statistics.</span></span>|  
|`BytesSent`|<span data-ttu-id="514e1-131">アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後に TDS パケット内の SQL Server に送信される、データのバイト数を返します。</span><span class="sxs-lookup"><span data-stu-id="514e1-131">Returns the number of bytes of data sent to SQL Server in TDS packets after the application has started using the provider and has enabled statistics.</span></span>|  
|`ConnectionTime`|<span data-ttu-id="514e1-132">統計情報が有効になった後に接続が開かれている時間 (ミリ秒) を示します (接続が開かれる前に統計情報が有効になっていた場合は、合計接続時間を示します)。</span><span class="sxs-lookup"><span data-stu-id="514e1-132">The amount of time (in milliseconds) that the connection has been opened after statistics have been enabled (total connection time if statistics were enabled before opening the connection).</span></span>|  
|`CursorOpens`|<span data-ttu-id="514e1-133">アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後に接続を通じて行われた、カーソルが開かれた回数を返します。</span><span class="sxs-lookup"><span data-stu-id="514e1-133">Returns the number of times a cursor was open through the connection once the application has started using the provider and has enabled statistics.</span></span><br /><br /> <span data-ttu-id="514e1-134">SELECT ステートメントにより返される読み取り専用/前方参照専用の結果は、カーソルが考慮されないため、このカウンターには影響しません。</span><span class="sxs-lookup"><span data-stu-id="514e1-134">Note that read-only/forward-only results returned by SELECT statements are not considered cursors and thus do not affect this counter.</span></span>|  
|`ExecutionTime`|<span data-ttu-id="514e1-135">統計情報が有効になってから、プロバイダーが処理に費やした累計時間 (ミリ秒) を返します。この時間には、サーバーからの応答を待つために費やされた時間と、プロバイダー自体がコードを実行するために費やした時間が含まれます。</span><span class="sxs-lookup"><span data-stu-id="514e1-135">Returns the cumulative amount of time (in milliseconds) that the provider has spent processing once statistics have been enabled, including the time spent waiting for replies from the server as well as the time spent executing code in the provider itself.</span></span><br /><br /> <span data-ttu-id="514e1-136">タイミング コードが含まれるクラスは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="514e1-136">The classes that include timing code are:</span></span><br /><br /> <span data-ttu-id="514e1-137">SqlConnection</span><span class="sxs-lookup"><span data-stu-id="514e1-137">SqlConnection</span></span><br /><br /> <span data-ttu-id="514e1-138">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="514e1-138">SqlCommand</span></span><br /><br /> <span data-ttu-id="514e1-139">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="514e1-139">SqlDataReader</span></span><br /><br /> <span data-ttu-id="514e1-140">SqlDataAdapter</span><span class="sxs-lookup"><span data-stu-id="514e1-140">SqlDataAdapter</span></span><br /><br /> <span data-ttu-id="514e1-141">SqlTransaction</span><span class="sxs-lookup"><span data-stu-id="514e1-141">SqlTransaction</span></span><br /><br /> <span data-ttu-id="514e1-142">SqlCommandBuilder</span><span class="sxs-lookup"><span data-stu-id="514e1-142">SqlCommandBuilder</span></span><br /><br /> <span data-ttu-id="514e1-143">パフォーマンスが重視されるメンバーをできるだけ小規模に保つため、次のメンバーは時刻指定されません。</span><span class="sxs-lookup"><span data-stu-id="514e1-143">To keep performance-critical members as small as possible, the following members are not timed:</span></span><br /><br /> <span data-ttu-id="514e1-144">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="514e1-144">SqlDataReader</span></span><br /><br /> <span data-ttu-id="514e1-145">this[] operator (all overloads)</span><span class="sxs-lookup"><span data-stu-id="514e1-145">this[] operator (all overloads)</span></span><br /><br /> <span data-ttu-id="514e1-146">GetBoolean</span><span class="sxs-lookup"><span data-stu-id="514e1-146">GetBoolean</span></span><br /><br /> <span data-ttu-id="514e1-147">GetChar</span><span class="sxs-lookup"><span data-stu-id="514e1-147">GetChar</span></span><br /><br /> <span data-ttu-id="514e1-148">GetDateTime</span><span class="sxs-lookup"><span data-stu-id="514e1-148">GetDateTime</span></span><br /><br /> <span data-ttu-id="514e1-149">GetDecimal</span><span class="sxs-lookup"><span data-stu-id="514e1-149">GetDecimal</span></span><br /><br /> <span data-ttu-id="514e1-150">GetDouble</span><span class="sxs-lookup"><span data-stu-id="514e1-150">GetDouble</span></span><br /><br /> <span data-ttu-id="514e1-151">GetFloat</span><span class="sxs-lookup"><span data-stu-id="514e1-151">GetFloat</span></span><br /><br /> <span data-ttu-id="514e1-152">GetGuid</span><span class="sxs-lookup"><span data-stu-id="514e1-152">GetGuid</span></span><br /><br /> <span data-ttu-id="514e1-153">GetInt16</span><span class="sxs-lookup"><span data-stu-id="514e1-153">GetInt16</span></span><br /><br /> <span data-ttu-id="514e1-154">GetInt32</span><span class="sxs-lookup"><span data-stu-id="514e1-154">GetInt32</span></span><br /><br /> <span data-ttu-id="514e1-155">GetInt64</span><span class="sxs-lookup"><span data-stu-id="514e1-155">GetInt64</span></span><br /><br /> <span data-ttu-id="514e1-156">GetName</span><span class="sxs-lookup"><span data-stu-id="514e1-156">GetName</span></span><br /><br /> <span data-ttu-id="514e1-157">GetOrdinal</span><span class="sxs-lookup"><span data-stu-id="514e1-157">GetOrdinal</span></span><br /><br /> <span data-ttu-id="514e1-158">GetSqlBinary</span><span class="sxs-lookup"><span data-stu-id="514e1-158">GetSqlBinary</span></span><br /><br /> <span data-ttu-id="514e1-159">GetSqlBoolean </span><span class="sxs-lookup"><span data-stu-id="514e1-159">GetSqlBoolean</span></span><br /><br /> <span data-ttu-id="514e1-160">GetSqlByte </span><span class="sxs-lookup"><span data-stu-id="514e1-160">GetSqlByte</span></span><br /><br /> <span data-ttu-id="514e1-161">GetSqlDateTime </span><span class="sxs-lookup"><span data-stu-id="514e1-161">GetSqlDateTime</span></span><br /><br /> <span data-ttu-id="514e1-162">GetSqlDecimal </span><span class="sxs-lookup"><span data-stu-id="514e1-162">GetSqlDecimal</span></span><br /><br /> <span data-ttu-id="514e1-163">GetSqlDouble </span><span class="sxs-lookup"><span data-stu-id="514e1-163">GetSqlDouble</span></span><br /><br /> <span data-ttu-id="514e1-164">GetSqlGuid </span><span class="sxs-lookup"><span data-stu-id="514e1-164">GetSqlGuid</span></span><br /><br /> <span data-ttu-id="514e1-165">GetSqlInt16 </span><span class="sxs-lookup"><span data-stu-id="514e1-165">GetSqlInt16</span></span><br /><br /> <span data-ttu-id="514e1-166">GetSqlInt32 </span><span class="sxs-lookup"><span data-stu-id="514e1-166">GetSqlInt32</span></span><br /><br /> <span data-ttu-id="514e1-167">GetSqlInt64 </span><span class="sxs-lookup"><span data-stu-id="514e1-167">GetSqlInt64</span></span><br /><br /> <span data-ttu-id="514e1-168">GetSqlMoney </span><span class="sxs-lookup"><span data-stu-id="514e1-168">GetSqlMoney</span></span><br /><br /> <span data-ttu-id="514e1-169">GetSqlSingle </span><span class="sxs-lookup"><span data-stu-id="514e1-169">GetSqlSingle</span></span><br /><br /> <span data-ttu-id="514e1-170">GetSqlString </span><span class="sxs-lookup"><span data-stu-id="514e1-170">GetSqlString</span></span><br /><br /> <span data-ttu-id="514e1-171">GetString</span><span class="sxs-lookup"><span data-stu-id="514e1-171">GetString</span></span><br /><br /> <span data-ttu-id="514e1-172">IsDBNull</span><span class="sxs-lookup"><span data-stu-id="514e1-172">IsDBNull</span></span>|  
|`IduCount`|<span data-ttu-id="514e1-173">アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後に接続を通じて実行された、INSERT、DELETE、および UPDATE ステートメントの合計数を返します。</span><span class="sxs-lookup"><span data-stu-id="514e1-173">Returns the total number of INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`IduRows`|<span data-ttu-id="514e1-174">アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後に接続を通じて実行された INSERT、DELETE、および UPDATE ステートメントにより影響を受けた、行の合計数を返します。</span><span class="sxs-lookup"><span data-stu-id="514e1-174">Returns the total number of rows affected by INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`NetworkServerTime`|<span data-ttu-id="514e1-175">アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後にプロバイダーがサーバーからの応答を待つために費やした累計時間 (ミリ秒) を返します。</span><span class="sxs-lookup"><span data-stu-id="514e1-175">Returns the cumulative amount of time (in milliseconds) that the provider spent waiting for replies from the server once the application has started using the provider and has enabled statistics.</span></span>|  
|`PreparedExecs`|<span data-ttu-id="514e1-176">アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後に接続を通じて実行された、準備コマンドの数を返します。</span><span class="sxs-lookup"><span data-stu-id="514e1-176">Returns the number of prepared commands executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`Prepares`|<span data-ttu-id="514e1-177">アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後に接続を通じて準備された、ステートメントの数を返します。</span><span class="sxs-lookup"><span data-stu-id="514e1-177">Returns the number of statements prepared through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`SelectCount`|<span data-ttu-id="514e1-178">アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後に接続を通じて実行された、SELECT ステートメントの数を返します。</span><span class="sxs-lookup"><span data-stu-id="514e1-178">Returns the number of SELECT statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="514e1-179">これには、カーソルから行を取得するための FETCH ステートメントが含まれます。SELECT ステートメントのカウントは、<xref:System.Data.SqlClient.SqlDataReader> の末尾に達すると更新されます。</span><span class="sxs-lookup"><span data-stu-id="514e1-179">This includes FETCH statements to retrieve rows from cursors, and the count for SELECT statements is updated when the end of a <xref:System.Data.SqlClient.SqlDataReader> is reached.</span></span>|  
|`SelectRows`|<span data-ttu-id="514e1-180">アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後に選択された、行の数を返します。</span><span class="sxs-lookup"><span data-stu-id="514e1-180">Returns the number of rows selected once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="514e1-181">このカウンターは、実際には呼び出し元により使用されなかった行を含め、SQL ステートメントにより生成されたすべての行を反映します。</span><span class="sxs-lookup"><span data-stu-id="514e1-181">This counter reflects all the rows generated by SQL statements, even those that were not actually consumed by the caller.</span></span> <span data-ttu-id="514e1-182">たとえば、結果セット全体を読み取る前にデータ リーダーを閉じても、カウントには影響しません。</span><span class="sxs-lookup"><span data-stu-id="514e1-182">For example, closing a data reader before reading the entire result set would not affect the count.</span></span> <span data-ttu-id="514e1-183">これには、FETCH ステートメントを通じてカーソルから取得された行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="514e1-183">This includes the rows retrieved from cursors through FETCH statements.</span></span>|  
|`ServerRoundtrips`|<span data-ttu-id="514e1-184">アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後に発生した、接続がサーバーにコマンドを送信して応答を受け取った回数を返します。</span><span class="sxs-lookup"><span data-stu-id="514e1-184">Returns the number of times the connection sent commands to the server and got a reply back once the application has started using the provider and has enabled statistics.</span></span>|  
|`SumResultSets`|<span data-ttu-id="514e1-185">アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後に使用された、結果セットの数を返します。</span><span class="sxs-lookup"><span data-stu-id="514e1-185">Returns the number of result sets that have been used once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="514e1-186">たとえば、これにはクライアントに返されるすべての結果セットが含まれます。</span><span class="sxs-lookup"><span data-stu-id="514e1-186">For example this would include any result set returned to the client.</span></span> <span data-ttu-id="514e1-187">カーソルについては、それぞれのフェッチ操作やブロック フェッチ操作は、単独の結果セットと見なされます。</span><span class="sxs-lookup"><span data-stu-id="514e1-187">For cursors, each fetch or block-fetch operation is considered an independent result set.</span></span>|  
|`Transactions`|<span data-ttu-id="514e1-188">アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後に開始された、ユーザー トランザクションの数を返します。これにはロールバックが含まれます。</span><span class="sxs-lookup"><span data-stu-id="514e1-188">Returns the number of user transactions started once the application has started using the provider and has enabled statistics, including rollbacks.</span></span> <span data-ttu-id="514e1-189">自動コミットがオンの状態で接続が実行されている場合、各コマンドはトランザクションと見なされます。</span><span class="sxs-lookup"><span data-stu-id="514e1-189">If a connection is running with auto commit on, each command is considered a transaction.</span></span><br /><br /> <span data-ttu-id="514e1-190">このカウンターは、トランザクションがコミットされるかどうか、または後にロール バックされるかどうかに関係なく、BEGIN TRAN ステートメントが実行された直後に、トランザクション カウントをインクリメントします。</span><span class="sxs-lookup"><span data-stu-id="514e1-190">This counter increments the transaction count as soon as a BEGIN TRAN statement is executed, regardless of whether the transaction is committed or rolled back later.</span></span>|  
|`UnpreparedExecs`|<span data-ttu-id="514e1-191">アプリケーションがプロバイダーを使って開始され、統計情報が有効になった後に接続を通じて準備解除された、ステートメントの数を返します。</span><span class="sxs-lookup"><span data-stu-id="514e1-191">Returns the number of unprepared statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
  
### <a name="retrieving-a-value"></a><span data-ttu-id="514e1-192">値の取得</span><span class="sxs-lookup"><span data-stu-id="514e1-192">Retrieving a Value</span></span>  
 <span data-ttu-id="514e1-193">次のコンソール アプリケーションは、接続で統計情報を有効にして、4 つの各統計情報の値を取得し、コンソール ウィンドウに出力する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="514e1-193">The following console application shows how to enable statistics on a connection, retrieve four individual statistic values, and write them out to the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="514e1-194">次の例は、サンプル**AdventureWorks** SQL Server に付属のデータベースです。</span><span class="sxs-lookup"><span data-stu-id="514e1-194">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="514e1-195">サンプル コードの接続文字列は、データベースがローカルのコンピューターにインストールされて利用可能な状態になっていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="514e1-195">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="514e1-196">必要に応じて、お使いの環境に合わせて接続文字列を変更してください。</span><span class="sxs-lookup"><span data-stu-id="514e1-196">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the   
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      ' Retrieve a few individual values  
      ' related to the previous command.  
      Dim bytesReceived As Long = _  
          CLng(currentStatistics.Item("BytesReceived"))  
      Dim bytesSent As Long = _  
          CLng(currentStatistics.Item("BytesSent"))  
      Dim selectCount As Long = _  
          CLng(currentStatistics.Item("SelectCount"))  
      Dim selectRows As Long = _  
          CLng(currentStatistics.Item("SelectRows"))  
  
      Console.WriteLine("BytesReceived: " & bytesReceived.ToString())  
      Console.WriteLine("BytesSent: " & bytesSent.ToString())  
      Console.WriteLine("SelectCount: " & selectCount.ToString())  
      Console.WriteLine("SelectRows: " & selectRows.ToString())  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrive it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetValue  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =   
          new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
          awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
          currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        // Retrieve a few individual values  
        // related to the previous command.  
        long bytesReceived =  
            (long) currentStatistics["BytesReceived"];  
        long bytesSent =  
            (long) currentStatistics["BytesSent"];  
        long selectCount =  
            (long) currentStatistics["SelectCount"];  
        long selectRows =  
            (long) currentStatistics["SelectRows"];  
  
        Console.WriteLine("BytesReceived: " +  
            bytesReceived.ToString());  
        Console.WriteLine("BytesSent: " +  
            bytesSent.ToString());  
        Console.WriteLine("SelectCount: " +  
            selectCount.ToString());  
        Console.WriteLine("SelectRows: " +  
            selectRows.ToString());  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrive it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a><span data-ttu-id="514e1-197">すべての値の取得</span><span class="sxs-lookup"><span data-stu-id="514e1-197">Retrieving All Values</span></span>  
 <span data-ttu-id="514e1-198">次のコンソール アプリケーションは、接続で統計情報を有効にし、使用可能なすべての統計情報の値を列挙子を使って取得して、コンソール ウィンドウに出力する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="514e1-198">The following console application shows how to enable statistics on a connection, retrieve all available statistic values using the enumerator, and write them to the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="514e1-199">次の例は、サンプル**AdventureWorks** SQL Server に付属のデータベースです。</span><span class="sxs-lookup"><span data-stu-id="514e1-199">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="514e1-200">サンプル コードの接続文字列は、データベースがローカルのコンピューターにインストールされて利用可能な状態になっていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="514e1-200">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="514e1-201">必要に応じて、お使いの環境に合わせて接続文字列を変更してください。</span><span class="sxs-lookup"><span data-stu-id="514e1-201">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the   
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      Console.WriteLine("Key Name and Value")  
  
      ' Note the entries are unsorted.  
      For Each entry As DictionaryEntry In currentStatistics  
        Console.WriteLine(entry.Key.ToString() & _  
            ": " & entry.Value.ToString())  
      Next  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrive it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetAll  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =  
            new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
            awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
            currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        Console.WriteLine("Key Name and Value");  
  
        // Note the entries are unsorted.  
        foreach (DictionaryEntry entry in currentStatistics)  
        {  
          Console.WriteLine(entry.Key.ToString() +  
              ": " + entry.Value.ToString());  
        }  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrive it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="514e1-202">関連項目</span><span class="sxs-lookup"><span data-stu-id="514e1-202">See Also</span></span>  
 [<span data-ttu-id="514e1-203">SQL Server と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="514e1-203">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="514e1-204">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="514e1-204">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
