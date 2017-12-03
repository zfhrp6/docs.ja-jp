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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 325497435e24843cc74e804ef38e562617f27167
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="serviceappdomain"></a><span data-ttu-id="dd6ee-102">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="dd6ee-102">ServiceAppDomain</span></span>
<span data-ttu-id="dd6ee-103">アプリケーション ドメインにサービスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-103">Maps a service to an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd6ee-104">構文</span><span class="sxs-lookup"><span data-stu-id="dd6ee-104">Syntax</span></span>  
  
```  
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="dd6ee-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="dd6ee-105">Methods</span></span>  
 <span data-ttu-id="dd6ee-106">ServiceAppDomain クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-106">The ServiceAppDomain class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="dd6ee-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="dd6ee-107">Properties</span></span>  
 <span data-ttu-id="dd6ee-108">ServiceAppDomain クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-108">The ServiceAppDomain class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="dd6ee-109">ref</span><span class="sxs-lookup"><span data-stu-id="dd6ee-109">ref</span></span>  
 <span data-ttu-id="dd6ee-110">データ型 : Service</span><span class="sxs-lookup"><span data-stu-id="dd6ee-110">Data type: Service</span></span>  
<span data-ttu-id="dd6ee-111">修飾子: キー</span><span class="sxs-lookup"><span data-stu-id="dd6ee-111">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="dd6ee-112">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="dd6ee-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dd6ee-113">このアプリケーション ドメインのサービスです。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-113">The service of this application domain.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="dd6ee-114">ref</span><span class="sxs-lookup"><span data-stu-id="dd6ee-114">ref</span></span>  
 <span data-ttu-id="dd6ee-115">データ型: AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="dd6ee-115">Data type: AppDomainInfo</span></span>  
<span data-ttu-id="dd6ee-116">修飾子: キー</span><span class="sxs-lookup"><span data-stu-id="dd6ee-116">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="dd6ee-117">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="dd6ee-117">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dd6ee-118">アプリケーション ドメインのプロパティが格納されています。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-118">Contains properties of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd6ee-119">要件</span><span class="sxs-lookup"><span data-stu-id="dd6ee-119">Requirements</span></span>  
  
|<span data-ttu-id="dd6ee-120">MOF</span><span class="sxs-lookup"><span data-stu-id="dd6ee-120">MOF</span></span>|<span data-ttu-id="dd6ee-121">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="dd6ee-121">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="dd6ee-122">Namespace</span><span class="sxs-lookup"><span data-stu-id="dd6ee-122">Namespace</span></span>|<span data-ttu-id="dd6ee-123">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="dd6ee-123">Defined in root\ServiceModel</span></span>|
