---
title: ".NET でのシリアル化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1a0d9f5fd32b5610e3d7b05455c7bd3c55b5b77e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="serialization-in-net"></a><span data-ttu-id="c06fb-102">.NET でのシリアル化</span><span class="sxs-lookup"><span data-stu-id="c06fb-102">Serialization in .NET</span></span>
<span data-ttu-id="c06fb-103">シリアル化とは、オブジェクトの状態を永続化または転送できる形式に変換するプロセスのことです。</span><span class="sxs-lookup"><span data-stu-id="c06fb-103">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="c06fb-104">シリアル化を補完するプロセスとして、ストリームをオブジェクトに変換する逆シリアル化があります。</span><span class="sxs-lookup"><span data-stu-id="c06fb-104">The complement of serialization is deserialization, which converts a stream into an object.</span></span> <span data-ttu-id="c06fb-105">これらのプロセスを組み合わせて使用することで、データを簡単に格納および転送できます。</span><span class="sxs-lookup"><span data-stu-id="c06fb-105">Together, these processes allow data to be easily stored and transferred.</span></span>  
  
<span data-ttu-id="c06fb-106">.NET 機能では、次の 2 つのシリアル化テクノロジを採用しています。</span><span class="sxs-lookup"><span data-stu-id="c06fb-106">.NET features two serialization technologies:</span></span>  
  
-   <span data-ttu-id="c06fb-107">バイナリ シリアル化は、型そのものを正確に維持するため、アプリケーションを次回起動するまでの間、オブジェクトの状態を維持するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c06fb-107">Binary serialization preserves type fidelity, which is useful for preserving the state of an object between different invocations of an application.</span></span> <span data-ttu-id="c06fb-108">たとえば、クリップボードを出力先としてオブジェクトをシリアル化することによって、そのオブジェクトを異なるアプリケーション間で共有できます。</span><span class="sxs-lookup"><span data-stu-id="c06fb-108">For example, you can share an object between different applications by serializing it to the Clipboard.</span></span> <span data-ttu-id="c06fb-109">オブジェクトをシリアル化して、ストリーム、ディスク、メモリ、ネットワーク上などに出力できます。</span><span class="sxs-lookup"><span data-stu-id="c06fb-109">You can serialize an object to a stream, to a disk, to memory, over the network, and so forth.</span></span> <span data-ttu-id="c06fb-110">リモート処理では、シリアル化を使用して、コンピューター間やアプリケーション ドメイン間でオブジェクトを "値渡し" します。</span><span class="sxs-lookup"><span data-stu-id="c06fb-110">Remoting uses serialization to pass objects "by value" from one computer or application domain to another.</span></span>  
  
-   <span data-ttu-id="c06fb-111">XML シリアル化では、パブリック プロパティとパブリック フィールドのみがシリアル化され、型そのものは維持されません。</span><span class="sxs-lookup"><span data-stu-id="c06fb-111">XML serialization serializes only public properties and fields and does not preserve type fidelity.</span></span> <span data-ttu-id="c06fb-112">これは、データを使用するアプリケーションに制限を加えずに、データを提供または処理する場合に有効です。</span><span class="sxs-lookup"><span data-stu-id="c06fb-112">This is useful when you want to provide or consume data without restricting the application that uses the data.</span></span> <span data-ttu-id="c06fb-113">XML はオープン標準であるため、Web 経由でデータを共有する場合には有用な選択肢となります。</span><span class="sxs-lookup"><span data-stu-id="c06fb-113">Because XML is an open standard, it is an attractive choice for sharing data across the Web.</span></span> <span data-ttu-id="c06fb-114">SOAP も同様のオープン標準であるため、有用な選択肢です。</span><span class="sxs-lookup"><span data-stu-id="c06fb-114">SOAP is likewise an open standard, which makes it an attractive choice.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c06fb-115">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c06fb-115">In This Section</span></span>  
[<span data-ttu-id="c06fb-116">シリアル化に関する「方法」トピック</span><span class="sxs-lookup"><span data-stu-id="c06fb-116">Serialization How-to Topics</span></span>](../../../docs/standard/serialization/serialization-how-to-topics.md)  
<span data-ttu-id="c06fb-117">このセクションに含まれている、方法を説明するトピックへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="c06fb-117">Lists links to How-to topics contained in this section.</span></span>
  
[<span data-ttu-id="c06fb-118">バイナリ シリアル化</span><span class="sxs-lookup"><span data-stu-id="c06fb-118">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)  
<span data-ttu-id="c06fb-119">共通言語ランタイムに付属しているバイナル シリアル化機構について説明します。</span><span class="sxs-lookup"><span data-stu-id="c06fb-119">Describes the binary serialization mechanism that is included with the common language runtime.</span></span>

[<span data-ttu-id="c06fb-120">XML シリアル化および SOAP シリアル化</span><span class="sxs-lookup"><span data-stu-id="c06fb-120">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
<span data-ttu-id="c06fb-121">共通言語ランタイムに付属している XML シリアル化および SOAP シリアル化機構について説明します。</span><span class="sxs-lookup"><span data-stu-id="c06fb-121">Describes the XML and SOAP serialization mechanism that is included with the common language runtime.</span></span>

[<span data-ttu-id="c06fb-122">シリアル化ツール</span><span class="sxs-lookup"><span data-stu-id="c06fb-122">Serialization Tools</span></span>](../../../docs/standard/serialization/serialization-tools.md)  
<span data-ttu-id="c06fb-123">これらのツールは、シリアル化コードの開発に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c06fb-123">These tools help develop serialization code.</span></span>

[<span data-ttu-id="c06fb-124">シリアル化のサンプル</span><span class="sxs-lookup"><span data-stu-id="c06fb-124">Serialization Samples</span></span>](../../../docs/standard/serialization/serialization-samples.md)  
<span data-ttu-id="c06fb-125">サンプルでは、シリアル化の方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c06fb-125">The samples demonstrate how to do serialization.</span></span>

## <a name="reference"></a><span data-ttu-id="c06fb-126">参照</span><span class="sxs-lookup"><span data-stu-id="c06fb-126">Reference</span></span>
<span data-ttu-id="c06fb-127"><xref:System.Runtime.Serialization>オブジェクトのシリアル化と逆シリアル化に使用できるクラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c06fb-127"><xref:System.Runtime.Serialization> Contains classes that can be used for serializing and deserializing objects.</span></span>
  
<xref:System.Xml.Serialization>  
<span data-ttu-id="c06fb-128">オブジェクトを XML 形式のドキュメントまたはストリームにシリアル化するために使用できるクラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c06fb-128">Contains classes that can be used to serialize objects into XML format documents or streams.</span></span>