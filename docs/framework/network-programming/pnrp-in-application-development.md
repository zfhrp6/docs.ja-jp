---
title: "アプリケーション開発での PNRP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d11f1b284ebb4e4a44d1dad442f727692fa26ffa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="pnrp-in-application-development"></a><span data-ttu-id="a3e5f-102">アプリケーション開発での PNRP</span><span class="sxs-lookup"><span data-stu-id="a3e5f-102">PNRP in Application Development</span></span>
<span data-ttu-id="a3e5f-103">Windows Vista では、ネットワーク アプリケーションは、簡単な PNRP アプリケーション プログラミング インターフェイス (API) を通して名前発行および名前解決機能にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a3e5f-103">In Windows Vista, networking applications can access name publication and resolution functions through a simplified PNRP application programming interface (API).</span></span>  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a><span data-ttu-id="a3e5f-104">ピア名解決プロトコルの実装</span><span class="sxs-lookup"><span data-stu-id="a3e5f-104">Implementing the Peer Name Resolution Protocol</span></span>  
 <span data-ttu-id="a3e5f-105">簡略化された PNRP API では、名前とアドレスを登録するためにクラウドを明示的に指定することはありません。PNRP コンポーネントは、参加する適切なクラウドと、クラウド内で公開するアドレスを、自動的に決定ます。</span><span class="sxs-lookup"><span data-stu-id="a3e5f-105">With the simplified PNRP API, clouds are not explicitly specified to register the name and addresses; the PNRP component automatically determines the appropriate clouds to join and the addresses to publish within the clouds.</span></span>  
  
 <span data-ttu-id="a3e5f-106">Windows Vista の非常に簡略化された PNRP 名前解決では、Windows Sockets 関数 getaddrinfo() に PNRP 名が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="a3e5f-106">For highly simplified PNRP name resolution in Windows Vista, PNRP names are now integrated into the getaddrinfo() Windows Sockets function.</span></span> <span data-ttu-id="a3e5f-107">PNRP を使って名前を IPv6 アドレスに変換する場合、getaddrinfo() 関数を使って完全修飾ドメイン名 (FQDN) name.prnp.net を解決できます。ここで name は解決されるピア名です。</span><span class="sxs-lookup"><span data-stu-id="a3e5f-107">To use PNRP to resolve a name to an IPv6 address, applications can use the getaddrinfo() function to resolve the Fully Qualified Domain Name (FQDN) name.prnp.net, in which name is peer name being resolved.</span></span> <span data-ttu-id="a3e5f-108">pnrp.net ドメインは、PNRP 名前解決のために Windows Vista で予約されているドメインです。</span><span class="sxs-lookup"><span data-stu-id="a3e5f-108">The pnrp.net domain is a reserved domain in Windows Vista for PNRP name resolution.</span></span>  
  
 <span data-ttu-id="a3e5f-109">PeerToPeer アプリケーション間でのメッセージの受け渡しは、依然として PeerChannel や WCF の[大規模データとストリーミング](http://go.microsoft.com/fwlink/?LinkID=179652)などの、基盤のアーキテクチャによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="a3e5f-109">Message passing between PeerToPeer applications is still handled by underlying architectures such as PeerChannel and WCF [Large Data and Streaming](http://go.microsoft.com/fwlink/?LinkID=179652).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3e5f-110">参照</span><span class="sxs-lookup"><span data-stu-id="a3e5f-110">See Also</span></span>  
 <xref:System.Net.PeerToPeer>
