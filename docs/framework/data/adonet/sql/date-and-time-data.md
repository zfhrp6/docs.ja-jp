---
title: "日付と時刻のデータ"
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
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a547bbb38d58d5b4c22e78bfd64fef4094865143
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="date-and-time-data"></a><span data-ttu-id="06bc6-102">日付と時刻のデータ</span><span class="sxs-lookup"><span data-stu-id="06bc6-102">Date and Time Data</span></span>
<span data-ttu-id="06bc6-103">SQL Server 2008 では、日付と時刻の情報を扱うための新しいデータ型が導入されました。</span><span class="sxs-lookup"><span data-stu-id="06bc6-103">SQL Server 2008 introduces new data types for handling date and time information.</span></span> <span data-ttu-id="06bc6-104">新しいデータ型には、日付と時刻の別個のデータ型と、範囲、有効桁数、タイム ゾーン処理が向上した拡張データ型が含まれています。</span><span class="sxs-lookup"><span data-stu-id="06bc6-104">The new data types include separate types for date and time, and expanded data types with greater range, precision, and time-zone awareness.</span></span> <span data-ttu-id="06bc6-105">.NET Framework 3.5 Service Pack (SP) 1 以降では、.NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) が SQL Server 2008 データベース エンジンの新機能すべてをサポートします。</span><span class="sxs-lookup"><span data-stu-id="06bc6-105">Starting with the .NET Framework version 3.5 Service Pack (SP) 1, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides full support for all the new features of the SQL Server 2008 Database Engine.</span></span> <span data-ttu-id="06bc6-106">SqlClient でこれらの新機能を使用するには、.NET Framework 3.5 SP1 以降をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="06bc6-106">You must install the .NET Framework 3.5 SP1 (or later) to use these new features with SqlClient.</span></span>  
  
 <span data-ttu-id="06bc6-107">SQL Server 2008 より前のバージョンの SQL Server では、日付と時刻に使用できるデータ型には `datetime` と `smalldatetime` の 2 つしかありませんでした。</span><span class="sxs-lookup"><span data-stu-id="06bc6-107">Versions of SQL Server earlier than SQL Server 2008 only had two data types for working with date and time values: `datetime` and `smalldatetime`.</span></span> <span data-ttu-id="06bc6-108">どちらのデータ型も日付値と時刻値の両方を保持するため、日付と時刻のどちらか一方の値のみを使用するのが困難でした。</span><span class="sxs-lookup"><span data-stu-id="06bc6-108">Both of these data types contain both the date value and a time value, which makes it difficult to work with only date or only time values.</span></span> <span data-ttu-id="06bc6-109">また、これらのデータ型でサポートされる日付は、英国で 1753 年にグレゴリオ暦が導入された後の日付に限られています。</span><span class="sxs-lookup"><span data-stu-id="06bc6-109">Also, these data types only support dates that occur after the introduction of the Gregorian calendar in England in 1753.</span></span> <span data-ttu-id="06bc6-110">もう 1 つの制限は、これらの古いデータ型はタイム ゾーンを処理できないことです。その結果、複数のタイム ゾーンから送られてくるデータの処理が難しくなっています。</span><span class="sxs-lookup"><span data-stu-id="06bc6-110">Another limitation is that these older data types are not time-zone aware, which makes it difficult to work with data that originates from multiple time zones.</span></span>  
  
 <span data-ttu-id="06bc6-111">SQL Server のデータ型に関する完全な説明は、SQL Server オンライン ブックに記載されています。</span><span class="sxs-lookup"><span data-stu-id="06bc6-111">Complete documentation for SQL Server data types is available in SQL Server Books Online.</span></span> <span data-ttu-id="06bc6-112">次の表は、バージョン別の日付と時刻のデータに関する初歩的なトピックの一覧です。</span><span class="sxs-lookup"><span data-stu-id="06bc6-112">The following table lists the version-specific entry-level topics for date and time data.</span></span>  
  
 <span data-ttu-id="06bc6-113">**SQL Server オンライン ブック**</span><span class="sxs-lookup"><span data-stu-id="06bc6-113">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="06bc6-114">日付と時刻のデータを使用します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-114">Using Date and Time Data</span></span>](http://go.microsoft.com/fwlink/?LinkID=98361)  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a><span data-ttu-id="06bc6-115">SQL Server 2008 で導入された日付/時刻データ型</span><span class="sxs-lookup"><span data-stu-id="06bc6-115">Date/Time Data Types Introduced in SQL Server 2008</span></span>  
 <span data-ttu-id="06bc6-116">次の表は、新しい日付と時刻のデータ型の説明です。</span><span class="sxs-lookup"><span data-stu-id="06bc6-116">The following table describes the new date and time data types.</span></span>  
  
|<span data-ttu-id="06bc6-117">SQL Server のデータ型</span><span class="sxs-lookup"><span data-stu-id="06bc6-117">SQL Server data type</span></span>|<span data-ttu-id="06bc6-118">説明</span><span class="sxs-lookup"><span data-stu-id="06bc6-118">Description</span></span>|  
|--------------------------|-----------------|  
|`date`|<span data-ttu-id="06bc6-119">データ型 `date` の範囲は 01 年 1 月 1 日から 9999 年 12 月 31 日までで、精度は 1 日です。</span><span class="sxs-lookup"><span data-stu-id="06bc6-119">The `date` data type has a range of January 1, 01 through December 31, 9999 with an accuracy of 1 day.</span></span> <span data-ttu-id="06bc6-120">既定値は 1900 年 1 月 1 日です。</span><span class="sxs-lookup"><span data-stu-id="06bc6-120">The default value is January 1, 1900.</span></span> <span data-ttu-id="06bc6-121">記憶領域のサイズは 3 バイトです。</span><span class="sxs-lookup"><span data-stu-id="06bc6-121">The storage size is 3 bytes.</span></span>|  
|`time`|<span data-ttu-id="06bc6-122">`time` データ型は、24 時間形式で時刻値のみを格納します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-122">The `time` data type stores time values only, based on a 24-hour clock.</span></span> <span data-ttu-id="06bc6-123">`time` データ型は、00:00:00.0000000 から 23:59:59.9999999 の範囲を 100 ナノ秒の精度で表すことができます。</span><span class="sxs-lookup"><span data-stu-id="06bc6-123">The `time` data type has a range of 00:00:00.0000000 through 23:59:59.9999999 with an accuracy of 100 nanoseconds.</span></span> <span data-ttu-id="06bc6-124">既定値は 00:00:00.0000000 (午前 0 時) です。</span><span class="sxs-lookup"><span data-stu-id="06bc6-124">The default value is 00:00:00.0000000 (midnight).</span></span> <span data-ttu-id="06bc6-125">`time` データ型はユーザー定義による 1 秒未満の時間の有効桁数をサポートし、記憶領域のサイズは、指定された有効桁数に応じて 3 バイト～ 6 バイトになります。</span><span class="sxs-lookup"><span data-stu-id="06bc6-125">The `time` data type supports user-defined fractional second precision, and the storage size varies from 3 to 6 bytes, based on the precision specified.</span></span>|  
|`datetime2`|<span data-ttu-id="06bc6-126">`datetime2` データ型は、`date` 型と `time` 型の範囲および有効桁数を単一のデータ型として組み合わせたものです。</span><span class="sxs-lookup"><span data-stu-id="06bc6-126">The `datetime2` data type combines the range and precision of the `date` and `time` data types into a single data type.</span></span><br /><br /> <span data-ttu-id="06bc6-127">既定値および文字列リテラルの形式は、`date` 型および `time` 型で定義されているものと同じです。</span><span class="sxs-lookup"><span data-stu-id="06bc6-127">The default values and string literal formats are the same as those defined in the `date` and `time` data types.</span></span>|  
|`datetimeoffset`|<span data-ttu-id="06bc6-128">`datetimeoffset` データ型は、`datetime2` のすべての機能に加えて、タイム ゾーン オフセットを持ちます。</span><span class="sxs-lookup"><span data-stu-id="06bc6-128">The `datetimeoffset` data type has all the features of `datetime2` with an additional time zone offset.</span></span> <span data-ttu-id="06bc6-129">タイム ゾーン オフセットは、として表されます。 [+ &#124;-] HH:MM。</span><span class="sxs-lookup"><span data-stu-id="06bc6-129">The time zone offset is represented as [+&#124;-] HH:MM.</span></span> <span data-ttu-id="06bc6-130">HH は、タイム ゾーン オフセットの時間数を表す 00 ～ 14 の 2 桁の数字です。</span><span class="sxs-lookup"><span data-stu-id="06bc6-130">HH is 2 digits ranging from 00 to 14 that represent the number of hours in the time zone offset.</span></span> <span data-ttu-id="06bc6-131">MM は、タイム ゾーン オフセットの付加的な分数を表す 0 ～ 59 の 2 桁の数字です。</span><span class="sxs-lookup"><span data-stu-id="06bc6-131">MM is 2 digits ranging from 00 to 59 that represent the number of additional minutes in the time zone offset.</span></span> <span data-ttu-id="06bc6-132">時刻の精度は 100 ナノ秒までサポートされます。</span><span class="sxs-lookup"><span data-stu-id="06bc6-132">Time formats are supported to 100 nanoseconds.</span></span> <span data-ttu-id="06bc6-133">必須の + 記号または - 記号は、ローカル時刻を取得する際、UTC (協定世界時またはグリニッジ標準時) を基準としてタイム ゾーン オフセットを加算するか、減算するかを示します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-133">The mandatory + or - sign indicates whether the time zone offset is added or subtracted from UTC (Universal Time Coordinate or Greenwich Mean Time) to obtain the local time.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="06bc6-134">`Type System Version` キーワードの使用方法の詳細については、「<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06bc6-134">For more information about using the `Type System Version` keyword, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
## <a name="date-format-and-date-order"></a><span data-ttu-id="06bc6-135">日付書式と表記順序</span><span class="sxs-lookup"><span data-stu-id="06bc6-135">Date Format and Date Order</span></span>  
 <span data-ttu-id="06bc6-136">SQL Server が日付と時刻の値をどのように処理するかは、型システムのバージョンとサーバーのバージョンだけでなく、サーバーの既定の言語と書式設定にも左右されます。</span><span class="sxs-lookup"><span data-stu-id="06bc6-136">How SQL Server parses date and time values depends not only on the type system version and server version, but also on the server's default language and format settings.</span></span> <span data-ttu-id="06bc6-137">日付文字列が、ある言語の日付書式で有効な場合でも、別の言語と日付書式を使用している接続でクエリを実行した場合には意味を持たない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="06bc6-137">A date string that works for the date formats of one language might be unrecognizable if the query is executed by a connection that uses a different language and date format setting.</span></span>  
  
 <span data-ttu-id="06bc6-138">Transact-SQL の SET LANGUAGE ステートメントは、日付の構成要素の並べ方を決定する DATEFORMAT を暗黙に設定します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-138">The Transact-SQL SET LANGUAGE statement implicitly sets the DATEFORMAT that determines the order of the date parts.</span></span> <span data-ttu-id="06bc6-139">日付構成要素の表記順序が MDY、DMY、YMD、YDM、MYD、DYM のいずれであるかを明確にするには、接続で Transact-SQL の SET DATEFORMAT ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-139">You can use the SET DATEFORMAT Transact-SQL statement on a connection to disambiguate date values by ordering the date parts in MDY, DMY, YMD, YDM, MYD, or DYM order.</span></span>  
  
 <span data-ttu-id="06bc6-140">接続で DATEFORMAT を指定しないと、SQL Server はその接続に関連付けられている既定の言語を使用します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-140">If you do not specify any DATEFORMAT for the connection, SQL Server uses the default language associated with the connection.</span></span> <span data-ttu-id="06bc6-141">たとえば、日付文字列 '01/02/03' は、言語が United States English に設定されているサーバーでは MDY (January 2, 2003) として、British English に設定されているサーバーでは DMY (February 1, 2003) として処理されます。</span><span class="sxs-lookup"><span data-stu-id="06bc6-141">For example, a date string of '01/02/03' would be interpreted as MDY (January 2, 2003) on a server with a language setting of United States English, and as DMY (February 1, 2003) on a server with a language setting of British English.</span></span> <span data-ttu-id="06bc6-142">年は、SQL Server の終了年の規則に従って決定されます。この規則では、世紀の値を割り当てるための終了日が定義されます。</span><span class="sxs-lookup"><span data-stu-id="06bc6-142">The year is determined by using SQL Server's cutoff year rule, which defines the cutoff date for assigning the century value.</span></span> <span data-ttu-id="06bc6-143">詳細については、次を参照してください。 [2 つの digit year cutoff オプション](http://go.microsoft.com/fwlink/?LinkId=120473)SQL Server オンライン ブック。</span><span class="sxs-lookup"><span data-stu-id="06bc6-143">For more information, see [two digit year cutoff Option](http://go.microsoft.com/fwlink/?LinkId=120473) in SQL Server Books Online.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06bc6-144">YDM 日付書式は、文字列形式から `date`、`time`、`datetime2`、または `datetimeoffset` に変換する場合にはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="06bc6-144">The YDM date format is not supported when converting from a string format to `date`, `time`, `datetime2`, or `datetimeoffset`.</span></span>  
  
 <span data-ttu-id="06bc6-145">SQL Server が日付と時刻のデータを解釈する方法の詳細については、次を参照してください。[を使用して日付と時刻のデータ](http://go.microsoft.com/fwlink/?LinkID=98361)SQL Server 2008 オンライン ブック。</span><span class="sxs-lookup"><span data-stu-id="06bc6-145">For more information about how SQL Server interprets date and time data, see [Using Date and Time Data](http://go.microsoft.com/fwlink/?LinkID=98361) in SQL Server 2008 Books Online.</span></span>  
  
## <a name="datetime-data-types-and-parameters"></a><span data-ttu-id="06bc6-146">Date/Time データ型とパラメーター</span><span class="sxs-lookup"><span data-stu-id="06bc6-146">Date/Time Data Types and Parameters</span></span>  
 <span data-ttu-id="06bc6-147"><xref:System.Data.SqlClient.SqlParameter> のデータ型は、<xref:System.Data.SqlDbType> 列挙型のいずれかの値を使って指定できます。</span><span class="sxs-lookup"><span data-stu-id="06bc6-147">You can specify the data type of a <xref:System.Data.SqlClient.SqlParameter> by using one of the <xref:System.Data.SqlDbType> enumerations.</span></span> <span data-ttu-id="06bc6-148">新しい日付型と時刻型をサポートするために、<xref:System.Data.SqlDbType> には、次の列挙値が追加されています。</span><span class="sxs-lookup"><span data-stu-id="06bc6-148">The following enumerations have been added to <xref:System.Data.SqlDbType> to support the new date and time data types.</span></span>  
  
-   `SqlDbType.Date`  
  
-   `SqlDbType.Time`  
  
-   `SqlDbType.DateTime2`  
  
-   `SqlDbType.DateTimeOffSet`  
  
 <span data-ttu-id="06bc6-149"><xref:System.Data.SqlClient.SqlParameter> オブジェクトの <xref:System.Data.SqlClient.SqlParameter.DbType%2A> プロパティを特定の `SqlParameter` 列挙値に設定することによって、<xref:System.Data.DbType> の型をジェネリックに指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="06bc6-149">You can also specify the type of a <xref:System.Data.SqlClient.SqlParameter> generically by setting the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> property of a `SqlParameter` object to a particular <xref:System.Data.DbType> enumeration value.</span></span> <span data-ttu-id="06bc6-150"><xref:System.Data.DbType> データ型と `datetime2` データ型をサポートするために、`datetimeoffset` には、次の列挙値が追加されています。</span><span class="sxs-lookup"><span data-stu-id="06bc6-150">The following enumeration values have been added to <xref:System.Data.DbType> to support the `datetime2` and `datetimeoffset` data types:</span></span>  
  
-   <span data-ttu-id="06bc6-151">DbType.DateTime2</span><span class="sxs-lookup"><span data-stu-id="06bc6-151">DbType.DateTime2</span></span>  
  
-   <span data-ttu-id="06bc6-152">DbType.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="06bc6-152">DbType.DateTimeOffset</span></span>  
  
 <span data-ttu-id="06bc6-153">これらの新しい列挙値は、以前のバージョンの .NET Framework に存在した `Date`、`Time`、および `DateTime` の各列挙値を補います。</span><span class="sxs-lookup"><span data-stu-id="06bc6-153">These new enumerations supplement the `Date`, `Time`, and `DateTime` enumerations, which existed in earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="06bc6-154">パラメーター オブジェクトの .NET Framework データ プロバイダー型は、パラメーター オブジェクトの値の .NET Framework 型か、またはパラメーター オブジェクトの `DbType` から推論されます。</span><span class="sxs-lookup"><span data-stu-id="06bc6-154">The .NET Framework data provider type of a parameter object is inferred from the .NET Framework type of the value of the parameter object, or from the `DbType` of the parameter object.</span></span> <span data-ttu-id="06bc6-155">新しい date 型と time 型をサポートするための新しい <xref:System.Data.SqlTypes> データ型は導入されていません。</span><span class="sxs-lookup"><span data-stu-id="06bc6-155">No new <xref:System.Data.SqlTypes> data types have been introduced to support the new date and time data types.</span></span> <span data-ttu-id="06bc6-156">SQL Server 2008 の date 型/time 型と CLR のデータ型のマッピングを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-156">The following table describes the mappings between the SQL Server 2008 date and time data types and the CLR data types.</span></span>  
  
|<span data-ttu-id="06bc6-157">SQL Server のデータ型</span><span class="sxs-lookup"><span data-stu-id="06bc6-157">SQL Server data type</span></span>|<span data-ttu-id="06bc6-158">.NET Framework 型</span><span class="sxs-lookup"><span data-stu-id="06bc6-158">.NET Framework type</span></span>|<span data-ttu-id="06bc6-159">System.Data.SqlDbType</span><span class="sxs-lookup"><span data-stu-id="06bc6-159">System.Data.SqlDbType</span></span>|<span data-ttu-id="06bc6-160">System.Data.DbType</span><span class="sxs-lookup"><span data-stu-id="06bc6-160">System.Data.DbType</span></span>|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|<span data-ttu-id="06bc6-161">date</span><span class="sxs-lookup"><span data-stu-id="06bc6-161">date</span></span>|<span data-ttu-id="06bc6-162">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="06bc6-162">System.DateTime</span></span>|<span data-ttu-id="06bc6-163">日付</span><span class="sxs-lookup"><span data-stu-id="06bc6-163">Date</span></span>|<span data-ttu-id="06bc6-164">日付</span><span class="sxs-lookup"><span data-stu-id="06bc6-164">Date</span></span>|  
|<span data-ttu-id="06bc6-165">時間</span><span class="sxs-lookup"><span data-stu-id="06bc6-165">time</span></span>|<span data-ttu-id="06bc6-166">System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="06bc6-166">System.TimeSpan</span></span>|<span data-ttu-id="06bc6-167">時刻</span><span class="sxs-lookup"><span data-stu-id="06bc6-167">Time</span></span>|<span data-ttu-id="06bc6-168">時刻</span><span class="sxs-lookup"><span data-stu-id="06bc6-168">Time</span></span>|  
|<span data-ttu-id="06bc6-169">datetime2</span><span class="sxs-lookup"><span data-stu-id="06bc6-169">datetime2</span></span>|<span data-ttu-id="06bc6-170">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="06bc6-170">System.DateTime</span></span>|<span data-ttu-id="06bc6-171">DateTime2</span><span class="sxs-lookup"><span data-stu-id="06bc6-171">DateTime2</span></span>|<span data-ttu-id="06bc6-172">DateTime2</span><span class="sxs-lookup"><span data-stu-id="06bc6-172">DateTime2</span></span>|  
|<span data-ttu-id="06bc6-173">datetimeoffset</span><span class="sxs-lookup"><span data-stu-id="06bc6-173">datetimeoffset</span></span>|<span data-ttu-id="06bc6-174">System.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="06bc6-174">System.DateTimeOffset</span></span>|<span data-ttu-id="06bc6-175">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="06bc6-175">DateTimeOffset</span></span>|<span data-ttu-id="06bc6-176">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="06bc6-176">DateTimeOffset</span></span>|  
|<span data-ttu-id="06bc6-177">datetime</span><span class="sxs-lookup"><span data-stu-id="06bc6-177">datetime</span></span>|<span data-ttu-id="06bc6-178">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="06bc6-178">System.DateTime</span></span>|<span data-ttu-id="06bc6-179">DateTime</span><span class="sxs-lookup"><span data-stu-id="06bc6-179">DateTime</span></span>|<span data-ttu-id="06bc6-180">DateTime</span><span class="sxs-lookup"><span data-stu-id="06bc6-180">DateTime</span></span>|  
|<span data-ttu-id="06bc6-181">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="06bc6-181">smalldatetime</span></span>|<span data-ttu-id="06bc6-182">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="06bc6-182">System.DateTime</span></span>|<span data-ttu-id="06bc6-183">DateTime</span><span class="sxs-lookup"><span data-stu-id="06bc6-183">DateTime</span></span>|<span data-ttu-id="06bc6-184">DateTime</span><span class="sxs-lookup"><span data-stu-id="06bc6-184">DateTime</span></span>|  
  
### <a name="sqlparameter-properties"></a><span data-ttu-id="06bc6-185">SqlParameter プロパティ</span><span class="sxs-lookup"><span data-stu-id="06bc6-185">SqlParameter Properties</span></span>  
 <span data-ttu-id="06bc6-186">次の表は、日付と時刻のデータ型に関係する `SqlParameter` プロパティの説明です。</span><span class="sxs-lookup"><span data-stu-id="06bc6-186">The following table describes `SqlParameter` properties that are relevant to date and time data types.</span></span>  
  
|<span data-ttu-id="06bc6-187">プロパティ</span><span class="sxs-lookup"><span data-stu-id="06bc6-187">Property</span></span>|<span data-ttu-id="06bc6-188">説明</span><span class="sxs-lookup"><span data-stu-id="06bc6-188">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|<span data-ttu-id="06bc6-189">値を NULL に設定できるかどうかを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-189">Gets or sets whether a value is nullable.</span></span> <span data-ttu-id="06bc6-190">サーバーに NULL パラメーター値を送る場合は、<xref:System.DBNull> (Visual Basic の場合は `null`) ではなく、`Nothing` を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="06bc6-190">When you send a null parameter value to the server, you must specify <xref:System.DBNull>, rather than `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="06bc6-191">データベースの null 値の詳細については、次を参照してください。 [Null 値の処理](../../../../../docs/framework/data/adonet/sql/handling-null-values.md)です。</span><span class="sxs-lookup"><span data-stu-id="06bc6-191">For more information about database nulls, see [Handling Null Values](../../../../../docs/framework/data/adonet/sql/handling-null-values.md).</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|<span data-ttu-id="06bc6-192">その値の最大桁数を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-192">Gets or sets the maximum number of digits used to represent the value.</span></span> <span data-ttu-id="06bc6-193">この設定値は date データ型と time データ型では無視されます。</span><span class="sxs-lookup"><span data-stu-id="06bc6-193">This setting is ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|<span data-ttu-id="06bc6-194">取得または設定、小数点以下桁数値の時刻部分は解決`Time`、 `DateTime2`、および`DateTimeOffset`です。</span><span class="sxs-lookup"><span data-stu-id="06bc6-194">Gets or sets the number of decimal places to which the time portion of the value is resolved for `Time`, `DateTime2`,and `DateTimeOffset`.</span></span> <span data-ttu-id="06bc6-195">既定値は 0 です。これは、実際の桁数が値から推論されてサーバーに送られることを意味します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-195">The default value is 0, which means that the actual scale is inferred from the value and sent to the server.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="06bc6-196">date データ型と time データ型では無視されます。</span><span class="sxs-lookup"><span data-stu-id="06bc6-196">Ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="06bc6-197">パラメーター値を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-197">Gets or sets the parameter value.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="06bc6-198">パラメーター値を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-198">Gets or sets the parameter value.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="06bc6-199">時刻の値が 0 と 24 の間にない場合は、<xref:System.ArgumentException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="06bc6-199">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
### <a name="creating-parameters"></a><span data-ttu-id="06bc6-200">パラメーターの作成</span><span class="sxs-lookup"><span data-stu-id="06bc6-200">Creating Parameters</span></span>  
 <span data-ttu-id="06bc6-201"><xref:System.Data.SqlClient.SqlParameter> オブジェクトは、そのコンストラクターを使って作成できるほか、<xref:System.Data.SqlClient.SqlCommand> の <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> メソッドを呼び出して、`Add`<xref:System.Data.SqlClient.SqlParameterCollection> コレクションにそれを追加することによって作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="06bc6-201">You can create a <xref:System.Data.SqlClient.SqlParameter> object by using its constructor, or by adding it to a <xref:System.Data.SqlClient.SqlCommand><xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection by calling the `Add` method of the <xref:System.Data.SqlClient.SqlParameterCollection>.</span></span> <span data-ttu-id="06bc6-202">`Add` メソッドは、入力としてコンストラクター引数または既存のパラメーター オブジェクトを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="06bc6-202">The `Add` method will take as input either constructor arguments or an existing parameter object.</span></span>  
  
 <span data-ttu-id="06bc6-203">このトピックの次のセクションでは、日付と時刻のパラメーターを指定する方法の例を示します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-203">The next sections in this topic provide examples of how to specify date and time parameters.</span></span> <span data-ttu-id="06bc6-204">パラメーターの操作の例については、次を参照してください。[構成パラメーターとパラメーターのデータ型](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)と[DataAdapter パラメーター](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)です。</span><span class="sxs-lookup"><span data-stu-id="06bc6-204">For additional examples of working with parameters, see [Configuring Parameters and Parameter Data Types](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md) and [DataAdapter Parameters](../../../../../docs/framework/data/adonet/dataadapter-parameters.md).</span></span>  
  
### <a name="date-example"></a><span data-ttu-id="06bc6-205">Date の例</span><span class="sxs-lookup"><span data-stu-id="06bc6-205">Date Example</span></span>  
 <span data-ttu-id="06bc6-206">次のコード フラグメントは、`date` パラメーターの指定方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="06bc6-206">The following code fragment demonstrates how to specify a `date` parameter.</span></span>  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Date";  
parameter.SqlDbType = SqlDbType.Date;  
parameter.Value = "2007/12/1";  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Date"  
parameter.SqlDbType = SqlDbType.Date  
parameter.Value = "2007/12/1"  
```  
  
### <a name="time-example"></a><span data-ttu-id="06bc6-207">Time の例</span><span class="sxs-lookup"><span data-stu-id="06bc6-207">Time Example</span></span>  
 <span data-ttu-id="06bc6-208">次のコード フラグメントは、`time` パラメーターの指定方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="06bc6-208">The following code fragment demonstrates how to specify a `time` parameter.</span></span>  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@time";  
parameter.SqlDbType = SqlDbType.Time;  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Time"  
parameter.SqlDbType = SqlDbType.Time  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
### <a name="datetime2-example"></a><span data-ttu-id="06bc6-209">Datetime2 の例</span><span class="sxs-lookup"><span data-stu-id="06bc6-209">Datetime2 Example</span></span>  
 <span data-ttu-id="06bc6-210">次のコード フラグメントは、`datetime2` パラメーターの日付と時刻の指定方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="06bc6-210">The following code fragment demonstrates how to specify a `datetime2` parameter with both the date and time parts.</span></span>  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Datetime2";  
parameter.SqlDbType = SqlDbType.DateTime2;  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Datetime2"  
parameter.SqlDbType = SqlDbType.DateTime2  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
### <a name="datetimeoffset-example"></a><span data-ttu-id="06bc6-211">DateTimeOffSet の例</span><span class="sxs-lookup"><span data-stu-id="06bc6-211">DateTimeOffSet Example</span></span>  
 <span data-ttu-id="06bc6-212">次のコード フラグメントは、`DateTimeOffSet` パラメーターの日付と時刻、およびタイム ゾーン オフセット 0 を指定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="06bc6-212">The following code fragment demonstrates how to specify a `DateTimeOffSet` parameter with a date, a time, and a time zone offset of 0.</span></span>  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@DateTimeOffSet";  
parameter.SqlDbType = SqlDbType.DateTimeOffSet;  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@DateTimeOffSet"  
parameter.SqlDbType = SqlDbType.DateTimeOffSet  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
### <a name="addwithvalue"></a><span data-ttu-id="06bc6-213">AddWithValue</span><span class="sxs-lookup"><span data-stu-id="06bc6-213">AddWithValue</span></span>  
 <span data-ttu-id="06bc6-214">次のコード フラグメントのように、`AddWithValue` の <xref:System.Data.SqlClient.SqlCommand> メソッドを使用してパラメーターを渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="06bc6-214">You can also supply parameters by using the `AddWithValue` method of a <xref:System.Data.SqlClient.SqlCommand>, as shown in the following code fragment.</span></span> <span data-ttu-id="06bc6-215">ただし、`AddWithValue` メソッドでは <xref:System.Data.SqlClient.SqlParameter.DbType%2A> または <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> をパラメーターに指定できません。</span><span class="sxs-lookup"><span data-stu-id="06bc6-215">However, the `AddWithValue` method does not allow you to specify the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> or <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> for the parameter.</span></span>  
  
```csharp  
command.Parameters.AddWithValue(   
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 <span data-ttu-id="06bc6-216">`@date`パラメーターにマップでした、 `date`、 `datetime`、または`datetime2`サーバー上のデータ型。</span><span class="sxs-lookup"><span data-stu-id="06bc6-216">The `@date` parameter could map to a `date`, `datetime`, or `datetime2` data type on the server.</span></span> <span data-ttu-id="06bc6-217">新しい `datetime` データ型を使用するときは、パラメーターの <xref:System.Data.SqlDbType> プロパティをそのインスタンスのデータ型に明示的に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="06bc6-217">When working with the new `datetime` data types, you must explicitly set the parameter's <xref:System.Data.SqlDbType> property to the data type of the instance.</span></span> <span data-ttu-id="06bc6-218"><xref:System.Data.SqlDbType.Variant> の使用やパラメーター値の明示的な指定により、`datetime` および `smalldatetime` データ型との下位互換性の問題が発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="06bc6-218">Using <xref:System.Data.SqlDbType.Variant> or implicitly supplying parameter values can cause problems with backward compatibility with the `datetime` and `smalldatetime` data types.</span></span>  
  
 <span data-ttu-id="06bc6-219">次の表は、どの `SqlDbTypes` がどの CLR 型から推論されるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="06bc6-219">The following table shows which `SqlDbTypes` are inferred from which CLR types:</span></span>  
  
|<span data-ttu-id="06bc6-220">CLR 型</span><span class="sxs-lookup"><span data-stu-id="06bc6-220">CLR type</span></span>|<span data-ttu-id="06bc6-221">推論される SqlDbType</span><span class="sxs-lookup"><span data-stu-id="06bc6-221">Inferred SqlDbType</span></span>|  
|--------------|------------------------|  
|<span data-ttu-id="06bc6-222">DateTime</span><span class="sxs-lookup"><span data-stu-id="06bc6-222">DateTime</span></span>|<span data-ttu-id="06bc6-223">SqlDbType.DateTime</span><span class="sxs-lookup"><span data-stu-id="06bc6-223">SqlDbType.DateTime</span></span>|  
|<span data-ttu-id="06bc6-224">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="06bc6-224">TimeSpan</span></span>|<span data-ttu-id="06bc6-225">SqlDbType.Time</span><span class="sxs-lookup"><span data-stu-id="06bc6-225">SqlDbType.Time</span></span>|  
|<span data-ttu-id="06bc6-226">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="06bc6-226">DateTimeOffset</span></span>|<span data-ttu-id="06bc6-227">SqlDbType.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="06bc6-227">SqlDbType.DateTimeOffset</span></span>|  
  
## <a name="retrieving-date-and-time-data"></a><span data-ttu-id="06bc6-228">日付と時刻データの取得</span><span class="sxs-lookup"><span data-stu-id="06bc6-228">Retrieving Date and Time Data</span></span>  
 <span data-ttu-id="06bc6-229">SQL Server 2008 の日付値および時刻値を取得するためのメソッドを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-229">The following table describes methods that are used to retrieve SQL Server 2008 date and time values.</span></span>  
  
|<span data-ttu-id="06bc6-230">SqlClient のメソッド</span><span class="sxs-lookup"><span data-stu-id="06bc6-230">SqlClient method</span></span>|<span data-ttu-id="06bc6-231">説明</span><span class="sxs-lookup"><span data-stu-id="06bc6-231">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|<span data-ttu-id="06bc6-232">指定された列の値を <xref:System.DateTime> 構造体として取得します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-232">Retrieves the specified column value as a <xref:System.DateTime> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|<span data-ttu-id="06bc6-233">指定された列の値を <xref:System.DateTimeOffset> 構造体として取得します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-233">Retrieves the specified column value as a <xref:System.DateTimeOffset> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|<span data-ttu-id="06bc6-234">特定のフィールドについて、基になるプロバイダー固有の型を返します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-234">Returns the type that is the underlying provider-specific type for the field.</span></span> <span data-ttu-id="06bc6-235">新しい date 型および time 型については、`GetFieldType` と同じ型が返されます。</span><span class="sxs-lookup"><span data-stu-id="06bc6-235">Returns the same types as `GetFieldType` for new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|<span data-ttu-id="06bc6-236">指定された列の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-236">Retrieves the value of the specified column.</span></span> <span data-ttu-id="06bc6-237">新しい date 型および time 型については、`GetValue` と同じ型が返されます。</span><span class="sxs-lookup"><span data-stu-id="06bc6-237">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|<span data-ttu-id="06bc6-238">指定された配列の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-238">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<span data-ttu-id="06bc6-239">列の値を <xref:System.Data.SqlTypes.SqlString> として取得します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-239">Retrieves the column value as a <xref:System.Data.SqlTypes.SqlString>.</span></span> <span data-ttu-id="06bc6-240">データを <xref:System.InvalidCastException> で表現できない場合、`SqlString` が発生します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-240">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a `SqlString`.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|<span data-ttu-id="06bc6-241">列データを対応する既定の `SqlDbType` として取得します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-241">Retrieves column data as its default `SqlDbType`.</span></span> <span data-ttu-id="06bc6-242">新しい date 型および time 型については、`GetValue` と同じ型が返されます。</span><span class="sxs-lookup"><span data-stu-id="06bc6-242">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|<span data-ttu-id="06bc6-243">指定された配列の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-243">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|<span data-ttu-id="06bc6-244">Type System Version が SQL Server 2005 に設定されている場合、列の値を文字列として取得します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-244">Retrieves the column value as a string if the Type System Version is set to SQL Server 2005.</span></span> <span data-ttu-id="06bc6-245">データを文字列で表現できない場合、<xref:System.InvalidCastException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-245">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a string.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|<span data-ttu-id="06bc6-246">指定された列の値を <xref:System.TimeSpan> 構造体として取得します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-246">Retrieves the specified column value as a <xref:System.TimeSpan> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|<span data-ttu-id="06bc6-247">指定された列の値を、基になる CLR 型として取得します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-247">Retrieves the specified column value as its underlying CLR type.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|<span data-ttu-id="06bc6-248">配列内の列の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-248">Retrieves column values in an array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|<span data-ttu-id="06bc6-249">結果セットのメタデータを表す <xref:System.Data.DataTable> を返します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-249">Returns a <xref:System.Data.DataTable> that describes the metadata of the result set.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="06bc6-250">新しい日付と時刻の `SqlDbTypes` は、SQL Server 内でインプロセスで実行されるコードではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="06bc6-250">The new date and time `SqlDbTypes` are not supported for code that is executing in-process in SQL Server.</span></span> <span data-ttu-id="06bc6-251">そのような型の 1 つがサーバーに渡されると、例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-251">An exception will be raised if one of these types is passed to the server.</span></span>  
  
## <a name="specifying-date-and-time-values-as-literals"></a><span data-ttu-id="06bc6-252">日付値と時刻値のリテラル指定</span><span class="sxs-lookup"><span data-stu-id="06bc6-252">Specifying Date and Time Values as Literals</span></span>  
 <span data-ttu-id="06bc6-253">日付と時刻のデータ型は、さまざまなリテラル文字列形式を使用して指定できます。SQL Server は、実行時にそれらを内部の日付/時刻構造体に変換します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-253">You can specify date and time data types by using a variety of different literal string formats, which SQL Server then evaluates at run time, converting them to internal date/time structures.</span></span> <span data-ttu-id="06bc6-254">SQL Server は、単一引用符 (') で囲まれた日付と時刻のデータを認識します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-254">SQL Server recognizes date and time data that is enclosed in single quotation marks (').</span></span> <span data-ttu-id="06bc6-255">次に文字列形式の例を示します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-255">The following examples demonstrate some formats:</span></span>  
  
-   <span data-ttu-id="06bc6-256">英数字の日付書式 (`'October 15, 2006'` など)。</span><span class="sxs-lookup"><span data-stu-id="06bc6-256">Alphabetic date formats, such as `'October 15, 2006'`.</span></span>  
  
-   <span data-ttu-id="06bc6-257">数字の日付書式 (`'10/15/2006'` など)。</span><span class="sxs-lookup"><span data-stu-id="06bc6-257">Numeric date formats, such as `'10/15/2006'`.</span></span>  
  
-   <span data-ttu-id="06bc6-258">区切りなしの文字列形式 (`'20061015'` など)。これは ISO 規格の日付書式では 2006 年 10 月 15 日と解釈されます。</span><span class="sxs-lookup"><span data-stu-id="06bc6-258">Unseparated string formats, such as `'20061015'`, which would be interpreted as October 15, 2006 if you are using the ISO standard date format.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06bc6-259">すべてのリテラル文字列形式と日付/時刻データ型のその他の特徴については、SQL Server オンライン ブックに完全な説明が記載されています。</span><span class="sxs-lookup"><span data-stu-id="06bc6-259">You can find complete documentation for all of the literal string formats and other features of the date and time data types in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="06bc6-260">時刻の値が 0 と 24 の間にない場合は、<xref:System.ArgumentException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="06bc6-260">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
## <a name="resources-in-sql-server-2008-books-online"></a><span data-ttu-id="06bc6-261">SQL Server 2008 オンライン ブックの関連トピック</span><span class="sxs-lookup"><span data-stu-id="06bc6-261">Resources in SQL Server 2008 Books Online</span></span>  
 <span data-ttu-id="06bc6-262">SQL Server 2008 での日付値と時刻値の使用方法の詳細については、SQL Server 2008 オンライン ブックで次の関連トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="06bc6-262">For more information about working with date and time values in SQL Server 2008, see the following resources in SQL Server 2008 Books Online.</span></span>  
  
|<span data-ttu-id="06bc6-263">トピック</span><span class="sxs-lookup"><span data-stu-id="06bc6-263">Topic</span></span>|<span data-ttu-id="06bc6-264">説明</span><span class="sxs-lookup"><span data-stu-id="06bc6-264">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="06bc6-265">日付および時刻データ型および関数 (TRANSACT-SQL)</span><span class="sxs-lookup"><span data-stu-id="06bc6-265">Date and Time Data Types and Functions (Transact-SQL)</span></span>](http://go.microsoft.com/fwlink/?LinkId=98360)|<span data-ttu-id="06bc6-266">Transact-SQL の日付と時刻のデータ型および関数の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-266">Provides an overview of all Transact-SQL date and time data types and functions.</span></span>|  
|[<span data-ttu-id="06bc6-267">日付と時刻のデータを使用します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-267">Using Date and Time Data</span></span>](http://go.microsoft.com/fwlink/?LinkId=98361)|<span data-ttu-id="06bc6-268">日付と時刻のデータ型と関数の情報、および使用例を示します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-268">Provides information about the date and time data types and functions, and examples of using them.</span></span>|  
|[<span data-ttu-id="06bc6-269">データ型 (TRANSACT-SQL)</span><span class="sxs-lookup"><span data-stu-id="06bc6-269">Data Types (Transact-SQL)</span></span>](http://go.microsoft.com/fwlink/?LinkId=98362)|<span data-ttu-id="06bc6-270">SQL Server 2008 のシステム データ型について説明します。</span><span class="sxs-lookup"><span data-stu-id="06bc6-270">Describes system data types in SQL Server 2008.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="06bc6-271">参照</span><span class="sxs-lookup"><span data-stu-id="06bc6-271">See Also</span></span>  
 [<span data-ttu-id="06bc6-272">SQL Server データ型のマッピング</span><span class="sxs-lookup"><span data-stu-id="06bc6-272">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [<span data-ttu-id="06bc6-273">パラメーターおよびパラメーター データ型の構成</span><span class="sxs-lookup"><span data-stu-id="06bc6-273">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="06bc6-274">SQL Server データ型と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="06bc6-274">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="06bc6-275">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="06bc6-275">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
