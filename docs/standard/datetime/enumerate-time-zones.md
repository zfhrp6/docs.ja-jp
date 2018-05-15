---
title: '方法: コンピューターに存在するタイム ゾーンを列挙'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], enumerating
- enumerating time zones [.NET Framework]
ms.assetid: bb7a42ab-6bd9-4c5c-b734-5546d51f8669
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfdc3993f6658ce5dc50050ed062c2de9d4cec29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a><span data-ttu-id="08b29-102">方法: コンピューターに存在するタイム ゾーンを列挙</span><span class="sxs-lookup"><span data-stu-id="08b29-102">How to: Enumerate time zones present on a computer</span></span>

<span data-ttu-id="08b29-103">指定されたタイム ゾーンを正しく処理するには、そのタイム ゾーンに関する情報がシステムで使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="08b29-103">Successfully working with a designated time zone requires that information about that time zone be available to the system.</span></span> <span data-ttu-id="08b29-104">Windows XP および Windows Vista オペレーティング システムでは、この情報をレジストリに格納します。</span><span class="sxs-lookup"><span data-stu-id="08b29-104">The Windows XP and Windows Vista operating systems store this information in the registry.</span></span> <span data-ttu-id="08b29-105">しかし、世界中に存在するタイム ゾーンの合計数は大きいものの、レジストリにはそれらの一部に関する情報しか含まれません。</span><span class="sxs-lookup"><span data-stu-id="08b29-105">However, although the total number of time zones that exist throughout the world is large, the registry contains information about only a subset of them.</span></span> <span data-ttu-id="08b29-106">さらに、レジストリ自体は、内容が意図的に、および誤って変更される可能性がある動的な構造です。</span><span class="sxs-lookup"><span data-stu-id="08b29-106">In addition, the registry itself is a dynamic structure whose contents are subject to both deliberate and accidental change.</span></span> <span data-ttu-id="08b29-107">その結果、アプリケーションは、特定のタイム ゾーンがシステムで定義され、使用できると常に想定することができません。</span><span class="sxs-lookup"><span data-stu-id="08b29-107">As a result, an application cannot always assume that a particular time zone is defined and available on a system.</span></span> <span data-ttu-id="08b29-108">タイム ゾーン情報のアプリケーションを使用する多くのアプリケーションの最初の手順は、必要なタイム ゾーンがローカル システムで使用できるかどうかを判断する、またはタイム ゾーンの一覧をユーザーに提供して選択させることです。</span><span class="sxs-lookup"><span data-stu-id="08b29-108">The first step for many applications that use time zone information applications is to determine whether required time zones are available on the local system, or to give the user a list of time zones from which to select.</span></span> <span data-ttu-id="08b29-109">これには、アプリケーションがローカル システムで定義されているタイム ゾーンを列挙する必要があります。</span><span class="sxs-lookup"><span data-stu-id="08b29-109">This requires that an application enumerate the time zones defined on a local system.</span></span>

> [!NOTE]
> <span data-ttu-id="08b29-110">アプリケーションがローカル システムで定義されていない可能性があります、特定のタイム ゾーンの存在に依存している場合、アプリケーションは、およびタイム ゾーンの情報を逆シリアル化によってその存在を保証できます。</span><span class="sxs-lookup"><span data-stu-id="08b29-110">If an application relies on the presence of a particular time zone that may not be defined on a local system, the application can ensure its presence by serializing and deserializing information about the time zone.</span></span> <span data-ttu-id="08b29-111">アプリケーション ユーザーが選択できるように、リスト コントロールにタイム ゾーンを追加し、できます。</span><span class="sxs-lookup"><span data-stu-id="08b29-111">The time zone can then be added to a list control so that the application user can select it.</span></span> <span data-ttu-id="08b29-112">詳細については、「[する方法: 埋め込みリソースにタイム ゾーンを保存](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)と[する方法: 埋め込みリソースからタイム ゾーンを復元](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)です。</span><span class="sxs-lookup"><span data-stu-id="08b29-112">For details, see [How to: Save Time Zones to an Embedded Resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) and [How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).</span></span>

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a><span data-ttu-id="08b29-113">ローカル システムに存在するタイム ゾーンを列挙するには</span><span class="sxs-lookup"><span data-stu-id="08b29-113">To enumerate the time zones present on the local system</span></span>

1. <span data-ttu-id="08b29-114"><xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="08b29-114">Call the <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="08b29-115">メソッドがジェネリック型を返します<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>のコレクション<xref:System.TimeZoneInfo>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="08b29-115">The method returns a generic <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> collection of <xref:System.TimeZoneInfo> objects.</span></span> <span data-ttu-id="08b29-116">コレクション内のエントリがにより並べ替えられた、<xref:System.TimeZoneInfo.DisplayName%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="08b29-116">The entries in the collection are sorted by their <xref:System.TimeZoneInfo.DisplayName%2A> property.</span></span> <span data-ttu-id="08b29-117">例えば:</span><span class="sxs-lookup"><span data-stu-id="08b29-117">For example:</span></span>

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. <span data-ttu-id="08b29-118">個々 の列挙<xref:System.TimeZoneInfo>を使用してコレクション内のオブジェクト、`foreach`ループ (c#) または`For Each`しています.`Next`</span><span class="sxs-lookup"><span data-stu-id="08b29-118">Enumerate the individual <xref:System.TimeZoneInfo> objects in the collection by using a `foreach` loop (in C#) or a `For Each`…`Next`</span></span> <span data-ttu-id="08b29-119">(Visual Basic の場合) のループし、各オブジェクトに対して、必要な処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="08b29-119">loop (in Visual Basic), and perform any necessary processing on each object.</span></span> <span data-ttu-id="08b29-120">たとえば、次のコードを列挙、<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>のコレクション<xref:System.TimeZoneInfo>で返される手順 1 のオブジェクトし、コンソールには、各タイム ゾーンの表示名を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="08b29-120">For example, the following code enumerates the <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> collection of <xref:System.TimeZoneInfo> objects returned in step 1 and lists the display name of each time zone on the console.</span></span>

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a><span data-ttu-id="08b29-121">ローカル システムに存在するタイム ゾーンの一覧をユーザーに表示するには</span><span class="sxs-lookup"><span data-stu-id="08b29-121">To present the user with a list of time zones present on the local system</span></span>

1. <span data-ttu-id="08b29-122"><xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="08b29-122">Call the <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="08b29-123">メソッドがジェネリック型を返します<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>のコレクション<xref:System.TimeZoneInfo>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="08b29-123">The method returns a generic <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> collection of <xref:System.TimeZoneInfo> objects.</span></span>

2. <span data-ttu-id="08b29-124">手順 1. で返されるコレクションに割り当てる、`DataSource`プロパティの Windows フォームや ASP.NET リスト コントロール。</span><span class="sxs-lookup"><span data-stu-id="08b29-124">Assign the collection returned in step 1 to the `DataSource` property of a Windows forms or ASP.NET list control.</span></span>

3. <span data-ttu-id="08b29-125">取得、<xref:System.TimeZoneInfo>ユーザーが選択したオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="08b29-125">Retrieve the <xref:System.TimeZoneInfo> object that the user has selected.</span></span>

<span data-ttu-id="08b29-126">この例では、Windows アプリケーションの具体的なを提供します。</span><span class="sxs-lookup"><span data-stu-id="08b29-126">The example provides an illustration for a Windows application.</span></span>

## <a name="example"></a><span data-ttu-id="08b29-127">例</span><span class="sxs-lookup"><span data-stu-id="08b29-127">Example</span></span>

<span data-ttu-id="08b29-128">例では、リスト ボックスで、システムで定義されているタイム ゾーンを表示する Windows アプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="08b29-128">The example starts a Windows application that displays the time zones defined on a system in a list box.</span></span> <span data-ttu-id="08b29-129">例では、値を含むダイアログ ボックスを表示、<xref:System.TimeZoneInfo.DisplayName%2A>ユーザーが選択したタイム ゾーン オブジェクトのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="08b29-129">The example then displays a dialog box that contains the value of the <xref:System.TimeZoneInfo.DisplayName%2A> property of the time zone object selected by the user.</span></span>

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

<span data-ttu-id="08b29-130">最もリスト コントロール (など、<xref:System.Windows.Forms.ListBox?displayProperty=nameWithType>または<xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType>コントロール) にするオブジェクト変数のコレクションを割り当てるには、その`DataSource`プロパティを実装するコレクションとならない限り、<xref:System.Collections.IEnumerable>インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="08b29-130">Most list controls (such as the <xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> or <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> control) allow you to assign a collection of object variables to their `DataSource` property as long as that collection implements the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="08b29-131">(ジェネリック<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>クラスがこれです)。コレクションでは個々 のオブジェクトを表示するには、このコントロールはそのオブジェクトを呼び出します。`ToString`オブジェクトを表すために使用する文字列を抽出するメソッド。</span><span class="sxs-lookup"><span data-stu-id="08b29-131">(The generic <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> class does this.) To display an individual object in the collection, the control calls that object's `ToString` method to extract the string that is used to represent the object.</span></span> <span data-ttu-id="08b29-132">場合、 <xref:System.TimeZoneInfo> 、オブジェクト、`ToString`メソッドを返します、<xref:System.TimeZoneInfo>オブジェクトの表示名 (の値、<xref:System.TimeZoneInfo.DisplayName%2A>プロパティ)。</span><span class="sxs-lookup"><span data-stu-id="08b29-132">In the case of <xref:System.TimeZoneInfo> objects, the `ToString` method returns the <xref:System.TimeZoneInfo> object's display name (the value of its <xref:System.TimeZoneInfo.DisplayName%2A> property).</span></span>

> [!NOTE]
> <span data-ttu-id="08b29-133">リスト コントロールを呼び出すオブジェクトのため`ToString`メソッドのコレクションを割り当てることができます<xref:System.TimeZoneInfo>コントロールにオブジェクトがある各オブジェクトについて、わかりやすい名前を表示し、取得、コントロール、<xref:System.TimeZoneInfo>ユーザーが選択したオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="08b29-133">Because list controls call an object's `ToString` method, you can assign a collection of <xref:System.TimeZoneInfo> objects to the control, have the control display a meaningful name for each object, and retrieve the <xref:System.TimeZoneInfo> object that the user has selected.</span></span> <span data-ttu-id="08b29-134">コレクション内の各オブジェクトの文字列を抽出、コントロールのさらに割り当てられているコレクションに文字列を割り当てる必要がある`DataSource`プロパティは、ユーザーが選択すると、文字列を取得し、この文字列を使用して、オブジェクトを抽出について説明します。</span><span class="sxs-lookup"><span data-stu-id="08b29-134">This eliminates the need to extract a string for each object in the collection, assign the string to a collection that is in turn assigned to the control's `DataSource` property, retrieve the string the user has selected, and then use this string to extract the object that it describes.</span></span> 

## <a name="compiling-the-code"></a><span data-ttu-id="08b29-135">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="08b29-135">Compiling the code</span></span>

<span data-ttu-id="08b29-136">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="08b29-136">This example requires:</span></span>

* <span data-ttu-id="08b29-137">される System.Core.dll への参照をプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="08b29-137">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="08b29-138">次の名前空間は、インポートします。</span><span class="sxs-lookup"><span data-stu-id="08b29-138">That the following namespaces be imported:</span></span>

  <span data-ttu-id="08b29-139"><xref:System> (c# コード)</span><span class="sxs-lookup"><span data-stu-id="08b29-139"><xref:System> (in C# code)</span></span>

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a><span data-ttu-id="08b29-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="08b29-140">See also</span></span>

<span data-ttu-id="08b29-141">[日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
[する方法: 埋め込みリソースにタイム ゾーンを保存](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
[する方法: 埋め込みリソースからタイム ゾーンを復元](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)</span><span class="sxs-lookup"><span data-stu-id="08b29-141">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
[How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)</span></span>
