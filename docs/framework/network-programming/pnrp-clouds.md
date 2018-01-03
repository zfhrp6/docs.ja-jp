---
title: "PNRP クラウド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a82e2bf1-62ab-4c2d-83f3-3217a6aead2e
caps.latest.revision: "4"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f142c7aaa71ab2dbee1d2955f2c235a65e6c8bfa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="pnrp-clouds"></a><span data-ttu-id="d8fd1-102">PNRP クラウド</span><span class="sxs-lookup"><span data-stu-id="d8fd1-102">PNRP Clouds</span></span>
<span data-ttu-id="d8fd1-103">PNRP "クラウド" は、ネットワーク経由で相互に通信できるノードのセットを表します。</span><span class="sxs-lookup"><span data-stu-id="d8fd1-103">A PNRP "cloud" represents a set of nodes that can communicate with each other through the network.</span></span> <span data-ttu-id="d8fd1-104">"クラウド" という用語は、"ピア メッシュ" や "ピアツーピア グラフ" と同義です。</span><span class="sxs-lookup"><span data-stu-id="d8fd1-104">The term "cloud" is synonymous with "peer mesh" and "peer-to-peer graph".</span></span>  
  
 <span data-ttu-id="d8fd1-105">異なるクラウド間でノード間通信を行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="d8fd1-105">Communication between nodes should never cross from one cloud to another.</span></span> <span data-ttu-id="d8fd1-106"><xref:System.Net.PeerToPeer.Cloud> インスタンスは、名前によって一意に識別されます。名前は大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="d8fd1-106">A <xref:System.Net.PeerToPeer.Cloud> instance is uniquely identified by its name, which is case-sensitive.</span></span> <span data-ttu-id="d8fd1-107">1 つのピアまたはノードを、複数のクラウドに接続できます。</span><span class="sxs-lookup"><span data-stu-id="d8fd1-107">A single peer or node may be connected to more than one cloud.</span></span>  
  
 <span data-ttu-id="d8fd1-108">クラウドは、ネットワーク インターフェイスに非常に密接に結び付けられています。</span><span class="sxs-lookup"><span data-stu-id="d8fd1-108">Clouds are tied very closely to network interfaces.</span></span>  <span data-ttu-id="d8fd1-109">異なるサブネットに接続された 2 つのネットワーク カードを備えるマルチホーム コンピューターでは、3 つのクラウドが返されます。1 インターフェイスにつきリンクローカル アドレスごとに 1 つ、グローバル スコープ クラウド用に 1 つです。</span><span class="sxs-lookup"><span data-stu-id="d8fd1-109">On a multi-homed machine with two network cards attached to different subnets, three clouds will be returned: one for each of the link local addresses per interface, and a single global scope cloud.</span></span>  
  
 <span data-ttu-id="d8fd1-110">PNRP は 3 つのクラウド "スコープ" を使います。スコープとは、互いに検出可能なコンピューターをグループ化したものです。</span><span class="sxs-lookup"><span data-stu-id="d8fd1-110">PNRP uses three cloud "scopes", in which a scope is a grouping of computers that are able to find each other:</span></span>  
  
-   <span data-ttu-id="d8fd1-111">グローバル クラウドはグローバル IPv6 アドレス スコープとグローバル アドレスに対応し、IPv6 インターネット全体のすべてのコンピューターを表しています。</span><span class="sxs-lookup"><span data-stu-id="d8fd1-111">The global cloud corresponds to the global IPv6 address scope and global addresses and represents all the computers on the entire IPv6 Internet.</span></span> <span data-ttu-id="d8fd1-112">グローバル クラウドは 1 つしか存在しません。</span><span class="sxs-lookup"><span data-stu-id="d8fd1-112">There is only a single global cloud.</span></span>  
  
-   <span data-ttu-id="d8fd1-113">リンクローカル クラウドは、リンクローカル IPv6 アドレス スコープとリンクローカル アドレスに対応します。</span><span class="sxs-lookup"><span data-stu-id="d8fd1-113">The link-local cloud corresponds to the link-local IPv6 address scope and link-local addresses.</span></span> <span data-ttu-id="d8fd1-114">リンクローカル クラウドは特定のリンクに使います。このリンクは通常、ローカルにアタッチされているサブネットに相当します。</span><span class="sxs-lookup"><span data-stu-id="d8fd1-114">A link-local cloud is for a specific link, which is typically the same as the locally attached subnet.</span></span> <span data-ttu-id="d8fd1-115">リンクローカル クラウドは複数存在できます。</span><span class="sxs-lookup"><span data-stu-id="d8fd1-115">There can be multiple link-local clouds.</span></span>  
  
 <span data-ttu-id="d8fd1-116">3 番目のクラウドであるサイト固有クラウドは、IPv6 アドレス スコープとサイトローカル アドレスに対応します。</span><span class="sxs-lookup"><span data-stu-id="d8fd1-116">A third cloud, the site-specific cloud, corresponds to the site IPv6 address scope and site-local addresses.</span></span> <span data-ttu-id="d8fd1-117">サイト固有クラウドは古いクラウドですが、PNRP ではまだサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d8fd1-117">This cloud has been deprecated, although it is still supported in PNRP.</span></span>  
  
## <a name="clouds"></a><span data-ttu-id="d8fd1-118">クラウド</span><span class="sxs-lookup"><span data-stu-id="d8fd1-118">Clouds</span></span>  
 <span data-ttu-id="d8fd1-119">PNRP クラウドは、<xref:System.Net.PeerToPeer.Cloud> クラスのインスタンスで表されます。</span><span class="sxs-lookup"><span data-stu-id="d8fd1-119">PNRP clouds are represented by instances of the <xref:System.Net.PeerToPeer.Cloud> class.</span></span> <span data-ttu-id="d8fd1-120">ピアを使うクラウドのグループは、列挙可能な <xref:System.Net.PeerToPeer.CloudCollection> クラスのインスタンスによって表されます。</span><span class="sxs-lookup"><span data-stu-id="d8fd1-120">Groups of clouds used a peer are represented by instances of the enumerable <xref:System.Net.PeerToPeer.CloudCollection> class.</span></span> <span data-ttu-id="d8fd1-121">現在のピアに認識される PNRP クラウドのコレクションは、静的 <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> メソッドを呼び出すことによって取得できます。</span><span class="sxs-lookup"><span data-stu-id="d8fd1-121">Collections of PNRP clouds known to the current peer can be obtained by calling the static <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> method.</span></span>  
  
 <span data-ttu-id="d8fd1-122">個々のクラウドには、256 文字の Unicode 文字列として表される一意の名前があります。</span><span class="sxs-lookup"><span data-stu-id="d8fd1-122">Individual clouds have unique names, represented as a 256 character Unicode string.</span></span> <span data-ttu-id="d8fd1-123">これらの名前および上記のスコープは、クラウド クラスの一意のインスタンスを作成するために使われます。</span><span class="sxs-lookup"><span data-stu-id="d8fd1-123">These names, along with the above-mentioned scope, are used to construct unique instances of the Cloud class.</span></span> <span data-ttu-id="d8fd1-124">これらのインスタンスは、永続的な使用のためにシリアル化および再構築できます。</span><span class="sxs-lookup"><span data-stu-id="d8fd1-124">These instances can be serialized and reconstructed for persistent usage.</span></span>  
  
 <span data-ttu-id="d8fd1-125">クラウド インスタンスを作成または取得した後は、それにピア名を登録して、既知のピアのメッシュを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d8fd1-125">Once a Cloud instance is created or obtained, peer names can be registered with it to create a mesh of known peers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8fd1-126">参照</span><span class="sxs-lookup"><span data-stu-id="d8fd1-126">See Also</span></span>  
 <xref:System.Net.PeerToPeer.Cloud>  
 [<span data-ttu-id="d8fd1-127">ピア名解決プロトコル</span><span class="sxs-lookup"><span data-stu-id="d8fd1-127">Peer Name Resolution Protocol</span></span>](../../../docs/framework/network-programming/peer-name-resolution-protocol.md)
