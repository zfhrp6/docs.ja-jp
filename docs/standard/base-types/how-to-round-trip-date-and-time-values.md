---
title: '方法 : 日付と時刻の値をラウンドトリップさせる'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26a1cafc7ed6e497e5aab9cd33654f3aa3d4d98c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-round-trip-date-and-time-values"></a><span data-ttu-id="eac7b-102">方法 : 日付と時刻の値をラウンドトリップさせる</span><span class="sxs-lookup"><span data-stu-id="eac7b-102">How to: Round-trip Date and Time Values</span></span>
<span data-ttu-id="eac7b-103">ある特定の時点を明確に表すように日付と時刻の値を保つことは、多くのアプリケーションに共通する要件です。</span><span class="sxs-lookup"><span data-stu-id="eac7b-103">In many applications, a date and time value is intended to unambiguously identify a single point in time.</span></span> <span data-ttu-id="eac7b-104">このトピックでは、<xref:System.DateTime> 値、<xref:System.DateTimeOffset> 値、日時値と時間帯の情報を保存し、復元する方法について説明します。復元した値によって、保存した値と同じ時刻が識別されるようにします。</span><span class="sxs-lookup"><span data-stu-id="eac7b-104">This topic shows how to save and restore a <xref:System.DateTime> value, a <xref:System.DateTimeOffset> value, and a date and time value with time zone information so that the restored value identifies the same time as the saved value.</span></span>  
  
### <a name="to-round-trip-a-datetime-value"></a><span data-ttu-id="eac7b-105">DateTime 値をラウンドトリップさせるには</span><span class="sxs-lookup"><span data-stu-id="eac7b-105">To round-trip a DateTime value</span></span>  
  
1.  <span data-ttu-id="eac7b-106"><xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> メソッドを "o" 書式指定子と共に呼び出して、<xref:System.DateTime> 値を対応する文字列形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="eac7b-106">Convert the <xref:System.DateTime> value to its string representation by calling the <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>  
  
2.  <span data-ttu-id="eac7b-107"><xref:System.DateTime> 値の文字列形式をファイルに保存するか、プロセス、アプリケーション ドメイン、またはマシン境界を通過させます。</span><span class="sxs-lookup"><span data-stu-id="eac7b-107">Save the string representation of the <xref:System.DateTime> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>  
  
3.  <span data-ttu-id="eac7b-108"><xref:System.DateTime> 値を表す文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="eac7b-108">Retrieve the string that represents the <xref:System.DateTime> value.</span></span>  
  
4.  <span data-ttu-id="eac7b-109"><xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> メソッドを呼び出し、`styles` パラメーターの値として <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> を渡します。</span><span class="sxs-lookup"><span data-stu-id="eac7b-109">Call the <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>  
  
 <span data-ttu-id="eac7b-110"><xref:System.DateTime> 値をラウンドトリップさせる方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="eac7b-110">The following example illustrates how to round-trip a <xref:System.DateTime> value.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
 [!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]  
  
 <span data-ttu-id="eac7b-111"><xref:System.DateTime> 値をラウンドトリップさせる場合、この方法により、あらゆる現地時刻と協定世界時刻を適切に保存できます。</span><span class="sxs-lookup"><span data-stu-id="eac7b-111">When round-tripping a <xref:System.DateTime> value, this technique successfully preserves the time for all local and universal times.</span></span> <span data-ttu-id="eac7b-112">たとえば、現地時刻の <xref:System.DateTime> 値が米国太平洋標準時タイム ゾーンのシステムで保存され、米国中部標準時タイム ゾーンのシステムで復元された場合、復元された日付と時刻は 2 つのタイム ゾーンの時差を反映し、元の時刻より 2 時間後になります。</span><span class="sxs-lookup"><span data-stu-id="eac7b-112">For example, if a local <xref:System.DateTime> value is saved on a system in the U.S. Pacific Standard Time zone and is restored on a system in the U.S. Central Standard Time zone, the restored date and time will be two hours later than the original time, which reflects the time difference between the two time zones.</span></span> <span data-ttu-id="eac7b-113">ただし、タイム ゾーンが指定されていない時刻の場合、この方法では必ずしも正確な結果を得られるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="eac7b-113">However, this technique is not necessarily accurate for unspecified times.</span></span> <span data-ttu-id="eac7b-114"><xref:System.DateTime.Kind%2A> プロパティが <xref:System.DateTimeKind.Unspecified> であるすべての <xref:System.DateTime> 値がローカル時間のように扱われます。</span><span class="sxs-lookup"><span data-stu-id="eac7b-114">All <xref:System.DateTime> values whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified> are treated as if they are local times.</span></span> <span data-ttu-id="eac7b-115">それ以外では、<xref:System.DateTime> は間違った時点を示すことになります。</span><span class="sxs-lookup"><span data-stu-id="eac7b-115">If this is not the case, the <xref:System.DateTime> will not successfully identify the correct point in time.</span></span> <span data-ttu-id="eac7b-116">この制限を回避するには、日付と時刻の値と該当するタイム ゾーンを確実に関連付けてから保存操作と復元操作を行います。</span><span class="sxs-lookup"><span data-stu-id="eac7b-116">The workaround for this limitation is to tightly couple a date and time value with its time zone for the save and restore operation.</span></span>  
  
### <a name="to-round-trip-a-datetimeoffset-value"></a><span data-ttu-id="eac7b-117">DateTimeOffset 値をラウンドトリップさせるには</span><span class="sxs-lookup"><span data-stu-id="eac7b-117">To round-trip a DateTimeOffset value</span></span>  
  
1.  <span data-ttu-id="eac7b-118"><xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> メソッドを "o" 書式指定子と共に呼び出して、<xref:System.DateTimeOffset> 値を対応する文字列形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="eac7b-118">Convert the <xref:System.DateTimeOffset> value to its string representation by calling the <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>  
  
2.  <span data-ttu-id="eac7b-119"><xref:System.DateTimeOffset> 値の文字列形式をファイルに保存するか、プロセス、アプリケーション ドメイン、またはマシン境界を通過させます。</span><span class="sxs-lookup"><span data-stu-id="eac7b-119">Save the string representation of the <xref:System.DateTimeOffset> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>  
  
3.  <span data-ttu-id="eac7b-120"><xref:System.DateTimeOffset> 値を表す文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="eac7b-120">Retrieve the string that represents the <xref:System.DateTimeOffset> value.</span></span>  
  
4.  <span data-ttu-id="eac7b-121"><xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> メソッドを呼び出し、`styles` パラメーターの値として <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> を渡します。</span><span class="sxs-lookup"><span data-stu-id="eac7b-121">Call the <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>  
  
 <span data-ttu-id="eac7b-122"><xref:System.DateTimeOffset> 値をラウンドトリップさせる方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="eac7b-122">The following example illustrates how to round-trip a <xref:System.DateTimeOffset> value.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
 [!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]  
  
 <span data-ttu-id="eac7b-123">この方法により、<xref:System.DateTimeOffset> 値は常にある特定の時点として明確に識別されます。</span><span class="sxs-lookup"><span data-stu-id="eac7b-123">This technique always unambiguously identifies a <xref:System.DateTimeOffset> value as a single point in time.</span></span> <span data-ttu-id="eac7b-124">識別されたら、<xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> メソッドを呼び出すことで、この値を協定世界時 (UTC) に変換できます。あるいは、<xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> または <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> メソッドを呼び出すことで、特定のタイム ゾーンの時刻に変換できます。</span><span class="sxs-lookup"><span data-stu-id="eac7b-124">The value can then be converted to Coordinated Universal Time (UTC) by calling the <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> method, or it can be converted to the time in a particular time zone by calling the <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> or <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="eac7b-125">この方法には、特定のタイム ゾーンの時刻を表す <xref:System.DateTimeOffset> 値に対して日付と時刻の演算を行ったときに、そのタイム ゾーンにおける正確な結果を得ることができない場合があるという重要な制限があります。</span><span class="sxs-lookup"><span data-stu-id="eac7b-125">The major limitation of this technique is that date and time arithmetic, when performed on a <xref:System.DateTimeOffset> value that represents the time in a particular time zone, may not produce accurate results for that time zone.</span></span> <span data-ttu-id="eac7b-126">これは、<xref:System.DateTimeOffset> 値をインスタンス化すると、対応するタイム ゾーンとの関連付けが解除されるためです。</span><span class="sxs-lookup"><span data-stu-id="eac7b-126">This is because when a <xref:System.DateTimeOffset> value is instantiated, it is disassociated from its time zone.</span></span> <span data-ttu-id="eac7b-127">したがって、日付と時刻の計算を実行した場合、タイム ゾーンの調整規則は適用されなくなります。</span><span class="sxs-lookup"><span data-stu-id="eac7b-127">Therefore, that time zone's adjustment rules can no longer be applied when you perform date and time calculations.</span></span> <span data-ttu-id="eac7b-128">この問題を回避するには、日付と時刻の値、および付随するタイム ゾーンの両方を保持するカスタム型を定義します。</span><span class="sxs-lookup"><span data-stu-id="eac7b-128">You can work around this problem by defining a custom type that includes both a date and time value and its accompanying time zone.</span></span>  
  
### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a><span data-ttu-id="eac7b-129">日時値とそのタイム ゾーンをラウンドトリップするには</span><span class="sxs-lookup"><span data-stu-id="eac7b-129">To round-trip a date and time value with its time zone</span></span>  
  
1.  <span data-ttu-id="eac7b-130">クラスまたは構造と 2 つのフィールドを定義します。</span><span class="sxs-lookup"><span data-stu-id="eac7b-130">Define a class or a structure with two fields.</span></span> <span data-ttu-id="eac7b-131">最初のフィールドは <xref:System.DateTime> または <xref:System.DateTimeOffset> オブジェクトです。2 つ目のフィールドは <xref:System.TimeZoneInfo> オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="eac7b-131">The first field is either a <xref:System.DateTime> or a <xref:System.DateTimeOffset> object, and the second is a <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="eac7b-132">次の例は、このような型を簡易にしたものです。</span><span class="sxs-lookup"><span data-stu-id="eac7b-132">The following example is a simple version of such a type.</span></span>  
  
     [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
     [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]  
  
2.  <span data-ttu-id="eac7b-133">クラスに <xref:System.SerializableAttribute> 属性を付けます。</span><span class="sxs-lookup"><span data-stu-id="eac7b-133">Mark the class with the <xref:System.SerializableAttribute> attribute.</span></span>  
  
3.  <span data-ttu-id="eac7b-134"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> メソッドを使用し、オブジェクトをシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="eac7b-134">Serialize the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> method.</span></span>  
  
4.  <span data-ttu-id="eac7b-135"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> メソッドを使用し、オブジェクトを復元します。</span><span class="sxs-lookup"><span data-stu-id="eac7b-135">Restore the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> method.</span></span>  
  
5.  <span data-ttu-id="eac7b-136">逆シリアル化されたオブジェクトを適切な型のオブジェクトにキャスト (C# の場合) するか、変換 (Visual Basic の場合) します。</span><span class="sxs-lookup"><span data-stu-id="eac7b-136">Cast (in C#) or convert (in Visual Basic) the deserialized object to an object of the appropriate type.</span></span>  
  
 <span data-ttu-id="eac7b-137">次の例では、日時とタイム ゾーン情報の両方を保存するオブジェクトをラウンドトリップする方法を確認できます。</span><span class="sxs-lookup"><span data-stu-id="eac7b-137">The following example illustrates how to round-trip an object that stores both date and time and time zone information.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
 [!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]  
  
 <span data-ttu-id="eac7b-138">この手法では、日時とタイム ゾーン オブジェクトを組み合わせるとき、日付値とタイム ゾーン値の同期が外れてはならないとき、保存と復元の前後で必ず、常に正しい時点を不明瞭なところなく反映する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eac7b-138">This technique should always unambiguously reflect the correct point of time both before and after it is saved and restored, provided that the implementation of the combined date and time and time zone object does not allow the date value to become out of sync with the time zone value.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="eac7b-139">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="eac7b-139">Compiling the Code</span></span>  
 <span data-ttu-id="eac7b-140">これらの例には次の項目が必要です。</span><span class="sxs-lookup"><span data-stu-id="eac7b-140">These examples require:</span></span>  
  
-   <span data-ttu-id="eac7b-141">次の名前空間を C# `using` ステートメントまたは Visual Basic `Imports` ステートメントでインポートすること:</span><span class="sxs-lookup"><span data-stu-id="eac7b-141">That the following namespaces be imported with C# `using` statements or Visual Basic `Imports` statements:</span></span>  
  
    -   <span data-ttu-id="eac7b-142"><xref:System> (C# のみ)。</span><span class="sxs-lookup"><span data-stu-id="eac7b-142"><xref:System> (C# only).</span></span>  
  
    -   <span data-ttu-id="eac7b-143"><xref:System.Globalization?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="eac7b-143"><xref:System.Globalization?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="eac7b-144"><xref:System.IO?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="eac7b-144"><xref:System.IO?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="eac7b-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="eac7b-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="eac7b-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="eac7b-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="eac7b-147">System.Core.dll の参照。</span><span class="sxs-lookup"><span data-stu-id="eac7b-147">A reference to System.Core.dll.</span></span>  
  
-   <span data-ttu-id="eac7b-148">`DateInTimeZone` クラス以外、各コード例はクラスまたは Visual Basic モジュールに含め、メソッドでラップし、`Main` メソッドから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="eac7b-148">Each code example, other than the `DateInTimeZone` class, should be included in a class or Visual Basic module, wrapped in methods, and called from the `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eac7b-149">参照</span><span class="sxs-lookup"><span data-stu-id="eac7b-149">See Also</span></span>  
 [<span data-ttu-id="eac7b-150">書式設定操作の実行</span><span class="sxs-lookup"><span data-stu-id="eac7b-150">Performing Formatting Operations</span></span>](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [<span data-ttu-id="eac7b-151">DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の使い分け</span><span class="sxs-lookup"><span data-stu-id="eac7b-151">Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>](../../../docs/standard/datetime/choosing-between-datetime.md)  
 [<span data-ttu-id="eac7b-152">Standard Date and Time Format Strings</span><span class="sxs-lookup"><span data-stu-id="eac7b-152">Standard Date and Time Format Strings</span></span>](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
