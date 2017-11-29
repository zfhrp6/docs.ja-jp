---
title: "バイナリ シリアル化"
ms.date: 08/11/2017
ms.prod: .net
ms.topic: article
helpviewer_keywords:
- binary serialization
- serialization, about serialization
- deserialization
- binary serialization, about serialization
- binary serialization, .net core serialization
- serialization, cross-framework
ms.assetid: 2b1ea3be-1152-4032-b2b3-07794054c405
caps.latest.revision: "5"
author: ViktorHofer
ms.author: mairaw
ms.openlocfilehash: 74ee4e21934c1e4f3fd008664b1315429dc47b37
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="binary-serialization"></a><span data-ttu-id="5cc6a-102">バイナリ シリアル化</span><span class="sxs-lookup"><span data-stu-id="5cc6a-102">Binary serialization</span></span>

<span data-ttu-id="5cc6a-103">シリアル化は、オブジェクトの状態をストレージ メディアに格納するプロセスとして定義することができます。</span><span class="sxs-lookup"><span data-stu-id="5cc6a-103">Serialization can be defined as the process of storing the state of an object to a storage medium.</span></span> <span data-ttu-id="5cc6a-104">このプロセスの実行中に、オブジェクトのパブリックおよびプライベートなフィールドとクラス (クラスを格納しているアセンブリを含む) の名前がバイト ストリームに変換され、データ ストリームに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="5cc6a-104">During this process, the public and private fields of the object and the name of the class, including the assembly containing the class, are converted to a stream of bytes, which is then written to a data stream.</span></span> <span data-ttu-id="5cc6a-105">続いてオブジェクトが逆シリアル化され、元のオブジェクトの完全な複製が作成されます。</span><span class="sxs-lookup"><span data-stu-id="5cc6a-105">When the object is subsequently deserialized, an exact clone of the original object is created.</span></span>

<span data-ttu-id="5cc6a-106">オブジェクト指向環境でシリアル化機構を実装する場合は、使いやすさと柔軟性の間での数多くのトレードオフについて考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5cc6a-106">When implementing a serialization mechanism in an object-oriented environment, you have to make a number of tradeoffs between ease of use and flexibility.</span></span> <span data-ttu-id="5cc6a-107">プロセスを十分に制御できる場合は、プロセスの大部分を自動化できます。</span><span class="sxs-lookup"><span data-stu-id="5cc6a-107">The process can be automated to a large extent, provided you are given sufficient control over the process.</span></span> <span data-ttu-id="5cc6a-108">たとえば、単純なバイナリ シリアル化では不十分な状況が発生する場合や、シリアル化が必要なクラス内のフィールドを決定するだけの明確な理由がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="5cc6a-108">For example, situations may arise where simple binary serialization is not sufficient, or there might be a specific reason to decide which fields in a class need to be serialized.</span></span> <span data-ttu-id="5cc6a-109">以下のセクションでは、.NET に用意されている堅牢なシリアル化機構について検討し、必要に応じてプロセスをカスタマイズするためのいくつかの重要な機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="5cc6a-109">The following sections examine the robust serialization mechanism provided with .NET and highlight a number of important features that allow you to customize the process to meet your needs.</span></span>

> [!NOTE]
> <span data-ttu-id="5cc6a-110">オブジェクトのシリアル化と逆シリアル化を行う際に使用した .NET Framework のバージョンが異なる場合、UTF-8 または UTF-7 でエンコードされたオブジェクトの状態は保持されません。</span><span class="sxs-lookup"><span data-stu-id="5cc6a-110">The state of a UTF-8 or UTF-7 encoded object is not preserved if the object is serialized and deserialized using different .NET Framework versions.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="5cc6a-111">バイナリ シリアル化の性質上、オブジェクト内でのプライベート メンバーの変更が可能であり、その状態が変化するため、パブリック API サーフェイスで動作する JSON.NET のような他のシリアル化フレームワークを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5cc6a-111">As the nature of binary serialization allows the modification of private members inside an object and therefore changing the state of it, other serialization frameworks like JSON.NET which operate on the public API surface are recommended.</span></span>

## <a name="binary-serialization-in-net-core"></a><span data-ttu-id="5cc6a-112">.NET Core でのバイナリ シリアル化</span><span class="sxs-lookup"><span data-stu-id="5cc6a-112">Binary serialization in .NET Core</span></span>

<span data-ttu-id="5cc6a-113">.NET Core では、型のサブセットでのバイナリ シリアル化がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="5cc6a-113">.NET Core supports binary serialization with a subset of types.</span></span> <span data-ttu-id="5cc6a-114">サポートされている型のリストは、「[シリアル化可能な型](#serializable-types)」で確認できます。</span><span class="sxs-lookup"><span data-stu-id="5cc6a-114">You can see the list of supported types in the [Serializable types section](#serializable-types).</span></span> <span data-ttu-id="5cc6a-115">定義済みの一連の型は、.NET Framework 4.5.1 以降のバージョンと .NET Core 2.0 以降のバージョン間でシリアル化できることが保証されていいます。</span><span class="sxs-lookup"><span data-stu-id="5cc6a-115">The defined set of types are guaranteed to be serializable between .NET Framework 4.5.1 and later versions and .NET Core 2.0 and later versions.</span></span> <span data-ttu-id="5cc6a-116">Mono などの他の .NET 実装は公式にサポートされておらず、また機能もしません。</span><span class="sxs-lookup"><span data-stu-id="5cc6a-116">Other .NET implementations, such as Mono, aren't officially supported but should also be working.</span></span>

### <a name="serializable-types"></a><span data-ttu-id="5cc6a-117">シリアル化可能な型</span><span class="sxs-lookup"><span data-stu-id="5cc6a-117">Serializable types</span></span>

- <xref:System.AggregateException?displayProperty=nameWithType>   
- <xref:System.Array?displayProperty=nameWithType>   
- <xref:System.ArraySegment%601?displayProperty=nameWithType>   
- <xref:System.Attribute?displayProperty=nameWithType>   
- <xref:System.Boolean?displayProperty=nameWithType>   
- <xref:System.Byte?displayProperty=nameWithType>   
- <xref:System.Char?displayProperty=nameWithType>   
- <xref:System.Collections.ArrayList?displayProperty=nameWithType>   
- <xref:System.Collections.BitArray?displayProperty=nameWithType>   
- <xref:System.Collections.Comparer?displayProperty=nameWithType>   
- <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.KeyValuePair%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.LinkedList%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedSet%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType>   
- <xref:System.Collections.Hashtable?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.Queue?displayProperty=nameWithType>   
- <xref:System.Collections.SortedList?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.HybridDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.ListDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.StringCollection?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.StringDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Stack?displayProperty=nameWithType>   
- <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType>   
- <span data-ttu-id="5cc6a-118"><xref:System.DBNull?displayProperty=nameWithType>(.NET Core 2.0.2 とそれ以降のバージョンで使用可能)</span><span class="sxs-lookup"><span data-stu-id="5cc6a-118"><xref:System.DBNull?displayProperty=nameWithType> (available in .NET Core 2.0.2 and later versions)</span></span>   
- <xref:System.Data.DataSet?displayProperty=nameWithType>   
- <xref:System.Data.DataTable?displayProperty=nameWithType>   
- <xref:System.Data.PropertyCollection?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType>   
- <xref:System.DateTime?displayProperty=nameWithType>   
- <xref:System.DateTimeOffset?displayProperty=nameWithType>   
- <xref:System.Decimal?displayProperty=nameWithType>   
- <xref:System.Double?displayProperty=nameWithType>   
- <xref:System.Drawing.Color?displayProperty=nameWithType>   
- <xref:System.Drawing.Point?displayProperty=nameWithType>   
- <xref:System.Drawing.PointF?displayProperty=nameWithType>   
- <xref:System.Drawing.Rectangle?displayProperty=nameWithType>   
- <xref:System.Drawing.RectangleF?displayProperty=nameWithType>   
- <xref:System.Drawing.Size?displayProperty=nameWithType>   
- <xref:System.Drawing.SizeF?displayProperty=nameWithType>   
- <xref:System.Enum?displayProperty=nameWithType>   
- <xref:System.Exception?displayProperty=nameWithType>   
- <xref:System.Globalization.CompareInfo?displayProperty=nameWithType>   
- <xref:System.Globalization.SortVersion?displayProperty=nameWithType>   
- <xref:System.Guid?displayProperty=nameWithType>   
- <xref:System.Int16?displayProperty=nameWithType>   
- <xref:System.Int32?displayProperty=nameWithType>   
- <xref:System.Int64?displayProperty=nameWithType>   
- <xref:System.IntPtr?displayProperty=nameWithType>   
- <xref:System.Net.Cookie?displayProperty=nameWithType>   
- <xref:System.Net.CookieCollection?displayProperty=nameWithType>   
- <xref:System.Net.CookieContainer?displayProperty=nameWithType>   
- <xref:System.Nullable%601?displayProperty=nameWithType>   
- <xref:System.Numerics.BigInteger?displayProperty=nameWithType>   
- <xref:System.Numerics.Complex?displayProperty=nameWithType>   
- <xref:System.Object?displayProperty=nameWithType>   
- <xref:System.SByte?displayProperty=nameWithType>   
- <xref:System.Single?displayProperty=nameWithType>   
- <xref:System.String?displayProperty=nameWithType>   
- <xref:System.StringComparer?displayProperty=nameWithType>   
- <xref:System.Text.StringBuilder?displayProperty=nameWithType>   
- <xref:System.TimeSpan?displayProperty=nameWithType>   
- <xref:System.TimeZoneInfo?displayProperty=nameWithType>   
- <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType>   
- <xref:System.Tuple?displayProperty=nameWithType>   
- <xref:System.UInt16?displayProperty=nameWithType>   
- <xref:System.UInt32?displayProperty=nameWithType>   
- <xref:System.UInt64?displayProperty=nameWithType>   
- <xref:System.UIntPtr?displayProperty=nameWithType>   
- <xref:System.Uri?displayProperty=nameWithType>   
- <span data-ttu-id="5cc6a-119"><xref:System.ValueTuple?displayProperty=nameWithType>(いない .NET Framework 4.7 と以前のバージョンでシリアル化可能)</span><span class="sxs-lookup"><span data-stu-id="5cc6a-119"><xref:System.ValueTuple?displayProperty=nameWithType> (not serializable in .NET Framework 4.7 and earlier versions)</span></span>  
- <xref:System.ValueType?displayProperty=nameWithType>   
- <xref:System.Version?displayProperty=nameWithType>   
- <xref:System.WeakReference?displayProperty=nameWithType>   
- <xref:System.WeakReference%601?displayProperty=nameWithType>   

## <a name="in-this-section"></a><span data-ttu-id="5cc6a-120">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="5cc6a-120">In this section</span></span>

 [<span data-ttu-id="5cc6a-121">シリアル化の概念</span><span class="sxs-lookup"><span data-stu-id="5cc6a-121">Serialization Concepts</span></span>](../../../docs/standard/serialization/serialization-concepts.md)  
 <span data-ttu-id="5cc6a-122">データをストレージに永続化するシナリオと、アプリケーション ドメインを越えてオブジェクトを受け渡しするシナリオの 2 つを例として、シリアル化の有効な利用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5cc6a-122">Discusses two scenarios where serialization is useful: when persisting data to storage and when passing objects across application domains.</span></span>  
  
 [<span data-ttu-id="5cc6a-123">基本的なシリアル化</span><span class="sxs-lookup"><span data-stu-id="5cc6a-123">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)  
 <span data-ttu-id="5cc6a-124">バイナリ フォーマッタと SOAP フォーマッタを使用してオブジェクトをシリアル化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5cc6a-124">Describes how to use the binary and SOAP formatters to serialize objects.</span></span>  
  
 [<span data-ttu-id="5cc6a-125">選択的シリアル化</span><span class="sxs-lookup"><span data-stu-id="5cc6a-125">Selective Serialization</span></span>](../../../docs/standard/serialization/selective-serialization.md)  
 <span data-ttu-id="5cc6a-126">クラスの一部のメンバーがシリアル化されないようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5cc6a-126">Describes how to prevent some members of a class from being serialized.</span></span>  
  
 [<span data-ttu-id="5cc6a-127">カスタムのシリアル化</span><span class="sxs-lookup"><span data-stu-id="5cc6a-127">Custom Serialization</span></span>](../../../docs/standard/serialization/custom-serialization.md)  
 <span data-ttu-id="5cc6a-128"><xref:System.Runtime.Serialization.ISerializable> インターフェイスを使用してクラスのシリアル化をカスタマイズする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5cc6a-128">Describes how to customize serialization for a class by using the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>  
  
 [<span data-ttu-id="5cc6a-129">シリアル化プロセスの手順</span><span class="sxs-lookup"><span data-stu-id="5cc6a-129">Steps in the Serialization Process</span></span>](../../../docs/standard/serialization/steps-in-the-serialization-process.md)  
 <span data-ttu-id="5cc6a-130">フォーマッタで <xref:System.Runtime.Serialization.Formatter.Serialize%2A> メソッドを呼び出した場合のシリアル化方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5cc6a-130">Describes the course of action serialization takes when the <xref:System.Runtime.Serialization.Formatter.Serialize%2A> method is called on a formatter.</span></span>  
  
 [<span data-ttu-id="5cc6a-131">バージョン トレラントなシリアル化</span><span class="sxs-lookup"><span data-stu-id="5cc6a-131">Version Tolerant Serialization</span></span>](../../../docs/standard/serialization/version-tolerant-serialization.md)  
 <span data-ttu-id="5cc6a-132">アプリケーションに例外をスローさせることなく後から変更できる、シリアル化可能な型の作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5cc6a-132">Explains how to create serializable types that can be modified over time without causing applications to throw exceptions.</span></span>  
  
 [<span data-ttu-id="5cc6a-133">シリアル化のガイドライン</span><span class="sxs-lookup"><span data-stu-id="5cc6a-133">Serialization Guidelines</span></span>](../../../docs/standard/serialization/serialization-guidelines.md)  
 <span data-ttu-id="5cc6a-134">オブジェクトをシリアル化するタイミングを決定するのに役立つ、いくつかの一般的なガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="5cc6a-134">Provides some general guidelines for deciding when to serialize an object.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5cc6a-135">参照</span><span class="sxs-lookup"><span data-stu-id="5cc6a-135">Reference</span></span>  
 <xref:System.Runtime.Serialization>  
 <span data-ttu-id="5cc6a-136">オブジェクトのシリアル化と逆シリアル化に使用できるクラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5cc6a-136">Contains classes that can be used for serializing and deserializing objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5cc6a-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="5cc6a-137">Related sections</span></span>  
 [<span data-ttu-id="5cc6a-138">XML シリアル化および SOAP シリアル化</span><span class="sxs-lookup"><span data-stu-id="5cc6a-138">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 <span data-ttu-id="5cc6a-139">共通言語ランタイムに付属している XML シリアル化機構について説明します。</span><span class="sxs-lookup"><span data-stu-id="5cc6a-139">Describes the XML serialization mechanism that is included with the common language runtime.</span></span>  
  
 [<span data-ttu-id="5cc6a-140">セキュリティとシリアル化</span><span class="sxs-lookup"><span data-stu-id="5cc6a-140">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)  
 <span data-ttu-id="5cc6a-141">シリアル化を実行するコードを記述する際に従う必要がある、安全なコーディングのガイドラインについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5cc6a-141">Describes the secure coding guidelines to follow when writing code that performs serialization.</span></span>  
  
 [<span data-ttu-id="5cc6a-142">リモート オブジェクト</span><span class="sxs-lookup"><span data-stu-id="5cc6a-142">Remote Objects</span></span>](http://msdn.microsoft.com/en-us/515686e6-0a8d-42f7-8188-73abede57c58)  
 <span data-ttu-id="5cc6a-143">.NET Framework でリモート通信に利用できるさまざまな通信方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5cc6a-143">Describes the various communications methods available in the .NET Framework for remote communications.</span></span>  
  
 [<span data-ttu-id="5cc6a-144">ASP.NET と XML Web サービス クライアントを使用して作成した XML Web サービス</span><span class="sxs-lookup"><span data-stu-id="5cc6a-144">XML Web Services Created Using ASP.NET and XML Web Service Clients</span></span>](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c)  
 <span data-ttu-id="5cc6a-145">ASP.NET を使用して作成した XML Web サービスのプログラミング方法について説明するトピックを示します。</span><span class="sxs-lookup"><span data-stu-id="5cc6a-145">Provides topics that describe and explain how to program XML Web services created using ASP.NET.</span></span>
