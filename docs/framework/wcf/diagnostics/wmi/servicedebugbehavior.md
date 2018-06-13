---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: 76c4992c5364ed9800e58d120c099aceedb2799c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485682"
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="6844c-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="6844c-102">ServiceDebugBehavior</span></span>
<span data-ttu-id="6844c-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="6844c-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6844c-104">構文</span><span class="sxs-lookup"><span data-stu-id="6844c-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="6844c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="6844c-105">Methods</span></span>  
 <span data-ttu-id="6844c-106">ServiceDebugBehavior クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="6844c-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6844c-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="6844c-107">Properties</span></span>  
 <span data-ttu-id="6844c-108">ServiceDebugBehavior クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="6844c-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="6844c-109">HttpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="6844c-109">HttpHelpPageEnabled</span></span>  
 <span data-ttu-id="6844c-110">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="6844c-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="6844c-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6844c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6844c-112">`HttpGetUrl` 属性によって制御されるアドレスで、サービスが WSDL を公開するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="6844c-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="6844c-113">HttpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="6844c-113">HttpHelpPageUrl</span></span>  
 <span data-ttu-id="6844c-114">データ型: string</span><span class="sxs-lookup"><span data-stu-id="6844c-114">Data type: string</span></span>  
  
 <span data-ttu-id="6844c-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6844c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6844c-116">HTTP を使用した取得のために、サービス WSDL が公開される場所を設定します。</span><span class="sxs-lookup"><span data-stu-id="6844c-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="6844c-117">HttpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="6844c-117">HttpsHelpPageEnabled</span></span>  
 <span data-ttu-id="6844c-118">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="6844c-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="6844c-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6844c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6844c-120">`HttpsGetUrl` 属性によって制御されるアドレスで、サービスが HTTPS を介して WSDL を公開するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="6844c-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="6844c-121">HttpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="6844c-121">HttpsHelpPageUrl</span></span>  
 <span data-ttu-id="6844c-122">データ型: string</span><span class="sxs-lookup"><span data-stu-id="6844c-122">Data type: string</span></span>  
  
 <span data-ttu-id="6844c-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6844c-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6844c-124">HTTPS を使用した取得のために、サービス WSDL が公開される場所を設定します。</span><span class="sxs-lookup"><span data-stu-id="6844c-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="6844c-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="6844c-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="6844c-126">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="6844c-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="6844c-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6844c-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6844c-128">デバッグの目的でクライアントに返される SOAP エラーの詳細に、マネージ例外情報を含めるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="6844c-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6844c-129">要件</span><span class="sxs-lookup"><span data-stu-id="6844c-129">Requirements</span></span>  
  
|<span data-ttu-id="6844c-130">MOF</span><span class="sxs-lookup"><span data-stu-id="6844c-130">MOF</span></span>|<span data-ttu-id="6844c-131">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="6844c-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6844c-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="6844c-132">Namespace</span></span>|<span data-ttu-id="6844c-133">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="6844c-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6844c-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="6844c-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>
