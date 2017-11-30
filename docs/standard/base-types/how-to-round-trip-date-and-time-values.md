---
title: "方法 : 日付と時刻の値をラウンドトリップさせる"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- round-trip date and time values
- dates [.NET Framework], round-trip values
- time zones [.NET Framework], round-trip date and time values
- time [.NET Framework], round-trip values
- formatting strings [.NET Framework], round-trip values
ms.assetid: b609b277-edc6-4c74-b03e-ea73324ecbdb
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 515a29e279cfa8fc100e0612fc19df7abc6a3b36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-round-trip-date-and-time-values"></a><span data-ttu-id="e77c5-102">方法 : 日付と時刻の値をラウンドトリップさせる</span><span class="sxs-lookup"><span data-stu-id="e77c5-102">How to: Round-trip Date and Time Values</span></span>
<span data-ttu-id="e77c5-103">ある特定の時点を明確に表すように日付と時刻の値を保つことは、多くのアプリケーションに共通する要件です。</span><span class="sxs-lookup"><span data-stu-id="e77c5-103">In many applications, a date and time value is intended to unambiguously identify a single point in time.</span></span> <span data-ttu-id="e77c5-104">このトピックの内容を保存および復元する方法を示しています、<xref:System.DateTime>値、<xref:System.DateTimeOffset>復元された値が保存されている値と同じ時間を識別できるようにゾーンの情報の値、および時刻と日付と時刻の値。</span><span class="sxs-lookup"><span data-stu-id="e77c5-104">This topic shows how to save and restore a <xref:System.DateTime> value, a <xref:System.DateTimeOffset> value, and a date and time value with time zone information so that the restored value identifies the same time as the saved value.</span></span>  
  
### <a name="to-round-trip-a-datetime-value"></a><span data-ttu-id="e77c5-105">DateTime 値をラウンドトリップさせるには</span><span class="sxs-lookup"><span data-stu-id="e77c5-105">To round-trip a DateTime value</span></span>  
  
1.  <span data-ttu-id="e77c5-106">変換、<xref:System.DateTime>を呼び出すことによって、文字列形式の値、 <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> "o"書式指定子を持つメソッドです。</span><span class="sxs-lookup"><span data-stu-id="e77c5-106">Convert the <xref:System.DateTime> value to its string representation by calling the <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>  
  
2.  <span data-ttu-id="e77c5-107">文字列形式を保存、<xref:System.DateTime>値をファイル、またはプロセス、アプリケーション ドメイン、またはコンピューターの境界を通過させます。</span><span class="sxs-lookup"><span data-stu-id="e77c5-107">Save the string representation of the <xref:System.DateTime> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>  
  
3.  <span data-ttu-id="e77c5-108">表す文字列を取得、<xref:System.DateTime>値。</span><span class="sxs-lookup"><span data-stu-id="e77c5-108">Retrieve the string that represents the <xref:System.DateTime> value.</span></span>  
  
4.  <span data-ttu-id="e77c5-109">呼び出す、<xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType>メソッド、およびパス<xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>の値として、`styles`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="e77c5-109">Call the <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>  
  
 <span data-ttu-id="e77c5-110">次の例を示していますラウンドト リップする方法、<xref:System.DateTime>値。</span><span class="sxs-lookup"><span data-stu-id="e77c5-110">The following example illustrates how to round-trip a <xref:System.DateTime> value.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
 [!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]  
  
 <span data-ttu-id="e77c5-111">場合にラウンド トリップ、<xref:System.DateTime>値、この手法は正常にすべてのローカルと協定世界時刻の時間保持します。</span><span class="sxs-lookup"><span data-stu-id="e77c5-111">When round-tripping a <xref:System.DateTime> value, this technique successfully preserves the time for all local and universal times.</span></span> <span data-ttu-id="e77c5-112">たとえば、ローカル<xref:System.DateTime>値は、米国内のシステムに保存米国中部標準時タイム ゾーンのシステムで復元された場合、復元された日付と時刻は 2 つのタイム ゾーンの時差を反映し、元の時刻より 2 時間後になります。</span><span class="sxs-lookup"><span data-stu-id="e77c5-112">For example, if a local <xref:System.DateTime> value is saved on a system in the U.S. Pacific Standard Time zone and is restored on a system in the U.S. Central Standard Time zone, the restored date and time will be two hours later than the original time, which reflects the time difference between the two time zones.</span></span> <span data-ttu-id="e77c5-113">ただし、タイム ゾーンが指定されていない時刻の場合、この方法では必ずしも正確な結果を得られるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="e77c5-113">However, this technique is not necessarily accurate for unspecified times.</span></span> <span data-ttu-id="e77c5-114">すべて<xref:System.DateTime>値を持つ<xref:System.DateTime.Kind%2A>プロパティは<xref:System.DateTimeKind.Unspecified>はローカル時刻として扱われます。</span><span class="sxs-lookup"><span data-stu-id="e77c5-114">All <xref:System.DateTime> values whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified> are treated as if they are local times.</span></span> <span data-ttu-id="e77c5-115">この場合、これがない場合、<xref:System.DateTime>は正常に、適切な時点を時間で識別できません。</span><span class="sxs-lookup"><span data-stu-id="e77c5-115">If this is not the case, the <xref:System.DateTime> will not successfully identify the correct point in time.</span></span> <span data-ttu-id="e77c5-116">この制限を回避するには、日付と時刻の値と該当するタイム ゾーンを確実に関連付けてから保存操作と復元操作を行います。</span><span class="sxs-lookup"><span data-stu-id="e77c5-116">The workaround for this limitation is to tightly couple a date and time value with its time zone for the save and restore operation.</span></span>  
  
### <a name="to-round-trip-a-datetimeoffset-value"></a><span data-ttu-id="e77c5-117">DateTimeOffset 値をラウンドトリップさせるには</span><span class="sxs-lookup"><span data-stu-id="e77c5-117">To round-trip a DateTimeOffset value</span></span>  
  
1.  <span data-ttu-id="e77c5-118">変換、<xref:System.DateTimeOffset>を呼び出すことによって、文字列形式の値、 <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> "o"書式指定子を持つメソッドです。</span><span class="sxs-lookup"><span data-stu-id="e77c5-118">Convert the <xref:System.DateTimeOffset> value to its string representation by calling the <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>  
  
2.  <span data-ttu-id="e77c5-119">文字列形式を保存、<xref:System.DateTimeOffset>値をファイル、またはプロセス、アプリケーション ドメイン、またはコンピューターの境界を通過させます。</span><span class="sxs-lookup"><span data-stu-id="e77c5-119">Save the string representation of the <xref:System.DateTimeOffset> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>  
  
3.  <span data-ttu-id="e77c5-120">表す文字列を取得、<xref:System.DateTimeOffset>値。</span><span class="sxs-lookup"><span data-stu-id="e77c5-120">Retrieve the string that represents the <xref:System.DateTimeOffset> value.</span></span>  
  
4.  <span data-ttu-id="e77c5-121">呼び出す、<xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType>メソッド、およびパス<xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>の値として、`styles`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="e77c5-121">Call the <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>  
  
 <span data-ttu-id="e77c5-122">次の例を示していますラウンドト リップする方法、<xref:System.DateTimeOffset>値。</span><span class="sxs-lookup"><span data-stu-id="e77c5-122">The following example illustrates how to round-trip a <xref:System.DateTimeOffset> value.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
 [!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]  
  
 <span data-ttu-id="e77c5-123">この手法を常に明確に識別、<xref:System.DateTimeOffset>時間内の単一ポイントとしての値。</span><span class="sxs-lookup"><span data-stu-id="e77c5-123">This technique always unambiguously identifies a <xref:System.DateTimeOffset> value as a single point in time.</span></span> <span data-ttu-id="e77c5-124">値から変換できるを世界協定時刻 (UTC) を呼び出して、<xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType>メソッド、またはそのは呼び出すことでの特定のタイム ゾーンの時刻に変換できる、<xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType>または<xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e77c5-124">The value can then be converted to Coordinated Universal Time (UTC) by calling the <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> method, or it can be converted to the time in a particular time zone by calling the <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> or <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e77c5-125">この手法の大きな限界は、その日付と時刻の算術演算子で実行されると、<xref:System.DateTimeOffset>を特定のタイム ゾーンの時刻を表す値ではそのタイム ゾーンの正確な結果が得られない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e77c5-125">The major limitation of this technique is that date and time arithmetic, when performed on a <xref:System.DateTimeOffset> value that represents the time in a particular time zone, may not produce accurate results for that time zone.</span></span> <span data-ttu-id="e77c5-126">これは、ためと、<xref:System.DateTimeOffset>値がインスタンス化される、そのタイム ゾーンの関連付けが解除されします。</span><span class="sxs-lookup"><span data-stu-id="e77c5-126">This is because when a <xref:System.DateTimeOffset> value is instantiated, it is disassociated from its time zone.</span></span> <span data-ttu-id="e77c5-127">したがって、日付と時刻の計算を実行した場合、タイム ゾーンの調整規則は適用されなくなります。</span><span class="sxs-lookup"><span data-stu-id="e77c5-127">Therefore, that time zone's adjustment rules can no longer be applied when you perform date and time calculations.</span></span> <span data-ttu-id="e77c5-128">この問題を回避するには、日付と時刻の値、および付随するタイム ゾーンの両方を保持するカスタム型を定義します。</span><span class="sxs-lookup"><span data-stu-id="e77c5-128">You can work around this problem by defining a custom type that includes both a date and time value and its accompanying time zone.</span></span>  
  
### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a><span data-ttu-id="e77c5-129">そのタイム ゾーンの日付と時刻の値をラウンドト リップさせる</span><span class="sxs-lookup"><span data-stu-id="e77c5-129">To round-trip a date and time value with its time zone</span></span>  
  
1.  <span data-ttu-id="e77c5-130">クラスまたは 2 つのフィールドを持つ構造体を定義します。</span><span class="sxs-lookup"><span data-stu-id="e77c5-130">Define a class or a structure with two fields.</span></span> <span data-ttu-id="e77c5-131">いずれかの最初のフィールドは、<xref:System.DateTime>または<xref:System.DateTimeOffset>オブジェクト、および 2 つ目は、<xref:System.TimeZoneInfo>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e77c5-131">The first field is either a <xref:System.DateTime> or a <xref:System.DateTimeOffset> object, and the second is a <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="e77c5-132">次の例は、このような型の簡易バージョンです。</span><span class="sxs-lookup"><span data-stu-id="e77c5-132">The following example is a simple version of such a type.</span></span>  
  
     [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
     [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]  
  
2.  <span data-ttu-id="e77c5-133">クラスを宣言、<xref:System.SerializableAttribute>属性。</span><span class="sxs-lookup"><span data-stu-id="e77c5-133">Mark the class with the <xref:System.SerializableAttribute> attribute.</span></span>  
  
3.  <span data-ttu-id="e77c5-134">使用してオブジェクトをシリアル化、<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e77c5-134">Serialize the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> method.</span></span>  
  
4.  <span data-ttu-id="e77c5-135">オブジェクトを使用して、復元、<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e77c5-135">Restore the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> method.</span></span>  
  
5.  <span data-ttu-id="e77c5-136">キャスト (C# の場合) か、適切な型のオブジェクトに逆シリアル化されたオブジェクト (Visual Basic で) に変換します。</span><span class="sxs-lookup"><span data-stu-id="e77c5-136">Cast (in C#) or convert (in Visual Basic) the deserialized object to an object of the appropriate type.</span></span>  
  
 <span data-ttu-id="e77c5-137">次の例では、日付と時刻とタイム ゾーン情報が格納されたオブジェクトをラウンドト リップさせる方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e77c5-137">The following example illustrates how to round-trip an object that stores both date and time and time zone information.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
 [!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]  
  
 <span data-ttu-id="e77c5-138">この方法は、どちらも、保存し、復元、および前に待機する時間組み合わされた日付と時刻とタイム ゾーン オブジェクトの実装と同期するように日付値を許可されていないこと、適切な時点を反映常に明確にする必要があります、タイム ゾーンの値です。</span><span class="sxs-lookup"><span data-stu-id="e77c5-138">This technique should always unambiguously reflect the correct point of time both before and after it is saved and restored, provided that the implementation of the combined date and time and time zone object does not allow the date value to become out of sync with the time zone value.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e77c5-139">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="e77c5-139">Compiling the Code</span></span>  
 <span data-ttu-id="e77c5-140">これらの例には次の項目が必要です。</span><span class="sxs-lookup"><span data-stu-id="e77c5-140">These examples require:</span></span>  
  
-   <span data-ttu-id="e77c5-141">次の名前空間は、c# を使用してインポートする`using`ステートメントまたは[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]`Imports`ステートメント。</span><span class="sxs-lookup"><span data-stu-id="e77c5-141">That the following namespaces be imported with C# `using` statements or [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] `Imports` statements:</span></span>  
  
    -   <span data-ttu-id="e77c5-142"><xref:System>(C# の場合のみ)。</span><span class="sxs-lookup"><span data-stu-id="e77c5-142"><xref:System> (C# only).</span></span>  
  
    -   <span data-ttu-id="e77c5-143"><xref:System.Globalization?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="e77c5-143"><xref:System.Globalization?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="e77c5-144"><xref:System.IO?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="e77c5-144"><xref:System.IO?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="e77c5-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="e77c5-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="e77c5-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="e77c5-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="e77c5-147">System.Core.dll への参照。</span><span class="sxs-lookup"><span data-stu-id="e77c5-147">A reference to System.Core.dll.</span></span>  
  
-   <span data-ttu-id="e77c5-148">各のコード例では、以外の場合、 `DateInTimeZone` 、クラスのクラスまたは Visual Basic モジュールに含まれる、メソッドでは、ラップされたおよびから呼び出される必要がある、`Main`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e77c5-148">Each code example, other than the `DateInTimeZone` class, should be included in a class or Visual Basic module, wrapped in methods, and called from the `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e77c5-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="e77c5-149">See Also</span></span>  
 [<span data-ttu-id="e77c5-150">書式設定操作の実行</span><span class="sxs-lookup"><span data-stu-id="e77c5-150">Performing Formatting Operations</span></span>](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [<span data-ttu-id="e77c5-151">DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の使い分け</span><span class="sxs-lookup"><span data-stu-id="e77c5-151">Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>](../../../docs/standard/datetime/choosing-between-datetime.md)  
 [<span data-ttu-id="e77c5-152">Standard Date and Time Format Strings</span><span class="sxs-lookup"><span data-stu-id="e77c5-152">Standard Date and Time Format Strings</span></span>](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
