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
ms.workload: dotnet
ms.openlocfilehash: 47de8c2449c46b12b8d10ac2a5269a18d1454f41
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="onewaybindingelement"></a><span data-ttu-id="3fa02-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="3fa02-102">OneWayBindingElement</span></span>
<span data-ttu-id="3fa02-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="3fa02-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fa02-104">構文</span><span class="sxs-lookup"><span data-stu-id="3fa02-104">Syntax</span></span>  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3fa02-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="3fa02-105">Methods</span></span>  
 <span data-ttu-id="3fa02-106">OneWayBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="3fa02-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3fa02-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="3fa02-107">Properties</span></span>  
 <span data-ttu-id="3fa02-108">OneWayBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="3fa02-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="3fa02-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="3fa02-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="3fa02-110">データ型 : ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="3fa02-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="3fa02-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3fa02-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3fa02-112">チャネル プールの設定。</span><span class="sxs-lookup"><span data-stu-id="3fa02-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="3fa02-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="3fa02-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="3fa02-114">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="3fa02-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="3fa02-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3fa02-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3fa02-116">許可されるチャネルの最大数。</span><span class="sxs-lookup"><span data-stu-id="3fa02-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="3fa02-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="3fa02-117">PacketRoutable</span></span>  
 <span data-ttu-id="3fa02-118">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="3fa02-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="3fa02-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3fa02-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3fa02-120">パケットがルーティング可能かどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="3fa02-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fa02-121">必要条件</span><span class="sxs-lookup"><span data-stu-id="3fa02-121">Requirements</span></span>  
  
|<span data-ttu-id="3fa02-122">MOF</span><span class="sxs-lookup"><span data-stu-id="3fa02-122">MOF</span></span>|<span data-ttu-id="3fa02-123">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="3fa02-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3fa02-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="3fa02-124">Namespace</span></span>|<span data-ttu-id="3fa02-125">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="3fa02-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3fa02-126">参照</span><span class="sxs-lookup"><span data-stu-id="3fa02-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
