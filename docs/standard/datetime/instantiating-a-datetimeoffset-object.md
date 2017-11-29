---
title: "DateTimeOffset オブジェクトのインスタンス化"
ms.custom: 
ms.date: 04/10/2017
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
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
- DateTimeOffset structure, converting to DateTime
- DateTimeOffset structure, instantiating
ms.assetid: 9648375f-d368-4373-a976-3332ece00c0a
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f072aecf45aaaf9bd4aec845a698d6f12916fedb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="instantiating-a-datetimeoffset-object"></a><span data-ttu-id="f3055-102">DateTimeOffset オブジェクトのインスタンス化</span><span class="sxs-lookup"><span data-stu-id="f3055-102">Instantiating a DateTimeOffset object</span></span>

<span data-ttu-id="f3055-103"><xref:System.DateTimeOffset>構造体は、さまざまな新しいを作成する方法を提供しています<xref:System.DateTimeOffset>値。</span><span class="sxs-lookup"><span data-stu-id="f3055-103">The <xref:System.DateTimeOffset> structure offers a number of ways to create new <xref:System.DateTimeOffset> values.</span></span> <span data-ttu-id="f3055-104">新規のインスタンス化に使用可能なメソッドに直接対応してそれらの多く<xref:System.DateTime>値、日付と時刻の値には世界協定時刻 (UTC) からのオフセットを指定するための機能強化。</span><span class="sxs-lookup"><span data-stu-id="f3055-104">Many of them correspond directly to the methods available for instantiating new <xref:System.DateTime> values, with enhancements that allow you to specify the date and time value's offset from Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="f3055-105">具体的には、インスタンスを作成できる、<xref:System.DateTimeOffset>次の方法で値。</span><span class="sxs-lookup"><span data-stu-id="f3055-105">In particular, you can instantiate a <xref:System.DateTimeOffset> value in the following ways:</span></span>

* <span data-ttu-id="f3055-106">日付と時刻のリテラルを使用します。</span><span class="sxs-lookup"><span data-stu-id="f3055-106">By using a date and time literal.</span></span>

* <span data-ttu-id="f3055-107">呼び出して、<xref:System.DateTimeOffset>コンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="f3055-107">By calling a <xref:System.DateTimeOffset> constructor.</span></span>

* <span data-ttu-id="f3055-108">値を暗黙的に変換して<xref:System.DateTimeOffset>値。</span><span class="sxs-lookup"><span data-stu-id="f3055-108">By implicitly converting a value to <xref:System.DateTimeOffset> value.</span></span>

* <span data-ttu-id="f3055-109">日付と時刻の文字列形式を解析する。</span><span class="sxs-lookup"><span data-stu-id="f3055-109">By parsing the string representation of a date and time.</span></span>

<span data-ttu-id="f3055-110">このトピックでは大きい詳細とコードを新しいのインスタンス化のこれらの方法を示す<xref:System.DateTimeOffset>値。</span><span class="sxs-lookup"><span data-stu-id="f3055-110">This topic provides greater detail and code examples that illustrate these methods of instantiating new <xref:System.DateTimeOffset> values.</span></span>

## <a name="date-and-time-literals"></a><span data-ttu-id="f3055-111">日付と時刻のリテラル</span><span class="sxs-lookup"><span data-stu-id="f3055-111">Date and time literals</span></span>

<span data-ttu-id="f3055-112">サポートされている、インスタンスを作成する最も一般的な方法のいずれかの言語、<xref:System.DateTime>値が日付と時刻をハード コーディングされたリテラル値としてを提供することです。</span><span class="sxs-lookup"><span data-stu-id="f3055-112">For languages that support it, one of the most common ways to instantiate a <xref:System.DateTime> value is to provide the date and time as a hard-coded literal value.</span></span> <span data-ttu-id="f3055-113">たとえば、次の Visual Basic コードを作成、<xref:System.DateTime>オブジェクトの値がある 2008 年 1 月 1 日午前 10時 00分です。</span><span class="sxs-lookup"><span data-stu-id="f3055-113">For example, the following Visual Basic code creates a <xref:System.DateTime> object whose value is January 1, 2008, at 10:00 AM.</span></span>

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]

<span data-ttu-id="f3055-114"><xref:System.DateTimeOffset>サポートする言語を使用する場合は、日付と時刻のリテラルを使用して値を初期化することも<xref:System.DateTime>リテラルです。</span><span class="sxs-lookup"><span data-stu-id="f3055-114"><xref:System.DateTimeOffset> values can also be initialized using date and time literals when using languages that support <xref:System.DateTime> literals.</span></span> <span data-ttu-id="f3055-115">たとえば、次の Visual Basic コードを作成、<xref:System.DateTimeOffset>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f3055-115">For example, the following Visual Basic code creates a <xref:System.DateTimeOffset> object.</span></span>

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]

<span data-ttu-id="f3055-116">コンソール出力に示す、<xref:System.DateTimeOffset>この方法で作成された値には、ローカル タイム ゾーンのオフセットが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="f3055-116">As the console output shows, the <xref:System.DateTimeOffset> value created in this way is assigned the offset of the local time zone.</span></span> <span data-ttu-id="f3055-117">つまり、<xref:System.DateTimeOffset>別のコンピューターに、コードが実行される場合に、リテラル文字を使用して割り当てられた値が 1 つの特定の時点を識別できません。</span><span class="sxs-lookup"><span data-stu-id="f3055-117">This means that a <xref:System.DateTimeOffset> value assigned using a character literal does not identify a single point of time if the code is run on different computers.</span></span>

## <a name="datetimeoffset-constructors"></a><span data-ttu-id="f3055-118">DateTimeOffset コンス トラクター</span><span class="sxs-lookup"><span data-stu-id="f3055-118">DateTimeOffset constructors</span></span>

<span data-ttu-id="f3055-119"><xref:System.DateTimeOffset>型は、6 つのコンス トラクターを定義します。</span><span class="sxs-lookup"><span data-stu-id="f3055-119">The <xref:System.DateTimeOffset> type defines six constructors.</span></span> <span data-ttu-id="f3055-120">直接対応しているうちの 4 つ<xref:System.DateTime>コンス トラクターには、追加のパラメーター型の<xref:System.TimeSpan>日付を定義して、UTC からの時刻のオフセットします。</span><span class="sxs-lookup"><span data-stu-id="f3055-120">Four of them correspond directly to <xref:System.DateTime> constructors, with an additional parameter of type <xref:System.TimeSpan> that defines the date and time's offset from UTC.</span></span> <span data-ttu-id="f3055-121">これらを定義できます、<xref:System.DateTimeOffset>個別の日付と時刻要素の値に基づいて値。</span><span class="sxs-lookup"><span data-stu-id="f3055-121">These allow you to define a <xref:System.DateTimeOffset> value based on the value of its individual date and time components.</span></span> <span data-ttu-id="f3055-122">次のコードがインスタンス化するこれら 4 つのコンス トラクターを使用するなど、 <xref:System.DateTimeOffset> 7/1/2008 のと同じ値を持つオブジェクト 12時 05分 AM +01: 00 です。</span><span class="sxs-lookup"><span data-stu-id="f3055-122">For example, the following code uses these four constructors to instantiate <xref:System.DateTimeOffset> objects with identical values of 7/1/2008 12:05 AM +01:00.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]

<span data-ttu-id="f3055-123">なお、ときの値、<xref:System.DateTimeOffset>を使用してインスタンス化されるオブジェクト、<xref:System.Globalization.PersianCalendar>オブジェクトとして、コンス トラクターへの引数のいずれかがコンソールに表示されたら、ペルシャ暦ではなく、グレゴリオ暦の日付として表されます。</span><span class="sxs-lookup"><span data-stu-id="f3055-123">Note that, when the value of the <xref:System.DateTimeOffset> object instantiated using a <xref:System.Globalization.PersianCalendar> object as one of the arguments to its constructor is displayed to the console, it is expressed as a date in the Gregorian rather than the Persian calendar.</span></span> <span data-ttu-id="f3055-124">ペルシャ暦を使用して日付を出力の例を参照してください。、<xref:System.Globalization.PersianCalendar>トピックです。</span><span class="sxs-lookup"><span data-stu-id="f3055-124">To output a date using the Persian calendar, see the example in the <xref:System.Globalization.PersianCalendar> topic.</span></span>

<span data-ttu-id="f3055-125">他の 2 つのコンス トラクターを作成、<xref:System.DateTimeOffset>オブジェクトから、<xref:System.DateTime>値。</span><span class="sxs-lookup"><span data-stu-id="f3055-125">The other two constructors create a <xref:System.DateTimeOffset> object from a <xref:System.DateTime> value.</span></span> <span data-ttu-id="f3055-126">最初のデータセットが 1 つのパラメーター、<xref:System.DateTime>に変換する値、<xref:System.DateTimeOffset>値。</span><span class="sxs-lookup"><span data-stu-id="f3055-126">The first of these has a single parameter, the <xref:System.DateTime> value to convert to a <xref:System.DateTimeOffset> value.</span></span> <span data-ttu-id="f3055-127">結果のオフセット<xref:System.DateTimeOffset>値によって異なります、<xref:System.DateTime.Kind%2A>コンス トラクターの 1 つのパラメーターのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="f3055-127">The offset of the resulting <xref:System.DateTimeOffset> value depends on the <xref:System.DateTime.Kind%2A> property of the constructor's single parameter.</span></span> <span data-ttu-id="f3055-128">値が場合<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>、オフセットに設定して<xref:System.TimeSpan.Zero?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="f3055-128">If its value is <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, the offset is set equal to <xref:System.TimeSpan.Zero?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f3055-129">それ以外の場合、オフセットはローカル タイム ゾーンのオフセットと等しい値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="f3055-129">Otherwise, its offset is set equal to that of the local time zone.</span></span> <span data-ttu-id="f3055-130">次の例は、インスタンスを作成するこのコンス トラクターの使用を示しています。 <xref:System.DateTimeOffset> UTC とローカル タイム ゾーンを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f3055-130">The following example illustrates the use of this constructor to instantiate <xref:System.DateTimeOffset> objects representing UTC and the local time zone:</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]

> [!NOTE]
> <span data-ttu-id="f3055-131">オーバー ロードを呼び出して、<xref:System.DateTimeOffset>を 1 つを持つコンス トラクター<xref:System.DateTime>パラメーターの暗黙の変換を実行するのには、<xref:System.DateTime>値を<xref:System.DateTimeOffset>値。</span><span class="sxs-lookup"><span data-stu-id="f3055-131">Calling the overload of the <xref:System.DateTimeOffset> constructor that has a single <xref:System.DateTime> parameter is equivalent to performing an implicit conversion of a <xref:System.DateTime> value to a <xref:System.DateTimeOffset> value.</span></span>

<span data-ttu-id="f3055-132">作成する 2 番目のコンス トラクター、<xref:System.DateTimeOffset>オブジェクトから、<xref:System.DateTime>値が 2 つのパラメーター:<xref:System.DateTime>変換対象の値と<xref:System.TimeSpan>UTC から日付と時刻を表す値のオフセットします。</span><span class="sxs-lookup"><span data-stu-id="f3055-132">The second constructor that creates a <xref:System.DateTimeOffset> object from a <xref:System.DateTime> value has two parameters: the <xref:System.DateTime> value to convert, and a <xref:System.TimeSpan> value representing the date and time's offset from UTC.</span></span> <span data-ttu-id="f3055-133">このオフセット値に対応する必要があります、<xref:System.DateTime.Kind%2A>コンス トラクターの最初のパラメーターのプロパティまたは<xref:System.ArgumentException>がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f3055-133">This offset value must correspond to the <xref:System.DateTime.Kind%2A> property of the constructor's first parameter or an <xref:System.ArgumentException> is thrown.</span></span> <span data-ttu-id="f3055-134">場合、<xref:System.DateTime.Kind%2A>最初のパラメーターのプロパティが<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>、2 番目のパラメーターの値である必要があります<xref:System.TimeSpan.Zero?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="f3055-134">If the <xref:System.DateTime.Kind%2A> property of the first parameter is <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, the value of the second parameter must be <xref:System.TimeSpan.Zero?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f3055-135">場合、<xref:System.DateTime.Kind%2A>最初のパラメーターのプロパティが<xref:System.DateTimeKind.Local?displayProperty=nameWithType>、2 番目のパラメーターの値は、ローカル システムのタイム ゾーンのオフセットである必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3055-135">If the <xref:System.DateTime.Kind%2A> property of the first parameter is <xref:System.DateTimeKind.Local?displayProperty=nameWithType>, the value of the second parameter must be the offset of the local system's time zone.</span></span> <span data-ttu-id="f3055-136">場合、<xref:System.DateTime.Kind%2A>最初のパラメーターのプロパティが<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>オフセットが有効な値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f3055-136">If the <xref:System.DateTime.Kind%2A> property of the first parameter is <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, the offset can be any valid value.</span></span> <span data-ttu-id="f3055-137">次のコードはこのコンス トラクターを呼び出して変換を<xref:System.DateTime>に<xref:System.DateTimeOffset>値。</span><span class="sxs-lookup"><span data-stu-id="f3055-137">The following code illustrates calls to this constructor to convert <xref:System.DateTime> to <xref:System.DateTimeOffset> values.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]

## <a name="implicit-type-conversion"></a><span data-ttu-id="f3055-138">暗黙の型変換</span><span class="sxs-lookup"><span data-stu-id="f3055-138">Implicit type conversion</span></span>

<span data-ttu-id="f3055-139"><xref:System.DateTimeOffset>型は、1 つの暗黙的な型変換をサポートしています: から、<xref:System.DateTime>値を<xref:System.DateTimeOffset>値。</span><span class="sxs-lookup"><span data-stu-id="f3055-139">The <xref:System.DateTimeOffset> type supports one implicit type conversion: from a <xref:System.DateTime> value to a <xref:System.DateTimeOffset> value.</span></span> <span data-ttu-id="f3055-140">(暗黙的な型変換とは、明示的なキャスト (C# の場合) または変換 (Visual Basic の場合) を必要とせず、情報を失わない 1 つの型から別の型への変換です)。</span><span class="sxs-lookup"><span data-stu-id="f3055-140">(An implicit type conversion is a conversion from one type to another that does not require an explicit cast (in C#) or conversion (in Visual Basic) and that does not lose information.</span></span> <span data-ttu-id="f3055-141">これにより、次のようなコードが可能となります。</span><span class="sxs-lookup"><span data-stu-id="f3055-141">It makes code like the following possible.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]

<span data-ttu-id="f3055-142">結果のオフセット<xref:System.DateTimeOffset>値によって異なります、<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>プロパティの値。</span><span class="sxs-lookup"><span data-stu-id="f3055-142">The offset of the resulting <xref:System.DateTimeOffset> value depends on the <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> property value.</span></span> <span data-ttu-id="f3055-143">値が場合<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>、オフセットに設定して<xref:System.TimeSpan.Zero?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="f3055-143">If its value is <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, the offset is set equal to <xref:System.TimeSpan.Zero?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f3055-144">いずれかの値が場合<xref:System.DateTimeKind.Local?displayProperty=nameWithType>または<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>、ローカル タイム ゾーンのオフセットを設定します。</span><span class="sxs-lookup"><span data-stu-id="f3055-144">If its value is either <xref:System.DateTimeKind.Local?displayProperty=nameWithType> or <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, the offset is set equal to that of the local time zone.</span></span>

## <a name="parsing-the-string-representation-of-a-date-and-time"></a><span data-ttu-id="f3055-145">日付と時刻の文字列形式を解析します。</span><span class="sxs-lookup"><span data-stu-id="f3055-145">Parsing the string representation of a date and time</span></span>

<span data-ttu-id="f3055-146"><xref:System.DateTimeOffset>の種類をサポートするために日時、日付の文字列形式に変換できる 4 つのメソッド、<xref:System.DateTimeOffset>値。</span><span class="sxs-lookup"><span data-stu-id="f3055-146">The <xref:System.DateTimeOffset> type supports four methods that allow you to convert the string representation of a date and time into a <xref:System.DateTimeOffset> value:</span></span>

* <span data-ttu-id="f3055-147"><xref:System.DateTimeOffset.Parse%2A>、に日時、日付の文字列形式に変換しようとする、<xref:System.DateTimeOffset>値し、変換が失敗した場合、例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="f3055-147"><xref:System.DateTimeOffset.Parse%2A>, which tries to convert the string representation of a date and time to a <xref:System.DateTimeOffset> value and throws an exception if the conversion fails.</span></span>

* <span data-ttu-id="f3055-148"><xref:System.DateTimeOffset.TryParse%2A>、に日時、日付の文字列形式に変換しようとする、<xref:System.DateTimeOffset>値を返す`false`場合は、変換は失敗します。</span><span class="sxs-lookup"><span data-stu-id="f3055-148"><xref:System.DateTimeOffset.TryParse%2A>, which tries to convert the string representation of a date and time to a <xref:System.DateTimeOffset> value and returns `false` if the conversion fails.</span></span>

* <span data-ttu-id="f3055-149"><xref:System.DateTimeOffset.ParseExact%2A>、日付と時刻を指定した形式の文字列形式に変換しようとする、<xref:System.DateTimeOffset>値。</span><span class="sxs-lookup"><span data-stu-id="f3055-149"><xref:System.DateTimeOffset.ParseExact%2A>, which tries to convert the string representation of a date and time in a specified format to a <xref:System.DateTimeOffset> value.</span></span> <span data-ttu-id="f3055-150">変換が失敗すると、メソッドは例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="f3055-150">The method throws an exception if the conversion fails.</span></span>

* <span data-ttu-id="f3055-151"><xref:System.DateTimeOffset.TryParseExact%2A>、日付と時刻を指定した形式の文字列形式に変換しようとする、<xref:System.DateTimeOffset>値。</span><span class="sxs-lookup"><span data-stu-id="f3055-151"><xref:System.DateTimeOffset.TryParseExact%2A>, which tries to convert the string representation of a date and time in a specified format to a <xref:System.DateTimeOffset> value.</span></span> <span data-ttu-id="f3055-152">変換が失敗すると、メソッドは `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="f3055-152">The method returns `false` if the conversion fails.</span></span>

<span data-ttu-id="f3055-153">次の例では、インスタンスを作成するこれらの 4 つの文字列変換メソッドを呼び出し、<xref:System.DateTimeOffset>値。</span><span class="sxs-lookup"><span data-stu-id="f3055-153">The following example illustrates calls to each of these four string conversion methods to instantiate a <xref:System.DateTimeOffset> value.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]

## <a name="see-also"></a><span data-ttu-id="f3055-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3055-154">See also</span></span>

[<span data-ttu-id="f3055-155">日付、時刻、およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="f3055-155">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
