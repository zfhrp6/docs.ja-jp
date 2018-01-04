---
title: "チャネル クラス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 073f0a2a2731a08acd914a7dd85cb2b419d98128
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="channel-class"></a><span data-ttu-id="dae13-102">チャネル クラス</span><span class="sxs-lookup"><span data-stu-id="dae13-102">Channel class</span></span>
<span data-ttu-id="dae13-103">チャネル</span><span class="sxs-lookup"><span data-stu-id="dae13-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dae13-104">構文</span><span class="sxs-lookup"><span data-stu-id="dae13-104">Syntax</span></span>  
  
```  
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="dae13-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="dae13-105">Methods</span></span>  
 <span data-ttu-id="dae13-106">チャネル クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="dae13-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="dae13-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="dae13-107">Properties</span></span>  
 <span data-ttu-id="dae13-108">チャネル クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="dae13-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="dae13-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="dae13-109">LocalAddress</span></span>  
 <span data-ttu-id="dae13-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="dae13-110">Data type: string</span></span>  
  
 <span data-ttu-id="dae13-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="dae13-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dae13-112">チャネルのローカル エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="dae13-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="dae13-113">ref</span><span class="sxs-lookup"><span data-stu-id="dae13-113">ref</span></span>  
 <span data-ttu-id="dae13-114">データ型 : Endpoint</span><span class="sxs-lookup"><span data-stu-id="dae13-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="dae13-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="dae13-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dae13-116">チャネルが接続するエンドポイントへの参照。</span><span class="sxs-lookup"><span data-stu-id="dae13-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="dae13-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="dae13-117">RemoteAddress</span></span>  
 <span data-ttu-id="dae13-118">データ型: string</span><span class="sxs-lookup"><span data-stu-id="dae13-118">Data type: string</span></span>  
  
 <span data-ttu-id="dae13-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="dae13-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dae13-120">チャネルに関連するリモート アドレス。</span><span class="sxs-lookup"><span data-stu-id="dae13-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="dae13-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="dae13-121">SessionId</span></span>  
 <span data-ttu-id="dae13-122">データ型: string</span><span class="sxs-lookup"><span data-stu-id="dae13-122">Data type: string</span></span>  
  
 <span data-ttu-id="dae13-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="dae13-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dae13-124">現在のセッション ID (存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="dae13-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="dae13-125">種類</span><span class="sxs-lookup"><span data-stu-id="dae13-125">Type</span></span>  
 <span data-ttu-id="dae13-126">データ型: string</span><span class="sxs-lookup"><span data-stu-id="dae13-126">Data type: string</span></span>  
  
 <span data-ttu-id="dae13-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="dae13-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dae13-128">チャネルの型。</span><span class="sxs-lookup"><span data-stu-id="dae13-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dae13-129">要件</span><span class="sxs-lookup"><span data-stu-id="dae13-129">Requirements</span></span>  
  
|<span data-ttu-id="dae13-130">MOF</span><span class="sxs-lookup"><span data-stu-id="dae13-130">MOF</span></span>|<span data-ttu-id="dae13-131">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="dae13-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="dae13-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="dae13-132">Namespace</span></span>|<span data-ttu-id="dae13-133">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="dae13-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dae13-134">参照</span><span class="sxs-lookup"><span data-stu-id="dae13-134">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelBase>
