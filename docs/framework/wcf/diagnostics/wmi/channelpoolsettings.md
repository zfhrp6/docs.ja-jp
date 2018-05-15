---
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: 48b41d2f3f45cd9c590f87151253450962b994de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="channelpoolsettings"></a><span data-ttu-id="efc7e-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="efc7e-102">ChannelPoolSettings</span></span>
<span data-ttu-id="efc7e-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="efc7e-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efc7e-104">構文</span><span class="sxs-lookup"><span data-stu-id="efc7e-104">Syntax</span></span>  
  
```  
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="efc7e-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="efc7e-105">Methods</span></span>  
 <span data-ttu-id="efc7e-106">ChannelPoolSettings クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="efc7e-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="efc7e-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="efc7e-107">Properties</span></span>  
 <span data-ttu-id="efc7e-108">ChannelPoolSettings クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="efc7e-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="efc7e-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="efc7e-109">IdleTimeout</span></span>  
 <span data-ttu-id="efc7e-110">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="efc7e-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="efc7e-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="efc7e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="efc7e-112">接続が切断されるまでの最大アイドル時間。</span><span class="sxs-lookup"><span data-stu-id="efc7e-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="efc7e-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="efc7e-113">LeaseTimeout</span></span>  
 <span data-ttu-id="efc7e-114">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="efc7e-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="efc7e-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="efc7e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="efc7e-116">リース操作の完了がタイムアウトするまでの最大時間。</span><span class="sxs-lookup"><span data-stu-id="efc7e-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="efc7e-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="efc7e-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="efc7e-118">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="efc7e-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="efc7e-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="efc7e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="efc7e-120">各エンドポイントでの送信チャネルの最大数。</span><span class="sxs-lookup"><span data-stu-id="efc7e-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efc7e-121">要件</span><span class="sxs-lookup"><span data-stu-id="efc7e-121">Requirements</span></span>  
  
|<span data-ttu-id="efc7e-122">MOF</span><span class="sxs-lookup"><span data-stu-id="efc7e-122">MOF</span></span>|<span data-ttu-id="efc7e-123">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="efc7e-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="efc7e-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="efc7e-124">Namespace</span></span>|<span data-ttu-id="efc7e-125">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="efc7e-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="efc7e-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="efc7e-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>
