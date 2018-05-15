---
title: チャネル クラス
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: 4b7c66560c0c136a258c527d8a681d491eb50aae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="channel-class"></a><span data-ttu-id="ab8c9-102">チャネル クラス</span><span class="sxs-lookup"><span data-stu-id="ab8c9-102">Channel class</span></span>
<span data-ttu-id="ab8c9-103">チャネル</span><span class="sxs-lookup"><span data-stu-id="ab8c9-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab8c9-104">構文</span><span class="sxs-lookup"><span data-stu-id="ab8c9-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="ab8c9-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="ab8c9-105">Methods</span></span>  
 <span data-ttu-id="ab8c9-106">チャネル クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="ab8c9-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ab8c9-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ab8c9-107">Properties</span></span>  
 <span data-ttu-id="ab8c9-108">チャネル クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="ab8c9-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="ab8c9-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="ab8c9-109">LocalAddress</span></span>  
 <span data-ttu-id="ab8c9-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="ab8c9-110">Data type: string</span></span>  
  
 <span data-ttu-id="ab8c9-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ab8c9-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab8c9-112">チャネルのローカル エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="ab8c9-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="ab8c9-113">ref</span><span class="sxs-lookup"><span data-stu-id="ab8c9-113">ref</span></span>  
 <span data-ttu-id="ab8c9-114">データ型 : Endpoint</span><span class="sxs-lookup"><span data-stu-id="ab8c9-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="ab8c9-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ab8c9-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab8c9-116">チャネルが接続するエンドポイントへの参照。</span><span class="sxs-lookup"><span data-stu-id="ab8c9-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="ab8c9-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="ab8c9-117">RemoteAddress</span></span>  
 <span data-ttu-id="ab8c9-118">データ型: string</span><span class="sxs-lookup"><span data-stu-id="ab8c9-118">Data type: string</span></span>  
  
 <span data-ttu-id="ab8c9-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ab8c9-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab8c9-120">チャネルに関連するリモート アドレス。</span><span class="sxs-lookup"><span data-stu-id="ab8c9-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="ab8c9-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="ab8c9-121">SessionId</span></span>  
 <span data-ttu-id="ab8c9-122">データ型: string</span><span class="sxs-lookup"><span data-stu-id="ab8c9-122">Data type: string</span></span>  
  
 <span data-ttu-id="ab8c9-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ab8c9-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab8c9-124">現在のセッション ID (存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="ab8c9-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="ab8c9-125">種類</span><span class="sxs-lookup"><span data-stu-id="ab8c9-125">Type</span></span>  
 <span data-ttu-id="ab8c9-126">データ型: string</span><span class="sxs-lookup"><span data-stu-id="ab8c9-126">Data type: string</span></span>  
  
 <span data-ttu-id="ab8c9-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ab8c9-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab8c9-128">チャネルの型。</span><span class="sxs-lookup"><span data-stu-id="ab8c9-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab8c9-129">要件</span><span class="sxs-lookup"><span data-stu-id="ab8c9-129">Requirements</span></span>  
  
|<span data-ttu-id="ab8c9-130">MOF</span><span class="sxs-lookup"><span data-stu-id="ab8c9-130">MOF</span></span>|<span data-ttu-id="ab8c9-131">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="ab8c9-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ab8c9-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="ab8c9-132">Namespace</span></span>|<span data-ttu-id="ab8c9-133">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="ab8c9-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab8c9-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab8c9-134">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelBase>
