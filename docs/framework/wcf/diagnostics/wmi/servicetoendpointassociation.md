---
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: b1e5b87b053e947432cba9f6e716f7d1ea8f013f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33484330"
---
# <a name="servicetoendpointassociation"></a><span data-ttu-id="61caf-102">ServiceToEndpointAssociation</span><span class="sxs-lookup"><span data-stu-id="61caf-102">ServiceToEndpointAssociation</span></span>
<span data-ttu-id="61caf-103">エンドポイントにサービスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="61caf-103">Maps a service to an endpoint.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61caf-104">構文</span><span class="sxs-lookup"><span data-stu-id="61caf-104">Syntax</span></span>  
  
```  
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="61caf-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="61caf-105">Methods</span></span>  
 <span data-ttu-id="61caf-106">ServiceToEndpointAssociation クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="61caf-106">The ServiceToEndpointAssociation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="61caf-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="61caf-107">Properties</span></span>  
 <span data-ttu-id="61caf-108">ServiceToEndpointAssociation クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="61caf-108">The ServiceToEndpointAssociation class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="61caf-109">ref</span><span class="sxs-lookup"><span data-stu-id="61caf-109">ref</span></span>  
 <span data-ttu-id="61caf-110">データ型 : Service</span><span class="sxs-lookup"><span data-stu-id="61caf-110">Data type: Service</span></span>  
  
 <span data-ttu-id="61caf-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="61caf-111">Access type: Read-only</span></span>  
<span data-ttu-id="61caf-112">修飾子: キー</span><span class="sxs-lookup"><span data-stu-id="61caf-112">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="61caf-113">エンドポイントに関連付けられるサービス。</span><span class="sxs-lookup"><span data-stu-id="61caf-113">The service associated with the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="61caf-114">ref</span><span class="sxs-lookup"><span data-stu-id="61caf-114">ref</span></span>  
 <span data-ttu-id="61caf-115">データ型 : Endpoint</span><span class="sxs-lookup"><span data-stu-id="61caf-115">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="61caf-116">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="61caf-116">Access type: Read-only</span></span>  
<span data-ttu-id="61caf-117">修飾子: キー</span><span class="sxs-lookup"><span data-stu-id="61caf-117">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="61caf-118">サービスに関連付けられるエンドポイント。</span><span class="sxs-lookup"><span data-stu-id="61caf-118">The endpoint associated with the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61caf-119">要件</span><span class="sxs-lookup"><span data-stu-id="61caf-119">Requirements</span></span>  
  
|<span data-ttu-id="61caf-120">MOF</span><span class="sxs-lookup"><span data-stu-id="61caf-120">MOF</span></span>|<span data-ttu-id="61caf-121">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="61caf-121">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="61caf-122">Namespace</span><span class="sxs-lookup"><span data-stu-id="61caf-122">Namespace</span></span>|<span data-ttu-id="61caf-123">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="61caf-123">Defined in root\ServiceModel</span></span>|
