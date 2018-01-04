---
title: SecurityBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 5de844bc2741768e1b3c53278f20ad4900ffaac1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="securitybindingelement"></a><span data-ttu-id="93ede-102">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="93ede-102">SecurityBindingElement</span></span>
<span data-ttu-id="93ede-103">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="93ede-103">SecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93ede-104">構文</span><span class="sxs-lookup"><span data-stu-id="93ede-104">Syntax</span></span>  
  
```  
class SecurityBindingElement : BindingElement  
{  
  string DefaultAlgorithmSuite;  
  boolean IncludeTimestamp;  
  string KeyEntropyMode;  
  LocalServiceSecuritySettings LocalServiceSecuritySettings;  
  string MessageSecurityVersion;  
  string SecurityHeaderLayout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="93ede-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="93ede-105">Methods</span></span>  
 <span data-ttu-id="93ede-106">SecurityBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="93ede-106">The SecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="93ede-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="93ede-107">Properties</span></span>  
 <span data-ttu-id="93ede-108">SecurityBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="93ede-108">The SecurityBindingElement class has the following properties:</span></span>  
  
### <a name="defaultalgorithmsuite"></a><span data-ttu-id="93ede-109">DefaultAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="93ede-109">DefaultAlgorithmSuite</span></span>  
 <span data-ttu-id="93ede-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="93ede-110">Data type: string</span></span>  
  
 <span data-ttu-id="93ede-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="93ede-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="93ede-112">バインディングで使用するアルゴリズムを指定します。</span><span class="sxs-lookup"><span data-stu-id="93ede-112">Specifies the algorithms to use with the binding.</span></span>  
  
### <a name="includetimestamp"></a><span data-ttu-id="93ede-113">IncludeTimestamp</span><span class="sxs-lookup"><span data-stu-id="93ede-113">IncludeTimestamp</span></span>  
 <span data-ttu-id="93ede-114">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="93ede-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="93ede-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="93ede-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="93ede-116">各メッセージにタイムスタンプが含まれるかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="93ede-116">A Boolean value that specifies whether each message contains a timestamp.</span></span>  
  
### <a name="keyentropymode"></a><span data-ttu-id="93ede-117">KeyEntropyMode</span><span class="sxs-lookup"><span data-stu-id="93ede-117">KeyEntropyMode</span></span>  
 <span data-ttu-id="93ede-118">データ型: string</span><span class="sxs-lookup"><span data-stu-id="93ede-118">Data type: string</span></span>  
  
 <span data-ttu-id="93ede-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="93ede-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="93ede-120">キーの作成に使用されるエントロピのソースです。</span><span class="sxs-lookup"><span data-stu-id="93ede-120">The source of entropy used to create keys.</span></span>  
  
### <a name="localservicesecuritysettings"></a><span data-ttu-id="93ede-121">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="93ede-121">LocalServiceSecuritySettings</span></span>  
 <span data-ttu-id="93ede-122">データ型 : LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="93ede-122">Data type: LocalServiceSecuritySettings</span></span>  
  
 <span data-ttu-id="93ede-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="93ede-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="93ede-124">ローカル サービスに対するバインディング固有のセキュリティ プロパティです。</span><span class="sxs-lookup"><span data-stu-id="93ede-124">The binding specific security properties for the local service.</span></span>  
  
### <a name="messagesecurityversion"></a><span data-ttu-id="93ede-125">MessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="93ede-125">MessageSecurityVersion</span></span>  
 <span data-ttu-id="93ede-126">データ型: string</span><span class="sxs-lookup"><span data-stu-id="93ede-126">Data type: string</span></span>  
  
 <span data-ttu-id="93ede-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="93ede-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="93ede-128">メッセージ セキュリティで使用されるバージョンです。</span><span class="sxs-lookup"><span data-stu-id="93ede-128">The version used for message security.</span></span>  
  
### <a name="securityheaderlayout"></a><span data-ttu-id="93ede-129">SecurityHeaderLayout</span><span class="sxs-lookup"><span data-stu-id="93ede-129">SecurityHeaderLayout</span></span>  
 <span data-ttu-id="93ede-130">データ型: string</span><span class="sxs-lookup"><span data-stu-id="93ede-130">Data type: string</span></span>  
  
 <span data-ttu-id="93ede-131">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="93ede-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="93ede-132">このバインディングのセキュリティ ヘッダー内の要素の順序です。</span><span class="sxs-lookup"><span data-stu-id="93ede-132">The order of elements in the security header for this binding.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93ede-133">要件</span><span class="sxs-lookup"><span data-stu-id="93ede-133">Requirements</span></span>  
  
|<span data-ttu-id="93ede-134">MOF</span><span class="sxs-lookup"><span data-stu-id="93ede-134">MOF</span></span>|<span data-ttu-id="93ede-135">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="93ede-135">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="93ede-136">Namespace</span><span class="sxs-lookup"><span data-stu-id="93ede-136">Namespace</span></span>|<span data-ttu-id="93ede-137">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="93ede-137">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="93ede-138">参照</span><span class="sxs-lookup"><span data-stu-id="93ede-138">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>
