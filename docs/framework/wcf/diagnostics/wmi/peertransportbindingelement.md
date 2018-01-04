---
title: PeerTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 25893b1f3cf6cf20ae674bade5090a70c5f381a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="6cd5b-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="6cd5b-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="6cd5b-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="6cd5b-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cd5b-104">構文</span><span class="sxs-lookup"><span data-stu-id="6cd5b-104">Syntax</span></span>  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6cd5b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="6cd5b-105">Methods</span></span>  
 <span data-ttu-id="6cd5b-106">PeerTransportBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="6cd5b-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6cd5b-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="6cd5b-107">Properties</span></span>  
 <span data-ttu-id="6cd5b-108">PeerTransportBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="6cd5b-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="6cd5b-109">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="6cd5b-109">ListenIPAddress</span></span>  
 <span data-ttu-id="6cd5b-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="6cd5b-110">Data type: string</span></span>  
  
 <span data-ttu-id="6cd5b-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6cd5b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6cd5b-112">ピア ノードがメッセージをリッスンする IP アドレスです。</span><span class="sxs-lookup"><span data-stu-id="6cd5b-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="6cd5b-113">ポート</span><span class="sxs-lookup"><span data-stu-id="6cd5b-113">Port</span></span>  
 <span data-ttu-id="6cd5b-114">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="6cd5b-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="6cd5b-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6cd5b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6cd5b-116">このバインディングがピア チャネル メッセージを処理するネットワーク インターフェイス ポートです。</span><span class="sxs-lookup"><span data-stu-id="6cd5b-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="6cd5b-117">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="6cd5b-117">Security</span></span>  
 <span data-ttu-id="6cd5b-118">データ型 : PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="6cd5b-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="6cd5b-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6cd5b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6cd5b-120">ピア トランスポートのセキュリティ設定です。</span><span class="sxs-lookup"><span data-stu-id="6cd5b-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cd5b-121">必要条件</span><span class="sxs-lookup"><span data-stu-id="6cd5b-121">Requirements</span></span>  
  
|<span data-ttu-id="6cd5b-122">MOF</span><span class="sxs-lookup"><span data-stu-id="6cd5b-122">MOF</span></span>|<span data-ttu-id="6cd5b-123">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="6cd5b-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6cd5b-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="6cd5b-124">Namespace</span></span>|<span data-ttu-id="6cd5b-125">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="6cd5b-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6cd5b-126">参照</span><span class="sxs-lookup"><span data-stu-id="6cd5b-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
