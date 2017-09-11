---
title: "方法: コンピューター上に存在するタイム ゾーンを列挙する"
description: "方法: コンピューター上に存在するタイム ゾーンを列挙する"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: c5ae4a6c-1790-4355-b5b1-879aaf956129
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: f30ba2a483ff7e5867417969946c2774175d5e3d
ms.contentlocale: ja-jp
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a><span data-ttu-id="c6c6b-104">方法: コンピューター上に存在するタイム ゾーンを列挙する</span><span class="sxs-lookup"><span data-stu-id="c6c6b-104">How to: enumerate time zones present on a computer</span></span>

<span data-ttu-id="c6c6b-105">指定されたタイム ゾーンを正しく処理するには、そのタイム ゾーンに関する情報がシステムで使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6c6b-105">Successfully working with a designated time zone requires that information about that time zone be available to the system.</span></span> <span data-ttu-id="c6c6b-106">たとえば、Windows オペレーティング システムでは、この情報はレジストリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="c6c6b-106">For example, the Windows operating system stores this information in the registry.</span></span> <span data-ttu-id="c6c6b-107">しかし、世界中に存在するタイム ゾーンの合計数は大きいものの、レジストリにはそれらの一部に関する情報しか含まれません。</span><span class="sxs-lookup"><span data-stu-id="c6c6b-107">However, although the total number of time zones that exist throughout the world is large, the registry contains information about only a subset of them.</span></span> <span data-ttu-id="c6c6b-108">さらに、レジストリ自体は、内容が意図的に、および誤って変更される可能性がある動的な構造です。</span><span class="sxs-lookup"><span data-stu-id="c6c6b-108">In addition, the registry itself is a dynamic structure whose contents are subject to both deliberate and accidental change.</span></span> <span data-ttu-id="c6c6b-109">その結果、アプリケーションは、特定のタイム ゾーンがシステムで定義され、使用できると常に想定することができません。</span><span class="sxs-lookup"><span data-stu-id="c6c6b-109">As a result, an application cannot always assume that a particular time zone is defined and available on a system.</span></span> <span data-ttu-id="c6c6b-110">タイム ゾーン情報のアプリケーションを使用する多くのアプリケーションの最初の手順は、必要なタイム ゾーンがローカル システムで使用できるかどうかを判断する、またはタイム ゾーンの一覧をユーザーに提供して選択させることです。</span><span class="sxs-lookup"><span data-stu-id="c6c6b-110">The first step for many applications that use time zone information applications is to determine whether required time zones are available on the local system, or to give the user a list of time zones from which to select.</span></span> <span data-ttu-id="c6c6b-111">これには、アプリケーションがローカル システムで定義されているタイム ゾーンを列挙する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6c6b-111">This requires that an application enumerate the time zones defined on a local system.</span></span> 

## <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a><span data-ttu-id="c6c6b-112">ローカル システムに存在するタイム ゾーンを列挙するには</span><span class="sxs-lookup"><span data-stu-id="c6c6b-112">To enumerate the time zones present on the local system</span></span>

1. <span data-ttu-id="c6c6b-113">[TimeZoneInfo.GetSystemTimeZones](xref:System.TimeZoneInfo.GetSystemTimeZones) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c6c6b-113">Call the [TimeZoneInfo.GetSystemTimeZones](xref:System.TimeZoneInfo.GetSystemTimeZones) method.</span></span> <span data-ttu-id="c6c6b-114">メソッドは [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトのジェネリック [ReadOnlyCollection&lt;T&gt;](xref:System.Collections.ObjectModel.ReadOnlyCollection%601) コレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="c6c6b-114">The method returns a generic [ReadOnlyCollection&lt;T&gt;](xref:System.Collections.ObjectModel.ReadOnlyCollection%601) collection of [TimeZoneInfo](xref:System.TimeZoneInfo) objects.</span></span> <span data-ttu-id="c6c6b-115">コレクション内のエントリは、[DisplayName](xref:System.TimeZoneInfo.DisplayName) プロパティによって並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="c6c6b-115">The entries in the collection are sorted by their [DisplayName](xref:System.TimeZoneInfo.DisplayName) property.</span></span> <span data-ttu-id="c6c6b-116">例:</span><span class="sxs-lookup"><span data-stu-id="c6c6b-116">For example:</span></span>

    ```csharp
    ReadOnlyCollection<TimeZoneInfo> tzCollection;
    tzCollection = TimeZoneInfo.GetSystemTimeZones();
    ```

    ```vb
    Dim tzCollection As ReadOnlyCollection(Of TimeZoneInfo) = TimeZoneInfo.GetSystemTimeZones
    ```

2. <span data-ttu-id="c6c6b-117">`foreach` ループ (C#) または `For Each…Next` ループ (Visual Basic) を使用して、コレクション内の個々の [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトを列挙し、各オブジェクトに対して必要な処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="c6c6b-117">Enumerate the individual [TimeZoneInfo](xref:System.TimeZoneInfo) objects in the collection by using a `foreach` loop (in C#) or a `For Each…Next` loop (in Visual Basic), and perform any necessary processing on each object.</span></span> <span data-ttu-id="c6c6b-118">たとえば、次のコードは、ステップ 1 で返された [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトの [ReadOnlyCollection&lt;T&gt;](xref:System.Collections.ObjectModel.ReadOnlyCollection%601) コレクションを列挙し、各タイム ゾーンの表示名をコンソールに一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="c6c6b-118">For example, the following code enumerates the [ReadOnlyCollection&lt;T&gt;](xref:System.Collections.ObjectModel.ReadOnlyCollection%601) collection of [TimeZoneInfo](xref:System.TimeZoneInfo) objects returned in step 1 and lists the display name of each time zone on the console.</span></span>

    ```csharp
    foreach (TimeZoneInfo timeZone in tzCollection)
    Console.WriteLine("   {0}: {1}", timeZone.Id, timeZone.DisplayName);
    ```

    ```vb
    For Each timeZone As TimeZoneInfo In tzCollection
        Console.WriteLine("   {0}: {1}", timeZone.Id, timeZone.DisplayName)
    Next
    ```

## <a name="see-also"></a><span data-ttu-id="c6c6b-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="c6c6b-119">See Also</span></span>

[<span data-ttu-id="c6c6b-120">日付、時刻およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="c6c6b-120">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="c6c6b-121">ローカル システムで定義されているタイム ゾーンの検索</span><span class="sxs-lookup"><span data-stu-id="c6c6b-121">Finding the time zones defined on a local system</span></span>](finding-the-time-zones-on-local-system.md)


