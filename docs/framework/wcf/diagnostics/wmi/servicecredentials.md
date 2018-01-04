---
title: ServiceCredentials
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 73fad36b5bf14745ca70d297fa988b90d46990df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="servicecredentials"></a><span data-ttu-id="3bc70-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="3bc70-102">ServiceCredentials</span></span>
<span data-ttu-id="3bc70-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="3bc70-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bc70-104">構文</span><span class="sxs-lookup"><span data-stu-id="3bc70-104">Syntax</span></span>  
  
```  
class ServiceCredentials : Behavior  
{  
  string ClientCertificate;  
  string IssuedTokenAuthentication;  
  string Peer;  
  string SecureConversationAuthentication;  
  string ServiceCertificate;  
  string UserNameAuthentication;  
  string WindowsAuthentication;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3bc70-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="3bc70-105">Methods</span></span>  
 <span data-ttu-id="3bc70-106">ServiceCredentials クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="3bc70-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3bc70-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="3bc70-107">Properties</span></span>  
 <span data-ttu-id="3bc70-108">ServiceCredentials クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="3bc70-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="3bc70-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="3bc70-109">ClientCertificate</span></span>  
 <span data-ttu-id="3bc70-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="3bc70-110">Data type: string</span></span>  
  
 <span data-ttu-id="3bc70-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3bc70-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3bc70-112">このサービスのための、クライアント証明認証および提供設定です。</span><span class="sxs-lookup"><span data-stu-id="3bc70-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="3bc70-113">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="3bc70-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="3bc70-114">データ型: string</span><span class="sxs-lookup"><span data-stu-id="3bc70-114">Data type: string</span></span>  
  
 <span data-ttu-id="3bc70-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3bc70-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3bc70-116">このサービスのための、現在発行されているトークンの認証設定です。</span><span class="sxs-lookup"><span data-stu-id="3bc70-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="3bc70-117">Peer</span><span class="sxs-lookup"><span data-stu-id="3bc70-117">Peer</span></span>  
 <span data-ttu-id="3bc70-118">データ型: string</span><span class="sxs-lookup"><span data-stu-id="3bc70-118">Data type: string</span></span>  
  
 <span data-ttu-id="3bc70-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3bc70-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3bc70-120">ピアのトランスポート エンドポイントによって使用される、現在の証明書の認証および提供の設定です。</span><span class="sxs-lookup"><span data-stu-id="3bc70-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="3bc70-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="3bc70-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="3bc70-122">データ型: string</span><span class="sxs-lookup"><span data-stu-id="3bc70-122">Data type: string</span></span>  
  
 <span data-ttu-id="3bc70-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3bc70-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3bc70-124">現在のセキュリティで保護された通信の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="3bc70-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="3bc70-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="3bc70-125">ServiceCertificate</span></span>  
 <span data-ttu-id="3bc70-126">データ型: string</span><span class="sxs-lookup"><span data-stu-id="3bc70-126">Data type: string</span></span>  
  
 <span data-ttu-id="3bc70-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3bc70-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3bc70-128">このサービスに関連付けられている証明書です。</span><span class="sxs-lookup"><span data-stu-id="3bc70-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="3bc70-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="3bc70-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="3bc70-130">データ型: string</span><span class="sxs-lookup"><span data-stu-id="3bc70-130">Data type: string</span></span>  
  
 <span data-ttu-id="3bc70-131">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3bc70-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3bc70-132">このサービスのユーザー名/パスワードの設定です。</span><span class="sxs-lookup"><span data-stu-id="3bc70-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="3bc70-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="3bc70-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="3bc70-134">データ型: string</span><span class="sxs-lookup"><span data-stu-id="3bc70-134">Data type: string</span></span>  
  
 <span data-ttu-id="3bc70-135">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3bc70-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3bc70-136">このサービスの Windows 認証の設定です。</span><span class="sxs-lookup"><span data-stu-id="3bc70-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bc70-137">必要条件</span><span class="sxs-lookup"><span data-stu-id="3bc70-137">Requirements</span></span>  
  
|<span data-ttu-id="3bc70-138">MOF</span><span class="sxs-lookup"><span data-stu-id="3bc70-138">MOF</span></span>|<span data-ttu-id="3bc70-139">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="3bc70-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3bc70-140">Namespace</span><span class="sxs-lookup"><span data-stu-id="3bc70-140">Namespace</span></span>|<span data-ttu-id="3bc70-141">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="3bc70-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3bc70-142">参照</span><span class="sxs-lookup"><span data-stu-id="3bc70-142">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceCredentials>
