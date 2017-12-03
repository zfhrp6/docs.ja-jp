---
title: ChannelPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e97e934673efbc6d0f72751c7cb1de6fba84a141
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="channelpoolsettings"></a><span data-ttu-id="5fd50-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="5fd50-102">ChannelPoolSettings</span></span>
<span data-ttu-id="5fd50-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="5fd50-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fd50-104">構文</span><span class="sxs-lookup"><span data-stu-id="5fd50-104">Syntax</span></span>  
  
```  
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5fd50-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="5fd50-105">Methods</span></span>  
 <span data-ttu-id="5fd50-106">ChannelPoolSettings クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="5fd50-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5fd50-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="5fd50-107">Properties</span></span>  
 <span data-ttu-id="5fd50-108">ChannelPoolSettings クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="5fd50-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="5fd50-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="5fd50-109">IdleTimeout</span></span>  
 <span data-ttu-id="5fd50-110">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="5fd50-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="5fd50-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="5fd50-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5fd50-112">接続が切断されるまでの最大アイドル時間。</span><span class="sxs-lookup"><span data-stu-id="5fd50-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="5fd50-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="5fd50-113">LeaseTimeout</span></span>  
 <span data-ttu-id="5fd50-114">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="5fd50-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="5fd50-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="5fd50-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5fd50-116">リース操作の完了がタイムアウトするまでの最大時間。</span><span class="sxs-lookup"><span data-stu-id="5fd50-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="5fd50-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="5fd50-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="5fd50-118">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="5fd50-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="5fd50-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="5fd50-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5fd50-120">各エンドポイントでの送信チャネルの最大数。</span><span class="sxs-lookup"><span data-stu-id="5fd50-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fd50-121">要件</span><span class="sxs-lookup"><span data-stu-id="5fd50-121">Requirements</span></span>  
  
|<span data-ttu-id="5fd50-122">MOF</span><span class="sxs-lookup"><span data-stu-id="5fd50-122">MOF</span></span>|<span data-ttu-id="5fd50-123">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="5fd50-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5fd50-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="5fd50-124">Namespace</span></span>|<span data-ttu-id="5fd50-125">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="5fd50-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5fd50-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="5fd50-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>
