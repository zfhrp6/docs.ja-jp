---
title: "方法: 埋め込みリソースにタイム ゾーンを保存"
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
- time zones [.NET Framework], saving
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 3c96d83a-a057-4496-abb0-8f4b12712558
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 96dd3f0a3ed27a9e09c62f3ad4f450ced5a8e644
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a><span data-ttu-id="76807-102">方法: 埋め込みリソースにタイム ゾーンを保存</span><span class="sxs-lookup"><span data-stu-id="76807-102">How to: Save time zones to an embedded resource</span></span>

<span data-ttu-id="76807-103">多くの場合、タイム ゾーンに対応するアプリケーションでは、特定のタイム ゾーンが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="76807-103">A time zone-aware application often requires the presence of a particular time zone.</span></span> <span data-ttu-id="76807-104">ただし、ため個々 の可用性<xref:System.TimeZoneInfo>オブジェクトは、ローカル システムのレジストリに格納されている情報によって異なります、慣例的でも使用できるタイム ゾーンが存在しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="76807-104">However, because the availability of individual <xref:System.TimeZoneInfo> objects depends on information stored in the local system's registry, even customarily available time zones may be absent.</span></span> <span data-ttu-id="76807-105">使用してさらに、カスタム タイム ゾーンに関する情報がインスタンス化、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>メソッドが他のタイム ゾーン情報がレジストリに保存されていません。</span><span class="sxs-lookup"><span data-stu-id="76807-105">In addition, information about custom time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method is not stored with other time zone information in the registry.</span></span> <span data-ttu-id="76807-106">必要なときにこれらのタイム ゾーンが使用可能なであることを確認するをシリアル化するして保存し、それらを逆シリアル化して後で復元することができます。</span><span class="sxs-lookup"><span data-stu-id="76807-106">To ensure that these time zones are available when they are needed, you can save them by serializing them, and later restore them by deserializing them.</span></span>

<span data-ttu-id="76807-107">通常、シリアル化する、<xref:System.TimeZoneInfo>オブジェクトが、タイム ゾーンに対応するアプリケーションとは別に発生します。</span><span class="sxs-lookup"><span data-stu-id="76807-107">Typically, serializing a <xref:System.TimeZoneInfo> object occurs apart from the time zone-aware application.</span></span> <span data-ttu-id="76807-108">シリアル化された保持するために使用されるデータ ストアによって<xref:System.TimeZoneInfo>オブジェクト、(たとえば、レジストリのアプリケーション キーでデータが格納されている場合)、セットアップまたはインストール ルーチンの一部として、またはを実行するユーティリティ ルーチンの一部としては、タイム ゾーンのデータをシリアル化される可能性があります前に、(たとえば、シリアル化されたデータは .NET の XML リソース (.resx) ファイルに格納されている) 場合、最終的なアプリケーションがコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="76807-108">Depending on the data store used to hold serialized <xref:System.TimeZoneInfo> objects, time zone data may be serialized as part of a setup or installation routine (for example, when the data is stored in an application key of the registry), or as part of a utility routine that runs before the final application is compiled (for example, when the serialized data is stored in a .NET XML resource (.resx) file).</span></span>

<span data-ttu-id="76807-109">ファイルに加え、リソース、アプリケーションでコンパイルされる、タイム ゾーン情報に関するその他のいくつかのデータ ストアを使用できます。</span><span class="sxs-lookup"><span data-stu-id="76807-109">In addition to a resource file that is compiled with the application, several other data stores can be used for time zone information.</span></span> <span data-ttu-id="76807-110">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="76807-110">These include the following:</span></span>

* <span data-ttu-id="76807-111">レジストリです。</span><span class="sxs-lookup"><span data-stu-id="76807-111">The registry.</span></span> <span data-ttu-id="76807-112">Hkey_local_machine NT\CurrentVersion\Time ゾーンのサブキーを使用するのではなく、カスタム タイム ゾーン データを格納するアプリケーションが独自のアプリケーション キーのサブキーを使用する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="76807-112">Note that an application should use the subkeys of its own application key to store custom time zone data rather than using the subkeys of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones.</span></span>

* <span data-ttu-id="76807-113">構成ファイル。</span><span class="sxs-lookup"><span data-stu-id="76807-113">Configuration files.</span></span>

* <span data-ttu-id="76807-114">その他のシステム ファイルです。</span><span class="sxs-lookup"><span data-stu-id="76807-114">Other system files.</span></span>

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a><span data-ttu-id="76807-115">.Resx ファイルにシリアル化することによって、タイム ゾーンを保存するには</span><span class="sxs-lookup"><span data-stu-id="76807-115">To save a time zone by serializing it to a .resx file</span></span>

1. <span data-ttu-id="76807-116">既存のタイム ゾーンを取得するか、新しいタイム ゾーンを作成します。</span><span class="sxs-lookup"><span data-stu-id="76807-116">Retrieve an existing time zone or create a new time zone.</span></span>

   <span data-ttu-id="76807-117">既存のタイム ゾーンを取得するには、次を参照してください。[する方法: 定義済みの UTC とローカル タイム ゾーン オブジェクトをアクセス](../../../docs/standard/datetime/access-utc-and-local.md)と[する方法: TimeZoneInfo オブジェクトをインスタンス化](../../../docs/standard/datetime/instantiate-time-zone-info.md)です。</span><span class="sxs-lookup"><span data-stu-id="76807-117">To retrieve an existing time zone, see [How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md) and [How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span></span>

   <span data-ttu-id="76807-118">新しいタイム ゾーンを作成するには、オーバー ロードのいずれかを呼び出して、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="76807-118">To create a new time zone, call one of the overloads of the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method.</span></span> <span data-ttu-id="76807-119">詳細については、次を参照してください。[する方法: 調整規則のないタイム ゾーンを作成](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)と[する方法: 調整規則のあるタイム ゾーンを作成する](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)です。</span><span class="sxs-lookup"><span data-stu-id="76807-119">For more information, see [How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) and [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span></span>

2. <span data-ttu-id="76807-120">呼び出す、<xref:System.TimeZoneInfo.ToSerializedString%2A>タイム ゾーンのデータを含む文字列を作成するメソッド。</span><span class="sxs-lookup"><span data-stu-id="76807-120">Call the <xref:System.TimeZoneInfo.ToSerializedString%2A> method to create a string that contains the time zone's data.</span></span>

3. <span data-ttu-id="76807-121">インスタンスを作成、<xref:System.IO.StreamWriter>オブジェクトの名前と必要に応じて、.resx ファイルへのパスを提供することによって、<xref:System.IO.StreamWriter>クラスのコンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="76807-121">Instantiate a <xref:System.IO.StreamWriter> object by providing the name and optionally the path of the .resx file to the <xref:System.IO.StreamWriter> class constructor.</span></span>

4. <span data-ttu-id="76807-122">インスタンスを作成、<xref:System.Resources.ResXResourceWriter>オブジェクトを渡すことによって、<xref:System.IO.StreamWriter>オブジェクトを<xref:System.Resources.ResXResourceWriter>クラスのコンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="76807-122">Instantiate a <xref:System.Resources.ResXResourceWriter> object by passing the <xref:System.IO.StreamWriter> object to the <xref:System.Resources.ResXResourceWriter> class constructor.</span></span>

5. <span data-ttu-id="76807-123">タイム ゾーンをパスする文字列をシリアル化、<xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="76807-123">Pass the time zone's serialized string to the <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> method.</span></span>

6. <span data-ttu-id="76807-124"><xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="76807-124">Call the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method.</span></span>

7. <span data-ttu-id="76807-125"><xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="76807-125">Call the <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> method.</span></span>

8. <span data-ttu-id="76807-126">閉じる、<xref:System.IO.StreamWriter>オブジェクトを呼び出してその<xref:System.IO.StreamWriter.Close%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="76807-126">Close the <xref:System.IO.StreamWriter> object by calling its <xref:System.IO.StreamWriter.Close%2A> method.</span></span>

9. <span data-ttu-id="76807-127">生成された .resx ファイルをアプリケーションの Visual Studio プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="76807-127">Add the generated .resx file to the application's Visual Studio project.</span></span>

10. <span data-ttu-id="76807-128">使用して、**プロパティ**Visual Studio で、ウィンドウことを確認して、.resx ファイルの**ビルド アクション**プロパティに設定されている**埋め込まれたリソース**です。</span><span class="sxs-lookup"><span data-stu-id="76807-128">Using the **Properties** window in Visual Studio, make sure that the .resx file's **Build Action** property is set to **Embedded Resource**.</span></span>

## <a name="example"></a><span data-ttu-id="76807-129">例</span><span class="sxs-lookup"><span data-stu-id="76807-129">Example</span></span>

<span data-ttu-id="76807-130">次の例のシリアル化、<xref:System.TimeZoneInfo>中部標準時を表すオブジェクト、および<xref:System.TimeZoneInfo>SerializedTimeZones.resx という名前の .NET XML リソース ファイルに Palmer ステーション、南極時間を表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="76807-130">The following example serializes a <xref:System.TimeZoneInfo> object that represents Central Standard Time and a <xref:System.TimeZoneInfo> object that represents the Palmer Station, Antarctica time to a .NET XML resource file that is named SerializedTimeZones.resx.</span></span> <span data-ttu-id="76807-131">中部標準時は通常、レジストリで定義されています。Palmer ステーション南極は、カスタム タイム ゾーンです。</span><span class="sxs-lookup"><span data-stu-id="76807-131">Central Standard Time is typically defined in the registry; Palmer Station, Antarctica is a custom time zone.</span></span>

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

<span data-ttu-id="76807-132">この例のシリアル化<xref:System.TimeZoneInfo>オブジェクトを使用できるように、リソース ファイルにコンパイル時にします。</span><span class="sxs-lookup"><span data-stu-id="76807-132">This example serializes <xref:System.TimeZoneInfo> objects so that they are available in a resource file at compile time.</span></span>

<span data-ttu-id="76807-133"><xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType>メソッドは、.NET の XML リソース ファイルに完全なヘッダー情報を追加し、リソースを追加する既存のファイルを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="76807-133">Because the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method adds complete header information to a .NET XML resource file, it cannot be used to add resources to an existing file.</span></span> <span data-ttu-id="76807-134">例では、これを処理 SerializedTimeZones.resx ファイルを確認して、存在する場合以外のすべてのリソースを格納する、2 つシリアル化されたジェネリック型にタイム ゾーン<xref:System.Collections.Generic.Dictionary%602>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="76807-134">The example handles this by checking for the SerializedTimeZones.resx file and, if it exists, storing all of its resources other than the two serialized time zones to a generic <xref:System.Collections.Generic.Dictionary%602> object.</span></span> <span data-ttu-id="76807-135">既存のファイルは削除し、され、既存のリソースが新しい SerializedTimeZones.resx ファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="76807-135">The existing file is then deleted and the existing resources are added to a new SerializedTimeZones.resx file.</span></span> <span data-ttu-id="76807-136">シリアル化されたタイム ゾーンのデータは、このファイルにも追加されます。</span><span class="sxs-lookup"><span data-stu-id="76807-136">The serialized time zone data is also added to this file.</span></span>

<span data-ttu-id="76807-137">キー (または**名前**) リソースのフィールドは空白文字を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="76807-137">The key (or **Name**) fields of resources should not contain embedded spaces.</span></span> <span data-ttu-id="76807-138"><xref:System.String.Replace%28System.String%2CSystem.String%29>リソース ファイルに割り当てられている前に、タイム ゾーン識別子ですべての埋め込みスペースを削除するメソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="76807-138">The <xref:System.String.Replace%28System.String%2CSystem.String%29> method is called to remove all embedded spaces in the time zone identifiers before they are assigned to the resource file.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="76807-139">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="76807-139">Compiling the code</span></span>

<span data-ttu-id="76807-140">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="76807-140">This example requires:</span></span>

* <span data-ttu-id="76807-141">System.Windows.Forms.dll および System.Core.dll への参照がプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="76807-141">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="76807-142">次の名前空間は、インポートします。</span><span class="sxs-lookup"><span data-stu-id="76807-142">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="76807-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="76807-143">See also</span></span>

<span data-ttu-id="76807-144">[日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
[タイム ゾーンの概要](../../../docs/standard/datetime/time-zone-overview.md)
[する方法: 埋め込みリソースからタイム ゾーンを復元](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)</span><span class="sxs-lookup"><span data-stu-id="76807-144">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md)
[How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)</span></span>
