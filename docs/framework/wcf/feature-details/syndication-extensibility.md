---
title: "配信の拡張"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d941175-74a2-4b15-81b3-086e8a95d25f
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5322ff2c79ab5051b3a9aaaeaafe7db6c9c2f683
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="syndication-extensibility"></a><span data-ttu-id="c3ae8-102">配信の拡張</span><span class="sxs-lookup"><span data-stu-id="c3ae8-102">Syndication Extensibility</span></span>
<span data-ttu-id="c3ae8-103">配信 API は、形式に依存せず、さまざま形式で概要コンテンツをネットワークに書き込むことができるプログラミング モデルを提供することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="c3ae8-103">The Syndication API is designed to provide a format-neutral programming model that allows syndicated content to be written to the wire in a variety of formats.</span></span> <span data-ttu-id="c3ae8-104">抽象データ モデルは、次のクラスで構成されています。</span><span class="sxs-lookup"><span data-stu-id="c3ae8-104">The abstract data model consists of the following classes:</span></span>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <span data-ttu-id="c3ae8-105">これらのクラスは、一部の名前が異なっていますが、Atom 1.0 仕様に規定されるコンストラクトに厳密にマップされています。</span><span class="sxs-lookup"><span data-stu-id="c3ae8-105">These classes map closely to the constructs defined in the Atom 1.0 specification, although some of the names are different.</span></span>  
  
 <span data-ttu-id="c3ae8-106">配信プロトコルの主な機能は拡張性です。</span><span class="sxs-lookup"><span data-stu-id="c3ae8-106">A key feature of syndication protocols is extensibility.</span></span> <span data-ttu-id="c3ae8-107">Atom 1.0 と RSS 2.0 のどちらも、仕様で定義されていない属性と要素を配信フィードに追加できます。</span><span class="sxs-lookup"><span data-stu-id="c3ae8-107">Both Atom 1.0 and RSS 2.0, add attributes and elements to syndication feeds that are not defined in the specifications.</span></span> <span data-ttu-id="c3ae8-108">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] の配信プログラミング モデルには、カスタム属性と拡張機能を扱う方法として、次のように、弱い型指定のアクセスと新しいクラスの派生が用意されています。</span><span class="sxs-lookup"><span data-stu-id="c3ae8-108">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] syndication programming model provides the following ways of working with custom attributes and extensions, loosely-typed access and deriving a new class.</span></span>  
  
## <a name="loosely-typed-access"></a><span data-ttu-id="c3ae8-109">弱い型指定のアクセス</span><span class="sxs-lookup"><span data-stu-id="c3ae8-109">Loosely Typed Access</span></span>  
 <span data-ttu-id="c3ae8-110">新しいクラスの派生によって拡張機能を追加するには、追加のコードを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3ae8-110">Adding extensions by deriving a new class requires writing additional code.</span></span> <span data-ttu-id="c3ae8-111">別の方法として、弱い型指定で拡張機能にアクセスする方法もあります。</span><span class="sxs-lookup"><span data-stu-id="c3ae8-111">Another option is accessing extensions in a loosely-typed way.</span></span> <span data-ttu-id="c3ae8-112">配信抽象データ モデルに定義される型にはすべて、`AttributeExtensions` および `ElementExtensions` という名前のプロパティが含まれます。ただし、<xref:System.ServiceModel.Syndication.SyndicationContent> には `AttributeExtensions` プロパティがありますが、`ElementExtensions` プロパティはありません。</span><span class="sxs-lookup"><span data-stu-id="c3ae8-112">All of the types defined in the syndication abstract data model contain properties named `AttributeExtensions` and `ElementExtensions` (with one exception, <xref:System.ServiceModel.Syndication.SyndicationContent> has an `AttributeExtensions` property but no `ElementExtensions` property).</span></span> <span data-ttu-id="c3ae8-113">この 2 つのプロパティはそれぞれ、`TryParseAttribute` メソッドと `TryParseElement` メソッドで処理されない拡張機能のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="c3ae8-113">These properties are collections of extensions not processed by the `TryParseAttribute` and `TryParseElement` methods respectively.</span></span> <span data-ttu-id="c3ae8-114">この処理されない拡張機能にアクセスするには、<xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection.ReadElementExtensions%2A?displayProperty=nameWithType>、`ElementExtensions`、<xref:System.ServiceModel.Syndication.SyndicationFeed>、<xref:System.ServiceModel.Syndication.SyndicationItem>、および <xref:System.ServiceModel.Syndication.SyndicationLink> の <xref:System.ServiceModel.Syndication.SyndicationPerson> プロパティで <xref:System.ServiceModel.Syndication.SyndicationCategory> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c3ae8-114">You can access these unprocessed extensions by calling <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection.ReadElementExtensions%2A?displayProperty=nameWithType> on the `ElementExtensions` property of <xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, <xref:System.ServiceModel.Syndication.SyndicationLink>, <xref:System.ServiceModel.Syndication.SyndicationPerson>, and <xref:System.ServiceModel.Syndication.SyndicationCategory>.</span></span> <span data-ttu-id="c3ae8-115">このメソッドのセットは、指定した名前と名前空間を持つ拡張機能をすべて検索し、個別に `TExtension` のインスタンスに逆シリアル化して `TExtension` オブジェクトのコレクションとして返します。</span><span class="sxs-lookup"><span data-stu-id="c3ae8-115">This set of methods finds all extensions with the specified name and namespace, deserializes them individually into instances of `TExtension` and returns them as a collection of `TExtension` objects.</span></span>  
  
## <a name="deriving-a-new-class"></a><span data-ttu-id="c3ae8-116">新しいクラスの派生</span><span class="sxs-lookup"><span data-stu-id="c3ae8-116">Deriving a New Class</span></span>  
 <span data-ttu-id="c3ae8-117">任意の既存抽象データ モデル クラスから、新しいクラスを派生できます。</span><span class="sxs-lookup"><span data-stu-id="c3ae8-117">You can derive a new class from any of the existing abstract data model classes.</span></span> <span data-ttu-id="c3ae8-118">これは、対象フィードのほとんどに特定の拡張機能が含まれるアプリケーションを実装する際に行います。</span><span class="sxs-lookup"><span data-stu-id="c3ae8-118">Do this when implementing an application in which most of the feeds you are working with have a particular extension.</span></span> <span data-ttu-id="c3ae8-119">このトピックでは、プログラムで処理するフィードのほとんどに、`MyExtension` 拡張機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c3ae8-119">In this topic, most of the feeds that the program works with contain a `MyExtension` extension.</span></span> <span data-ttu-id="c3ae8-120">プログラミング性を向上するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="c3ae8-120">To provide an improved programming experience, do the following steps:</span></span>  
  
-   <span data-ttu-id="c3ae8-121">拡張機能データを保持するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="c3ae8-121">Create a class to hold the extension data.</span></span> <span data-ttu-id="c3ae8-122">この場合、MyExtension というクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="c3ae8-122">In this case, create a class called MyExtension.</span></span>  
  
-   <span data-ttu-id="c3ae8-123">プログラミング性を向上するには、<xref:System.ServiceModel.Syndication.SyndicationItem> から MyExtensionItem というクラスを派生させ、MyExtension 型のプロパティを公開します。</span><span class="sxs-lookup"><span data-stu-id="c3ae8-123">Derive a class called MyExtensionItem from <xref:System.ServiceModel.Syndication.SyndicationItem> to expose a property of type MyExtension for programmability purposes.</span></span>  
  
-   <span data-ttu-id="c3ae8-124">MyExtensionItem クラスの <xref:System.ServiceModel.Syndication.SyndicationItem.TryParseElement%28System.Xml.XmlReader%2CSystem.String%29> をオーバーライドし、MyExtension が読み込まれたら新しい MyExtension インスタンスをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="c3ae8-124">Override <xref:System.ServiceModel.Syndication.SyndicationItem.TryParseElement%28System.Xml.XmlReader%2CSystem.String%29> in the MyExtensionItem class to instantiate a new MyExtension instance when a MyExtension is read in.</span></span>  
  
-   <span data-ttu-id="c3ae8-125">MyExtensionItem クラスの <xref:System.ServiceModel.Syndication.SyndicationItem.WriteElementExtensions%28System.Xml.XmlWriter%2CSystem.String%29> をオーバーライドし、MyExtension プロパティのコンテンツを XML ライターに書き出します。</span><span class="sxs-lookup"><span data-stu-id="c3ae8-125">Override <xref:System.ServiceModel.Syndication.SyndicationItem.WriteElementExtensions%28System.Xml.XmlWriter%2CSystem.String%29> in the MyExtensionItem class to write the contents of the MyExtension property to an XML writer.</span></span>  
  
-   <span data-ttu-id="c3ae8-126"><xref:System.ServiceModel.Syndication.SyndicationFeed> から、MyExtensionFeed というクラスを派生させます。</span><span class="sxs-lookup"><span data-stu-id="c3ae8-126">Derive a class called MyExtensionFeed from <xref:System.ServiceModel.Syndication.SyndicationFeed>.</span></span>  
  
-   <span data-ttu-id="c3ae8-127">MyExtensionFeed クラスの <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateItem> をオーバーライドし、既定の <xref:System.ServiceModel.Syndication.SyndicationItem> の代わりに MyExtensionItem をインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="c3ae8-127">Override <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateItem> in the MyExtensionFeed class to instantiate a MyExtensionItem instead of the default <xref:System.ServiceModel.Syndication.SyndicationItem>.</span></span> <span data-ttu-id="c3ae8-128"><xref:System.ServiceModel.Syndication.SyndicationFeed> および <xref:System.ServiceModel.Syndication.SyndicationItem> に、<xref:System.ServiceModel.Syndication.SyndicationLink>、<xref:System.ServiceModel.Syndication.SyndicationCategory>、および <xref:System.ServiceModel.Syndication.SyndicationPerson> の各オブジェクトを生成する一連のメソッドが定義されます (たとえば、<xref:System.ServiceModel.Syndication.SyndicationFeed.CreateLink>、<xref:System.ServiceModel.Syndication.SyndicationFeed.CreateCategory>、<xref:System.ServiceModel.Syndication.SyndicationFeed.CreatePerson> など)。</span><span class="sxs-lookup"><span data-stu-id="c3ae8-128">A series of methods are defined in <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> that can create <xref:System.ServiceModel.Syndication.SyndicationLink>, <xref:System.ServiceModel.Syndication.SyndicationCategory>, and <xref:System.ServiceModel.Syndication.SyndicationPerson> objects (for example, <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateLink>, <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateCategory>, and <xref:System.ServiceModel.Syndication.SyndicationFeed.CreatePerson>).</span></span> <span data-ttu-id="c3ae8-129">そのどれもが、カスタム派生クラスを作成するためにオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="c3ae8-129">All of which can be overridden to create a custom derived class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3ae8-130">参照</span><span class="sxs-lookup"><span data-stu-id="c3ae8-130">See Also</span></span>  
 [<span data-ttu-id="c3ae8-131">WCF 配信の概要</span><span class="sxs-lookup"><span data-stu-id="c3ae8-131">WCF Syndication Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)  
 [<span data-ttu-id="c3ae8-132">配信のアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="c3ae8-132">Architecture of Syndication</span></span>](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)
