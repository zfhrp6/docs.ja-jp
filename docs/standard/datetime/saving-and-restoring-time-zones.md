---
title: 保存と復元のタイム ゾーン
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- restoring time zones
- deserialization [.NET Framework], time zones
- serialization [.NET Framework], time zones
- time zone objects [.NET Framework], restoring
- saving time zones
- time zone objects [.NET Framework], deserializing
- time zones [.NET Framework], saving
- time zones [.NET Framework], restoring
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 4028b310-e7ce-49d4-a646-1e83bfaf6f9d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7c9aefa08d837ce93e718ff32a463d95dabcdc3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="saving-and-restoring-time-zones"></a><span data-ttu-id="90441-102">保存と復元のタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="90441-102">Saving and restoring time zones</span></span>

<span data-ttu-id="90441-103"><xref:System.TimeZoneInfo>クラスが定義済みのタイム ゾーン データを取得する、レジストリに依存します。</span><span class="sxs-lookup"><span data-stu-id="90441-103">The <xref:System.TimeZoneInfo> class relies on the registry to retrieve predefined time zone data.</span></span> <span data-ttu-id="90441-104">ただし、レジストリは、動的な構造です。</span><span class="sxs-lookup"><span data-stu-id="90441-104">However, the registry is a dynamic structure.</span></span> <span data-ttu-id="90441-105">さらに、レジストリが含まれているタイム ゾーン情報は、現在の年の時刻の調整および変換を処理するには、主に、オペレーティング システムによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="90441-105">Additionally, the time zone information that the registry contains is used by the operating system primarily to handle time adjustments and conversions for the current year.</span></span> <span data-ttu-id="90441-106">これは、正確なタイム ゾーン データに依存するアプリケーションの 2 つの主要な影響があります。</span><span class="sxs-lookup"><span data-stu-id="90441-106">This has two major implications for applications that rely on accurate time zone data:</span></span>

* <span data-ttu-id="90441-107">アプリケーションで必要とされるタイム ゾーンは、レジストリで、定義されていない可能性があります。 または名前が変更されているか、レジストリから削除します。</span><span class="sxs-lookup"><span data-stu-id="90441-107">A time zone that is required by an application may not be defined in the registry, or it may have been renamed or removed from the registry.</span></span>

* <span data-ttu-id="90441-108">レジストリで定義されているタイム ゾーンには、履歴のタイム ゾーンの変換に必要な特定の調整規則の情報が不足している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="90441-108">A time zone that is defined in the registry may lack information about the particular adjustment rules that are necessary for historical time zone conversions.</span></span>

<span data-ttu-id="90441-109"><xref:System.TimeZoneInfo>クラス (保存) をシリアル化および逆シリアル化のタイム ゾーンのデータを (復元) のサポートにより、これらの制限に対処します。</span><span class="sxs-lookup"><span data-stu-id="90441-109">The <xref:System.TimeZoneInfo> class addresses these limitations through its support for serialization (saving) and deserialization (restoring) of time zone data.</span></span>

## <a name="time-zone-serialization-and-deserialization"></a><span data-ttu-id="90441-110">タイム ゾーンのシリアル化および逆シリアル化</span><span class="sxs-lookup"><span data-stu-id="90441-110">Time zone serialization and deserialization</span></span>

<span data-ttu-id="90441-111">保存とタイム ゾーンのデータをシリアル化およびタイム ゾーンを復元するには、2 つのメソッド呼び出しが含まれます。</span><span class="sxs-lookup"><span data-stu-id="90441-111">Saving and restoring a time zone by serializing and deserializing time zone data involves just two method calls:</span></span>

* <span data-ttu-id="90441-112">シリアル化することができます、<xref:System.TimeZoneInfo>を呼び出してそのオブジェクトのオブジェクト<xref:System.TimeZoneInfo.ToSerializedString%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="90441-112">You can serialize a <xref:System.TimeZoneInfo> object by calling that object's <xref:System.TimeZoneInfo.ToSerializedString%2A> method.</span></span> <span data-ttu-id="90441-113">メソッドは、パラメーターを受け取らないし、タイム ゾーン情報を含む文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="90441-113">The method takes no parameters and returns a string that contains time zone information.</span></span>

* <span data-ttu-id="90441-114">逆シリアル化することができます、<xref:System.TimeZoneInfo>オブジェクトには、その文字列を渡すことによってシリアル化された文字列から、 `static` (`Shared` Visual Basic で)<xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="90441-114">You can deserialize a <xref:System.TimeZoneInfo> object from a serialized string by passing that string to the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> method.</span></span>

## <a name="serialization-and-deserialization-scenarios"></a><span data-ttu-id="90441-115">シリアル化および逆シリアル化のシナリオ</span><span class="sxs-lookup"><span data-stu-id="90441-115">Serialization and deserialization scenarios</span></span>

<span data-ttu-id="90441-116">保存 (またはシリアル化) する機能、<xref:System.TimeZoneInfo>オブジェクトを文字列と復元 (または逆シリアル化)、後で使用できるユーティリティとの柔軟性の両方が増加、<xref:System.TimeZoneInfo>クラスです。</span><span class="sxs-lookup"><span data-stu-id="90441-116">The ability to save (or serialize) a <xref:System.TimeZoneInfo> object to a string and to restore (or deserialize) it for later use increases both the utility and the flexibility of the <xref:System.TimeZoneInfo> class.</span></span> <span data-ttu-id="90441-117">ここでは、一部のシリアル化および逆シリアル化は最も有用な状況について説明します。</span><span class="sxs-lookup"><span data-stu-id="90441-117">This section examines some of the situations in which serialization and deserialization are most useful.</span></span>

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a><span data-ttu-id="90441-118">シリアル化して、アプリケーションでのタイム ゾーン データを逆シリアル化</span><span class="sxs-lookup"><span data-stu-id="90441-118">Serializing and deserializing time zone data in an application</span></span>

<span data-ttu-id="90441-119">必要な場合、文字列からシリアル化されたタイム ゾーンを復元することができます。</span><span class="sxs-lookup"><span data-stu-id="90441-119">A serialized time zone can be restored from a string when it is needed.</span></span> <span data-ttu-id="90441-120">レジストリから取得されたタイム ゾーンが特定の日付範囲内での日付を正しく変換できない場合は、アプリケーションでこれを行うことがあります。</span><span class="sxs-lookup"><span data-stu-id="90441-120">An application might do this if the time zone retrieved from the registry is unable to correctly convert a date and time within a particular date range.</span></span> <span data-ttu-id="90441-121">Windows XP のレジストリのタイム ゾーン データでは、通常、Windows Vista のレジストリで定義されているタイム ゾーンは約 2 つの調整規則の情報を提供します、単一の調整規則をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="90441-121">For example, time zone data in the Windows XP registry supports a single adjustment rule, while time zones defined in the Windows Vista registry typically provide information about two adjustment rules.</span></span> <span data-ttu-id="90441-122">これは、過去の時刻の変換が不正確であることを意味します。</span><span class="sxs-lookup"><span data-stu-id="90441-122">This means that historical time conversions may be inaccurate.</span></span> <span data-ttu-id="90441-123">シリアル化とタイム ゾーンのデータの逆シリアル化は、この制限を処理できます。</span><span class="sxs-lookup"><span data-stu-id="90441-123">Serialization and deserialization of time zone data can handle this limitation.</span></span>

<span data-ttu-id="90441-124">次の例では、カスタム<xref:System.TimeZoneInfo>米国を表すための調整規則がないクラスが定義されています。東部標準時のゾーンは 1883 1917、米国の州の夏時間の導入前にします。</span><span class="sxs-lookup"><span data-stu-id="90441-124">In the following example, a custom <xref:System.TimeZoneInfo> class that has no adjustment rules is defined to represent the U.S. Eastern Standard Time zone from 1883 to 1917, before the introduction of daylight saving time in the United States.</span></span> <span data-ttu-id="90441-125">カスタムのタイム ゾーンがグローバル スコープを持つ変数にシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="90441-125">The custom time zone is serialized in a variable that has global scope.</span></span> <span data-ttu-id="90441-126">タイム ゾーンの変換メソッド`ConvertUtcTime`は変換する世界協定世界時 (UTC) の時間に渡されます。</span><span class="sxs-lookup"><span data-stu-id="90441-126">The time zone conversion method, `ConvertUtcTime`, is passed Coordinated Universal Time (UTC) times to convert.</span></span> <span data-ttu-id="90441-127">日付と時刻は、1917年またはそれ以前に発生する場合、カスタム東部標準時ゾーンはシリアル化された文字列から復元され、レジストリから取得されたタイム ゾーンが置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="90441-127">If the date and time occurs in 1917 or earlier, the custom Eastern Standard Time zone is restored from a serialized string and replaces the time zone retrieved from the registry.</span></span>

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a><span data-ttu-id="90441-128">タイム ゾーンの例外を処理</span><span class="sxs-lookup"><span data-stu-id="90441-128">Handling time zone exceptions</span></span>

<span data-ttu-id="90441-129">レジストリは動的な構造であるため、その内容は次偶発的または意図的な変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="90441-129">Because the registry is a dynamic structure, its contents are subject to accidental or deliberate modification.</span></span> <span data-ttu-id="90441-130">つまり、レジストリで定義されている必要があり、正常に実行するアプリケーションに必要なタイム ゾーンが存在しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="90441-130">This means that a time zone that should be defined in the registry and that is required for an application to execute successfully may be absent.</span></span> <span data-ttu-id="90441-131">タイム ゾーンのシリアル化および逆シリアル化をサポートせず、その結果を処理するが、ほとんどの選択肢がある<xref:System.TimeZoneNotFoundException>アプリケーションを終了しています。</span><span class="sxs-lookup"><span data-stu-id="90441-131">Without support for time zone serialization and deserialization, you have little choice but to handle the resulting <xref:System.TimeZoneNotFoundException> by ending the application.</span></span> <span data-ttu-id="90441-132">ただし、タイム ゾーンのシリアル化および逆シリアル化を使用することができますを処理する、予期しない<xref:System.TimeZoneNotFoundException>復元することによって、シリアル化された文字列と、アプリケーションから必要なタイム ゾーンは引き続き実行します。</span><span class="sxs-lookup"><span data-stu-id="90441-132">However, by using time zone serialization and deserialization, you can handle an unexpected <xref:System.TimeZoneNotFoundException> by restoring the required time zone from a serialized string, and the application will continue to run.</span></span>

<span data-ttu-id="90441-133">次の例では、作成し、カスタム中部標準時ゾーンのシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="90441-133">The following example creates and serializes a custom Central Standard Time zone.</span></span> <span data-ttu-id="90441-134">中部標準時ゾーンのレジストリから取得が試行されます。</span><span class="sxs-lookup"><span data-stu-id="90441-134">It then tries to retrieve the Central Standard Time zone from the registry.</span></span> <span data-ttu-id="90441-135">取得操作では、いずれかがスローされた場合、<xref:System.TimeZoneNotFoundException>または<xref:System.InvalidTimeZoneException>、例外ハンドラーは、タイム ゾーンを逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="90441-135">If the retrieval operation throws either a <xref:System.TimeZoneNotFoundException> or an <xref:System.InvalidTimeZoneException>, the exception handler deserializes the time zone.</span></span>

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a><span data-ttu-id="90441-136">シリアル化された文字列を格納して、必要なときにそれを復元します。</span><span class="sxs-lookup"><span data-stu-id="90441-136">Storing a serialized string and restoring it when needed</span></span>

<span data-ttu-id="90441-137">前の例では、文字列変数にタイム ゾーン情報を格納し、必要なときにこれを復元します。</span><span class="sxs-lookup"><span data-stu-id="90441-137">The previous examples have stored time zone information to a string variable and restored it when needed.</span></span> <span data-ttu-id="90441-138">ただし、シリアル化されたタイム ゾーン情報自体に格納できる、外部のファイル、リソース ファイルなど、いくつかのストレージ メディアを格納する文字列は、アプリケーション、またはレジストリに埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="90441-138">However, the string that contains serialized time zone information can itself be stored in some storage medium, such as an external file, a resource file embedded in the application, or the registry.</span></span> <span data-ttu-id="90441-139">(カスタム タイム ゾーンに関する情報をレジストリで、システムのタイム ゾーンのキーとは別に保存するかを注意してください)。</span><span class="sxs-lookup"><span data-stu-id="90441-139">(Note that information about custom time zones should be stored apart from the system's time zone keys in the registry.)</span></span>

<span data-ttu-id="90441-140">この方法でシリアル化されたタイム ゾーン文字列を格納すると、タイム ゾーンの作成ルーチンも、アプリケーション自体とは別になります。</span><span class="sxs-lookup"><span data-stu-id="90441-140">Storing a serialized time zone string in this manner also separates the time zone creation routine from the application itself.</span></span> <span data-ttu-id="90441-141">たとえば、タイム ゾーンの作成ルーチンは実行し、アプリケーションが使用できる履歴タイム ゾーン情報を含むデータ ファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="90441-141">For example, a time zone creation routine can execute and create a data file that contains historical time zone information that an application can use.</span></span> <span data-ttu-id="90441-142">データ ファイルを指定できます、アプリケーションと共にインストールして開くことがし、1 つまたは複数のタイム ゾーンの逆シリアル化できます、アプリケーションで必要なときにします。</span><span class="sxs-lookup"><span data-stu-id="90441-142">The data file can be then be installed with the application, and it can be opened and one or more of its time zones can be deserialized when the application requires them.</span></span>

<span data-ttu-id="90441-143">タイム ゾーンのシリアル化されたデータを保存する埋め込みリソースを使用する例は、次を参照してください。[する方法: 埋め込みリソースにタイム ゾーンを保存](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)と[する方法: 埋め込みリソースからタイム ゾーンを復元](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)です。</span><span class="sxs-lookup"><span data-stu-id="90441-143">For an example that uses an embedded resource to store serialized time zone data, see [How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) and [How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="90441-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="90441-144">See also</span></span>

[<span data-ttu-id="90441-145">日付、時刻、およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="90441-145">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
