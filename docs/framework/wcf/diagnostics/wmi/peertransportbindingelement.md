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
ms.openlocfilehash: 193000acf2f3c8a0eddb2552559ee40a0f5fced9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="52135-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="52135-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="52135-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="52135-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52135-104">構文</span><span class="sxs-lookup"><span data-stu-id="52135-104">Syntax</span></span>  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="52135-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="52135-105">Methods</span></span>  
 <span data-ttu-id="52135-106">PeerTransportBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="52135-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="52135-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="52135-107">Properties</span></span>  
 <span data-ttu-id="52135-108">PeerTransportBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="52135-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="52135-109">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="52135-109">ListenIPAddress</span></span>  
 <span data-ttu-id="52135-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="52135-110">Data type: string</span></span>  
  
 <span data-ttu-id="52135-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="52135-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52135-112">ピア ノードがメッセージをリッスンする IP アドレスです。</span><span class="sxs-lookup"><span data-stu-id="52135-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="52135-113">ポート</span><span class="sxs-lookup"><span data-stu-id="52135-113">Port</span></span>  
 <span data-ttu-id="52135-114">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="52135-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="52135-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="52135-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52135-116">このバインディングがピア チャネル メッセージを処理するネットワーク インターフェイス ポートです。</span><span class="sxs-lookup"><span data-stu-id="52135-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="52135-117">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="52135-117">Security</span></span>  
 <span data-ttu-id="52135-118">データ型 : PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="52135-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="52135-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="52135-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52135-120">ピア トランスポートのセキュリティ設定です。</span><span class="sxs-lookup"><span data-stu-id="52135-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52135-121">要件</span><span class="sxs-lookup"><span data-stu-id="52135-121">Requirements</span></span>  
  
|<span data-ttu-id="52135-122">MOF</span><span class="sxs-lookup"><span data-stu-id="52135-122">MOF</span></span>|<span data-ttu-id="52135-123">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="52135-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="52135-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="52135-124">Namespace</span></span>|<span data-ttu-id="52135-125">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="52135-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="52135-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="52135-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
