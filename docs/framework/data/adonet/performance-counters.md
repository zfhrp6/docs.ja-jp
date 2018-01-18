---
title: "ADO.NET でのパフォーマンス カウンター"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0b121b71-78f8-4ae2-9aa1-0b2e15778e57
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 729c9d5d6841b5cfcae175d8984302ac816ed8b8
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="performance-counters-in-adonet"></a><span data-ttu-id="6c067-102">ADO.NET でのパフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="6c067-102">Performance Counters in ADO.NET</span></span>
<span data-ttu-id="6c067-103">ADO.NET 2.0 では、<xref:System.Data.SqlClient> と <xref:System.Data.OracleClient> の両方をサポートする新しいパフォーマンス カウンターが導入されました。</span><span class="sxs-lookup"><span data-stu-id="6c067-103">ADO.NET 2.0 introduced expanded support for performance counters that includes support for both <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient>.</span></span> <span data-ttu-id="6c067-104">以前のバージョンの ADO.NET で利用されていた <xref:System.Data.SqlClient> のパフォーマンス カウンターは廃止され、このトピックで説明する新しいパフォーマンス カウンターに置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="6c067-104">The <xref:System.Data.SqlClient> performance counters available in previous versions of ADO.NET have been deprecated and replaced with the new performance counters discussed in this topic.</span></span> <span data-ttu-id="6c067-105">ADO.NET のパフォーマンス カウンターを使用することで、アプリケーションやそれによって使用される接続リソースのステータスを監視できます。</span><span class="sxs-lookup"><span data-stu-id="6c067-105">You can use ADO.NET performance counters to monitor the status of your application and the connection resources that it uses.</span></span> <span data-ttu-id="6c067-106">パフォーマンス カウンターは、Windows パフォーマンス モニターを使って監視できるほか、<xref:System.Diagnostics.PerformanceCounter> 名前空間の <xref:System.Diagnostics> クラスを使用することでプログラムから監視することもできます。</span><span class="sxs-lookup"><span data-stu-id="6c067-106">Performance counters can be monitored by using Windows Performance Monitor or can be accessed programmatically using the <xref:System.Diagnostics.PerformanceCounter> class in the <xref:System.Diagnostics> namespace.</span></span>  
  
## <a name="available-performance-counters"></a><span data-ttu-id="6c067-107">利用可能なパフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="6c067-107">Available Performance Counters</span></span>  
 <span data-ttu-id="6c067-108">次の表に示したように、<xref:System.Data.SqlClient> および <xref:System.Data.OracleClient> には現在、14 種類のパフォーマンス カウンターが存在します。</span><span class="sxs-lookup"><span data-stu-id="6c067-108">Currently there are 14 different performance counters available for <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient> as described in the following table.</span></span> <span data-ttu-id="6c067-109">個々のカウンターの名前は、Microsoft .NET Framework の地域別バージョン全体でローカライズされているわけではないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6c067-109">Note that the names for the individual counters are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="6c067-110">パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="6c067-110">Performance counter</span></span>|<span data-ttu-id="6c067-111">説明</span><span class="sxs-lookup"><span data-stu-id="6c067-111">Description</span></span>|  
|-------------------------|-----------------|  
|`HardConnectsPerSecond`|<span data-ttu-id="6c067-112">データベース サーバーに対する 1 秒あたりの接続数。</span><span class="sxs-lookup"><span data-stu-id="6c067-112">The number of connections per second that are being made to a database server.</span></span>|  
|`HardDisconnectsPerSecond`|<span data-ttu-id="6c067-113">データベース サーバーに対する 1 秒あたりの切断数。</span><span class="sxs-lookup"><span data-stu-id="6c067-113">The number of disconnects per second that are being made to a database server.</span></span>|  
|`NumberOfActiveConnectionPoolGroups`|<span data-ttu-id="6c067-114">アクティブな一意の接続プール グループの数。</span><span class="sxs-lookup"><span data-stu-id="6c067-114">The number of unique connection pool groups that are active.</span></span> <span data-ttu-id="6c067-115">このカウンターは、AppDomain に見つかった一意の接続文字列数によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="6c067-115">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|  
|`NumberOfActiveConnectionPools`|<span data-ttu-id="6c067-116">接続プールの合計数。</span><span class="sxs-lookup"><span data-stu-id="6c067-116">The total number of connection pools.</span></span>|  
|`NumberOfActiveConnections`|<span data-ttu-id="6c067-117">現在使用中のアクティブな接続の数。</span><span class="sxs-lookup"><span data-stu-id="6c067-117">The number of active connections that are currently in use.</span></span> <span data-ttu-id="6c067-118">**注:**既定でこのパフォーマンス カウンターが有効にできません。</span><span class="sxs-lookup"><span data-stu-id="6c067-118">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="6c067-119">このパフォーマンス カウンターを有効にするを参照してください。[既定ではオフになってカウンターのアクティブ化](#ActivatingOffByDefault)です。</span><span class="sxs-lookup"><span data-stu-id="6c067-119">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`NumberOfFreeConnections`|<span data-ttu-id="6c067-120">接続プール内の利用可能な接続数。</span><span class="sxs-lookup"><span data-stu-id="6c067-120">The number of connections available for use in the connection pools.</span></span> <span data-ttu-id="6c067-121">**注:**既定でこのパフォーマンス カウンターが有効にできません。</span><span class="sxs-lookup"><span data-stu-id="6c067-121">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="6c067-122">このパフォーマンス カウンターを有効にするを参照してください。[既定ではオフになってカウンターのアクティブ化](#ActivatingOffByDefault)です。</span><span class="sxs-lookup"><span data-stu-id="6c067-122">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`NumberOfInactiveConnectionPoolGroups`|<span data-ttu-id="6c067-123">排除対象としてマークされた一意の接続プール グループの数。</span><span class="sxs-lookup"><span data-stu-id="6c067-123">The number of unique connection pool groups that are marked for pruning.</span></span> <span data-ttu-id="6c067-124">このカウンターは、AppDomain に見つかった一意の接続文字列数によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="6c067-124">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|  
|`NumberOfInactiveConnectionPools`|<span data-ttu-id="6c067-125">最近のアクティビティが存在せず、破棄待ち状態となっている、アクティブでない接続プールの数。</span><span class="sxs-lookup"><span data-stu-id="6c067-125">The number of inactive connection pools that have not had any recent activity and are waiting to be disposed.</span></span>|  
|`NumberOfNonPooledConnections`|<span data-ttu-id="6c067-126">プールされていないアクティブな接続の数。</span><span class="sxs-lookup"><span data-stu-id="6c067-126">The number of active connections that are not pooled.</span></span>|  
|`NumberOfPooledConnections`|<span data-ttu-id="6c067-127">接続プール インフラストラクチャによって管理されているアクティブな接続の数。</span><span class="sxs-lookup"><span data-stu-id="6c067-127">The number of active connections that are being managed by the connection pooling infrastructure.</span></span>|  
|`NumberOfReclaimedConnections`|<span data-ttu-id="6c067-128">アプリケーションによって `Close` も `Dispose` も呼び出されなかった場合に、ガベージ コレクションによって回収された接続の数。</span><span class="sxs-lookup"><span data-stu-id="6c067-128">The number of connections that have been reclaimed through garbage collection where `Close` or `Dispose` was not called by the application.</span></span> <span data-ttu-id="6c067-129">接続を明示的に閉じるか破棄しないと、パフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="6c067-129">Not explicitly closing or disposing connections hurts performance.</span></span>|  
|`NumberOfStasisConnections`|<span data-ttu-id="6c067-130">現在アクションの完了を待っている (そのためにアプリケーションからは使用できない) 接続の数。</span><span class="sxs-lookup"><span data-stu-id="6c067-130">The number of connections currently awaiting completion of an action and which are therefore unavailable for use by your application.</span></span>|  
|`SoftConnectsPerSecond`|<span data-ttu-id="6c067-131">接続プールからプルされているアクティブな接続の数。</span><span class="sxs-lookup"><span data-stu-id="6c067-131">The number of active connections being pulled from the connection pool.</span></span> <span data-ttu-id="6c067-132">**注:**既定でこのパフォーマンス カウンターが有効にできません。</span><span class="sxs-lookup"><span data-stu-id="6c067-132">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="6c067-133">このパフォーマンス カウンターを有効にするを参照してください。[既定ではオフになってカウンターのアクティブ化](#ActivatingOffByDefault)です。</span><span class="sxs-lookup"><span data-stu-id="6c067-133">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`SoftDisconnectsPerSecond`|<span data-ttu-id="6c067-134">接続プールに戻されているアクティブな接続の数。</span><span class="sxs-lookup"><span data-stu-id="6c067-134">The number of active connections that are being returned to the connection pool.</span></span> <span data-ttu-id="6c067-135">**注:**既定でこのパフォーマンス カウンターが有効にできません。</span><span class="sxs-lookup"><span data-stu-id="6c067-135">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="6c067-136">このパフォーマンス カウンターを有効にするを参照してください。[既定ではオフになってカウンターのアクティブ化](#ActivatingOffByDefault)です。</span><span class="sxs-lookup"><span data-stu-id="6c067-136">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
  
### <a name="connection-pool-groups-and-connection-pools"></a><span data-ttu-id="6c067-137">接続プール グループと接続プール</span><span class="sxs-lookup"><span data-stu-id="6c067-137">Connection Pool Groups and Connection Pools</span></span>  
 <span data-ttu-id="6c067-138">Windows 認証 (統合セキュリティ) を使用している場合、`NumberOfActiveConnectionPoolGroups` と `NumberOfActiveConnectionPools` の両方のパフォーマンス カウンターを監視する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c067-138">When using Windows Authentication (integrated security), you must monitor both the `NumberOfActiveConnectionPoolGroups` and `NumberOfActiveConnectionPools` performance counters.</span></span> <span data-ttu-id="6c067-139">なぜなら、接続プール グループは接続文字列単位でマップされるためです。</span><span class="sxs-lookup"><span data-stu-id="6c067-139">The reason is that connection pool groups map to unique connection strings.</span></span> <span data-ttu-id="6c067-140">統合セキュリティを使用した場合、接続文字列にマップされた接続プールの他に、個々の Windows ID 用に別々のプールが作成されます。</span><span class="sxs-lookup"><span data-stu-id="6c067-140">When integrated security is used, connection pools map to connection strings and additionally create separate pools for individual Windows identities.</span></span> <span data-ttu-id="6c067-141">たとえば、同じ AppDomain に属する Fred と Julie が、どちらも `"Data Source=MySqlServer;Integrated Security=true"` という接続文字列を使用した場合、その接続文字列に対応した接続プール グループが作成され、それに加えて、2 つのプール (Fred 用と Julie 用) が作成されます。</span><span class="sxs-lookup"><span data-stu-id="6c067-141">For example, if Fred and Julie, each within the same AppDomain, both use the connection string `"Data Source=MySqlServer;Integrated Security=true"`, a connection pool group is created for the connection string, and two additional pools are created, one for Fred and one for Julie.</span></span> <span data-ttu-id="6c067-142">John と Martha が同一の SQL Server ログインで接続文字列を使用する場合`"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`の 1 つのプールのみが作成され、 **lowPrivUser**の id。</span><span class="sxs-lookup"><span data-stu-id="6c067-142">If John and Martha use a connection string with an identical SQL Server login, `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`, then only a single pool is created for the **lowPrivUser** identity.</span></span>  
  
<a name="ActivatingOffByDefault"></a>   
### <a name="activating-off-by-default-counters"></a><span data-ttu-id="6c067-143">既定ではオフになっているカウンターのアクティブ化</span><span class="sxs-lookup"><span data-stu-id="6c067-143">Activating Off-By-Default Counters</span></span>  
 <span data-ttu-id="6c067-144">`NumberOfFreeConnections`、`NumberOfActiveConnections`、`SoftDisconnectsPerSecond`、`SoftConnectsPerSecond` の各パフォーマンス カウンターは、既定ではオフになっています。</span><span class="sxs-lookup"><span data-stu-id="6c067-144">The performance counters `NumberOfFreeConnections`, `NumberOfActiveConnections`, `SoftDisconnectsPerSecond`, and `SoftConnectsPerSecond` are off by default.</span></span> <span data-ttu-id="6c067-145">有効にするには、アプリケーションの構成ファイルに次の情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="6c067-145">Add the following information to the application's configuration file to enable them:</span></span>  
  
```xml  
<system.diagnostics>  
  <switches>  
    <add name="ConnectionPoolPerformanceCounterDetail"  
         value="4"/>  
  </switches>  
</system.diagnostics>  
```  
  
## <a name="retrieving-performance-counter-values"></a><span data-ttu-id="6c067-146">パフォーマンス カウンターの値の取得</span><span class="sxs-lookup"><span data-stu-id="6c067-146">Retrieving Performance Counter Values</span></span>  
 <span data-ttu-id="6c067-147">次のコンソール アプリケーションは、アプリケーションでパフォーマンス カウンターの値を取得する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="6c067-147">The following console application shows how to retrieve performance counter values in your application.</span></span> <span data-ttu-id="6c067-148">すべての ADO.NET パフォーマンス カウンターの情報を取得できるように、接続を開いてアクティブにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c067-148">Connections must be open and active for information to be returned for all of the ADO.NET performance counters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c067-149">この例は、サンプルを使用して**AdventureWorks**データベースに含まれている[!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="6c067-149">This example uses the sample **AdventureWorks** database included with [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6c067-150">サンプル コードの接続文字列は、データベースがローカル コンピューターにインストールされていること、SqlExpress というインスタンス名で実行されていること、接続文字列に指定された情報と一致する SQL Server ログインが作成済みであることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="6c067-150">The connection strings provided in the sample code assume that the database is installed and available on the local computer with an instance name of SqlExpress, and that you have created SQL Server logins that match those supplied in the connection strings.</span></span> <span data-ttu-id="6c067-151">既定のセキュリティ設定を使用するようにサーバーが構成されている場合、そのままでは Windows 認証しか許可されないため、SQL Server ログインを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c067-151">You may need to enable SQL Server logins if your server is configured using the default security settings which allow only Windows Authentication.</span></span> <span data-ttu-id="6c067-152">接続文字列は環境に合わせて変更してください。</span><span class="sxs-lookup"><span data-stu-id="6c067-152">Modify the connection strings as necessary to suit your environment.</span></span>  
  
### <a name="example"></a><span data-ttu-id="6c067-153">例</span><span class="sxs-lookup"><span data-stu-id="6c067-153">Example</span></span>  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System.Data.SqlClient  
Imports System.Diagnostics  
Imports System.Runtime.InteropServices  
  
Class Program  
  
    Private PerfCounters(9) As PerformanceCounter  
    Private connection As SqlConnection = New SqlConnection  
  
    Public Shared Sub Main()  
        Dim prog As Program = New Program  
        ' Open a connection and create the performance counters.   
        prog.connection.ConnectionString = _  
           GetIntegratedSecurityConnectionString()  
        prog.SetUpPerformanceCounters()  
        Console.WriteLine("Available Performance Counters:")  
  
        ' Create the connections and display the results.  
        prog.CreateConnections()  
        Console.WriteLine("Press Enter to finish.")  
        Console.ReadLine()  
    End Sub  
  
    Private Sub CreateConnections()  
        ' List the Performance counters.  
        WritePerformanceCounters()  
  
        ' Create 4 connections and display counter information.  
        Dim connection1 As SqlConnection = New SqlConnection( _  
           GetIntegratedSecurityConnectionString)  
        connection1.Open()  
        Console.WriteLine("Opened the 1st Connection:")  
        WritePerformanceCounters()  
  
        Dim connection2 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionStringDifferent)  
        connection2.Open()  
        Console.WriteLine("Opened the 2nd Connection:")  
        WritePerformanceCounters()  
  
        Console.WriteLine("Opened the 3rd Connection:")  
        Dim connection3 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionString)  
        connection3.Open()  
        WritePerformanceCounters()  
  
        Dim connection4 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionString)  
        connection4.Open()  
        Console.WriteLine("Opened the 4th Connection:")  
        WritePerformanceCounters()  
  
        connection1.Close()  
        Console.WriteLine("Closed the 1st Connection:")  
        WritePerformanceCounters()  
  
        connection2.Close()  
        Console.WriteLine("Closed the 2nd Connection:")  
        WritePerformanceCounters()  
  
        connection3.Close()  
        Console.WriteLine("Closed the 3rd Connection:")  
        WritePerformanceCounters()  
  
        connection4.Close()  
        Console.WriteLine("Closed the 4th Connection:")  
        WritePerformanceCounters()  
    End Sub  
  
    Private Enum ADO_Net_Performance_Counters  
        NumberOfActiveConnectionPools  
        NumberOfReclaimedConnections  
        HardConnectsPerSecond  
        HardDisconnectsPerSecond  
        NumberOfActiveConnectionPoolGroups  
        NumberOfInactiveConnectionPoolGroups  
        NumberOfInactiveConnectionPools  
        NumberOfNonPooledConnections  
        NumberOfPooledConnections  
        NumberOfStasisConnections  
        ' The following performance counters are more expensive to track.  
        ' Enable ConnectionPoolPerformanceCounterDetail in your config file.  
        '     SoftConnectsPerSecond  
        '     SoftDisconnectsPerSecond  
        '     NumberOfActiveConnections  
        '     NumberOfFreeConnections  
    End Enum  
  
    Private Sub SetUpPerformanceCounters()  
        connection.Close()  
        Me.PerfCounters(9) = New PerformanceCounter()  
  
        Dim instanceName As String = GetInstanceName()  
        Dim apc As Type = GetType(ADO_Net_Performance_Counters)  
        Dim i As Integer = 0  
        Dim s As String = ""  
        For Each s In [Enum].GetNames(apc)  
            Me.PerfCounters(i) = New PerformanceCounter()  
            Me.PerfCounters(i).CategoryName = ".NET Data Provider for SqlServer"  
            Me.PerfCounters(i).CounterName = s  
            Me.PerfCounters(i).InstanceName = instanceName  
            i = (i + 1)  
        Next  
    End Sub  
  
    Private Declare Function GetCurrentProcessId Lib "kernel32.dll" () As Integer  
  
    Private Function GetInstanceName() As String  
        'This works for Winforms apps.   
        Dim instanceName As String = _  
           System.Reflection.Assembly.GetEntryAssembly.GetName.Name  
  
        ' Must replace special characters like (, ), #, /, \\   
        Dim instanceName2 As String = _  
           AppDomain.CurrentDomain.FriendlyName.ToString.Replace("(", "[") _  
           .Replace(")", "]").Replace("#", "_").Replace("/", "_").Replace("\\", "_")  
  
        'For ASP.NET applications your instanceName will be your CurrentDomain's   
        'FriendlyName. Replace the line above that sets the instanceName with this:   
        'instanceName = AppDomain.CurrentDomain.FriendlyName.ToString.Replace("(", "[") _  
        '    .Replace(")", "]").Replace("#", "_").Replace("/", "_").Replace("\\", "_")  
  
        Dim pid As String = GetCurrentProcessId.ToString  
        instanceName = (instanceName + ("[" & (pid & "]")))  
        Console.WriteLine("Instance Name: {0}", instanceName)  
        Console.WriteLine("---------------------------")  
        Return instanceName  
    End Function  
  
    Private Sub WritePerformanceCounters()  
        Console.WriteLine("---------------------------")  
        For Each p As PerformanceCounter In Me.PerfCounters  
            Console.WriteLine("{0} = {1}", p.CounterName, p.NextValue)  
        Next  
        Console.WriteLine("---------------------------")  
    End Sub  
  
    Private Shared Function GetIntegratedSecurityConnectionString() As String  
        ' To avoid storing the connection string in your code,   
        ' you can retrive it from a configuration file.   
        Return ("Data Source=.\SqlExpress;Integrated Security=True;" &   
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionString() As String  
        ' To avoid storing the connection string in your code,   
        ' you can retrive it from a configuration file.   
        Return ("Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" &   
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionStringDifferent() As String  
        ' To avoid storing the connection string in your code,   
        ' you can retrive it from a configuration file.   
        Return ("Initial Catalog=AdventureWorks;Data Source=.\SqlExpress;" & _  
          "User Id=LowPriv;Password=Data!05;")  
    End Function  
End Class  
```  
  
```csharp  
using System;  
using System.Data.SqlClient;  
using System.Diagnostics;  
using System.Runtime.InteropServices;  
  
class Program  
{  
    PerformanceCounter[] PerfCounters = new PerformanceCounter[10];  
    SqlConnection connection = new SqlConnection();  
  
    static void Main()  
    {  
        Program prog = new Program();  
        // Open a connection and create the performance counters.  
        prog.connection.ConnectionString =  
           GetIntegratedSecurityConnectionString();  
        prog.SetUpPerformanceCounters();  
        Console.WriteLine("Available Performance Counters:");  
  
        // Create the connections and display the results.  
        prog.CreateConnections();  
        Console.WriteLine("Press Enter to finish.");  
        Console.ReadLine();  
    }  
  
    private void CreateConnections()  
    {  
        // List the Performance counters.  
        WritePerformanceCounters();  
  
        // Create 4 connections and display counter information.  
        SqlConnection connection1 = new SqlConnection(  
              GetIntegratedSecurityConnectionString());  
        connection1.Open();  
        Console.WriteLine("Opened the 1st Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection2 = new SqlConnection(  
              GetSqlConnectionStringDifferent());  
        connection2.Open();  
        Console.WriteLine("Opened the 2nd Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection3 = new SqlConnection(  
              GetSqlConnectionString());  
        connection3.Open();  
        Console.WriteLine("Opened the 3rd Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection4 = new SqlConnection(  
              GetSqlConnectionString());  
        connection4.Open();  
        Console.WriteLine("Opened the 4th Connection:");  
        WritePerformanceCounters();  
  
        connection1.Close();  
        Console.WriteLine("Closed the 1st Connection:");  
        WritePerformanceCounters();  
  
        connection2.Close();  
        Console.WriteLine("Closed the 2nd Connection:");  
        WritePerformanceCounters();  
  
        connection3.Close();  
        Console.WriteLine("Closed the 3rd Connection:");  
        WritePerformanceCounters();  
  
        connection4.Close();  
        Console.WriteLine("Closed the 4th Connection:");  
        WritePerformanceCounters();  
    }  
  
    private enum ADO_Net_Performance_Counters  
    {  
        NumberOfActiveConnectionPools,  
        NumberOfReclaimedConnections,  
        HardConnectsPerSecond,  
        HardDisconnectsPerSecond,  
        NumberOfActiveConnectionPoolGroups,  
        NumberOfInactiveConnectionPoolGroups,  
        NumberOfInactiveConnectionPools,  
        NumberOfNonPooledConnections,  
        NumberOfPooledConnections,  
        NumberOfStasisConnections  
        // The following performance counters are more expensive to track.  
        // Enable ConnectionPoolPerformanceCounterDetail in your config file.  
        //     SoftConnectsPerSecond  
        //     SoftDisconnectsPerSecond  
        //     NumberOfActiveConnections  
        //     NumberOfFreeConnections  
    }  
  
    private void SetUpPerformanceCounters()  
    {  
        connection.Close();  
        this.PerfCounters = new PerformanceCounter[10];  
        string instanceName = GetInstanceName();  
        Type apc = typeof(ADO_Net_Performance_Counters);  
        int i = 0;  
        foreach (string s in Enum.GetNames(apc))  
        {  
            this.PerfCounters[i] = new PerformanceCounter();  
            this.PerfCounters[i].CategoryName = ".NET Data Provider for SqlServer";  
            this.PerfCounters[i].CounterName = s;  
            this.PerfCounters[i].InstanceName = instanceName;  
            i++;  
        }  
    }  
  
    [DllImport("kernel32.dll", SetLastError = true)]  
    static extern int GetCurrentProcessId();  
  
    private string GetInstanceName()  
    {  
        //This works for Winforms apps.  
        string instanceName =  
            System.Reflection.Assembly.GetEntryAssembly().GetName().Name;  
  
        // Must replace special characters like (, ), #, /, \\  
        string instanceName2 =  
            AppDomain.CurrentDomain.FriendlyName.ToString().Replace('(', '[')  
            .Replace(')', ']').Replace('#', '_').Replace('/', '_').Replace('\\', '_');  
  
        // For ASP.NET applications your instanceName will be your CurrentDomain's   
        // FriendlyName. Replace the line above that sets the instanceName with this:  
        // instanceName = AppDomain.CurrentDomain.FriendlyName.ToString().Replace('(','[')  
        // .Replace(')',']').Replace('#','_').Replace('/','_').Replace('\\','_');  
  
        string pid = GetCurrentProcessId().ToString();  
        instanceName = instanceName + "[" + pid + "]";  
        Console.WriteLine("Instance Name: {0}", instanceName);  
        Console.WriteLine("---------------------------");  
        return instanceName;  
    }  
  
    private void WritePerformanceCounters()  
    {  
        Console.WriteLine("---------------------------");  
        foreach (PerformanceCounter p in this.PerfCounters)  
        {  
            Console.WriteLine("{0} = {1}", p.CounterName, p.NextValue());  
        }  
        Console.WriteLine("---------------------------");  
    }  
  
    private static string GetIntegratedSecurityConnectionString()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrive it from a configuration file.  
        return @"Data Source=.\SqlExpress;Integrated Security=True;" +  
          "Initial Catalog=AdventureWorks";  
    }  
    private static string GetSqlConnectionString()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrive it from a configuration file.  
        return @"Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" +  
        //  "Initial Catalog=AdventureWorks";  
    }  
  
    private static string GetSqlConnectionStringDifferent()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrive it from a configuration file.  
        return @"Initial Catalog=AdventureWorks;Data Source=.\SqlExpress;" +  
          "User Id=LowPriv;Password=Data!05;";  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c067-154">参照</span><span class="sxs-lookup"><span data-stu-id="6c067-154">See Also</span></span>  
 [<span data-ttu-id="6c067-155">データ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="6c067-155">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="6c067-156">OLE DB、ODBC、および Oracle 接続プール</span><span class="sxs-lookup"><span data-stu-id="6c067-156">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 [<span data-ttu-id="6c067-157">ASP.NET 用のパフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="6c067-157">Performance Counters for ASP.NET</span></span>](http://msdn.microsoft.com/library/1e122fcb-05c0-4f9f-bef1-f47023fa1ac6)  
 [<span data-ttu-id="6c067-158">ランタイム プロファイリング</span><span class="sxs-lookup"><span data-stu-id="6c067-158">Runtime Profiling</span></span>](../../../../docs/framework/debug-trace-profile/runtime-profiling.md)  
 [<span data-ttu-id="6c067-159">パフォーマンスしきい値の監視の概要</span><span class="sxs-lookup"><span data-stu-id="6c067-159">Introduction to Monitoring Performance Thresholds</span></span>](http://msdn.microsoft.com/en-us/d40f10b9-e2b7-4ec8-a9b3-706929e5bf35)  
 [<span data-ttu-id="6c067-160">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="6c067-160">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
