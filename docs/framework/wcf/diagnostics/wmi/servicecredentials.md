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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e4cc9d7d7d46157b7df202c6daffb31b90fa98c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="servicecredentials"></a><span data-ttu-id="48b51-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="48b51-102">ServiceCredentials</span></span>
<span data-ttu-id="48b51-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="48b51-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48b51-104">構文</span><span class="sxs-lookup"><span data-stu-id="48b51-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="48b51-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="48b51-105">Methods</span></span>  
 <span data-ttu-id="48b51-106">ServiceCredentials クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="48b51-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="48b51-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="48b51-107">Properties</span></span>  
 <span data-ttu-id="48b51-108">ServiceCredentials クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="48b51-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="48b51-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="48b51-109">ClientCertificate</span></span>  
 <span data-ttu-id="48b51-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="48b51-110">Data type: string</span></span>  
  
 <span data-ttu-id="48b51-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="48b51-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="48b51-112">このサービスのための、クライアント証明認証および提供設定です。</span><span class="sxs-lookup"><span data-stu-id="48b51-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="48b51-113">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="48b51-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="48b51-114">データ型: string</span><span class="sxs-lookup"><span data-stu-id="48b51-114">Data type: string</span></span>  
  
 <span data-ttu-id="48b51-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="48b51-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="48b51-116">このサービスのための、現在発行されているトークンの認証設定です。</span><span class="sxs-lookup"><span data-stu-id="48b51-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="48b51-117">Peer</span><span class="sxs-lookup"><span data-stu-id="48b51-117">Peer</span></span>  
 <span data-ttu-id="48b51-118">データ型: string</span><span class="sxs-lookup"><span data-stu-id="48b51-118">Data type: string</span></span>  
  
 <span data-ttu-id="48b51-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="48b51-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="48b51-120">ピアのトランスポート エンドポイントによって使用される、現在の証明書の認証および提供の設定です。</span><span class="sxs-lookup"><span data-stu-id="48b51-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="48b51-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="48b51-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="48b51-122">データ型: string</span><span class="sxs-lookup"><span data-stu-id="48b51-122">Data type: string</span></span>  
  
 <span data-ttu-id="48b51-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="48b51-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="48b51-124">現在のセキュリティで保護された通信の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="48b51-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="48b51-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="48b51-125">ServiceCertificate</span></span>  
 <span data-ttu-id="48b51-126">データ型: string</span><span class="sxs-lookup"><span data-stu-id="48b51-126">Data type: string</span></span>  
  
 <span data-ttu-id="48b51-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="48b51-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="48b51-128">このサービスに関連付けられている証明書です。</span><span class="sxs-lookup"><span data-stu-id="48b51-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="48b51-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="48b51-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="48b51-130">データ型: string</span><span class="sxs-lookup"><span data-stu-id="48b51-130">Data type: string</span></span>  
  
 <span data-ttu-id="48b51-131">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="48b51-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="48b51-132">このサービスのユーザー名/パスワードの設定です。</span><span class="sxs-lookup"><span data-stu-id="48b51-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="48b51-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="48b51-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="48b51-134">データ型: string</span><span class="sxs-lookup"><span data-stu-id="48b51-134">Data type: string</span></span>  
  
 <span data-ttu-id="48b51-135">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="48b51-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="48b51-136">このサービスの Windows 認証の設定です。</span><span class="sxs-lookup"><span data-stu-id="48b51-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48b51-137">要件</span><span class="sxs-lookup"><span data-stu-id="48b51-137">Requirements</span></span>  
  
|<span data-ttu-id="48b51-138">MOF</span><span class="sxs-lookup"><span data-stu-id="48b51-138">MOF</span></span>|<span data-ttu-id="48b51-139">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="48b51-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="48b51-140">Namespace</span><span class="sxs-lookup"><span data-stu-id="48b51-140">Namespace</span></span>|<span data-ttu-id="48b51-141">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="48b51-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="48b51-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="48b51-142">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceCredentials>
