---
title: ServiceMetadataBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9d10fdd9e33b078fa392e0ef359372913f9ba133
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="030ac-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="030ac-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="030ac-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="030ac-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="030ac-104">構文</span><span class="sxs-lookup"><span data-stu-id="030ac-104">Syntax</span></span>  
  
```  
class ServiceMetadataBehavior : Behavior  
{  
  string ExternalMetadataLocation;  
  boolean HttpGetEnabled;  
  string HttpGetUrl;  
  boolean HttpsGetEnabled;  
  string HttpsGetUrl;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="030ac-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="030ac-105">Methods</span></span>  
 <span data-ttu-id="030ac-106">ServiceMetadataBehavior クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="030ac-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="030ac-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="030ac-107">Properties</span></span>  
 <span data-ttu-id="030ac-108">ServiceMetadataBehavior クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="030ac-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="030ac-109">ExternalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="030ac-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="030ac-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="030ac-110">Data type: string</span></span>  
  
 <span data-ttu-id="030ac-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="030ac-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="030ac-112">サービスがメタデータ要求をリダイレクトする場所を設定します。</span><span class="sxs-lookup"><span data-stu-id="030ac-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="030ac-113">HttpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="030ac-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="030ac-114">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="030ac-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="030ac-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="030ac-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="030ac-116">`HttpGetUrl` 属性によって制御されるアドレスで、サービスが WSDL を公開するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="030ac-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="030ac-117">HttpGetUrl</span><span class="sxs-lookup"><span data-stu-id="030ac-117">HttpGetUrl</span></span>  
 <span data-ttu-id="030ac-118">データ型: string</span><span class="sxs-lookup"><span data-stu-id="030ac-118">Data type: string</span></span>  
  
 <span data-ttu-id="030ac-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="030ac-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="030ac-120">HTTP を使用した取得のために、サービス WSDL が公開される場所を設定します。</span><span class="sxs-lookup"><span data-stu-id="030ac-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="030ac-121">HttpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="030ac-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="030ac-122">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="030ac-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="030ac-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="030ac-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="030ac-124">`HttpsGetUrl` 属性によって制御されるアドレスで、サービスが HTTPS を介して WSDL を公開するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="030ac-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="030ac-125">HttpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="030ac-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="030ac-126">データ型: string</span><span class="sxs-lookup"><span data-stu-id="030ac-126">Data type: string</span></span>  
  
 <span data-ttu-id="030ac-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="030ac-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="030ac-128">HTTPS を使用した取得のために、サービス WSDL が公開される場所を設定します。</span><span class="sxs-lookup"><span data-stu-id="030ac-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="030ac-129">要件</span><span class="sxs-lookup"><span data-stu-id="030ac-129">Requirements</span></span>  
  
|<span data-ttu-id="030ac-130">MOF</span><span class="sxs-lookup"><span data-stu-id="030ac-130">MOF</span></span>|<span data-ttu-id="030ac-131">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="030ac-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="030ac-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="030ac-132">Namespace</span></span>|<span data-ttu-id="030ac-133">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="030ac-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="030ac-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="030ac-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
