---
title: AsymmetricSecurityBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 82e5365a440d103727f354e682d0ebecb5f46a46
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="a3e67-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="a3e67-102">AsymmetricSecurityBindingElement</span></span>
<span data-ttu-id="a3e67-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="a3e67-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3e67-104">構文</span><span class="sxs-lookup"><span data-stu-id="a3e67-104">Syntax</span></span>  
  
```  
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a3e67-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a3e67-105">Methods</span></span>  
 <span data-ttu-id="a3e67-106">AsymmetricSecurityBindingElement クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="a3e67-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a3e67-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="a3e67-107">Properties</span></span>  
 <span data-ttu-id="a3e67-108">AsymmetricSecurityBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="a3e67-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="a3e67-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="a3e67-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="a3e67-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="a3e67-110">Data type: string</span></span>  
  
 <span data-ttu-id="a3e67-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="a3e67-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a3e67-112">このバインディングのメッセージの暗号化と署名の命令。</span><span class="sxs-lookup"><span data-stu-id="a3e67-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="a3e67-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="a3e67-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="a3e67-114">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="a3e67-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="a3e67-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="a3e67-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a3e67-116">バインディングで署名の確認が必要かどうか。</span><span class="sxs-lookup"><span data-stu-id="a3e67-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3e67-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="a3e67-117">Requirements</span></span>  
  
|<span data-ttu-id="a3e67-118">MOF</span><span class="sxs-lookup"><span data-stu-id="a3e67-118">MOF</span></span>|<span data-ttu-id="a3e67-119">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="a3e67-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a3e67-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="a3e67-120">Namespace</span></span>|<span data-ttu-id="a3e67-121">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="a3e67-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a3e67-122">参照</span><span class="sxs-lookup"><span data-stu-id="a3e67-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
