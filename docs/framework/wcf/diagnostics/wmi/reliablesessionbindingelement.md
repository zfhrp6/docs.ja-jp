---
title: ReliableSessionBindingElement
ms.date: 03/30/2017
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
ms.openlocfilehash: 2f04e6794342d7bd0acd51481efcbeceb04fd459
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="reliablesessionbindingelement"></a><span data-ttu-id="bb0d8-102">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="bb0d8-102">ReliableSessionBindingElement</span></span>
<span data-ttu-id="bb0d8-103">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="bb0d8-103">ReliableSessionBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb0d8-104">構文</span><span class="sxs-lookup"><span data-stu-id="bb0d8-104">Syntax</span></span>  
  
```  
class ReliableSessionBindingElement : BindingElement  
{  
  datetime AcknowledgementInterval;  
  boolean FlowControlEnabled;  
  datetime InactivityTimeout;  
  sint32 MaxPendingChannels;  
  sint32 MaxRetryCount;  
  sint32 MaxTransferWindowSize;  
  boolean Ordered;  
  integer ReliableMessagingVersion;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="bb0d8-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="bb0d8-105">Methods</span></span>  
 <span data-ttu-id="bb0d8-106">ReliableSessionBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="bb0d8-106">The ReliableSessionBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="bb0d8-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="bb0d8-107">Properties</span></span>  
 <span data-ttu-id="bb0d8-108">ReliableSessionBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="bb0d8-108">The ReliableSessionBindingElement class has the following properties:</span></span>  
  
### <a name="acknowledgementinterval"></a><span data-ttu-id="bb0d8-109">AcknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="bb0d8-109">AcknowledgementInterval</span></span>  
 <span data-ttu-id="bb0d8-110">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="bb0d8-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="bb0d8-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="bb0d8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bb0d8-112">ファクトリによって作成された信頼できるチャネルで、メッセージの送信元に受信確認を送信するまで送信先が待機する時間</span><span class="sxs-lookup"><span data-stu-id="bb0d8-112">The interval of time that a destination waits before sending an acknowledgement to the message source on reliable channels that are created by the factory.</span></span>  
  
### <a name="flowcontrolenabled"></a><span data-ttu-id="bb0d8-113">FlowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="bb0d8-113">FlowControlEnabled</span></span>  
 <span data-ttu-id="bb0d8-114">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="bb0d8-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="bb0d8-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="bb0d8-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bb0d8-116">フロー制御を有効にするかどうかを示すブール値</span><span class="sxs-lookup"><span data-stu-id="bb0d8-116">A Boolean value that specifies whether flow control is enabled.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="bb0d8-117">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="bb0d8-117">InactivityTimeout</span></span>  
 <span data-ttu-id="bb0d8-118">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="bb0d8-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="bb0d8-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="bb0d8-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bb0d8-120">他の通信相手がチャネルにメッセージを送信せずにいられる最長期間を指定します。他の通信相手がメッセージを送信しない期間がこの値を超えると、チャネルでエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="bb0d8-120">Specifies the maximum duration the channel is going to allow the other communicating party not to send any messages before faulting the channel.</span></span>  
  
### <a name="maxpendingchannels"></a><span data-ttu-id="bb0d8-121">MaxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="bb0d8-121">MaxPendingChannels</span></span>  
 <span data-ttu-id="bb0d8-122">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="bb0d8-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="bb0d8-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="bb0d8-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bb0d8-124">リスナーで受け入れを待機できるチャネルの最大数。</span><span class="sxs-lookup"><span data-stu-id="bb0d8-124">The maximum number of channels that can wait to be accepted on the listener.</span></span>  
  
### <a name="maxretrycount"></a><span data-ttu-id="bb0d8-125">MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="bb0d8-125">MaxRetryCount</span></span>  
 <span data-ttu-id="bb0d8-126">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="bb0d8-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="bb0d8-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="bb0d8-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bb0d8-128">基になるチャネルで `Send` を呼び出すことで、信頼できるチャネルが受信確認を受信していないメッセージの再転送を試みる最大回数</span><span class="sxs-lookup"><span data-stu-id="bb0d8-128">The maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgement for, by calling `Send` on its underlying channel.</span></span>  
  
### <a name="maxtransferwindowsize"></a><span data-ttu-id="bb0d8-129">MaxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="bb0d8-129">MaxTransferWindowSize</span></span>  
 <span data-ttu-id="bb0d8-130">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="bb0d8-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="bb0d8-131">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="bb0d8-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bb0d8-132">信頼できるセッションの転送ウィンドウの最大サイズ</span><span class="sxs-lookup"><span data-stu-id="bb0d8-132">The maximum transfer window size for the reliable session.</span></span>  
  
### <a name="ordered"></a><span data-ttu-id="bb0d8-133">順序あり</span><span class="sxs-lookup"><span data-stu-id="bb0d8-133">Ordered</span></span>  
 <span data-ttu-id="bb0d8-134">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="bb0d8-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="bb0d8-135">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="bb0d8-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bb0d8-136">メッセージが送信された順序で到着されることを保証するかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="bb0d8-136">A Boolean value that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span>  
  
### <a name="reliablemessagingversion"></a><span data-ttu-id="bb0d8-137">ReliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="bb0d8-137">ReliableMessagingVersion</span></span>  
 <span data-ttu-id="bb0d8-138">データ型 : integer</span><span class="sxs-lookup"><span data-stu-id="bb0d8-138">Data type: integer</span></span>  
  
 <span data-ttu-id="bb0d8-139">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="bb0d8-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bb0d8-140">信頼できるセッションで使用される WS-ReliableMessaging プロトコルのバージョンを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="bb0d8-140">An integer that specifies the WS-ReliableMessaging protocol version used in the reliable session.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb0d8-141">要件</span><span class="sxs-lookup"><span data-stu-id="bb0d8-141">Requirements</span></span>  
  
|<span data-ttu-id="bb0d8-142">MOF</span><span class="sxs-lookup"><span data-stu-id="bb0d8-142">MOF</span></span>|<span data-ttu-id="bb0d8-143">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="bb0d8-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="bb0d8-144">Namespace</span><span class="sxs-lookup"><span data-stu-id="bb0d8-144">Namespace</span></span>|<span data-ttu-id="bb0d8-145">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="bb0d8-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bb0d8-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb0d8-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
