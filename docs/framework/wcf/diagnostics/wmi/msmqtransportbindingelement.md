---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 643ab0f30c771f79df8ef7dd885013d5186fba59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485909"
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="423df-102">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="423df-102">MsmqTransportBindingElement</span></span>
<span data-ttu-id="423df-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="423df-103">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="423df-104">構文</span><span class="sxs-lookup"><span data-stu-id="423df-104">Syntax</span></span>  
  
```  
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="423df-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="423df-105">Methods</span></span>  
 <span data-ttu-id="423df-106">MsmqTransportBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="423df-106">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="423df-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="423df-107">Properties</span></span>  
 <span data-ttu-id="423df-108">MsmqTransportBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="423df-108">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="423df-109">MaxPoolSize</span><span class="sxs-lookup"><span data-stu-id="423df-109">MaxPoolSize</span></span>  
 <span data-ttu-id="423df-110">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="423df-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="423df-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="423df-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="423df-112">内部 MSMQ メッセージ オブジェクトを含むプールの最大サイズです。</span><span class="sxs-lookup"><span data-stu-id="423df-112">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="423df-113">QueueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="423df-113">QueueTransferProtocol</span></span>  
 <span data-ttu-id="423df-114">データ型: string</span><span class="sxs-lookup"><span data-stu-id="423df-114">Data type: string</span></span>  
  
 <span data-ttu-id="423df-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="423df-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="423df-116">このバインディングが使用するキューに置かれた通信チャネルのトランスポートを示す列挙値です。</span><span class="sxs-lookup"><span data-stu-id="423df-116">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="423df-117">UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="423df-117">UseActiveDirectory</span></span>  
 <span data-ttu-id="423df-118">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="423df-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="423df-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="423df-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="423df-120">キューのアドレスを Active Directory を使用して変換する必要があるかどうかを示すブール値を返します。</span><span class="sxs-lookup"><span data-stu-id="423df-120">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="423df-121">要件</span><span class="sxs-lookup"><span data-stu-id="423df-121">Requirements</span></span>  
  
|<span data-ttu-id="423df-122">MOF</span><span class="sxs-lookup"><span data-stu-id="423df-122">MOF</span></span>|<span data-ttu-id="423df-123">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="423df-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="423df-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="423df-124">Namespace</span></span>|<span data-ttu-id="423df-125">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="423df-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="423df-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="423df-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
