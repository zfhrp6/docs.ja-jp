---
title: Binding2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6553d1e1c030a30eed74ff81d3e07e28a9f25b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="binding"></a><span data-ttu-id="6d6ef-102">バインド</span><span class="sxs-lookup"><span data-stu-id="6d6ef-102">Binding</span></span>
<span data-ttu-id="6d6ef-103">wmi バインディング</span><span class="sxs-lookup"><span data-stu-id="6d6ef-103">wmi Binding</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d6ef-104">構文</span><span class="sxs-lookup"><span data-stu-id="6d6ef-104">Syntax</span></span>  
  
```  
class Binding  
{  
  BindingElement BindingElements[];  
  datetime CloseTimeout;  
  string Name;  
  string Namespace;  
  datetime OpenTimeout;  
  datetime ReceiveTimeout;  
  string Scheme;  
  datetime SendTimeout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6d6ef-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="6d6ef-105">Methods</span></span>  
 <span data-ttu-id="6d6ef-106">Binding クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="6d6ef-106">The Binding class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6d6ef-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="6d6ef-107">Properties</span></span>  
 <span data-ttu-id="6d6ef-108">Binding クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="6d6ef-108">The Binding class has the following properties.</span></span>  
  
### <a name="bindingelements"></a><span data-ttu-id="6d6ef-109">BindingElements</span><span class="sxs-lookup"><span data-stu-id="6d6ef-109">BindingElements</span></span>  
 <span data-ttu-id="6d6ef-110">データ型 : BindingElement 配列</span><span class="sxs-lookup"><span data-stu-id="6d6ef-110">Data type: BindingElement array</span></span>  
  
 <span data-ttu-id="6d6ef-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6d6ef-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d6ef-112">バインディングによって実装されるバインド要素のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="6d6ef-112">The collection of binding elements implemented by the binding.</span></span>  
  
### <a name="closetimeout"></a><span data-ttu-id="6d6ef-113">CloseTimeout</span><span class="sxs-lookup"><span data-stu-id="6d6ef-113">CloseTimeout</span></span>  
 <span data-ttu-id="6d6ef-114">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="6d6ef-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="6d6ef-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6d6ef-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d6ef-116">クローズ操作が完了するまで待機する時間です。</span><span class="sxs-lookup"><span data-stu-id="6d6ef-116">The interval of time provided for a close operation to complete.</span></span>  
  
### <a name="name"></a><span data-ttu-id="6d6ef-117">name</span><span class="sxs-lookup"><span data-stu-id="6d6ef-117">Name</span></span>  
 <span data-ttu-id="6d6ef-118">データ型: string</span><span class="sxs-lookup"><span data-stu-id="6d6ef-118">Data type: string</span></span>  
  
 <span data-ttu-id="6d6ef-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6d6ef-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d6ef-120">バインディングの名前。</span><span class="sxs-lookup"><span data-stu-id="6d6ef-120">The name of the binding.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="6d6ef-121">名前空間</span><span class="sxs-lookup"><span data-stu-id="6d6ef-121">Namespace</span></span>  
 <span data-ttu-id="6d6ef-122">データ型: string</span><span class="sxs-lookup"><span data-stu-id="6d6ef-122">Data type: string</span></span>  
  
 <span data-ttu-id="6d6ef-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6d6ef-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d6ef-124">バインディングの XML 名前空間。</span><span class="sxs-lookup"><span data-stu-id="6d6ef-124">The XML namespace of the binding.</span></span>  
  
### <a name="opentimeout"></a><span data-ttu-id="6d6ef-125">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="6d6ef-125">OpenTimeout</span></span>  
 <span data-ttu-id="6d6ef-126">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="6d6ef-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="6d6ef-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6d6ef-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d6ef-128">オープン操作が完了するまで待機する時間です。</span><span class="sxs-lookup"><span data-stu-id="6d6ef-128">The interval of time provided for an open operation to complete.</span></span>  
  
### <a name="receivetimeout"></a><span data-ttu-id="6d6ef-129">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="6d6ef-129">ReceiveTimeout</span></span>  
 <span data-ttu-id="6d6ef-130">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="6d6ef-130">Data type: datetime</span></span>  
  
 <span data-ttu-id="6d6ef-131">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6d6ef-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d6ef-132">受信操作が完了するまで待機する時間です。</span><span class="sxs-lookup"><span data-stu-id="6d6ef-132">The interval of time provided for a receive operation to complete.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="6d6ef-133">Scheme</span><span class="sxs-lookup"><span data-stu-id="6d6ef-133">Scheme</span></span>  
 <span data-ttu-id="6d6ef-134">データ型: string</span><span class="sxs-lookup"><span data-stu-id="6d6ef-134">Data type: string</span></span>  
  
 <span data-ttu-id="6d6ef-135">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6d6ef-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d6ef-136">このバインディングに組み込まれているチャネルおよびリスナー ファクトリによって使用される URI トランスポート スキームです。</span><span class="sxs-lookup"><span data-stu-id="6d6ef-136">The URI transport scheme that is used by the channel and listener factories that are built by the binding.</span></span>  
  
### <a name="sendtimeout"></a><span data-ttu-id="6d6ef-137">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="6d6ef-137">SendTimeout</span></span>  
 <span data-ttu-id="6d6ef-138">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="6d6ef-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="6d6ef-139">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6d6ef-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d6ef-140">送信操作が完了するまで待機する時間です。</span><span class="sxs-lookup"><span data-stu-id="6d6ef-140">The interval of time provided for a send operation to complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d6ef-141">必要条件</span><span class="sxs-lookup"><span data-stu-id="6d6ef-141">Requirements</span></span>  
  
|<span data-ttu-id="6d6ef-142">MOF</span><span class="sxs-lookup"><span data-stu-id="6d6ef-142">MOF</span></span>|<span data-ttu-id="6d6ef-143">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="6d6ef-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6d6ef-144">Namespace</span><span class="sxs-lookup"><span data-stu-id="6d6ef-144">Namespace</span></span>|<span data-ttu-id="6d6ef-145">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="6d6ef-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6d6ef-146">参照</span><span class="sxs-lookup"><span data-stu-id="6d6ef-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>
