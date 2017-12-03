---
title: ServiceDebugBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c829f68fe994b47fe880febb4d3ac2020fde2d1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="f5346-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="f5346-102">ServiceDebugBehavior</span></span>
<span data-ttu-id="f5346-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="f5346-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5346-104">構文</span><span class="sxs-lookup"><span data-stu-id="f5346-104">Syntax</span></span>  
  
```  
class ServiceDebugBehavior : Behavior  
{  
  boolean HttpHelpPageEnabled;  
  string HttpHelpPageUrl;  
  boolean HttpsHelpPageEnabled;  
  string HttpsHelpPageUrl;  
  boolean IncludeExceptionDetailInFaults;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f5346-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="f5346-105">Methods</span></span>  
 <span data-ttu-id="f5346-106">ServiceDebugBehavior クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="f5346-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f5346-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f5346-107">Properties</span></span>  
 <span data-ttu-id="f5346-108">ServiceDebugBehavior クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="f5346-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="f5346-109">HttpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="f5346-109">HttpHelpPageEnabled</span></span>  
 <span data-ttu-id="f5346-110">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="f5346-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="f5346-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="f5346-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f5346-112">`HttpGetUrl` 属性によって制御されるアドレスで、サービスが WSDL を公開するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="f5346-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="f5346-113">HttpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="f5346-113">HttpHelpPageUrl</span></span>  
 <span data-ttu-id="f5346-114">データ型: string</span><span class="sxs-lookup"><span data-stu-id="f5346-114">Data type: string</span></span>  
  
 <span data-ttu-id="f5346-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="f5346-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f5346-116">HTTP を使用した取得のために、サービス WSDL が公開される場所を設定します。</span><span class="sxs-lookup"><span data-stu-id="f5346-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="f5346-117">HttpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="f5346-117">HttpsHelpPageEnabled</span></span>  
 <span data-ttu-id="f5346-118">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="f5346-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="f5346-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="f5346-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f5346-120">`HttpsGetUrl` 属性によって制御されるアドレスで、サービスが HTTPS を介して WSDL を公開するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="f5346-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="f5346-121">HttpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="f5346-121">HttpsHelpPageUrl</span></span>  
 <span data-ttu-id="f5346-122">データ型: string</span><span class="sxs-lookup"><span data-stu-id="f5346-122">Data type: string</span></span>  
  
 <span data-ttu-id="f5346-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="f5346-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f5346-124">HTTPS を使用した取得のために、サービス WSDL が公開される場所を設定します。</span><span class="sxs-lookup"><span data-stu-id="f5346-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="f5346-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="f5346-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="f5346-126">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="f5346-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="f5346-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="f5346-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f5346-128">デバッグの目的でクライアントに返される SOAP エラーの詳細に、マネージ例外情報を含めるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f5346-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5346-129">要件</span><span class="sxs-lookup"><span data-stu-id="f5346-129">Requirements</span></span>  
  
|<span data-ttu-id="f5346-130">MOF</span><span class="sxs-lookup"><span data-stu-id="f5346-130">MOF</span></span>|<span data-ttu-id="f5346-131">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="f5346-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f5346-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="f5346-132">Namespace</span></span>|<span data-ttu-id="f5346-133">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="f5346-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f5346-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5346-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>
