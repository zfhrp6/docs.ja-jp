---
title: ServiceAppDomain
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 36048f56c3b54447a112e6f0a457624062ce965a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="serviceappdomain"></a><span data-ttu-id="186e2-102">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="186e2-102">ServiceAppDomain</span></span>
<span data-ttu-id="186e2-103">アプリケーション ドメインにサービスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="186e2-103">Maps a service to an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="186e2-104">構文</span><span class="sxs-lookup"><span data-stu-id="186e2-104">Syntax</span></span>  
  
```  
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="186e2-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="186e2-105">Methods</span></span>  
 <span data-ttu-id="186e2-106">ServiceAppDomain クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="186e2-106">The ServiceAppDomain class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="186e2-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="186e2-107">Properties</span></span>  
 <span data-ttu-id="186e2-108">ServiceAppDomain クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="186e2-108">The ServiceAppDomain class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="186e2-109">ref</span><span class="sxs-lookup"><span data-stu-id="186e2-109">ref</span></span>  
 <span data-ttu-id="186e2-110">データ型 : Service</span><span class="sxs-lookup"><span data-stu-id="186e2-110">Data type: Service</span></span>  
<span data-ttu-id="186e2-111">修飾子: キー</span><span class="sxs-lookup"><span data-stu-id="186e2-111">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="186e2-112">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="186e2-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="186e2-113">このアプリケーション ドメインのサービスです。</span><span class="sxs-lookup"><span data-stu-id="186e2-113">The service of this application domain.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="186e2-114">ref</span><span class="sxs-lookup"><span data-stu-id="186e2-114">ref</span></span>  
 <span data-ttu-id="186e2-115">データ型: AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="186e2-115">Data type: AppDomainInfo</span></span>  
<span data-ttu-id="186e2-116">修飾子: キー</span><span class="sxs-lookup"><span data-stu-id="186e2-116">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="186e2-117">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="186e2-117">Access type: Read-only</span></span>  
  
 <span data-ttu-id="186e2-118">アプリケーション ドメインのプロパティが格納されています。</span><span class="sxs-lookup"><span data-stu-id="186e2-118">Contains properties of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="186e2-119">要件</span><span class="sxs-lookup"><span data-stu-id="186e2-119">Requirements</span></span>  
  
|<span data-ttu-id="186e2-120">MOF</span><span class="sxs-lookup"><span data-stu-id="186e2-120">MOF</span></span>|<span data-ttu-id="186e2-121">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="186e2-121">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="186e2-122">Namespace</span><span class="sxs-lookup"><span data-stu-id="186e2-122">Namespace</span></span>|<span data-ttu-id="186e2-123">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="186e2-123">Defined in root\ServiceModel</span></span>|
