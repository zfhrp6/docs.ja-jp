---
title: ServiceToEndpointAssociation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2d2755294ba02b4d67bd7f62cf020a44525874d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="servicetoendpointassociation"></a><span data-ttu-id="cd100-102">ServiceToEndpointAssociation</span><span class="sxs-lookup"><span data-stu-id="cd100-102">ServiceToEndpointAssociation</span></span>
<span data-ttu-id="cd100-103">エンドポイントにサービスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="cd100-103">Maps a service to an endpoint.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd100-104">構文</span><span class="sxs-lookup"><span data-stu-id="cd100-104">Syntax</span></span>  
  
```  
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="cd100-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="cd100-105">Methods</span></span>  
 <span data-ttu-id="cd100-106">ServiceToEndpointAssociation クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="cd100-106">The ServiceToEndpointAssociation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cd100-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="cd100-107">Properties</span></span>  
 <span data-ttu-id="cd100-108">ServiceToEndpointAssociation クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="cd100-108">The ServiceToEndpointAssociation class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="cd100-109">ref</span><span class="sxs-lookup"><span data-stu-id="cd100-109">ref</span></span>  
 <span data-ttu-id="cd100-110">データ型 : Service</span><span class="sxs-lookup"><span data-stu-id="cd100-110">Data type: Service</span></span>  
  
 <span data-ttu-id="cd100-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="cd100-111">Access type: Read-only</span></span>  
<span data-ttu-id="cd100-112">修飾子: キー</span><span class="sxs-lookup"><span data-stu-id="cd100-112">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="cd100-113">エンドポイントに関連付けられるサービス。</span><span class="sxs-lookup"><span data-stu-id="cd100-113">The service associated with the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="cd100-114">ref</span><span class="sxs-lookup"><span data-stu-id="cd100-114">ref</span></span>  
 <span data-ttu-id="cd100-115">データ型 : Endpoint</span><span class="sxs-lookup"><span data-stu-id="cd100-115">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="cd100-116">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="cd100-116">Access type: Read-only</span></span>  
<span data-ttu-id="cd100-117">修飾子: キー</span><span class="sxs-lookup"><span data-stu-id="cd100-117">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="cd100-118">サービスに関連付けられるエンドポイント。</span><span class="sxs-lookup"><span data-stu-id="cd100-118">The endpoint associated with the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd100-119">要件</span><span class="sxs-lookup"><span data-stu-id="cd100-119">Requirements</span></span>  
  
|<span data-ttu-id="cd100-120">MOF</span><span class="sxs-lookup"><span data-stu-id="cd100-120">MOF</span></span>|<span data-ttu-id="cd100-121">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="cd100-121">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="cd100-122">Namespace</span><span class="sxs-lookup"><span data-stu-id="cd100-122">Namespace</span></span>|<span data-ttu-id="cd100-123">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="cd100-123">Defined in root\ServiceModel</span></span>|
