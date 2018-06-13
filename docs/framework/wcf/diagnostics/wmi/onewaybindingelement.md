---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: ee7cfed20234175ba54dd25dbbbab4615c1ed7af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485758"
---
# <a name="onewaybindingelement"></a><span data-ttu-id="76557-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="76557-102">OneWayBindingElement</span></span>
<span data-ttu-id="76557-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="76557-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76557-104">構文</span><span class="sxs-lookup"><span data-stu-id="76557-104">Syntax</span></span>  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="76557-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="76557-105">Methods</span></span>  
 <span data-ttu-id="76557-106">OneWayBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="76557-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="76557-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="76557-107">Properties</span></span>  
 <span data-ttu-id="76557-108">OneWayBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="76557-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="76557-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="76557-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="76557-110">データ型 : ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="76557-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="76557-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="76557-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="76557-112">チャネル プールの設定。</span><span class="sxs-lookup"><span data-stu-id="76557-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="76557-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="76557-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="76557-114">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="76557-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="76557-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="76557-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="76557-116">許可されるチャネルの最大数。</span><span class="sxs-lookup"><span data-stu-id="76557-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="76557-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="76557-117">PacketRoutable</span></span>  
 <span data-ttu-id="76557-118">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="76557-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="76557-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="76557-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="76557-120">パケットがルーティング可能かどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="76557-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76557-121">要件</span><span class="sxs-lookup"><span data-stu-id="76557-121">Requirements</span></span>  
  
|<span data-ttu-id="76557-122">MOF</span><span class="sxs-lookup"><span data-stu-id="76557-122">MOF</span></span>|<span data-ttu-id="76557-123">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="76557-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="76557-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="76557-124">Namespace</span></span>|<span data-ttu-id="76557-125">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="76557-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="76557-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="76557-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
