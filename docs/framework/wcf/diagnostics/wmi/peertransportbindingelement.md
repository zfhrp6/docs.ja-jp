---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: 68e6a25e4e3f47c556363e2fd5aa8d3bb9946449
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485646"
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="38f56-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="38f56-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="38f56-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="38f56-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38f56-104">構文</span><span class="sxs-lookup"><span data-stu-id="38f56-104">Syntax</span></span>  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="38f56-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="38f56-105">Methods</span></span>  
 <span data-ttu-id="38f56-106">PeerTransportBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="38f56-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="38f56-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="38f56-107">Properties</span></span>  
 <span data-ttu-id="38f56-108">PeerTransportBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="38f56-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="38f56-109">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="38f56-109">ListenIPAddress</span></span>  
 <span data-ttu-id="38f56-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="38f56-110">Data type: string</span></span>  
  
 <span data-ttu-id="38f56-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="38f56-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38f56-112">ピア ノードがメッセージをリッスンする IP アドレスです。</span><span class="sxs-lookup"><span data-stu-id="38f56-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="38f56-113">ポート</span><span class="sxs-lookup"><span data-stu-id="38f56-113">Port</span></span>  
 <span data-ttu-id="38f56-114">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="38f56-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="38f56-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="38f56-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38f56-116">このバインディングがピア チャネル メッセージを処理するネットワーク インターフェイス ポートです。</span><span class="sxs-lookup"><span data-stu-id="38f56-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="38f56-117">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="38f56-117">Security</span></span>  
 <span data-ttu-id="38f56-118">データ型 : PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="38f56-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="38f56-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="38f56-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38f56-120">ピア トランスポートのセキュリティ設定です。</span><span class="sxs-lookup"><span data-stu-id="38f56-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38f56-121">要件</span><span class="sxs-lookup"><span data-stu-id="38f56-121">Requirements</span></span>  
  
|<span data-ttu-id="38f56-122">MOF</span><span class="sxs-lookup"><span data-stu-id="38f56-122">MOF</span></span>|<span data-ttu-id="38f56-123">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="38f56-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="38f56-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="38f56-124">Namespace</span></span>|<span data-ttu-id="38f56-125">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="38f56-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="38f56-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="38f56-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
