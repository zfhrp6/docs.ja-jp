---
title: OneWayBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: abaacfb6541d41019a8d0cd6df53913c6b7911f2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="onewaybindingelement"></a><span data-ttu-id="6bfe6-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="6bfe6-102">OneWayBindingElement</span></span>
<span data-ttu-id="6bfe6-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="6bfe6-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bfe6-104">構文</span><span class="sxs-lookup"><span data-stu-id="6bfe6-104">Syntax</span></span>  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6bfe6-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="6bfe6-105">Methods</span></span>  
 <span data-ttu-id="6bfe6-106">OneWayBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="6bfe6-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6bfe6-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="6bfe6-107">Properties</span></span>  
 <span data-ttu-id="6bfe6-108">OneWayBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="6bfe6-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="6bfe6-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="6bfe6-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="6bfe6-110">データ型 : ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="6bfe6-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="6bfe6-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6bfe6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6bfe6-112">チャネル プールの設定。</span><span class="sxs-lookup"><span data-stu-id="6bfe6-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="6bfe6-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="6bfe6-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="6bfe6-114">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="6bfe6-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="6bfe6-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6bfe6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6bfe6-116">許可されるチャネルの最大数。</span><span class="sxs-lookup"><span data-stu-id="6bfe6-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="6bfe6-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="6bfe6-117">PacketRoutable</span></span>  
 <span data-ttu-id="6bfe6-118">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="6bfe6-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="6bfe6-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6bfe6-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6bfe6-120">パケットがルーティング可能かどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="6bfe6-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bfe6-121">要件</span><span class="sxs-lookup"><span data-stu-id="6bfe6-121">Requirements</span></span>  
  
|<span data-ttu-id="6bfe6-122">MOF</span><span class="sxs-lookup"><span data-stu-id="6bfe6-122">MOF</span></span>|<span data-ttu-id="6bfe6-123">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="6bfe6-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6bfe6-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="6bfe6-124">Namespace</span></span>|<span data-ttu-id="6bfe6-125">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="6bfe6-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6bfe6-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="6bfe6-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
