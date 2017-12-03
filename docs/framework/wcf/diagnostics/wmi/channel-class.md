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
ms.openlocfilehash: 93632d6a178c0f58143fc148a0e1eb51be94ed17
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="channel-class"></a><span data-ttu-id="f0ee8-102">チャネル クラス</span><span class="sxs-lookup"><span data-stu-id="f0ee8-102">Channel class</span></span>
<span data-ttu-id="f0ee8-103">チャネル</span><span class="sxs-lookup"><span data-stu-id="f0ee8-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0ee8-104">構文</span><span class="sxs-lookup"><span data-stu-id="f0ee8-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="f0ee8-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="f0ee8-105">Methods</span></span>  
 <span data-ttu-id="f0ee8-106">チャネル クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="f0ee8-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f0ee8-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f0ee8-107">Properties</span></span>  
 <span data-ttu-id="f0ee8-108">チャネル クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="f0ee8-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="f0ee8-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="f0ee8-109">LocalAddress</span></span>  
 <span data-ttu-id="f0ee8-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="f0ee8-110">Data type: string</span></span>  
  
 <span data-ttu-id="f0ee8-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="f0ee8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0ee8-112">チャネルのローカル エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="f0ee8-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="f0ee8-113">ref</span><span class="sxs-lookup"><span data-stu-id="f0ee8-113">ref</span></span>  
 <span data-ttu-id="f0ee8-114">データ型 : Endpoint</span><span class="sxs-lookup"><span data-stu-id="f0ee8-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="f0ee8-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="f0ee8-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0ee8-116">チャネルが接続するエンドポイントへの参照。</span><span class="sxs-lookup"><span data-stu-id="f0ee8-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="f0ee8-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="f0ee8-117">RemoteAddress</span></span>  
 <span data-ttu-id="f0ee8-118">データ型: string</span><span class="sxs-lookup"><span data-stu-id="f0ee8-118">Data type: string</span></span>  
  
 <span data-ttu-id="f0ee8-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="f0ee8-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0ee8-120">チャネルに関連するリモート アドレス。</span><span class="sxs-lookup"><span data-stu-id="f0ee8-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="f0ee8-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="f0ee8-121">SessionId</span></span>  
 <span data-ttu-id="f0ee8-122">データ型: string</span><span class="sxs-lookup"><span data-stu-id="f0ee8-122">Data type: string</span></span>  
  
 <span data-ttu-id="f0ee8-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="f0ee8-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0ee8-124">現在のセッション ID (存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="f0ee8-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="f0ee8-125">種類</span><span class="sxs-lookup"><span data-stu-id="f0ee8-125">Type</span></span>  
 <span data-ttu-id="f0ee8-126">データ型: string</span><span class="sxs-lookup"><span data-stu-id="f0ee8-126">Data type: string</span></span>  
  
 <span data-ttu-id="f0ee8-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="f0ee8-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0ee8-128">チャネルの型。</span><span class="sxs-lookup"><span data-stu-id="f0ee8-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0ee8-129">要件</span><span class="sxs-lookup"><span data-stu-id="f0ee8-129">Requirements</span></span>  
  
|<span data-ttu-id="f0ee8-130">MOF</span><span class="sxs-lookup"><span data-stu-id="f0ee8-130">MOF</span></span>|<span data-ttu-id="f0ee8-131">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="f0ee8-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f0ee8-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="f0ee8-132">Namespace</span></span>|<span data-ttu-id="f0ee8-133">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="f0ee8-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f0ee8-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="f0ee8-134">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelBase>
