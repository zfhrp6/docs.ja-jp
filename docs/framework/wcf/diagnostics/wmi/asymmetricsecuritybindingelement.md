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
ms.openlocfilehash: 104810fc24cfe7c4c6ddf7ee5ece9f16a345c80c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="51432-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="51432-102">AsymmetricSecurityBindingElement</span></span>
<span data-ttu-id="51432-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="51432-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51432-104">構文</span><span class="sxs-lookup"><span data-stu-id="51432-104">Syntax</span></span>  
  
```  
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="51432-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="51432-105">Methods</span></span>  
 <span data-ttu-id="51432-106">AsymmetricSecurityBindingElement クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="51432-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="51432-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="51432-107">Properties</span></span>  
 <span data-ttu-id="51432-108">AsymmetricSecurityBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="51432-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="51432-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="51432-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="51432-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="51432-110">Data type: string</span></span>  
  
 <span data-ttu-id="51432-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="51432-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51432-112">このバインディングのメッセージの暗号化と署名の命令。</span><span class="sxs-lookup"><span data-stu-id="51432-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="51432-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="51432-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="51432-114">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="51432-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="51432-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="51432-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51432-116">バインディングで署名の確認が必要かどうか。</span><span class="sxs-lookup"><span data-stu-id="51432-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51432-117">要件</span><span class="sxs-lookup"><span data-stu-id="51432-117">Requirements</span></span>  
  
|<span data-ttu-id="51432-118">MOF</span><span class="sxs-lookup"><span data-stu-id="51432-118">MOF</span></span>|<span data-ttu-id="51432-119">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="51432-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="51432-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="51432-120">Namespace</span></span>|<span data-ttu-id="51432-121">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="51432-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="51432-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="51432-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
