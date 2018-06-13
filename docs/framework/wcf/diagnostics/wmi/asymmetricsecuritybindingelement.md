---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 09bfaa3ab4f2aceb3e80644953a87686fca9830c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33484363"
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="87536-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="87536-102">AsymmetricSecurityBindingElement</span></span>
<span data-ttu-id="87536-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="87536-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87536-104">構文</span><span class="sxs-lookup"><span data-stu-id="87536-104">Syntax</span></span>  
  
```  
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="87536-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="87536-105">Methods</span></span>  
 <span data-ttu-id="87536-106">AsymmetricSecurityBindingElement クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="87536-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="87536-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="87536-107">Properties</span></span>  
 <span data-ttu-id="87536-108">AsymmetricSecurityBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="87536-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="87536-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="87536-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="87536-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="87536-110">Data type: string</span></span>  
  
 <span data-ttu-id="87536-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="87536-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="87536-112">このバインディングのメッセージの暗号化と署名の命令。</span><span class="sxs-lookup"><span data-stu-id="87536-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="87536-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="87536-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="87536-114">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="87536-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="87536-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="87536-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="87536-116">バインディングで署名の確認が必要かどうか。</span><span class="sxs-lookup"><span data-stu-id="87536-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87536-117">要件</span><span class="sxs-lookup"><span data-stu-id="87536-117">Requirements</span></span>  
  
|<span data-ttu-id="87536-118">MOF</span><span class="sxs-lookup"><span data-stu-id="87536-118">MOF</span></span>|<span data-ttu-id="87536-119">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="87536-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="87536-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="87536-120">Namespace</span></span>|<span data-ttu-id="87536-121">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="87536-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="87536-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="87536-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
