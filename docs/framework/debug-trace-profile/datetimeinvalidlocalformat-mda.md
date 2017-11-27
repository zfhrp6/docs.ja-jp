---
title: dateTimeInvalidLocalFormat MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dates [.NET Framework], formatting
- invalid date time local format
- invalid local formats
- MDAs (managed debugging assistants), invalid local formats
- managed debugging assistants (MDAs), invalid local formats
- dateTimeInvalidLocalFormat MDA
- date formatting
- time formatting
- UTC formatting
ms.assetid: c4a942bb-2651-4b65-8718-809f892a0659
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3181acec440f2d01e928bb051b297fba75de1e2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="datetimeinvalidlocalformat-mda"></a><span data-ttu-id="02925-102">dateTimeInvalidLocalFormat MDA</span><span class="sxs-lookup"><span data-stu-id="02925-102">dateTimeInvalidLocalFormat MDA</span></span>
<span data-ttu-id="02925-103">`dateTimeInvalidLocalFormat` MDA は、世界協定時刻 (UTC) として格納されている <xref:System.DateTime> インスタンスが、ローカル <xref:System.DateTime> インスタンス専用の形式で書式指定されたときにアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="02925-103">The `dateTimeInvalidLocalFormat` MDA is activated when a <xref:System.DateTime> instance that is stored as a Universal Coordinated Time (UTC) is formatted using a format that is intended to be used only for local <xref:System.DateTime> instances.</span></span> <span data-ttu-id="02925-104">この MDA は、未指定または既定の <xref:System.DateTime> インスタンスに対してはアクティブになりません。</span><span class="sxs-lookup"><span data-stu-id="02925-104">This MDA is not activated for unspecified or default <xref:System.DateTime> instances.</span></span>  
  
## <a name="symptom"></a><span data-ttu-id="02925-105">症状</span><span class="sxs-lookup"><span data-stu-id="02925-105">Symptom</span></span>  
 <span data-ttu-id="02925-106">アプリケーションで、次のようなローカル形式を使用して UTC <xref:System.DateTime> インスタンスを手動でシリアル化しています。</span><span class="sxs-lookup"><span data-stu-id="02925-106">An application is manually serializing a UTC <xref:System.DateTime> instance using a local format:</span></span>  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a><span data-ttu-id="02925-107">原因</span><span class="sxs-lookup"><span data-stu-id="02925-107">Cause</span></span>  
 <span data-ttu-id="02925-108"><xref:System.DateTime.ToString%2A?displayProperty=nameWithType> メソッドの 'z' 形式には、ローカル タイム ゾーン オフセット (たとえば、シドニー時間の場合は "+10:00") が含まれます。</span><span class="sxs-lookup"><span data-stu-id="02925-108">The 'z' format for the <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> method includes the local time zone offset, for example, "+10:00" for Sydney time.</span></span> <span data-ttu-id="02925-109">そのため、<xref:System.DateTime> の値がローカルの場合にのみ、有意な結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="02925-109">As such, it will only produce a meaningful result if the value of the <xref:System.DateTime> is local.</span></span> <span data-ttu-id="02925-110">値が UTC 時刻の場合、<xref:System.DateTime.ToString%2A?displayProperty=nameWithType> には、ローカル タイム ゾーン オフセットが含まれますが、タイム ゾーン指定子の表示や調整は行われません。</span><span class="sxs-lookup"><span data-stu-id="02925-110">If the value is UTC time, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> includes the local time zone offset, but it does not display or adjust the time zone specifier.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="02925-111">解像度</span><span class="sxs-lookup"><span data-stu-id="02925-111">Resolution</span></span>  
 <span data-ttu-id="02925-112">UTC <xref:System.DateTime> インスタンスが UTC であることを示すように書式設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="02925-112">UTC <xref:System.DateTime> instances should be formatted in a way that indicates that they are UTC.</span></span> <span data-ttu-id="02925-113">UTC 時刻の形式としては、次のように 'Z' を使用して UTC 時刻を示すようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="02925-113">The recommended format for UTC times to use a 'Z' to denote UTC time:</span></span>  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 <span data-ttu-id="02925-114">また、インスタンスがローカル、UTC、未指定のいずれの場合でも正しくシリアル化する <xref:System.DateTime.Kind%2A> プロパティを利用して <xref:System.DateTime> をシリアル化する "o" 形式もあります。</span><span class="sxs-lookup"><span data-stu-id="02925-114">There is also an "o" format that serializes a <xref:System.DateTime> making use of the <xref:System.DateTime.Kind%2A> property that serializes correctly regardless of whether the instance is local, UTC, or unspecified:</span></span>  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="02925-115">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="02925-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="02925-116">この MDA はランタイムに影響しません。</span><span class="sxs-lookup"><span data-stu-id="02925-116">This MDA does not affect the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="02925-117">出力</span><span class="sxs-lookup"><span data-stu-id="02925-117">Output</span></span>  
 <span data-ttu-id="02925-118">この MDA がアクティブになっても特別な出力は生成されませんが、呼び出し履歴を使用すると、この MDA をアクティブにした <xref:System.DateTime.ToString%2A> 呼び出しの位置を確認できます。</span><span class="sxs-lookup"><span data-stu-id="02925-118">There is no special output as a result of this MDA activating., However, the call stack can be used to determine the location of the <xref:System.DateTime.ToString%2A> call that activated the MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="02925-119">構成</span><span class="sxs-lookup"><span data-stu-id="02925-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="02925-120">例</span><span class="sxs-lookup"><span data-stu-id="02925-120">Example</span></span>  
 <span data-ttu-id="02925-121">次のように、<xref:System.Xml.XmlConvert> または <xref:System.Data.DataSet> クラスを使用して UTC <xref:System.DateTime> 値を間接的にシリアル化するアプリケーションについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="02925-121">Consider an application that is indirectly serializing a UTC <xref:System.DateTime> value by using the <xref:System.Xml.XmlConvert> or <xref:System.Data.DataSet> class, in the following manner.</span></span>  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <span data-ttu-id="02925-122"><xref:System.Xml.XmlConvert> と <xref:System.Data.DataSet> のシリアル化では、既定でシリアル化用のローカル形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="02925-122">The <xref:System.Xml.XmlConvert> and <xref:System.Data.DataSet> serializations use local formats for serialization by default.</span></span> <span data-ttu-id="02925-123">UTC など、他の種類の <xref:System.DateTime> 値をシリアル化する場合は、追加のオプションが必要です。</span><span class="sxs-lookup"><span data-stu-id="02925-123">Additional options are required to serialize other kinds of <xref:System.DateTime> values, such as UTC.</span></span>  
  
 <span data-ttu-id="02925-124">この特定の例では、`XmlConvert` での `ToString` 呼び出しに `XmlDateTimeSerializationMode.RoundtripKind` を渡します。</span><span class="sxs-lookup"><span data-stu-id="02925-124">For this specific example, pass in `XmlDateTimeSerializationMode.RoundtripKind` to the `ToString` call on `XmlConvert`.</span></span> <span data-ttu-id="02925-125">これで、データが UTC 時刻としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="02925-125">This serializes the data as a UTC time.</span></span>  
  
 <span data-ttu-id="02925-126"><xref:System.Data.DataSet> を使用する場合は、<xref:System.Data.DataColumn> オブジェクトの <xref:System.Data.DataColumn.DateTimeMode%2A> プロパティを <xref:System.Data.DataSetDateTime.Utc> に設定します。</span><span class="sxs-lookup"><span data-stu-id="02925-126">If using a <xref:System.Data.DataSet>, set the <xref:System.Data.DataColumn.DateTimeMode%2A> property on the <xref:System.Data.DataColumn> object to <xref:System.Data.DataSetDateTime.Utc>.</span></span>  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a><span data-ttu-id="02925-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="02925-127">See Also</span></span>  
 <xref:System.Globalization.DateTimeFormatInfo>  
 [<span data-ttu-id="02925-128">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="02925-128">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
