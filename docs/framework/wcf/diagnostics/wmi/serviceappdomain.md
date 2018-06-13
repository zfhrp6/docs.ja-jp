---
title: ServiceAppDomain
ms.date: 03/30/2017
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
ms.openlocfilehash: aef0a0da9d107b92d9d3017968d5554205a6fd71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485669"
---
# <a name="serviceappdomain"></a><span data-ttu-id="ef527-102">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="ef527-102">ServiceAppDomain</span></span>
<span data-ttu-id="ef527-103">アプリケーション ドメインにサービスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="ef527-103">Maps a service to an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef527-104">構文</span><span class="sxs-lookup"><span data-stu-id="ef527-104">Syntax</span></span>  
  
```  
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ef527-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="ef527-105">Methods</span></span>  
 <span data-ttu-id="ef527-106">ServiceAppDomain クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="ef527-106">The ServiceAppDomain class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ef527-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ef527-107">Properties</span></span>  
 <span data-ttu-id="ef527-108">ServiceAppDomain クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="ef527-108">The ServiceAppDomain class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="ef527-109">ref</span><span class="sxs-lookup"><span data-stu-id="ef527-109">ref</span></span>  
 <span data-ttu-id="ef527-110">データ型 : Service</span><span class="sxs-lookup"><span data-stu-id="ef527-110">Data type: Service</span></span>  
<span data-ttu-id="ef527-111">修飾子: キー</span><span class="sxs-lookup"><span data-stu-id="ef527-111">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="ef527-112">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ef527-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef527-113">このアプリケーション ドメインのサービスです。</span><span class="sxs-lookup"><span data-stu-id="ef527-113">The service of this application domain.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="ef527-114">ref</span><span class="sxs-lookup"><span data-stu-id="ef527-114">ref</span></span>  
 <span data-ttu-id="ef527-115">データ型: AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="ef527-115">Data type: AppDomainInfo</span></span>  
<span data-ttu-id="ef527-116">修飾子: キー</span><span class="sxs-lookup"><span data-stu-id="ef527-116">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="ef527-117">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ef527-117">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef527-118">アプリケーション ドメインのプロパティが格納されています。</span><span class="sxs-lookup"><span data-stu-id="ef527-118">Contains properties of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef527-119">要件</span><span class="sxs-lookup"><span data-stu-id="ef527-119">Requirements</span></span>  
  
|<span data-ttu-id="ef527-120">MOF</span><span class="sxs-lookup"><span data-stu-id="ef527-120">MOF</span></span>|<span data-ttu-id="ef527-121">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="ef527-121">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ef527-122">Namespace</span><span class="sxs-lookup"><span data-stu-id="ef527-122">Namespace</span></span>|<span data-ttu-id="ef527-123">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="ef527-123">Defined in root\ServiceModel</span></span>|
